# IATelligence Import Address Table (IAT) from a PE&#x20;

IATelligence Import Address Table (IAT) from a PE file&#x20;

IATelligence is a Python script that extracts the Import Address Table (IAT) from a PE file and uses OpenAI's GPT-3 model to provide details about each Windows API imported by the file. The script also searches for related MITRE ATT\&CK techniques and explains how the API could potentially be used by attackers.

It also displays the hashes of the file and estimates the cost of the GPT-3 requests. IATelligence is a proof of concept for using GPT-3 for malware analysis and quickly assessing the behavior of a malware based on its IAT.

Below is a quick example of the result you'll get. Notice that the request can take longer depending of the size of the IAT.

<figure><img src="../../.gitbook/assets/image (142).png" alt=""><figcaption></figcaption></figure>

Download

{% embed url="https://github.com/fr0gger/IATelligence" %}
