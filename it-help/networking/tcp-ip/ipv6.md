# IPv6

| Term           | Definition                                                                                                               |
| -------------- | ------------------------------------------------------------------------------------------------------------------------ |
| Global-Unicast | An IPv6 address type that is publicly routable and can be used in the internet.                                          |
| Unique-Local   | An IPv6 address type that indicates the IP address is a private IP address.                                              |
| Link-Local     | An IPv6 address type that indicates that the IP address was configured by default.                                       |
| Multicast      | An IPv6 address type that indicates that the packet is addressed to a number of hosts on the network, but not all hosts. |
| Prefix ID      | The leftmost bits of the IPv6 address, also know as the network ID. The prefix is used for routing IPv6 packets.         |
| Interface ID   | The rightmost bits of the IPv6 address used to uniquely identify a network card (interface) in a host.                   |

IPv6 Address Rules

IPv6 follows the same basic rules as IPv4.

* Each host on the same logical network must have the same network address.
* Hosts can communicate directly only with other hosts on the same logical network.
* Each host must have a unique IPv6 address.
* Each host on the same logical network must have the same network address.
* Hosts can only communicate directly with other hosts on the same logical network.

IPv6 Address Structure

The following table describes the structure of an IPv6 address.

| Component     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Format        | <p>IPv6 uses a 128-bit address made up of 32 hexadecimal numbers organized into eight quartets.</p><ul><li>The quartets are separated by colons.</li><li>Each quartet is represented as a hexadecimal number between 0 and FFFF.</li><li>Each quartet represents 16 bits of data (FFFF = 1111 1111 1111 1111).</li></ul>                                                                                                                                                                                                                                                                                                                                                                                  |
| Leading Zeros | <p>Leading zeros can be omitted in each section. For example, the quartet 0284 could also be represented by 284.</p><ul><li><p>Addresses with consecutive zeros can be expressed more concisely by substituting double colons for the group of zeros.<br>For example:</p><ul><li>FEC0:0:0:0:78CD:1283:F398:23AB</li><li>FEC0::78CD:1283:F398:23AB (concise form)</li></ul></li><li><p>If an address has more than one consecutive location where one or more quartets are all zeros, only one location can be abbreviated.<br>For example, FEC2:0:0:0:78CA:0:0:23AB could be abbreviated as either one of the following:</p><ul><li>FEC2::78CA:0:0:23AB</li><li>FEC2:0:0:0:78CA::23AB</li></ul></li></ul> |

| <ul><li>FEC2::78CA::23AB is not a valid IPv6 address.</li></ul> |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| --------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Prefix                                                          | <ul><li>The first 64 bits are known as the prefix. The <em>prefix</em> is equivalent to the IPv4 network ID.</li><li><p></p><ul><li>The prefix can be divided into various parts that identify things such as geographic region, the ISP, the network, and the subnet.</li><li>The prefix length identifies the number of bits in the relevant portion of the prefix. To indicate the prefix length, add a slash (/) followed by the prefix length number. Full quartets with trailing 0s in the prefix address can be omitted (e.g., 2001:0DB8:4898:DAFC::/64).</li><li>IPv6 addresses are allocated based on physical location, and the prefix includes the global routing information.</li><li>Because addresses are allocated based on physical location, the prefix generally identifies the location of the host. The 64-bit prefix is often referred to as the <em>global routing</em> prefix.</li><li>Routers can be configured to announce the prefix.</li><li>Subnetting can be performed with the same formulas as IPv4.</li></ul></li></ul> |
| Interface ID                                                    | <ul><li><p>The last 64 bits make up the <em>interface ID</em>.</p><ul><li>The interface ID is the unique address assigned to an interface.</li><li>Clients can use a randomly generated host address or the Extended Unique Identifier 64 (EUI-64).</li><li><p>Each host has a unique 48-bit hardware address called a <em>MAC address</em> (also called the <em>burned-in</em> address) that is assigned to each device by the vendor. The MAC address is guaranteed to be unique through design. The EUI-64 format uses the unique MAC address by:</p><ol><li>Splitting the MAC address into 24-bit halves.</li><li>Inserting 16 bits (represented by hex FFFE) between the two halves.</li></ol></li></ul></li></ul>                                                                                                                                                                                                                                                                                                                                 |

* For example, a host with a MAC address of 20-0C-FB-BC-A0-07 would start with the following EUI-64 interface ID: 200C:FBFF:FEBC:A007.
*   To be complete, the EUI-64 format requires setting the seventh bit in the first byte to binary 1 (reading from left to right, this is the second hex value in the interface ID). This bit is called the _universal/local (U/L) bit_.

    * When the U/L bit is set to 0, the MAC address is a burned-in MAC address.
    * When the U/L bit is set to 1, the MAC address has been configured locally. EUI-64 requires the U/L bit to be set to 1.

    Review the following examples:

    * 200C:FBFF:FEBC:A007 (Incorrect interface ID, as the U/L bit is still set to 0)
    * 220C:FBFF:FEBC:A007 (Correct interface ID)

