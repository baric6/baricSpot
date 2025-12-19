# Detection Searches

#### Defender

Defender Detected malware

```
index="<defender index>"
(EventCode=1116 OR EventCode=1160 OR EventCode=1117 OR EventCode=1118)
| rex field=_raw "Name:\s*(?<ThreatName>[^\r\n]+)"
| rex field=_raw "ID:\s*(?<ThreatID>\d+)"
| rex field=_raw "Severity:\s*(?<Severity>\w+)"
| rex field=_raw "Category:\s*(?<Category>[^\r\n]+)"
| rex field=_raw "Path:\s*file:(?<FilePath>[^\r\n]+)"
| rex field=_raw "Detection Origin:\s*(?<DetectionOrigin>[^\r\n]+)"
| rex field=_raw "Detection Type:\s*(?<DetectionType>[^\r\n]+)"
| rex field=_raw "Detection Source:\s*(?<DetectionSource>[^\r\n]+)"
| rex field=_raw "User:\s*(?<DetectedUser>[^\r\n]+)"
| rex field=_raw "Process Name:\s*(?<ProcessName>[^\r\n]+)"
| table _time, DetectedUser, ComputerName, ThreatName, ThreatID, Severity, Category, FilePath, DetectionOrigin, DetectionType, DetectionSource, DetectedUser, ProcessName
```

Detect Defender Tampering

```
index="<defender index>"
(EventCode=5001 OR EventCode=5010 OR EventCode=5012 OR EventCode=5014 OR EventCode=5017 OR EventCode=5019)
| table _time, ComputerName, EventCode, Message, User
| sort -_time
```

#### Machine

Bad Power-shell commands ran endpoint

```
(index=main OR index=sysmon) OR EventCode=4104 OR EventCode=4103

| search (
    "Set-ExecutionPolicy" OR
    "Mimikatz" OR
    "EncodedCommand" OR
    "Payload" OR
    "Find-AVSignature" OR
    "DllInjection" OR
    "ReflectivePEInjection" OR
    "Invoke-Shellcode" OR
    "Invoke — Shellcode" OR
    "Invoke-ShellcodeMSIL" OR
    "Get-GPPPassword" OR
    "Get-Keystrokes" OR
    "Get-TimedScreenshot" OR
    "Get-VaultCredential" OR
    "Invoke-CredentialInjection" OR
    "Invoke-NinjaCopy" OR
    "Invoke-TokenManipulation" OR
    "Out-Minidump" OR
    "Set-MasterBootRecord" OR
    "New-ElevatedPersistenceOption" OR
    "Invoke-CallbackIEX" OR
    "Invoke-PSInjection" OR
    "Invoke-DllEncode" OR
    "Get-ServiceUnquoted" OR
    "Get-ServiceEXEPerms" OR
    "Get-ServicePerms" OR
    "Invoke-ServiceUserAdd" OR
    "Invoke-ServiceCMD" OR
    "Write-UserAddServiceBinary" OR
    "Write-CMDServiceBinary" OR
    "Write-UserAddMSI" OR
    "Write-ServiceEXF"
)
| where Product != "Microsoft Malware Protection"
| where Description != "Microsoft Malware Protection Recovery"
| table _time host user Product Company Description EventCode SourceName CommandLine Message
| sort -_time
```

MSI installed on endpoint

```
index=*
(
    (EventCode=1 AND (Image="*.exe" OR match(CommandLine, "\.msi"))) 
    OR 
    (EventCode=12 AND (TargetObject="*\\Uninstall\\*" OR TargetObject="*WOW6432Node\\Uninstall\\*"))
)
| eval Action=case(
    EventCode=1 AND match(CommandLine, "/i"), "Install",
    EventCode=1 AND match(CommandLine, "/x"), "Uninstall",
    EventCode=1, "Process Execution",
    EventCode=12, "Registry Change"
)
| eval Software=case(
    EventCode=12, replace(TargetObject,"^.*/Uninstall/",""),
    match(CommandLine, "\.msi"), CommandLine,
    EventCode=1, Image
)
| where Action == "Install"
| where NOT match(Software, "(?i)chrome|edge")
| table _time, User, ComputerName, Action, Software, CommandLine, TargetObject
| sort -_time
```

#### Azure&#x20;

Excessive Failed Logins

```
| from datamodel:"Authentication"."Failed_Authentication"
| bin _time span=5m
| stats values(tag) as tag,
        dc(user) as user_count,
        values(user) as users,
        dc(dest) as dest_count,
        count by app, src, _time
| where count >= 6
| iplocation src
| eval Country=coalesce(Country, "Unknown")
| eval State=coalesce(Region, "Unknown")
| eval src=src . " (" . Country . ", " . State . ")"
| table _time app src Country State users user_count dest_count count blacklist_hit
```

Login out of US - Failed

```
| tstats count from datamodel=Authentication.Authentication 
    where Authentication.action="failure" 
    by _time, Authentication.user, Authentication.src, Authentication.app
| rename "Authentication.user" AS user, 
         "Authentication.src" AS src_ip, 
         "Authentication.app" AS app
| iplocation src_ip
| eval Country=coalesce(Country, "Unknown"), 
       State=coalesce(Region, "Unknown")
| lookup abuseipdb_blacklist_lookup ip AS src_ip OUTPUT ip AS blacklist_ip
| eval blacklist_hit=if(isnotnull(blacklist_ip), "Yes", "No")
| eval src=src_ip . " (" . Country . ", " . State . ")" . if(blacklist_hit=="Yes", " [Blacklist]", "")
| where Country!="United States"
| table _time user src app blacklist_hit Country State count
| sort -_time
```
