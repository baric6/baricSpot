# Wazuh manager server and agent upgrade

to check what version is the wazuh server

```
/var/ossec/bin/wazuh-control -j info
```

**Upgrade Documentation**

{% embed url="https://documentation.wazuh.com/current/upgrade-guide/upgrading-central-components.html" %}

_**note**_

#### for indexer upgrade

* skip Disable shard allocation
* skip Stop non-essential indexing and perform a synced flush
* skip Check that the newly-upgraded node joins the cluster.
* skip Re-enable shard allocation.
* skip Check again the status of the cluster to see if shard allocation has finished.

## Upgrade agent

you are looking for a tool within the manager called agent\_upgrade

located:

```
/var/ossec/bin/agent_upgrade
```

to see outdated agents

```
./agent_upgrade -l
```

to upgrade a single agent

```
./agent_upgrade -a 002 // the number is agent number
```

to upgrade multi agents at once

```
agent_upgrade -l | awk '$1 ~ /^[0-9]+$/ {print "Starting upgrade on agent " $1; system("/var/ossec/bin/agent_upgrade -a " $1)}'
```
