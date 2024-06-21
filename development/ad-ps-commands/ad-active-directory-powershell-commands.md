# ( AD ) Active Directory Powershell Commands

## Get all users by last login

```
Get-ADUser -filter {enabled -eq $true} -Properties * | Select-Object Name, @{N='LastLogon'; E={[DateTime]::FromFileTime($_.LastLogon)}}|Sort-Object LastLogon -Descending
```

```
Get-ADUser -filter * -Properties "LastLogonDate" | select name, LastLogonDate
```

## Get all users password expiration times

```
Get-ADUser -filter {Enabled -eq $True -and PasswordNeverExpires -eq $False} -Properties "DisplayName", "msDS-UserPasswordExpiryTimeComputed"  |Select-Object -Property "Displayname",@{Name="ExpiryDate";Expression={[datetime]::FromFileTime($_."msDS-UserPasswordExpiryTimeComputed")}}
```

## Get one user by email

```
Get-ADUser -Identity "<username>" -Properties "LastLogonDate"
```

Better way to get all users and sort to make a file after propeties add what you want to display also put after select object

```
Get-ADUser -filter {enabled -eq $true} -Properties emailaddress,lastlogondate | Select-Object 	Name,emailaddress,lastlogondate 
```

## Finding accounts that is locked, or disabled

Users on the domain is locked out

```
Search-ADAccount -Locked |Select Name, LockedOut, LastLogonDate
```

Users that has expired account

```
Search-ADAccount -AccountExpired
```

Users that has disabled account

```
Search-ADAccount -AccountDisabled
```

Users that has inactive account

```
Search-ADAccount -AccountInactive
```

All inactive accounts

```
Search-ADAccount -AccountInactive | Where-Object {$_.Enabled -match 'False'} | select Name, LastLogonDate,Enabled 
```

or

```
$InactiveUsers = Get-ADUser -Filter {LastLogonDate -lt ((Get-Date).AddDays(-90))} -SearchBase "DC=$DomainName" -Property Name, LastLogonDate
Write-Host "The following user accounts have been inactive for more than 90 days:"
Foreach ($InactiveUser in $InactiveUsers)
{
    Write-Host $InactiveUser.Name
}
```

## Users

Get when user is created

```
Get-ADUser Toms -Properties whenCreated | Select Name,whenCreated
```

Get user count in hole of Domain

```
(Get-ADUser -filter *).count
```

Get device count

```
(Get-ADComputer -filter *).count
```

Get count disabled users Count

```
(Get-ADUser -LDAPFilter '(userAccountControl:1.2.840.113556.1.4.803:=2)').count
```

Get count enabled users&#x20;

```
a. (Get-ADUser -LDAPFilter '(!userAccountControl:1.2.840.113556.1.4.803:=2)').count
```

```
b. (Get-ADUser -filter "enabled -eq 'true'").count
```

Users that password that never expires count

```
(Search-ADAccount -PasswordNeverExpires | FT Name,ObjectCkass -A).count
```

What Users that password that never expires count

```
(Search-ADAccount -PasswordNeverExpires | FT Name,ObjectCkass -A)
```

Get user last time he changed his password

```
get-aduser -properties pwdlastset | select @{Name="PasswordLastSet";Expression={\[datetime\]::FromFileTimeUTC($_.pwdlastset)}}
```

Find when user changed their password last

```
get-aduser <username> -properties pwdlastset | select @{Name="PasswordLastSet";Expression={\[datetime\]::FromFileTimeUTC($_.pwdlastset)}}
```

```
get-aduser -identity <username> -properties passwordlastset | ft Name, passwordlastset
```

Users after a month of not logging in

```
(Get-ADUser -Filter * -Properties OperatingSystem, LastLogonDate | Where { $_.LastLogonDate -LT (Get-Date).AddDays(-30) }).count
```

Users who clocked in within a month

```
(Get-ADUser -Filter * -Properties OperatingSystem, LastLogonDate | Where { $_.LastLogonDate -GT (Get-Date).AddDays(-30) }).count
```

Get when user accounts was created

```
$When = ((Get-Date).AddDays(-30)).Date
Get-ADUser -Filter {whenCreated -ge $When} -Properties whenCreated
```

### Groups

Finding users who have not changed their password recently - Specops Software Get all users and their groups

```
Get-ADGroup -filter * | Get-ADGroupMember -Recursive | Get-ADUser -Properties * | select Name, MemberOf
```

Get all groups

```
Get-ADGroup -Filter *
```

```
(Get-ADGroup -Filter * ).count
```

```
Get-ADGroup -filter * | select Name
```

Get groups that has no users

```
Get-ADGroup -Filter * -Properties Members | where {-not $_.members} | select Name
```

Find counts of members in all groups

```
Get-ADGroup -Filter * -Properties Member | Select Name,@{n="MemberCount";e={$_.Member.Count}}
```

```
Get-ADGroup -Filter * -Properties Member | Select Name,@{n="MemberCount";e={$_.Member.Count}} | Sort-Object MemberCount
```

Get when AD groups was created

```
$When = ((Get-Date).AddDays(-30)).Date
Get-ADGroup -Filter {whenChanged -ge $When} -Properties whenChanged
```

Get filtered group name

```
Get-ADGroup -Filter {Name -like '*legal*'} | Select-Object Name
```

### Group members

Basic

```
Get-AdGroupMember
```

Get group members by group name and select properties

```
Get-ADGroupMember -Identity Administrators | Select-Object name, objectClass,distinguishedName
```

Get group members by group  scope

```
Get-ADGroup -Filter {GroupScope -eq "DomainLocal"} | Get-ADGroupMember | Select-Object name, objectClass,distinguishedName
```

Get all group members

```
Get-ADGroupMember -Identity "2022 Legal Hold" | Select-Object Name, SamAccountName
```

```
Get-ADGroupMember -Identity 'Enterprise Admins' -Recursive
```

Get group members output grid

```

Get-ADGroupMember -Identity Administrators | Select-Object name, objectClass,distinguishedName | Out-GridView
```

## Devices&#x20;

Get count of what operating system is on the network

```
Get-ADComputer -Filter "name -like '*'" -Properties operatingSystem | group -Property operatingSystem | Select Name,Count
```

Get device names for operating system

```
Get-ADComputer -Filter 'operatingsystem -like "*server*" -and enabled -eq "true"' `
-Properties Name,Operatingsystem,OperatingSystemVersion,IPv4Address |
Sort-Object -Property Operatingsystem |
Select-Object -Property Name,Operatingsystem,OperatingSystemVersion,IPv4Address
```

Get count for computers in searched filter

```
(Get-ADComputer -Filter 'operatingsystem -like "*7*" -and enabled -eq "true"' 
 -Properties Name,Operatingsystem,OperatingSystemVersion,IPv4Address |
 Sort-Object -Property Operatingsystem |
 Select-Object -Property Name,Operatingsystem,OperatingSystemVersion,IPv4Address).count
```

Get count of exact name of computers no wild cards

```
(Get-ADComputer -Filter "OperatingSystem -eq 'Windows 10 Pro'" | ft).count
```

