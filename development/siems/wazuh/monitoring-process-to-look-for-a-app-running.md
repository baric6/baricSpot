# Monitoring process to look for a app running

**simple**

agent runs a file that it points to every x amount of minutes

1. make a bat file called tasklist.bat
2. put the file in a folder location C:/ can be anywhere really
   * this script just gets all processes as a task list

```
@Echo Off
setlocal enableDelayedExpansion

for /f "delims=" %%a in ('powershell -command "& tasklist"') do (
    echo tasklist: %%a
)

exit /b
```

##

2. put the below command inside of `<ossec_config>`

```
  <wodle name="command">
    <disabled>no</disabled>
    <tag>tasklist</tag>
    <command>PowerShell.exe C:\tasklist.bat</command>
    <interval>30m</interval>
    <run_on_start>yes</run_on_start>
    <timeout>10</timeout>
  </wodle>
```

##

3. add the remaining steps like decoder and rule follow the process at: https://documentation.wazuh.com/current/user-manual/capabilities/command-monitoring/use-cases/monitoring-running-processes.html

_**note**_ to change what app the alert goes to the rule you created:

1. `regex type="pcre2">(?i)Paint.exe</regex>` change paint.exe to any ext in the tasks list
2. `<description>Paint.exe is running.</description>` is just what the alert will print out

```
<group name="process_monitor,">
  <rule id="100010" level="6">
    <decoded_as>tasklist</decoded_as>
    <regex type="pcre2">(?i)Paint.exe</regex>
    <description>Paint.exe is running.</description>
  </rule>
</group>
```
