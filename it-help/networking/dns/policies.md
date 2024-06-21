# Policies

Key terms for this section include the following:

| Term                        | Definition                                                                                             |
| --------------------------- | ------------------------------------------------------------------------------------------------------ |
| DNS Policy                  | A new feature in Windows Server 2016 that gives the DNS server flexibility when responding to queries. |
| DNS Query Resolution Policy | A policy that specifies how incoming resolution queries are handled by a DNS server.                   |
| DNS Recursion Policy        | A policy that controls how the DNS server performs recursion for a query.                              |
| DNS Transfer Policy         | A policy that controls whether a zone transfer is allowed.                                             |

* DNS policy purposes
* Policies types
* Configuring a DNS policy

DNS Policy Purposes

DNS policies can be used for:

* Application load balancing between application instances at different sites.
* Geolocation-based traffic management to allow primary and secondary DNS servers to respond to DNS client queries based on the geographical location of the client and the resource.
* Split-brain DNS where DNS clients receive query responses based on whether they're internal or external.
* DNS filtering where query filters respond in a custom manner based on the query and the client that sent the query.
* Forensics by redirecting malicious DNS clients to a non-existent IP address or by redirecting DNS clients based on the time of day.

Policies Types

There are three different types of DNS policies.

| DNS Policy Type  | Description                                                                                    |
| ---------------- | ---------------------------------------------------------------------------------------------- |
| Query Resolution | Query resolution policies specify how incoming resolution queries are handled by a DNS server. |
| Recursion        | Recursion policies control how the DNS server performs recursion for a query.                  |
| Zone Transfer    | Zone transfer policies control whether a zone transfer is allowed or not.                      |

Configuring a DNS policy

Following is an example of how to create a DNS query resolution policy based on the geography of the DNS client.

* When clients in the 192.168.1.0/24 subnet query for IntraNet, they receive the IP address 192.168.1.40
* When clients in the 192.168.1.0/24 subnet query for IntraNet, they receive the IP address 192.168.2.40

PowerShell commands:

PS C:\\>Add-DnsServerClientSubnet -Name "SouthSubnet" -IPv4Subnet "192.168.1.0/24"\
PS C:\\>Add-DnsServerClientSubnet -Name "NorthSubnet" -IPv4Subnet "192.168.2.0/24"\
\
PS C:\\>Add-DnsServerZoneScope -ZoneName "corpnet.xyz" -Name "SouthScope"\
PS C:\\>Add-DnsServerZoneScope -ZoneName "corpnet.xyz" -Name "NorthScope"\
\
PS C:\\>Add-DnsServerREsourceRecord -ZoneName "corpnet.xyz" -A -Name "IntraNet" -IPv4Address "192.168.1.40" -ZoneScope "SouthScope"\
PS C:\\>Add-DnsServerREsourceRecord -ZoneName "corpnet.xyz" -A -Name "IntraNet" -IPv4Address "192.168.2.40" -ZoneScope "NorthScope"\
\
PS C:\\>Add-DnsServerQueryResolutionPolicy -Name "SouthPolicy" -Action ALLOW -ClientSubnet "eq,SouthSubnet" -ZoneScope "SouthScope,1" -ZoneName "corpnet.com"\
PS C:\\>Add-DnsServerQueryResolutionPolicy -Name "NorthPolicy" -Action ALLOW -ClientSubnet "eq,NorthSubnet" -ZoneScope "NorthScope,1" -ZoneName "corpnet.com"
