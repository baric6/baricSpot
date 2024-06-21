# Adding windows defender logs

{% embed url="https://documentation.wazuh.com/current/user-manual/capabilities/malware-detection/win-defender-logs-collection.html" %}

```
<localfile>
  <location>Microsoft-Windows-Windows Defender/Operational</location>
  <log_format>eventchannel</log_format>
</localfile>
```
