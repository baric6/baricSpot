# Default register agent config

```
<localfile>
	<location>Microsoft-Windows-Windows Defender/Operational</location>
	<log_format>eventchannel</log_format>
</localfile>

<syscheck>
	<directories realtime="yes">C:\Users\*\Desktop</directories>
	<directories realtime="yes">C:\Users\*\Downloads</directories>
	<directories realtime="yes">C:\Users\*\Documents</directories>
	<directories realtime="yes">%PROGRAMDATA%\Microsoft\Windows\Start Menu\Programs\Startup</directories>
</syscheck>

<localfile>
	<log_format>command</log_format>
	<command>Powershell -c "Get-Volume -DriveLetter C | Select-Object -Property @{'Name' = '% Free'; Expression = {'{0:P}' -f ($_.SizeRemaining / $_.Size)}}"</command>
	<alias>check_win_disk_space</alias>
	<frequency>44000</frequency>
</localfile>

<!--need to have a file go with this-->
<wodle name="command">
    <disabled>no</disabled>
    <tag>tasklist</tag>
    <command>PowerShell.exe C:\tasklist.bat</command>
    <interval>30m</interval>
    <run_on_start>yes</run_on_start>
    <timeout>10</timeout>
  </wodle>

```
