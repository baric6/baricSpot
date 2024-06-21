# AD PywerView

As a pentester, I love using PowerView during my assignments. It makes it so easy to find vulnerable machines, or list what domain users were added to the local Administrators group of a machine, and much more.

However, running PowerView on a computer which is not connected to the domain is a pain: I always find myself using mimikatz's sekurlsa::pth to run a Powershell prompt with stolen domain credentials, and that's not easy to script. Plus, I'm a Linux guy and I've always found it a shame that there were no complete Windows/Active Directory enumeration tool on Linux.

That's why I decided to rewrite some of PowerView's functionalities in Python, using the wonderful impacket library.

Download

{% embed url="https://github.com/the-useless-one/pywerview" %}
