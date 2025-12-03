# SYSMON and Splunk forwarder

#### Download

{% embed url="https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon" %}

Config File

{% file src="../../../../.gitbook/assets/sysmonconfig-export.xml" %}

#### Install

**Sysmon is just a service so running the exe will do nothing you need to run a Power-shell script**

Navigate to the location of the above files easier if they are in the same folder

```
Sysmon64.exe -accepteula -i sysmonconfig-export.xml
```

To check if the service is running

```
Get-Service sysmon64
```

If running it should look like below if running, else it wont return anything if not running

<figure><img src="../../../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

Check if Event log channel exists

```
wevtutil el | findstr /i sysmon
```

#### In Splunk Web UI

Make a index named **win\_sysmon**

#### Splunk Universal Forwarder&#x20;

Add this to the inputs.conf of your app

```
[WinEventLog://Microsoft-Windows-Sysmon/Operational]
disabled = 0
index = win_sysmon
sourcetype = WinEventLog:Sysmon
current_only = 0
checkpointInterval = 5
evt_resolve_ad_obj = true
start_from = oldest
```

Restart the forwarder

#### **In Splunk Web UI you should see data coming into the index**&#x20;

#### Troubleshooting

If you see errors like the ones below and are not receiving anything to the Splunk index&#x20;

```
ERROR ExecProcessor [5084 ExecProcessor] - message from ""C:\Program Files\SplunkUniversalForwarder\bin\splunk-winevtlog.exe"" splunk-winevtlog - WinEventLogChannel::subscribeToEvtChannel: Could not subscribe to Windows Event Log channel 'Microsoft-Windows-Sysmon/Operational'
ERROR ExecProcessor [5084 ExecProcessor] - message from ""C:init: Init failed, unable to subscribe to Windows Event Log channel 'Microsoft-Windows-Sysmon/Operational': errorCode=5

```

When you see errorCode=5 this is a permission issue and the Splunk forwarder cant read it. You need to give Splunk forwarder access to read the symon logs

```
net localgroup "Event Log Readers" "NT SERVICE\SplunkForwarder" /add
```

Restart the Forwarder and check the index you created in the Splunk web UI
