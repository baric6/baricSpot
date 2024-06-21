# Search Queries

## 0365 Account

### Find Users that logged in out of the US

`m365_default_index sourcetype="o365:management:activity" Workload=AzureActiveDirectory Operation=UserLoginFailed | iplocation ClientIP | search Country!="United States" | table _time UserId LogonError ClientIP Country | rename app AS App UserId AS User ExtendedProperties{}.Value AS Reason ClientIP AS "Client IP" | sort - _time`

### Users who changed passwords

`app=AzureActiveDirectory command="Change user password."`&#x20;









## Exchange

### Malicious Emails zapped

`(index=main OR index=*) sourcetype="o365:management:activity" Workload=SecurityComplianceCenter earliest=-3d latest=now | spath Name | search Name="Email messages containing malicious URL removed after delivery​"`

### User Report Email as Phish or malware

`m365_default_index sourcetype=o365:management:activity Workload=SecurityComplianceCenter Operation=AlertTriggered | dedup AlertId | rex field=Data ""(?[\w\d.-]+@[\w\d.]+)"" | stats count by _time, Severity, Status, email, Name, Comments, Category, AlertType, Data | fields - count | sort -_time`









## SharePoint

### Find city requests count

`(index=main OR index=*) sourcetype="o365:management:activity" Workload=SharePoint | iplocation src | rare limit=40 City`









## Meraki

### Blocked network actions

`host="<meraki link>" action=blocked earliest=-1d latest=now`
