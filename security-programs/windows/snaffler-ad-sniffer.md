# Snaffler AD sniffer

<figure><img src="../../.gitbook/assets/image (175).png" alt=""><figcaption></figcaption></figure>

Broadly speaking - it gets a list of Windows computers from Active Directory, then spreads out its snaffly appendages to them all to figure out which ones have file shares, and whether you can read them.

Then YET MORE snaffly appendages enumerate all the files in those shares and use LEARNED ARTIFACTUAL INTELLIGENCE for MACHINES to figure out which ones a grubby little hacker like you might want.

Actually it doesn't do any ML stuff, because doing that right would require training data, and that would require an enormous amount of time that we don't have. Instead, like all good "ML" projects, it just uses a shitload of if statements and regexen.&#x20;

Download&#x20;

{% embed url="https://github.com/SnaffCon/Snaffler" %}
