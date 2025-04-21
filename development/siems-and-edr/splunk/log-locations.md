# Log Locations

### Basic log to see what the forwarder/agent is done on the client machine

`C:\Program Files\SplunkUniversalForwarder\var\log\splunk\splunkd.log`



### Tail the Splunkd.log and colorize output

Get-Content "var\log\splunk\splunkd.log" -Wait -Tail 10 | Where-Object { ($\_ -match "TCP|UDP") } | ForEach-Object { Write-Host $\_ -ForegroundColor Cyan }
