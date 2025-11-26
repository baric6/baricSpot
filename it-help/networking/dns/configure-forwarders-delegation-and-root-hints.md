# Configure forwarders, delegation and root hints

As you study this section, answer the following questions:

* How does a DNS client perform name resolution?
* What is the purpose of the DNS client cache?
* What is the purpose of the hosts file?
* What is the purpose of the DNS server cache?
* What is an authoritative DNS?
* Under what conditions should a conditional forwarder be used?
* When does a DNS server use DNS forwarding?
* When does a DNS server use Root Hints?
* What is involved in the DNS delegation process?
* What is the purpose of a stub zone?

In this section, you will learn to:

* Configure forwarding.
* Configure conditional forwarders.
* Configure root hints.
* Configure delegations.

Key terms for this section include the following:

| Term                                            | Definition                                                                                                                              |
| ----------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| DNS Client                                      | A client computer that is configured to send name resolution queries to a DNS server.                                                   |
| <p>DNS Client Cache<br>(DNS Resolver Cache)</p> | A temporary database maintained by the DNS client that contains previously resolved FQDNs and their matching IP addresses.              |
| Host File                                       | A plain text file that maps FQDNs to IP addresses.                                                                                      |
| DNS Server                                      | A type of name server that responds to DNS queries using a database of hostnames and their associated records.                          |
| DNS Server Cache                                | A temporary database maintained by the DNS server that contains previously resolved FQDNs and their matching IP addresses.              |
| Authoritative DNS                               | A DNS server that holds original and definitive DNS records for the domains it is responsible for.                                      |
| DNS Forwarding                                  | Occurs when one DNS server queries another DNS server when it can't resolve a FQDN.                                                     |
| Conditional Forwarding                          | Occurs when a DNS server forwards queries for certain DNS domains to certain DNS servers.                                               |
| Stub Zone                                       | A DNS zone containing a list of authoritative DNS servers for a specific DNS domain.                                                    |
| Root Hints                                      | The process of resolving FQDNs by first contacting root DNS servers followed by contacting delegated DNS servers.                       |
|  Delegation                                     | The process of responding to DNS queries by delegating to a DNS server that is lower in the DNS tree, but closer to the requested FQDN. |

The Domain Name System (DNS) includes DNS clients and DNS servers. There are rules that govern how DNS resolves fully qualified domain names (FQDNs) to IP addresses.

This lesson covers the following topics:

* DNS client cache
* Host files
* Authoritative DNS
* Conditional forwarding
* Forwarding
* Root hints and delegation
* Stub zones

DNS Client Cache

To resolve an FQDN, the DNS client checks its own DNS cache before it queries a DNS server. To view and clear the cache, use the following command:

| Command              | Results                                                                                                                                                                 |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ipconfig /displaydns | Displays records in the DNS client cache, which includes both entries preloaded from the local Hosts file and any recently obtained resource records from a DNS server. |
| ipconfig /flushdns   | Flushes and resets the contents of the DNS client cache.                                                                                                                |

Host File

The Host file can be used to add records to the DNS client cache that have not been actively resolved by the client. The host file:

* Is located in the %WINDIR%\system32\drivers\etc folder. The name of the file is hosts. The file name does not have an extension.
* Pre-populates the DNS client cache.
* Can be edited with a text editor such as Notepad, never with Microsoft Word.
* Can be used when one client needs a different IP address for a host that is different from the IP address received by other clients from a DNS.

If an entry remains in the DNS client cache after you use ipconfig /flushdns, the entry must be in the hosts file.

Authoritative DNS

If the client cannot resolve a FQDN using its cache, it queries its primary DNS server. It does not contact a secondary DNS server unless there is no response from the primary. The DNS server:

* Checks its own DNS server cache for the FQDN.<br>
* Use dnscmd /clearcache to clear the DNS server cache.
* Determines if it is authoritative for the DNS zone specified in the query.
  * If a record for the FQDN is found in the DNS zone, the DNS server gives an authoritative response containing the IP address of the FQDN.
  * If a record for the FQDN is not found in the DNS zone, the DNS server gives an authoritative response that the host was not found.

Conditional Forwarding

