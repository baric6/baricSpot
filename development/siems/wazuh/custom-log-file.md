# Custom Log File

## Send file to manager

We can make use of the log collector module to read those JSON logs and let archives.json write them without triggering any alert. Please follow these steps:

To enable archives.json logging, open your manager's ossec.conf and change the option \<logall\_json> from no to yes. Then, restart your manager to apply changes: systemctl restart wazuh-manager or service wazuh-manager restart.

If the file openapi.log is in the Wazuh manager, write this localfile block in the manager's

`/var/ossec/etc/ossec.conf:`

```
<localfile>
  <log_format>json</log_format>
  <location>/test/test_localfile</location>
</localfile>
```

if openapi.log is in a Wazuh agent, you have the possibility to write the local file configuration locally in the agent's ossec.conf or to send the configuration remotely from the Wazuh manager. To send the configuration remotely, your agent should belong to any group. By default, every agent belong to the default group. You can also make your agents belong to multiple groups. This command will let you know which groups your agent belongs to:

`/var/ossec/bin/agent_groups -s -i 000`

Once you know the group you are going to use (let's say you decided to use the default group), please write the following lines in the manager's

&#x20;`/var/ossec/etc/shared/default/agent.conf`

```
<agent_config>
   <localfile>
     <log_format>json</log_format>
     <location>/test/test_localfile</location>
   </localfile>
</agent_config>
```

For Windows agents, you can find that file in C:\Program Files (x86)\ossec-agent\shared\agent.conf.

After sending the remote configuration, the agent may take a while to fetch it. You can accelerate the process by restarting the manager.
