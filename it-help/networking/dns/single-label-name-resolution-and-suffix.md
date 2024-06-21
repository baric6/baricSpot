# Single- Label Name Resolution and Suffix

Key terms for this section include the following:

| Term                         | Definition                                                                                                                                                           |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Single-Label Name Resolution | The process of resolving a non-FQDN host name to an IP address.                                                                                                      |
| Primary DNS suffix           | The name of the DNS domain to which a client belongs.                                                                                                                |
| DNS Devolution               | Part of the single-label name resolution process where the DNS client will automatically append portions of primary DNS suffix when sending queries to a DNS server. |
| GlobalNames Zone             |  A zone containing a the static list of global records with single-label names mapped to IP addresses.                                                               |
| DNS Suffix Search List       | A list of DNS domains appended by the DNS client to single-label names when sending queries to a DNS server.                                                         |

Primary DNS Suffix

When a client attempts to resolve a single-label name, its first action is to append the primary DNS suffix.

* The primary DNS suffix is the name of the domain that a client belongs to.
* The primary DNS suffix is appended to the single-label name and sent to a DNS server as a query.

DNS Devolution

If a DNS query formed by appending the primary DNS suffix to a single-label name isn't resolved by the DNS server, the client uses DNS devolution next.

* Using the primary DNS suffix, the client forms a DNS query by appending the single-label name to every DNS domain above it in the DNS tree.
* For example, the single-label name is Client2, and the primary DNS suffix is Sales.West.CorpNet.com, The client queries for:
  * Client2.Sales.West.CorpNet.com
  * Client2.West.CorpNet.com
  * Client2.CorpNet.com

GlobalNames Zone

GlobalNames zones were intended to transfer the functionality of WINS to DNS. WINS was the database that allowed dynamic registration of NetBIOS names.

* When a single-label name query is received by a DNS server, it checks its GlobalNames zone for matching host records.
* To implement a GlobalNames zone:
  * Create a new primary zone with the name GlobalNames.
  * Run the following command:\
    C:\\>dnscmd /enableglobalnamesupport 1
  * Create CNAME records for all the single-label named clients in the new zone.

DNS Suffix Search List

If a single-label named clients are on different DNS domain than the DNS client, the DNS client can be configured with a DNS suffix search list.

* A DNS suffix search list is a list of DNS domains.
* Each DNS domain in the list is appended to the single-label name and sent to a DNS server as a query.
* A DNS suffix search list is useful in a complicated DNS forest.
* Each entry in the DNS suffix search list can be in a different DNS tree than the DNS client.

Connection Specific Suffix

A separate DNS suffix can be configured for each network interface. This connection-specific suffix is obtained from a DHCP server as the interface is initialized.



