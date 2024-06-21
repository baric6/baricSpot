# Advanced Scopes - Super-scopes, Multicast Scopes and IPv6

* Create a multicast scope.
* Create an IPv6 scope.
* Configure DHCPv6 scope options.
* Create and configure a superscope.

Key terms for this section include the following:

| Term            | Definition                                                                                                                                                                            |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Multicast Scope | A type of DHCP scope that allows multicast addresses to be dynamically assigned to multicast servers and clients using Multicast Address Dynamic Client Allocation Protocol (MADCAP). |
| Superscope      | A special type of scope consisting of one or more member scopes that allows a DHCP server to service multiple IP subnets on a single physical network.                                |
| DHCP Version 6  | The IPv6 version of DHCP, which supports the longer IP 128-bit addresses.                                                                                                             |

## Superscopes

A superscope allows a DHCP server to provide leases from more than one scope to clients on a single physical network. Superscopes are used in multinetted environments where the network has multiple logical IP subnets configured on a single physical network.\
Before you create a superscope, you must define all scopes to be included. Scopes that are part of a superscope are called member scopes. Superscopes are not very common. They are are created to solve issues such as:

* Depletion of IP addresses in a address pool
* Migrating clients to a new DHCP scope

## Multicast Scopes

DHCP is used to assign each DHCP client on a network with a single unique IP address from a range of IP addresses configured in a scope. You can extend this functionality to create multicast scopes so that messages destined for a multicast IP address can be sent to all clients in a group (as apposed to the unicasting process, in which a message is sent to a specific recipient).

\
Important facts about multicast scopes include the following:

* Multicast scopes cannot use reservations.
* You cannot set additional options such as DNS and routing.
* The default duration of a multicast scope is 30 days.
* A multicast server uses a group of Class D IP addresses, which include the range of 224.0.0.0 – 239.255.255.255.
* Multicast scopes are supported through a protocol known as the Multicast Address Dynamic Client Allocation protocol.

## Creating a Super-Scope

1. Configure and activate a scope as follows:
   1. In Hyper-V Manager, select CAMPUSSERVER1.
   2. Under Virtual Machines, right-click CampusDCHP\_1 and select Connect.
   3. In Server Manager, select Tools > DHCP.
   4. In the left pane, expand CampusDHCP\_1.PartnerNet.com.
   5. Right-click IPv4 and select New Scope.
   6. Click Next to start the New Scope wizard.
   7. In the Name field, enter Campus1b and click Next.
   8. In the Start IP address field, enter 10.10.11.1.
   9. In the End IP address field, enter 10.10.11.254.
   10. In the Subnet mask, enter 255.255.255.0.
   11. Click Next.
   12. Click Next to ignore any exclusions and delays.
   13. Under Days, enter 15 as the lease duration.
   14. Click Next.
   15. Select No, I will configure these options later to postpone configuring other DHCP options and click Next.
   16. Click Finish to close the wizard and create the scope.
   17. Right-click Scope \[10.10.11.1] Campus1b and select Activate.
2. Configure a superscope as follows:
   1. In the left pane, right-click IPv4 and select New Superscope.
   2. Click Next to start the New Superscope wizard.
   3. In the Name field, enter Campus1-Super and click Next.
   4. Select Campus1.
   5. Press Shift and select Campus1b.
   6. Click Next.
   7. Click Finish to close the wizard and create the Superscope.

Uses for IPv6 DHCP

You can use DHCP in an IPv6 environment to:

* Deliver DNS server and other configuration information that cannot be delivered by the router. This is referred to as stateless DHCPv6.\
  On the router, set the M flag to 0 and the O flag to 1.
* Deliver all configuration information, including the prefix and the interface ID. This is referred to as stateful DHCPv6.\
  On the router, set both the M and the O flags to 1.

IPv6 DHCP Stateful Process

When a client starts, it contacts the router to identify how it should get configuration information. If stateful DHCPv6 is used, the following messages are exchanged between the client and the DHCP server:

