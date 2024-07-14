# Bruter IP locate

Bruter is a simple app that was built as an experiment while learning Go. It is indeed very much inspired by https://github.com/evilsocket/xray (but hey not copied ;)). The tooling can be used to test webservers and validate webservers configurations, but not just!

What does it do?

* It grabs HostInfo data from Shodan APIs, so you will need a Token to try this out
* It collects banners for various services FTP, SSH, MYSQL, IRC, SMTP
* It collects HTTP headers
* It brute force directories on WebServers and reports results (200, 403)
* It produces a Web UI for presentation&#x20;

<figure><img src="../../.gitbook/assets/image (8) (1) (1).png" alt=""><figcaption></figcaption></figure>

Download

{% embed url="https://github.com/CyberRoute/bruter" %}
