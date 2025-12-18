# Azure Active Directory Powershell Commands

## Sign In and Out

```
Connect-AzureAD
```

```
Disconnect-AzureAD
```

## Devices

get devices

```
Get-AzureADDevice
```

get devices count

```
(ss  Get-AzureADDevice).count 
```

## Users

search for user

```
Get-AzureADUser -SearchString "Joe"
```
