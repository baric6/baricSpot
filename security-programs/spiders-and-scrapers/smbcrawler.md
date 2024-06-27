# SmbCrawler

SmbCrawler is no-nonsense tool that takes credentials and a list of hosts and 'crawls' (or 'spiders') through those shares. Features:

* takes host names, IP addresses, IP ranges, or an nmap xml file as input
* checks permissions (check for 'write' permissions is opt-in, because it requires creating an empty directory on the share)
* crawling depth is customizable
* threaded
* outputs machine-readable formats
* pass-the-hash support
* auto-download interesting files
* report potential secrets
* pausable
* interactively skips single shares and hosts

{% embed url="https://github.com/SySS-Research/smbcrawler" %}
