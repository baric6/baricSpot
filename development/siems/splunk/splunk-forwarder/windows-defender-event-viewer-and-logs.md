# Windows Defender event-viewer and logs

#### **Location Windows**&#x20;

input.conf

```
C:\Program Files\SplunkUniversalForwarder\etc\apps\SplunkUniversalForwarder\local\input.conf
```

#### **When to Use Each**

| **Scenario**                      | **Use Event Logs** | **Use Files** |
| --------------------------------- | ------------------ | ------------- |
| Real-time threat detection        | ✅ Yes              | ❌ No          |
| Simplicity and ease of setup      | ✅ Yes              | ❌ No          |
| Detailed debugging or diagnostics | ❌ No               | ✅ Yes         |
| Centralized log collection        | ✅ Yes              | ❌ No          |
| No access to Event Log system     | ❌ No               | ✅ Yes         |

### Microsoft Defender logs can be accessed via

* **Event Logs**: Defender writes logs to the Windows Event Log (`Microsoft-Windows-Windows Defender/Operational`).
* **Files**: Defender activity may also be written to log files depending on your organization's configuration.

### For Event Logs

1. Open `SplunkUniversalForwarder\etc\apps\Splunk_TA_Windows\local\inputs.conf` or create the file if it doesn’t exist.
2. Add the following to collect Defender logs:

```
[WinEventLog://Microsoft-Windows-Windows Defender/Operational]
disabled = 0
index = defender
sourcetype = WinEventLog:Defender
```

3. Replace `index = defender` with the index where you want to store the logs in Splunk.
4. Restart the Universal Forwarder to apply the configuration:

```
splunk restart
```

### For Files

1. Identify the directory where Defender logs are stored.
2. Add a file monitor input in `inputs.conf`:

```
[monitor://C:\Path\To\DefenderLogs\*.log]
disabled = 0
index = defender
sourcetype = defender:log
```
