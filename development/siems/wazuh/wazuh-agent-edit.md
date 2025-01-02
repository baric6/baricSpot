# Wazuh agent (edit)

## Agent stop calling back to server <a href="#agent-stop-calling-back-to-server" id="agent-stop-calling-back-to-server"></a>

`NET START WazuhSvc`

## Wazuh agent / remove

**if installing via cmd the agent UI location:**

`C:\Program Files (x86)\ossec-agent\Win32ui.exe`

## Install

Command to install no GUI agent&#x20;

{% embed url="https://documentation.wazuh.com/current/installation-guide/wazuh-agent/index.html" %}

## **Restart service**

`NET START WazuhSvc`

## Gui agent

{% embed url="https://documentation.wazuh.com/current/installation-guide/wazuh-agent/wazuh-agent-package-windows.html" %}

shows a example of agent config from group menu

<figure><img src="../../../.gitbook/assets/image (253).png" alt=""><figcaption></figcaption></figure>

## Remove

```
cd /var/ossec/bin/
```

```
./manage_agents
```

<figure><img src="../../../.gitbook/assets/image (254).png" alt=""><figcaption></figcaption></figure>
