# Wazuh remote commands endpoint agent

custom config elements if you have execute remote scripts off on a endpoint these commands will have to be manually put on the agent

## getting hdd fullness data

**note need to set a `<interval>` or a `<frequency>`**

without frequency tag it will be a default of 360s or 6 mins

```
<localfile>
   	<log_format>command</log_format>
   	<command>Powershell -c "Get-Volume -DriveLetter C | Select-Object -Property @{'Name' = '% Free'; Expression = {'{0:P}' -f ($_.SizeRemaining / $_.Size)}}"</command>
   	<alias>check_win_disk_space</alias>
   	<frequency>44000</frequency>
</localfile>
```

the frequency 44000 means every 12 hours about

#### rule

```
<group name="disk_space_utilization,">
 <!-- Rule to check C: Drive free space -->
 <rule id="100014" level="7">
   <if_sid>530</if_sid>
   <match>^ossec: output: 'check_win_disk_space': </match>
   <regex type="pcre2">[0-1]\d.\d+%$</regex>
   <description>C: Drive free space less than 20%.</description>
 </rule>

 <!-- Rule for disk space between 20% and 50% -->
 <rule id="100015" level="5">
   <if_sid>530</if_sid>
   <match>^ossec: output: 'check_win_disk_space': </match>
   <regex type="pcre2">[2-4]\d.\d+%$</regex>
   <description>C: Drive free space between 20% and 50%.</description>
 </rule>

 <!-- Rule for disk space between 50% and 80% -->
 <rule id="100016" level="3">
   <if_sid>530</if_sid>
   <match>^ossec: output: 'check_win_disk_space': </match>
   <regex type="pcre2">[5-7]\d.\d+%$</regex>
   <description>C: Drive free space between 50% and 80%.</description>
 </rule>

 <!-- Rule for disk space above 80% -->
 <rule id="100017" level="10">
   <if_sid>530</if_sid>
   <match>^ossec: output: 'check_win_disk_space': </match>
   <regex type="pcre2">[89]\d.\d+%$</regex>
   <description>C: Drive free space above 80%.</description>
 </rule>
 
 
</group>
```
