# Powershell Auditing Commands

### History of Commands Ran&#x20;

```powershell
Get-Content "$env:UserProfile\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadLine\ConsoleHost_history.txt"
```

### WinEvent Powershell Operations Export to CSV

```powershell
Get-WinEvent -LogName "Microsoft-Windows-PowerShell/Operational" | Select-Object TimeCreated, Message | Export-Csv -Path "PowerShell_Operational_Logs.csv" -NoTypeInformation -Encoding UTF8
```

### Active Network Connections

```powershell
Get-NetTCPConnection | Where-Object { $_.RemoteAddress -match "<Suspicious IP>" }
```

### Find by port

```powershell
Get-NetTCPConnection | Where-Object { $_.RemotePort -eq 443 } | Sort-Object State, RemoteAddress
```

### Search Event Logs

```powershell
Get-WinEvent -LogName Security | Where-Object { $_.Message -match "miner" } | Select-Object TimeCreated, Message
```

### Scheduled Task

```
Get-ScheduledTask | Where-Object { $_.TaskName -match "crypto|xmrig|miner" }
```

### Process Info Sorted by highest

```powershell
Get-Process | Select-Object Name, Id, Path, CPU, StartTime | Sort-Object CPU -Descending
```

### Check for certain name of process

```powershell
Get-Process | Where-Object { $_.Name -match "xmrig" }
```

### Event Logs for Installation

**Event ID 19**: Successful installation of updates.

**Event ID 17**: Updates downloaded but not yet installed.

```powershell
Get-WinEvent -LogName "Microsoft-Windows-WindowsUpdateClient/Operational" | Where-Object { $_.Id -eq 19 } | Select-Object TimeCreated, Message
```

### Find install date for programs

```powershell
Get-ItemProperty -Path "HKLM:\Software\Microsoft\Windows\CurrentVersion\Uninstall\*" | Select-Object DisplayName, DisplayVersion, InstallDate
```