| <ul><li><p></p><ul><li><p></p><ol><li>Addresses are assigned to interfaces (network connections), not to the host. Technically, the interface ID is not a host address.</li></ol></li></ul></li></ul> |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

IPv6 Address Facts

When using IPv6, be aware that:

* The IPv6 loopback address is ::1.
* IPv6 eliminates the need for DHCP to issue IP addresses. DHCP is needed only to provide additional information, such as the DNS server information.
* IPv6 makes it possible for each device to have a publicly registered address. Having a unique address for each device removes the need for NAT and PAT.

IPv6 Address Types

The following table compares IPv6 address types with IPv4 address types:

| IPv4 Address         | IPv6 Address   | IPv6 Starts With |
| -------------------- | -------------- | ---------------- |
| Public Addresses     | Global-Unicast | 2 or 3           |
| Private IP Addresses | Unique-Local   | FC or FD         |
| APIPA                | Link-Local     | FE8              |
| Multicast            | Multicast      | FF               |

Keep in mind the following about addressing types:

* A Unique-Local, previously referred to as Site-Local, address type indicates a private IP Address.
* A Link-Local address type indicates that the IP address was configured by default. Link-Local addresses are only valid for communications within the network segment (link) or the broadcast domain that the host is connected to.
* Multicast indicates that the packet is addressed to a number of hosts on the network, but not all hosts.

IPv6 Features

| Feature                     | Description                                                                                                                                                                                                           |
| --------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Auto-configuration          | Because hardware IDs are used for node IDs, IPv6 nodes simply need to discover their network IDs. This can be done by communicating with a router.                                                                    |
| Built-in Quality of Service | Built-in support for bandwidth reservations makes guaranteed data transfer rates possible. (Quality of service features are available as add-ons within an IPv4 environment but are not part of the native protocol.) |
| Built-in Security Features  | IPv6 has built-in support for security protocols such as IPsec. (IPsec security features are available as add-ons within an IPv4 environment.)                                                                        |
| Source Intelligent Routing  | IPv6 nodes have the option to include addresses that determine part or all of the route a packet will take through the network.                                                                                       |

Configuration Methods

An IPv6 address can be configured using any of the following methods:

| Method                      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| --------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Static Full Assignment      | The entire 128-bit address and all other configuration information is statically assigned to the host.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Static Partial Assignment   | The prefix is statically assigned, and the interface ID is derived from the MAC address.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| Stateless Autoconfiguration | <p>Clients automatically generate the interface ID and learn the subnet prefix and default gateway through the Neighbor Discovery Protocol (NDP). NDP uses the following messages for autoconfiguration:</p><ul><li>A <em>Router solicitation</em> (RS) is a message sent by the client requesting that routers respond.</li><li>A <em>Router advertisement</em> (RA) is a message sent by the router both periodically periodically and in response to RS messages, informing clients of the IPv6 subnet prefix and the default gateway address.</li></ul><p>Hosts also use NDP to discover the addresses of other interfaces on the network, removing the need for the Address Resolution Protocol (ARP).</p> |

| NDP provides enough information for the addressing of the client and for clients to learn the addresses of other clients on the network. It does not provide the client with DNS server information or any other IP configuration information besides the IP address and the default gateway. |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DHCPv6                                                                                                                                                                                                                                                                                        | <p>IPv6 uses an updated version of DHCP (called DHCPv6) that operates in one of two modes:</p><ul><li><em>Stateful</em> DHCPv6 provides each client an IP address, default gateway, and other IP configuration information (such as the DNS server IP address). The DHCP server tracks the status (or state) of the client.</li><li><em>Stateless</em> DHCPv6 does not provide the client an IP address and does not track the status of each client. It is instead used to supply the client with the DNS server IP address. Stateless DHCPv6 is most useful when used in conjunction with stateless autoconfiguration.</li></ul> |

IPv6 Configuration Process

When a host starts up, it uses the following process to configure the IPv6 address for each interface:

1. The host generates an IPv6 address using the link-local prefix (FE80::/10) and modifies the MAC address to get the interface ID. For example, if the MAC address is 20-0C-FB-BC-A0-07, the link-local address for the interface would be FE80::220C:FBFF:FEBC:A007.
2. The host sends a neighbor solicitation (NS) message addressed to its own link-local address to see if the address it has chosen is already in use.
   * If the address is in use, the other network host responds with a neighbor advertisement (NA) message. The process stops, and manual configuration of the host is required.
   * If the address is not in use (no NA message is received), the process continues.
3. The host waits for an RA message from a router to learn the prefix.
   * If an RA message is not received, the host sends an RS message addressed to all routers on the subnet using the multicast address FF02::2.
   * The router sends an RA message addressed to all interfaces on the subnet using the multicast address FF02::1.
   * If no routers respond, the host attempts to use stateful DHCPv6 to receive configuration information.