| Broadcast            | Description                                                                            |
| -------------------- | -------------------------------------------------------------------------------------- |
| Solicit Packet (S)   | This table entry should use class="content"                                            |
| Advertise Packet (A) | This table entry should use class="content"                                            |
| Request Packet (R)   | The client uses this packet as its official request for an addressing assignment.      |
| Reply Packet (R)     | The DHCPv6 server sends this packet to acknowledge the client's addressing assignment. |

IPv6 Configuration Process

Configuration on the DHCP server for IPv6 is separate from configuration of DHCP for IPv4, but the two are similar. Following are some IPv6 configuration tips.

* If the server is a domain member, authorize the server in Active Directory.
* Configure scopes, exclusions, and reservations. Activate the scope.
* Configure server, scope, and reservation options. The most common option you will configure is the 00023 DNS Recursive Name Server IPV6 Address List to identify the DNS servers.
* If required, configure dynamic DNS.\
  To enable dynamic DNS, right-click DHCPv6 and then select Properties. On the DNS tab, enable dynamic updates.\
  To enable name protection for IPv6, click Configure under Name Protection on the DNS tab and then mark Enable Name Protection. This will cause the registration of AAAA and PTR records to fail if duplicate records have already been registered by a different client.

When using IPv6, be aware that:

* The IPv6 loopback address is ::1
* IPv6 eliminates the need for DHCP to issue IP addresses. DHCP is needed only to provide additional information, such as the DNS server information.
* IPv6 makes it possible for each device to have a publicly registered address. Having a unique address for each device removes the need for NAT and PAT.

Keep in mind the following about IPv6 addressing:

* A Global-Unicast address is an address on the Internet.
* Unique-Local, previously referred to as Site-Local, indicates a private IP Address.
* Link-Local indicates that the IP address was configured by default.
* Multicast indicates that the packet is addressed to a number of hosts on the network, but not all hosts.

Structure of an IPv6 address

| Component     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Format        | <p>IPv6 uses a 128-bit address made up of 32 hexadecimal numbers, organized into 8 quartets:</p><ul><li>The quartets are separated by colons.</li><li>Each quartet is represented as a hexadecimal number between 0 and FFFF. Each quartet represents 16-bits of data (FFFF = 1111 1111 1111 1111).</li></ul>                                                                                                                                                                                                                                                                                                                                                                                        |
| Leading zeros | <p>Leading zeros can be omitted in each section. For example, the quartet 0284 could also be represented by 284:</p><ul><li><p>Addresses with consecutive zeros can be expressed more concisely by substituting a double-colon for the group of zeros. For example:</p><ul><li>FEC0:0:0:0:78CD:1283:F398:23AB</li><li>FEC0::78CD:1283:F398:23AB (concise form)</li></ul></li><li><p>If an address has more than one consecutive location where one or more quartets are all zeros, only one location can be abbreviated. For example, FEC2:0:0:0:78CA:0:0:23AB could be abbreviated as either one of the following:</p><ul><li>FEC2::78CA:0:0:23AB</li><li>FEC2:0:0:0:78CA::23AB</li></ul></li></ul> |

| <ul><li>FEC2::78CA::23AB is not a valid IPv6 address.</li></ul> |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| --------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Prefix and interface ID                                         | <p>The 128-bit address contains two parts:</p><ul><li><p>The <em>prefix</em> is equivalent to the IPv4 network ID:</p><ul><li>The prefix is typically 64 bits.</li><li>IPv6 addresses are allocated based on physical location, with the prefix also including the global routing information.</li><li>The 64-bit prefix is often referred to as the <em>global routing</em> prefix.</li><li>Routers can be configured to announce the prefix.</li><li>Subnetting can be done using the same formulas as IPv4.</li></ul></li><li><p>The last 64-bits make up the <em>interface ID</em>:</p><ul><li>This is the unique address assigned to an interface.</li><li>Clients can use a randomly generated host address or the Extended Unique Identifier 64 (EUI-64).</li></ul></li></ul> |

| <ul><li>Addresses are assigned to interfaces (network connections), not to the host. Technically, the interface ID is <em>not</em> a host address.</li></ul> |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------ |

IPv6 address comparisons to IPv4

