# Powershell History Logs

#### Agent

Navigate to in windows system

```
C:\Program Files\SplunkUniversalForwarder\etc\apps\SplunkUniversalForwarder\local\inputs.conf
```

Add the following code

```
[monitor://C:\Users\*\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadLine\ConsoleHost_history.txt]
sourcetype = powershell_history
index = powershellHistory

[monitor://C:\Users\*\AppData\Roaming\Microsoft\PowerShell\PSReadLine\History]
sourcetype = powershell_history_json
index = powershellHistory
```

* monitor - this line will monitor all power-shell histories on all users&#x20;
* sourcetype - can be anything
* index - you will make a index in Splunk and this needs to be the same as that  in my case i named the index powershellHistory

#### Adding a index to Splunk

1. Hit settings in the top right corner > then click on indexes
2. Hit the button ![](<../../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png>)
3. Name the index powershellHistory in this case, also change the app to "Search & Reporting"

<figure><img src="../../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

1. save

#### Restart agent

1. on the PC that has the forwarder go into services and find splunk forwarder service and hit restart

<figure><img src="../../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

#### Finding data in splunk

1. in the search of splunk type in&#x20;

```
index="poweshellhistory"
```
