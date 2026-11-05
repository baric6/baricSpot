# RDP - Server Cert failure changeing the RDP to "Connect and dont warn me" then fails

<figure><img src="../../../.gitbook/assets/image (485).png" alt=""><figcaption></figcaption></figure>

You can go into RDP edit and go into the advanced tab and select "Connect and don't warn me"

<figure><img src="../../../.gitbook/assets/image (486).png" alt=""><figcaption></figcaption></figure>

#### Scripting Way

```powershell
# Sets RDP "If server authentication fails" to "Connect and don't warn me"
# for every user profile under C:\Users (logged in or not),
# plus the Default profile so new users get it on first logon.
# Run elevated or as SYSTEM.
 
$UserFilter = 'C:\Users\*'
$SubKey     = 'Software\Microsoft\Terminal Server Client'
$ValueName  = 'AuthenticationLevelOverride'
$Value      = 0   # 0 = Connect and don't warn, 1 = Do not connect, 2 = Warn me
 
function Set-OfflineHive($hivePath, $label) {
    $temp = "HKU\Temp_$label"
    reg load $temp $hivePath 2>$null | Out-Null
    if ($LASTEXITCODE -ne 0) {
        Write-Warning "Could not load hive: $hivePath"
        return
    }
    reg add "$temp\$SubKey" /v $ValueName /t REG_DWORD /d $Value /f | Out-Null
    [System.GC]::Collect()
    reg unload $temp | Out-Null
    Write-Output "Updated (logged out): $hivePath"
}
 
# Existing profiles
$profiles = Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\ProfileList' |
    Where-Object { (Get-ItemProperty $_.PSPath).ProfileImagePath -like $UserFilter }
 
foreach ($prof in $profiles) {
    $sid  = $prof.PSChildName
    $path = (Get-ItemProperty $prof.PSPath).ProfileImagePath
 
    if (Test-Path "Registry::HKU\$sid") {
        reg add "HKU\$sid\$SubKey" /v $ValueName /t REG_DWORD /d $Value /f | Out-Null
        Write-Output "Updated (logged in):  $path"
    }
    else {
        Set-OfflineHive "$path\NTUSER.DAT" $sid
    }
}
 
# Default profile (applies to users who log on for the first time)
Set-OfflineHive 'C:\Users\Default\NTUSER.DAT' 'DefaultUser'
 
```

#### One-Liner&#x20;

```powershell
gci "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\ProfileList" | ? { (gp $.PSPath).ProfileImagePath -like 'C:\Users\*' } | % { $s=$.PSChildName; $p=(gp $.PSPath).ProfileImagePath; if (Test-Path "Registry::HKU$s") { reg add "HKU$s\Software\Microsoft\Terminal Server Client" /v AuthenticationLevelOverride /t REG_DWORD /d 0 /f } else { reg load "HKU\T$s" "$p\NTUSER.DAT" | Out-Null; reg add "HKU\T_$s\Software\Microsoft\Terminal Server Client" /v AuthenticationLevelOverride /t REG_DWORD /d 0 /f; [gc]::Collect(); reg unload "HKU\T_$s" | Out-Null }; $p }
```