The following table compares IPv6 address types with IPv4 address types:

<table><thead><tr><th width="153">IPv4 Address</th><th>IPv6 Address</th><th width="146">IPv6 Starts With</th></tr></thead><tbody><tr><td>Public Addresses</td><td>Global-Unicast</td><td>2 or 3</td></tr><tr><td>Private IP Addresses</td><td>Unique-Local</td><td>FC or FD</td></tr><tr><td>APIPA</td><td>Link-Local</td><td>FE8</td></tr><tr><td>Multicast</td><td>Multicast</td><td>FF</td></tr></tbody></table>

## IPv6 scope and options

1. Connect to the CorpDHCP virtual machine as follows:
   1. From Hyper-V Manager, select **CORPSERVER**.
   2. To view all of the virtual machines, maximize Hyper-V Manager.
   3. From the Virtual Machines pane, right-click **CorpDCHP** and select Connect.\
      The virtual machine is opened.
2. Configure an IPv6 scope as follows:
   1. From Server Manager, select Tools > DHCP.
   2. From the left pane, expand **CorpNet.com**.
   3. Right-click **IPv6** and select **New Scope.**
   4. Click **Next** to start the _New Scope wizard_.
   5. In the Name field, enter **Subnet1-IPv6** and then click **Next**.
   6. In the Prefix field, enter: **FD00:0:0:1::**
   7. Make sure that the Preference option is configured for **0**.
   8. Click **Next**.
   9. Enter the starting and ending addresses for the exclusion.
   10. Click **Add**.
   11. Click **Next**.
   12. Configure the scope lease durations.
   13. Click **Next**.
   14. To activate the scope, select **Yes**.
   15. Click **Finish** to create the scope.
3. Configure the DHCPv6 Scope options as follows:
   1. From the left pane of the DHCP window, expand and select **IPv6 > Scope \[fd00:0:0:0:1::] > Scope Options**.
   2. Right-click **Scope Options** and select **Configure Options**.
   3. From Available Options, mark **00023 DNS Recursive Name Server IPV6 Address List**.
   4. In the _New IPv6 address_ field, enter the _first IPv6 address_ of the DNS server.
   5. Click **Add**.
   6. In the _New IPv6 address_ field, enter the _second IPv6 address_ of the DNS server.
   7. Click **Add**.
   8. Click **OK** to save the options you have defined.

| Flag Setting                                  | Configuration Method            | Process Description                                                                                                                                                                                                                                                                                                                           |
| --------------------------------------------- | ------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>M and O flags<br>set to 0</p>              | Use stateless autoconfiguration | <ol><li>The interface ID is set automatically.</li><li>The subnet prefix and default gateway are retrieved from the RA message.</li></ol><p>This method provides only IP addressing and default gateway information. It does not provide the DNS server address.</p>                                                                          |
| <p>M and O flags<br>set to 1</p>              | Use stateful autoconfiguration  | <ol><li>The interface ID, subnet prefix, default gateway, and all other configuration information are obtained from a DHCPv6 server.</li><li>The host sends out a REQUEST message addressed to the multicast address FF02::1:2 to request this information from the DHCPv6 server.</li></ol>                                                  |
| <p>M flag set to 0 and<br>O flag set to 1</p> | Use stateless autoconfiguration | <ol><li>The subnet prefix and default gateway are retrieved from the RA message.</li><li>The DNS and other configuration information are retrieved from a DHCPv6 server.</li><li>The host sends out an INFORMATION-REQUEST message addressed to the multicast address FF02::1:2 to request this information from the DHCPv6 server.</li></ol> |

| Broadcast            | Description                                                                                                |
| -------------------- | ---------------------------------------------------------------------------------------------------------- |
| Solicit Packet (S)   | This is the packet the client uses to solicit addressing information.                                      |
| Advertise Packet (A) | The DHCPv6 server uses this packet to indicate to the client that it has available addressing information. |
| Request Packet (R)   | The client uses this packet as its official request for an addressing assignment.                          |
| Reply Packet (R)     | The DHCPv6 server sends this packet to acknowledge the client's addressing assignment.                     |