4.  The RA message contains information that identifies how the IPv6 address and other information should be configured. The following table shows possible combinations:

    | Configuration Method       | Description                                                                                                                    |
    | -------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
    | Stateful Autoconfiguration | <p>Obtains the interface ID, subnet prefix, default gateway, and other configuration information from a DHCPv6 server.<br></p> |

| The host sends out a REQUEST message addressed to the multicast address FF02::1:2, requesting this information from the DHCPv6 server. |                                                                                                                                                                                                |
| -------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Stateless Autoconfiguration                                                                                                            | <p>Sets the interface ID automatically.<br>Obtains the subnet prefix and default gateway from the RA message.<br>Obtains DNS and other configuration information from a DHCPv6 server.<br></p> |

* | The host sends out an INFORMATION-REQUEST message addressed to the multicast address FF02::1:2, requesting this information from the DHCPv6 server. |
  | --------------------------------------------------------------------------------------------------------------------------------------------------- |
* If a manual address or stateful autoconfiguration is used, the host sends an NS message to make sure the address is not already in use. If stateless autoconfiguration is used, the NS message at this step is unnecessary because the interface ID was verified in step 2.



## Task Summary Actions&#x20;

![Incorrect](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAsAAAALCAYAAACprHcmAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyJpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMy1jMDExIDY2LjE0NTY2MSwgMjAxMi8wMi8wNi0xNDo1NjoyNyAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNiAoV2luZG93cykiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6MTU0MzEyOTA5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6MTU0MzEyOTE5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDoxNTQzMTI4RTk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIgc3RSZWY6ZG9jdW1lbnRJRD0ieG1wLmRpZDoxNTQzMTI4Rjk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PvDFWeEAAAEASURBVHjabI+9agJBFIXvDhZC6uA2WgaSLpDnsREszCYgKvGnjqvYmc0W1oLPkyIJpAlosy8QSDMzOWe4S6bwwrfn/nHnbHIcj1siUoElWLQ3G6njNJlQnsEcpMY7VwEBc/B0HI3CIpW19plXxjo3A6KswP33cJhQta5ns4azdoVDP2CrrxdgAG7kPx7BS+K9l68BZ5IBGm5GS7+AxourspSwzPjs94NV0I6WT6BzvduFwvDz3usJ7GTgEkgE64xzRvLW7VIfIs+Mj3OeG9baKZI8GtB7qT9ZaI+HLgyWcyDKFLze7veeqnU9yw08pepvCdZ3h0M4RWWtfebpnwADAAUyxgiIGBh2AAAAAElFTkSuQmCC)Use 2620:14F0:45EA:0001:192:168:0:10 as the IPv6 address on the vEthernet (External) network adapter![Incorrect](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAsAAAALCAYAAACprHcmAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyJpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMy1jMDExIDY2LjE0NTY2MSwgMjAxMi8wMi8wNi0xNDo1NjoyNyAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNiAoV2luZG93cykiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6MTU0MzEyOTA5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6MTU0MzEyOTE5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDoxNTQzMTI4RTk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIgc3RSZWY6ZG9jdW1lbnRJRD0ieG1wLmRpZDoxNTQzMTI4Rjk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PvDFWeEAAAEASURBVHjabI+9agJBFIXvDhZC6uA2WgaSLpDnsREszCYgKvGnjqvYmc0W1oLPkyIJpAlosy8QSDMzOWe4S6bwwrfn/nHnbHIcj1siUoElWLQ3G6njNJlQnsEcpMY7VwEBc/B0HI3CIpW19plXxjo3A6KswP33cJhQta5ns4azdoVDP2CrrxdgAG7kPx7BS+K9l68BZ5IBGm5GS7+AxourspSwzPjs94NV0I6WT6BzvduFwvDz3usJ7GTgEkgE64xzRvLW7VIfIs+Mj3OeG9baKZI8GtB7qT9ZaI+HLgyWcyDKFLze7veeqnU9yw08pepvCdZ3h0M4RWWtfebpnwADAAUyxgiIGBh2AAAAAElFTkSuQmCC)Use 64 as the subnet prefix length for the IPv6 addressExplanation

Complete this lab as follows:

1. In the notification area, right-click the Network icon and select Open Network and Sharing Center.
2. On the left, select Change adapter settings.
3. Right-click the vEthernet (External) adapter and select Properties.
4. Select Internet Protocol Version 6 (TCP/IPv6).
5. Select Properties.
6. Select Use the following IPv6 address.
7. In the IPv6 address field, enter 2620:14F0:45EA:0001:192:168:0:10 as the IPv6 address.
8. In the Subnet prefix length field, enter 64.
9. Click OK.
10. Click Close.
11. In the Search the web and Windows field, enter cmd.
12. Under Best match, right-click Command Prompt and select Run as Administrator.
13. At the command prompt, type ipconfig /all and press Enter to view the IPv6 address.

