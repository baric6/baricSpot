# Wazuh endpoint agent custom config elements

## To scan custom directories

```
<syscheck>
   <directories realtime="yes">/specialdir3</directories>
</syscheck>
```

the directories tags goes inside of the `<syscheck>`

```
<directories realtime="yes">C:\Users\*\Desktop</directories>
<directories realtime="yes">C:\Users\*\Downloads</directories>
<directories realtime="yes">C:\Users\*\Documents</directories>
```
