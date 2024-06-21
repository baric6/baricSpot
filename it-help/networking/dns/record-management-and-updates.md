# Record Management and Updates

Key terms for this section include the following:

| Term                   | Definition                                                                                                                                                                                |
| ---------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Secure Dynamic Updates | The process of integrating DNS with Active Directory so that DNS host and pointer records can only be updated by authenticated computers that are members of the Active Directory domain. |
| Round Robin            | The DNS process of responding to client queries for an FQDN that has multiple IP addresses. The IP addresses are reordered in a round robin fashion by the DNS server.                    |
| Netmask Ordering       | The DNS process of responding to client queries for an FQDN that has multiple IP addresses. The IP address are ordered by IP address proximity.                                           |

Dynamic DNS Updates

DNS records can be dynamically updated by clients and DHCP servers.

* As a client’s network interface initializes, it registers its FQDN and IP address with the DNS server.
  * The DNS server dynamically creates host (A and AAAA) records and pointer (PTR) records.
* If a client obtains its IP address from DHCP, the DHCP server registers the client’s information with DNS.
  * The record timestamps in DNS will be consistent with the address leases in DHCP.

There are three Dynamic Updates options that control how a DNS server handles record updates. This setting can be different for each DNS zone.

| Dynamic Updates option | Description                                                                                                                                                                                                                                                                                      |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| None                   | <p>This option is used in ultra-secure environments.</p><ul><li>No automatic DNS updates are allowed.</li><li>Every DNS record must be added manually.</li></ul>                                                                                                                                 |
| Secure Only            | Only users and computers contained in an access control list are able to make dynamic updates. By default, Secure Only computers are Active Directory members.                                                                                                                                   |
| Nonsecure and Secure   | <p>This is the least secure option.</p><ul><li>All clients can add and update DNS records.</li><li>The DNS server is open to spoofing and man-in-the-middle attacks.</li><li>Attackers can pollute the DNS with bad records that point DNS clients to services outside of the network.</li></ul> |

Round Robin Ordering

The Round Robin option can be used to balance the load between servers that offer the same service.

* DNS servers respond to host queries by returning all host records that have the same host name, but always in the same order.
* Round Robin causes the DNS server to vary the response order in a round robin fashion.

Following is an example of query responses when Round Robin is enabled and three records exist for the www host name:

| <p>Response<br>Number</p> | Order                                               |
| ------------------------- | --------------------------------------------------- |
| 1                         | <p>192.168.0.50<br>192.168.0.60<br>192.168.0.70</p> |
| 2                         | <p>192.168.0.60<br>192.168.0.70<br>192.168.0.50</p> |
| 3                         | <p>192.168.0.70<br>192.168.0.50<br>192.168.0.60</p> |
| 4                         | <p>192.168.0.50<br>192.168.0.60<br>192.168.0.70</p> |

Netmask Ordering

The Netmask Ordering option varies the order of DNS query responses when there are duplicate host records. The response variation is based on IP address proximity.

* If a DNS query comes from a Class C IP address, the DNS server responds with a list of IP addresses, but with the Class C address at the top.
* If a DNS query comes from a Class B IP address, the DNS server responds with a list of IP addresses, but with the Class B address at the top.
* If a DNS query comes from a Class A IP address, the DNS server responds with a list of IP addresses, but with the Class A address at the top.

Normally, Netmask Ordering only compares the first octet of the IP address. This can be changed using the following command:

C:\\>dnscmd /config /localnetprioritynetmask \<mask>

The mask is a hexadecimal number with two characters representing each octet in the IP address. An example is 0x0000ffff.

* The mask works like a subnet mask.
* The mask begins with 0s and ends in Fs.
  * The 0s indicate the part of the IP address to compare.
  * The Fs indicate the part of the IP address to ignore.

Round Robin, Netmask Ordering, and IPv6 Precedence

Round Robin and Netmask Ordering can be used independently. The following precedence rules apply:

* If both Round Robin and Netmask Ordering are enabled, Netmask Ordering takes precedence.
* Netmask Ordering only works with IPv4 addresses.
* Windows has a preference for IPv6.
  * If there are multiple IPv4 records and multiple IPv6 records for the same host, IPv6 records are returned first, followed by IPv4 records.
* IPv4 addresses are varied according to both the Round Robin and Netmask Ordering settings.
* IPv6 addresses are only varied according to the Round Robin setting.
*   Netmask Ordering is built into the DNS client.

    * &#x20;Regardless of the order that IPv6 addresses are received from the DNS server, the client automatically picks the IPv6 address that is closest in proximity to its own IPv6 address.



