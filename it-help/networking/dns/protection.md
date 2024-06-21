# Protection

Key terms for this section include the following:

| Term                                       | Definition                                                                                                                                                                                                                            |
| ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>DNS Security Extensions<br>(DNSSEC)</p> | A technology used to secure the Domain Name System (DNS) process. DNSSEC is used to verify whether a response was actually what was sent out by the replying server and whether the server sending it is really who they claim to be. |
| DNS Socket Pooling                         | A DNS security feature where multiple TCP ports are used when performing queries.                                                                                                                                                     |
| DNS Cache Locking                          | A DNS security feature that controls how long before a cached entry can be overwritten. This helps prevent attacks that attempt to pollute information in the cache to direct traffic to a malicious site.                            |
| Response Rate Limiting                     | A DNS security feature that helps protect a DNS server from denial of service attacks by limiting the frequency and size of the response to a query.                                                                                  |
| DANE                                       | A protocol that allows X.509 certificates (commonly used for Transport Layer Security), to be bound to DNS names to help prevent man-in-the-middle attacks.                                                                           |

* DNSSEC
* DNS socket pooling
* DNS cache locking
* Response rate limiting
* DANE
* Delegated administration

DNSSEC

DNS Security Extensions (DNSSEC) is designed to protect the DNS client. It is used to verify whether a response was actually what was sent out by the replying server and whether the server sending it is really who they claim to be.

* When DNSSEC is configured, the DNS server signs responses to DNS queries with a digital certificate. With the certificate, the DNS client knows:
  * The response came from the correct DNS server.
  * The response was not modified in transit.

DNSSEC is implemented on a DNS zone by:

* Digitally signing the zone.
  * This requires a key signing key and a zone signing key.
* Choosing NSEC or NSEC3 for authenticated denial of existence.
* Enabling the distribution of trust anchors.
* Configuring a group policy to require DNS clients to use DNSSEC.

DSNSEC can be configured on the DNS server using the PowerShell command:\
\
PS C:\\>Invoke\_DnsServerZoneSign -ZoneName <_zone_> -SignWithDefault -Force

DNS Socket Pooling

DNS socket pooling protects the DNS server.

* By default, a DNS servers uses port 53 for DNS queries. This port is easy to attack.
* DNS socket pooling configures a pool of ports for DNS to use for DNS queries.

DNS socket pooling is enabled by default for Windows Server 2008 R2 and newer systems. In Windows Server 2016, DNS socket pooling is set to a pool size of 2500 ports. DNS socket pooling can be viewed and changed using either PowerShell or from a command prompt.\
\
To configure the socket pool size from the command prompt using the command:\
\
C:\\>dnssec /config /socketpoolsize <_number of ports>_

DNS Cache Locking

DNS cache locking controls how long a cache entry is locked so that it can't be overwritten. This helps prevent attacks that attempt to pollute information in the cache to direct traffic to a malicious site.

* Cache locking is configured as a percent value.
  * Cache entries are not overwritten within this percentage of the record's time-to-live value.
* Cache locking can be implemented from the command prompt.
  * The command to view the cache locking percent is:\
    C:\\>dnscmd /info /cachelockingpercent
  * The command to set the cache locking percent is:\
    C:\\>dnscmd /config /cachelockingpercent <_percent_>
* You can implement cache locking using PowerShell.
  * The cmdlet to view the cache locking percent is:\
    PS C:\\>Get-DnsServerCache
  * The cmdlet to set the cache locking percent is:\
    PS C:\\>Set-DnsServerCache -LockingPercent <_percent_>

Response Rate Limiting

Response rate limiting helps protect a DNS server from denial of service attacks.

* Attackers attempt to overwhelm a DNS server by sending large numbers of DNS queries.
* Response rate limiting stops the server from responding too frequently or limits the size of the response.
* An exception list exempts DNS client queries from response rate limiting.

Response rate limiting is implemented using PowerShell. The ccdlets are:\
\
PS C:\\>Get-DnsServerResponseRateLimiting\
PS C:\\>Set-DnsServerResponseRateLimiting -Mode Enable -MaximumResponsesPerWindow <_number_>\
PS C:\\>Get-DnsServerResponseRateLimitingExceptionlist\
PS C:\\>Add-DnsServerResponseRateLimitingExceptionlist -Name <_host name_> -ServerInterfaceIP <_DNS server IP address_>

DANE

DANE stands for DNS-based Authentication of Named Entities.

* DANE provides information to DNS clients to ensure domain name certificates are from the proper certification authority.
* DANE prevents man-in-the-middle attacks where attackers attempt to corrupt the DNS cache to point to their own website.
* DANE prevents attackers from using certificates that are issued from an improper certificate authority.

Delegated Administration

DNS administration rights can be delegated to users by:

* Adding users to the DnsAdmins Active Directory security group.
* Configuring security in the DNS Manager utility.
  * Users added under the Security tab of the DNS server properties dialog have administrative rights to the server.
  * Users added under the Security tab of the zone properties dialog have administrative rights to the zone.



You should set the SocketPoolExcludedPortRanges setting in the registry on the DNS servers to 49308-49308.

You should implement the DNS Cache Locking feature.

Implement DNS Security Extensions (DNSSEC).

In DNS Manager, right-click the westsim.com zone and click DNSSEC > Sign the Zone.

In Group Policy, configure a Name Resolution Policy.

Distribute a Trust Anchor to all DNS servers that are not authoritative for the corpnet.com zone.
