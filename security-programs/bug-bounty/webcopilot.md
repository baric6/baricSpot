# WebCopilot

<figure><img src="../../.gitbook/assets/image (391).png" alt=""><figcaption></figcaption></figure>

**WebCopilot** is an automation tool designed to enumerate subdomains of the target and detect bugs using different open-source tools.

The script first enumerate all the subdomains of the given target domain using assetfinder, sublister, subfinder, amass, findomain, hackertarget, riddler and crt then do active subdomain enumeration using gobuster from SecLists wordlist then filters out all the live subdomains using dnsx then it extract titles of the subdomains using httpx & scans for subdomain takeover using subjack. Then it uses gau/gauplus, waybackurls, or waymore to crawl all the endpoints of the given subdomains then it use gf patterns to filters out xss, lfi, ssrf, sqli, open redirect & rce parameters from that given subdomains, and then it scans for vulnerabilities on the subdomains using different open-source tools (like kxss, dalfox, openredirex, nuclei, etc). Then it'll print out the result of the scan and save all the output in a specified directory.

{% embed url="https://meterpreter.org/webcopilot-all-in-one-web-vulnerability-scanner-find-xss-sqli-rce-and-more/" %}

{% embed url="https://github.com/h4r5h1t/webcopilot" %}
