# convoC2

Command and Control infrastructure that allows Red Teamers to execute system commands on compromised hosts through Microsoft Teams. It infiltrates data into hidden span tags in Microsoft Teams messages and exfiltrates data by embedding command outputs in Adaptive Cards image URLs, triggering out-of-bound requests to a C2 server. The lack of direct communication between the victim and the attacker, combined with the fact that the victim only sends http requests to Microsoft servers and antiviruses don't look into MS Teams log files, makes detection more difficult.

<figure><img src="../../.gitbook/assets/377950186-d126a4cb-dc62-4a18-8b89-3501a4319d6e.png" alt=""><figcaption></figcaption></figure>

{% embed url="https://github.com/cxnturi0n/convoC2?tab=readme-ov-file" %}