When a DNS server receives a query for an FQDN that is not in its cache and the DNS server is not authoritative for the DNS zone, it then checks for conditional forwarding.

* The DNS server compares the FQDN with its DNS domain name conditions.
* If a match is made, it forwards the query to the IP address associated with the domain name condition.
  * If more than one match is made, it uses the longest domain name condition.
* The DNS server returns the result of the query to the DNS client.

Forwarding

A DNS server can forward a query to another DNS server. It will only do so after it determines that:

* The FQDN is not in the DNS server cache.
* The DNS server it is not authoritative for the DNS zone.
* There are no conditional forwarders that match the domain name.

The DNS server returns the result of the forwarded query to the DNS client. You can configure the server based on your priorities:

* For better security, configure all internal DNS servers to forward to a DNS server in the DMZ.
  * Internal DNS servers are authoritative for internal queries.
  * Internet queries are forwarded to the DMZ DNS.
  * Only the DMZ DNS is vulnerable to external attacks.
* For better performance, configure all non-authoritative queries to go to a DNS server with greater computing resources.

Root Hints and Delegation

If a DNS server has no forwarders, it can use Root Hints and delegation to resolve an FQDN.

* By default, Microsoft DNS servers are configured with a list of root servers.
* The DNS server performs an iterative name query.
  1. The DNS server queries the root server.
  2. The root server replies with a delegation record containing information on the top-level DNS server to contact.
  3. The DNS server queries the top-level DNS server.
  4. The top-level DNS server replies with a delegation record containing information on the second-level DNS server to contact.
  5. The DNS server queries the second-level DNS server.
  6. The second-level DNS server replies with either:
     * A delegation record that contains information on a sub-domain DNS server to contact.
     * The IP address of the original FQDN.
     *
*
  1.
     * Delegation can continue through multiple sub-domains if necessary.

The following graphic provides an example of a DNS server contacting a second-level DNS server when using Root Hints and Delegation to resolve the FQDN www.yahoo.com.

![Name Resolution Process - A DNS server contacting a second-level DNS server when using Root Hints and Delegation to resolve an FQDN for www.yahoo.com](https://cdn.testout.com/_version_405/serverpro2016network-741v4-en-us/en-us/resources/text/t_dns_name_resolution_spn4/root_hints_example.png)

Stub Zones

Stub zones act like conditional forwarders, but with the following differences:

| Characteristic             | Conditional Forwarder                                                                                                                                                                                                                                   | Stub Zone                                                                                                                                                                                                                                      |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Requires No Permissions    | ![Stub zones act like conditional forwarders - Requires no permissions - Conditional Forwarder has a green check](https://cdn.testout.com/_version_405/serverpro2016network-741v4-en-us/en-us/resources/text/t_dns_name_resolution_spn4/greencheck.png) | ![Stub zones act like conditional forwarders - Requires no permissions - Stub zone has a red X](https://cdn.testout.com/_version_405/serverpro2016network-741v4-en-us/en-us/resources/text/t_dns_name_resolution_spn4/redx.png)                |
| No Records Transferred     | ![Stub zones act like conditional forwarders - No records transferred - Conditional Forwarder has a green check](https://cdn.testout.com/_version_405/serverpro2016network-741v4-en-us/en-us/resources/text/t_dns_name_resolution_spn4/greencheck.png)  | ![Stub zones act like conditional forwarders - No records transferred - Stub zone has a red X](https://cdn.testout.com/_version_405/serverpro2016network-741v4-en-us/en-us/resources/text/t_dns_name_resolution_spn4/redx.png)                 |
| Records Dynamically Change | ![Stub zones act like conditional forwarders - Records dynamically change - Conditional Forwarder has a red X](https://cdn.testout.com/_version_405/serverpro2016network-741v4-en-us/en-us/resources/text/t_dns_name_resolution_spn4/redx.png)          | ![Stub zones act like conditional forwarders - Records dynamically change - Stub Zone has a green check](https://cdn.testout.com/_version_405/serverpro2016network-741v4-en-us/en-us/resources/text/t_dns_name_resolution_spn4/greencheck.png) |

While stub zones require permissions, the number of records that are transferred is small. The greatest advantage of stub zones is that the local records dynamically change when the original records change on the distant DNS server.
