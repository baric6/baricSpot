# Network Powershell Commands

To flush dns

```
$ ipconfig /flushdns
```

To register new dns

```
$ ipconfig /registerdns
```

Get gpo policy of local pc

```
$ gpresult /r /scope:computer
```

Update gpo policy

```
$ gpupdate /result
```

Network data:

```
$ Get-NetIPConfiguration
```

List all network adapters

```
$ Get-NetAdapter
```

Get adapter by name

```
$ Get-NetAdapter -Name Ethernet
```

Get more data on adapter

```
$ Get-NetAdapter | ft Name, Status, Linkspeed, VlanID
```

Get network driver

```
$ Get-NetAdapter | ft Name, DriverName, DriverVersion, DriverInformation, DriverFileName 
```

Disable and enable network adapter

```
$ Disable-NetAdapter -Name "Wireless Network Connection"
$ Enable-NetAdapter -Name "Wireless Network Connection"
```

Get IP and Dns info

```
$ Get-NetAdapter -Name "Local Area Connection" | Get-NetIPAdapter
```

Ping

```
$ Test-Connection google.com
```

Better command for ping

```
$ Test-NetConnection -ComputerName www.google.com
```

Tracert

```
$ Test-NetConnection www.google.com -TraceRoute
```

NSlookup in powershell

```
$ Resolve-DnsName www.google.com
$ Resolve-DnsName www.google.com Type MX -Server 8.8.8.8
```

Netstat

```
$ Get-NetTCPConnection
$ Get NetTCPConnection -State Established
```

Remove TWINUI through powershell

```
$ Get-AppXPackage | Foreach {Add-AppxPackage -DisableDevelopmentMode - Register "$($_.InstallLocation)\AppXManifest.xml"}
```
