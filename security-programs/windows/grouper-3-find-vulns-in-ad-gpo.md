# Grouper 3 find vulns in AD GPO

<figure><img src="../../.gitbook/assets/image (188).png" alt=""><figcaption></figcaption></figure>

Like its ancestors, Group3r is a tool for pentesters and red teamers to rapidly enumerate relevant settings in AD Group Policy, and to identify exploitable misconfigurations in same. It does this by talking LDAP to Domain Controllers, parsing GPO config files off the domain SYSVOL share, and also by looking at other files (usually on file shares) that are referenced within GPOs, like scripts, MSI packages, exes, etc.

It might also be useful for other people doing other stuff, but it is explicitly NOT meant to be an audit tool. If you want to check your policy configs against some particular standard, you probably want Microsoft's Security and Compliance Toolkit, not Group3r.

I'll say it again extra clear: Group3r is even more focused on being useful for attackers and even less of an audit tool than previous iterations.

Download

{% embed url="https://github.com/Group3r/Group3r" %}
