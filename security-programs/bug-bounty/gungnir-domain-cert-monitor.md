# Gungnir - Domain cert monitor

Gungnir is a command-line tool written in Go that continuously monitors certificate transparency (CT) logs for newly issued SSL/TLS certificates. Its primary purpose is to aid security researchers and penetration testers in discovering new domains and subdomains as soon as they are issued certificates, allowing for timely security testing.

The tool connects to multiple CT logs and actively watches for new certificate entries. Whenever a new certificate is detected, Gungnir extracts the domains and subdomains present in the certificate's subject alternative names (SANs) and Common Name (CN) and prints them to stdout in real-time.

By running Gungnir continuously, security professionals can stay ahead of the curve and rapidly identify potential attack surfaces as soon as new domains or subdomains become active on the web. This proactive approach enables early reconnaissance, vulnerability scanning, and prompt remediation of any identified issues.

{% embed url="https://github.com/g0ldencybersec/gungnir" %}
