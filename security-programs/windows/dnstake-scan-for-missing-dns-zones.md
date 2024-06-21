# DNSTake scan for missing dns zones

<figure><img src="../../.gitbook/assets/image (184).png" alt=""><figcaption></figcaption></figure>

&#x20;DNS takeover vulnerabilities occur when a subdomain (subdomain.example.com) or domain has its authoritative nameserver set to a provider (e.g. AWS Route 53, Akamai, Microsoft Azure, etc.) but the hosted zone has been removed or deleted. Consequently, when making a request for DNS records the server responds with a SERVFAIL error. This allows an attacker to create the missing hosted zone on the service that was being used and thus control all DNS records for that (sub)domain.

Download&#x20;

{% embed url="https://github.com/pwnesia/dnstake" %}
