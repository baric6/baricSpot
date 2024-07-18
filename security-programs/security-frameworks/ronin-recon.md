# Ronin-Recon

* Uses asynchronous I/O and fibers.
* Supports defining recon modules as plain old Ruby class.
* Provides built-in recon workers for:
  * IP range enumeration.
  * DNS lookup of host-names.
  * Querying nameservers.
  * Querying mailservers.
  * DNS reverse lookup of IP addresses.
  * DNS SRV record enumeration.
  * DNS subdomain enumeration.
  * Service/port scanning with `nmap`.
  * Enumerates the Common Name (`CN`) and `subjectAltName`s within all SSL/TLS certificates.
  * Web spidering.
  * HTTP directory enumeration.

{% embed url="https://github.com/ronin-rb/ronin-recon" %}
