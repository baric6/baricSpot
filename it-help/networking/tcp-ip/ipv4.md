# IPv4

| Term                                            | Definition                                                                                                                                              |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Subnetting                                      | The process of dividing a large network into smaller networks.                                                                                          |
| Supernetting                                    | The process of combining two or more networks.                                                                                                          |
| <p>Classless Inter-Domain Routing<br>(CIDR)</p> | A set of internet protocol standards used to create unique identifiers for networks and host devices.                                                   |
| ANDing                                          | The process used to determine the network address/ID.                                                                                                   |
| Subnet Mask                                     | A 32-bit number that defines which portion of an IPv4 address identifies the network address and which portion of the address defines the host address. |
| Network ID                                      | A 32-bit number that identifies network an IPv4 address belongs to.                                                                                     |

IPv4 Rules and Concepts

IP addresses and routers are responsible for sorting and delivering packets to and from clients on a network. Each packet contains the IP address of both the sender and the recipient. Routers use the IP address to send the packets to the specified destination. IPv4 addresses allow hosts to participate on IPv4-based networks.

The three most important IPv4 address rules are:

* Each host must have a unique IPv4 address.
* Each host on the same logical network must have the same network address.
* Hosts can only communicate directly with other hosts on the same logical network.

The following table describes IPv4 concepts you should be aware of.

| Concept             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Host                | A _host_ (also known as a network host) is a computer or device (such a router) on a network.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| IP Address          | The _IP address_ is a number assigned to identify hosts and other devices on a network.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| Network address     | The _network address_ (also referred to as the network ID) is the portion of the IP address that identifies a specific network.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| Host Address        | The _host address_ (also referred to as a host ID) is the remaining portion of the IP address that identifies the specific host or other device on the network.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| Subnet Mask         | A _subnet mask_ identifies the portion of the IP address that defines the network address and the portion of the IP address that defines the specific host.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| Address Class       | IPv4 addresses are divided into _classes_. The _address class_ identifies the range of IPv4 addresses and a default subnet mask used for the range.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Default Subnet Mask | <p>A <em>default subnet mask</em> is assigned to classes A - C as follows:</p><ul><li>255.0.0.0 is the default subnet mask for class A networks.</li><li>255.255.0.0 is the default subnet mask for class B networks.</li><li>255.255.255.0 is the default subnet mask for class C networks.</li></ul>                                                                                                                                                                                                                                                                                                                                                         |
| Broadcast Address   | The _broadcast address_ is the last address in the IP address range and is used to send messages to all hosts on the network.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Default Gateway     | <p>The <em>default gateway</em> is a device that performs routing and enables a host to communicate with hosts on other networks through the routing process.</p><ul><li>A default gateway address must be configured on each host to allow internetwork communication. Without the default gateway, hosts can only communicate with devices within the same subnet.</li><li><p>The default gateway address must be on the same subnet as the host computer.</p><ul><li>Routers have multiple network interface cards attached to multiple networks.</li><li>When configuring the default gateway, choose the address on the local subnet.</li></ul></li></ul> |

IP Address Structure

An IPv4 network address is a grouping of four numbers. Each number in the group is separated by a period (referred to as a dot). IPv4 addresses can be represented in the following ways:

* Decimal notation:\
  In decimal notation, each of the four numbers must be between 0 and 255. Example: 131.107.2.200 (spoken as 137 dot 107 dot 2 dot 200).
* Binary notation:\
  In binary notation, each of the four numbers is an octet (consisting of 8 bits). Each bit is either a 1 or a 0.\
  \
  Example: 10000011.01101011.00000010.11001000

On occasion, such as when working with subnet masks, you may need to convert an IP address from a binary value to decimal (or vice versa). Therefore, it is important to understand that each bit position in a binary octet is assigned a decimal value, as shown in the following table:

| 8-Bit Octet   |     |    |    |    |   |   |   |   |
| ------------- | --- | -- | -- | -- | - | - | - | - |
| Bit Position  | 7   | 6  | 5  | 4  | 3 | 2 | 1 | 0 |
| Decimal Value | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |

To convert from binary to decimal, add the decimal equivalent for each bit position containing the binary value of 1.\
For example, the decimal equivalent of 10010101 is 128 + 16 + 4 + 1 = 149. This concept is sometimes easier to see in a table:

| Decimal Value for Each Bit | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |         |
| -------------------------- | --- | -- | -- | -- | - | - | - | - | ------- |
| Binary Value for Each Bit  | 1   | 0  | 0  | 1  | 0 | 1 | 0 | 1 |         |
| Decimal Values             | 128 | +  |    | 16 | + | 4 | + | 1 | = 149   |

Subnet Masks

A subnet mask identifies which portion of the IP address represents network and, consequentially, which portion represents the host address. The structure of a subnet mask is identical to that of an IP address.

* In binary form, the subnet mask is always a series of 1s followed by a series of 0s (1s and 0s are never mixed in sequence in the mask).
* In decimal, each number used to indicate that it is part of the network will will be the value of 255. For example, 255.255.255.0 means that the first three numbers (octets) are reserved for the network portion of an IP address.\
  When using complex subnet masks, the last number of the network portion may be any number as long as that number converted to binary is made of all 1s followed by all 0s. For example, a decimal subnet mask of 255.255.255.240 converted to binary is 11111111.11111111.11111111.11110000. In this address, the first four bits of the last octet are part of the network address.

Classless Inter-Domain Routing (CIDR)

Classless Inter-Domain Routing (CIDR) is a method by which all of the bits used for the subnet mask are written in a single decimal number. For example, when an IP address is written as 10.10.1.16 /16, the "/16" is the CIDR. The /16 indicates that the first two octets (8-bits + 8-bit = /16) are used for the network address.

CIDR notation is most useful when one of the network octets does not comprise the entire octet. For example, when an IP address is written as 10.10.1.16 /18, the "/18" indicates that part of the third octet is used as part of the network address (8-bits + 8-bit + 2-bit = /18).

The following table shows the default address class for each IPv4 address range with its default subnet mask (also represented in CIDR notation).

| Class | Address Range                | First Octet Range                             | Default Subnet Mask | CIDR Notation |
| ----- | ---------------------------- | --------------------------------------------- | ------------------- | ------------- |
| A     | 1.0.0.0 to 126.255.255.255   | <p>1-126<br>(00000001--01111110 binary)</p>   | 255.0.0.0           | /8            |
| B     | 128.0.0.0 to 191.255.255.255 | <p>128-191<br>(10000000--10111111 binary)</p> | 255.255.0.0         | /16           |
| C     | 192.0.0.0 to 223.255.255.255 | <p>192-223<br>(11000000--11011111 binary)</p> | 255.255.255.0       | /24           |
| D     | 224.0.0.0 to 239.255.255.255 | <p>224-239<br>(11100000--11101111 binary)</p> | n/a                 | n/a           |
| E     | 240.0.0.0 to 255.255.255.255 | <p>240-255<br>(11110000--11111111 binary)</p> | n/a                 | n/a           |

When using CIDR notation, you must know how to find your subnet mask. When you find the subnet mask, you will know what bits are available for the network address. To convert a CIDR to a subnet mask, use the following steps:

1. If the CIDR is greater than or equal to 8, write 255 in the first available octet (on the left) and then subtract 8 from the CIDR.
2. Repeat step 1 until the number is less than 8. The octets found using these first two steps will be the first part of you subnet mask.
3. Convert the remaining number (which will be less than eight) to 1s and pad the remaining bits (up to 8) with 0. This will be the last octet in your subnet mask.\
   Examples: If the remaining number is:
   * 3 the converted number is written as 11100000
   * 5 the converted number is written as 11111000
   * 7 the converted number is written as 11111110
4. Convert the 1s in the last (interesting) octet to a decimal number. This number is the subnet mask for this octet.\
   Examples:
   * 11100000 = 224
   * 11111000 = 248
   * 11111110 = 254
5. Any unused octets are represented with a 0.

CIDR conversion example: IP address /CIDR = 196.200.45.5  /20

1. Find simple subnet mask octets:
   1. 12 -8 = 4. 4 is less than 8. Therefore, move to the next step.
2. The number 4 is changed to four 1s with the remaining bits for this octet padded with 0s:\
   111100000
3. As a result, the full subnet mask is 255.255.240.0..

Address Assignment

The following table describes options for assigning IPv4 addresses and other IPv4 configuration values.

| Method                                              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| --------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Dynamic Host Configuration Protocol (DHCP)          | <p>DHCP is a method used to automatically assign IPv4 addresses and other TCP/IPv4 configuration parameters to hosts. Client computers contact a DHCP server to receive TCP/IPv4 configuration information.</p><p>Use DHCP:</p><ul><li>For small, medium, or large networks</li><li>For automatic host configuration</li><li>To automatically deliver additional configuration parameters such as default gateway and DNS servers</li></ul><p>By default, all Windows computers try to use DHCP for TCP/IPv4 configuration information.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| <p>Automatic Private IPv4 Addressing<br>(APIPA)</p> | <p>APIPA is an automatic configuration method where hosts automatically select their own IPv4 address within a specific range.</p><p>When using APIPA:</p><ul><li>Windows computers will use APIPA if a DHCP server cannot be contacted.</li><li>Hosts select an IPv4 address in the 169.254.0.1 to 169.254.255.255 range with a mask of 255.255.0.0. After choosing the address, the host verifies that no other host on the network is using the selected address.</li><li>APIPA sets only the IPv4 address and mask. Because it does not assign a default gateway, APIPA can be used on a single subnet, but cannot be used if communication with other subnets is required.</li></ul><p>Use APIPA for small single-subnet networks that do not use DNS servers or do not have internet or connectivity outside of the local subnet.</p>                                                                                                                                                                                                                                                                |
| Static (Manual) Assignment                          | <p>Static/manual IPv4 address assignment means that you manually enter in the required IPv4 address and associated IP information for a host.</p><ul><li>When you configure a static IPv4 address, you must also configure the subnet mask and default gateway.</li><li>When you configure a static IPv4 address, you disable DHCP and APIPA.</li><li>If you use DHCP, you can also assign DNS server addresses manually.</li></ul><p>Use static addressing:</p><ul><li>For small networks that do not often change or grow.</li><li>If your network does not have a DHCP server or if you want to eliminate DHCP traffic from your network.</li><li>For specific hosts that must have the same address each time (such as servers). You can use DHCP on the rest of the network and use static addressing for only a few hosts. However, before you use static addressing, explore the possibility of using a DHCP server to assign the same IPv4 address to specific hosts each time an address is requested.</li><li>For non-DHCP hosts (hosts that cannot accept an IPv4 address from DHCP).</li></ul> |

| Ensure that duplicate addresses are not assigned to hosts on the same network. |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Alternate IPv4 Configuration                                                   | <p>When an alternate IPv4 configuration is enabled, the host attempts to use DHCP for TCP/IPv4 configuration information. If a DHCP server cannot be contacted, the alternate IPv4 values are used.</p><p>Use an alternate configuration:</p><ul><li>For computers (such as a laptop) that connect to two networks; one with a DHCP server and another without a DHCP server.</li><li>To provide values to properly configure the computer in the event that the DHCP server is unavailable.</li></ul> |

| When you configure an alternate IPv4 address, APIPA will never be used. |
| ----------------------------------------------------------------------- |

Network Address Translation (NAT) Routers

A Network Address Translation (NAT) router translates multiple private addresses into the single registered IP address.

* The internet is classified as a _public_ network. All devices on the public network must have a unique registered IP address. This address is assigned by the ISP. No two hosts on a public network can have the same IP address.
* The internal network is classified as a _private_ network. All devices on the private network use private IP addresses internally, but share the public IP address when accessing the internet.
* A NAT router associates a port number with each private IP address. Port assignments are made automatically by the NAT router. Communications from the internet are sent to the public IP address. The NAT router translates the public IP address into the private IP address of the host.
* A private network can use addresses in the following ranges that have been reserved for private use by IANA:
  * 10.0.0.0 to 10.255.255.2555
  * 172.16.0.0 to 172.31.255.255
  * 192.168.0.0 to 192.168.255.255

By default, internet routers are configured not to route private IP addresses.

Address Concepts

| Concept                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| ------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Subnetting                     | _Subnetting_ is the process of dividing a large network into smaller networks. When you subnet a network, each network segment, or subnet, has a different network address (also called a subnet address).                                                                                                                                                                                                                                                                                      |
| Supernetting                   | Supernetting is the process of combining two or more networks. When you create a supernet, you decrease the number of masked bits in the subnet mask. This reduces the number of available subnets, but increases the number of hosts on each subnet.                                                                                                                                                                                                                                           |
| <p>Classless<br>Addressing</p> | <p>Using custom subnet masks is often called <em>classless</em> addressing because the subnet mask cannot be inferred from the class of a given IP address.</p><ul><li>Classless addressing is made possible by Classless Inter-Domain Routing (CIDR).</li><li>The <em>CIDR</em> notation is a syntax for identifying the subnet mask.</li><li>The format for the CIDR notation is the slash (/) symbol and the decimal number that identifies the number of ones in the subnet mask.</li></ul> |
| ANDing                         | ANDing is the processed used to determine which network an IPv4 address belongs to. This process is typically performed by a router. Sometimes it is useful to perform it manually when troubleshooting or setting up networks.  (See ANDing below.)                                                                                                                                                                                                                                            |

ANDing

The term ANDing refers to the process of comparing the binary values of an IPv4 address and its subnet mask. If the two bits being compared are a 1 and a 1, the result of the comparison is a 1. All other combinations (such as 1 + 0 or 0 + 0) result in a 0.&#x20;

| <p>Perform ANDing<br>Directly Below Top Number</p> | <p>Single Octet<br>Binary</p> | <p>Single Octet<br>Decimal</p> |
| -------------------------------------------------- | ----------------------------- | ------------------------------ |
| IP Address                                         | 1 1 0 0 0 0 1 0               | 194                            |
| Subnet Mask                                        | 1 1 1 1 0 0 0 0               | 240                            |
| ANDing Result                                      | 1 1 0 0 0 0 0 0               | 192                            |

After you complete the ANDing procedure for each octet, you convert the resulting binary value to decimal. This decimal number is the network address/ID.

| ANDing               |                |                |                |          |
| -------------------- | -------------- | -------------- | -------------- | -------- |
| IP Address (Decimal) | 192            | 168            | 10             | 50       |
| IP Address (Binary)  | 11000000       | 10101000       | 00001010       | 00110010 |
| Subnet Mask (Binary) | 11111111 (255) | 11111111 (255) | 11111111 (255) | 00100000 |
| Network ID (Binary)  | 11000000       | 10101000       | 00001010       | 00100000 |
| Network ID (Decimal) | 192            | 168            | 10             | 32       |

To reduce the time spent completing the ANDing process, the network number for any octet with a subnet mask of 255 (11111111) is the same as the IP address. Therefore, you can simply record that value in its applicable location without actually completing the ANDing process for the octet.

Determining Subnets

Subnetting is dividing a larger network in to smaller networks. Subnetting always results in an even number of subnets, and each subnet has an equal number of hosts.

To subnet a network and find the network address for each subnet, you must:

* Find the custom subnet mask.
* Find the network IDs.
* Find the usable IP address ranges for each subnet.

Scenario: As you learn how to complete each of the above steps, use the following requirements:

* The assigned network is 192.168.1.0 /24
* The current subnet mask is 255.255.255.0 or 8 + 8 + 8 = /24
* Three subnets are required.
* You need at least 50 hosts on each subnet.

Find the Custom Subnet Mask

Find the custom subnet mask using the following steps:

1. Use the formula of 2x is greater than or equal to the number of required networks.
2. Solve for X.
3. Add X to the CIDR.
4. Convert this new CIDR to a subnet mask.

Following are steps for creating the required networks:

1. 2x = 3 (Three is used because a minimum of three networks are required.)
2. 22 = 4\
   X  = 2 (X needs to be 2, because 22 is greater than or equal to the number of networks required.)
3. The default CIDR is /24.  /24 + 2 = /26. Therefore, your new CIDR is /26.
4.  /26 converted to a subnet equals 192, as follows:

    <table><thead><tr><th width="20" align="right">26</th><th></th></tr></thead><tbody><tr><td align="right">-8</td><td></td></tr><tr><td align="right">18</td><td></td></tr><tr><td align="right">-8</td><td></td></tr><tr><td align="right">10</td><td></td></tr><tr><td align="right">-8</td><td></td></tr><tr><td align="right">2</td><td></td></tr></tbody></table>

    Change the 2 to two binary ones (11), and add the remaining 0s to make a full octet: 11000000.\
    Note that 11000000=192. Therefore, the last octet of your new subnet mask is 192. The full custom subnet mask is 255.255.255.192. The first three octets come from the original subnet mask.

Find the Network IDs

The next step is to determine what the network address (or Network ID) will be for each of the four new networks. This can be accomplished in one of two ways.

Method 1:\
From the previous step, you discovered that the first two bits in the last octet will now be used for subnet addresses. To calculate the network IDs, find the decimal value for every possible new network bit combination. In this example, this means the following network IDs are possible:

| <p>Binary<br>Combinations for<br>First Two Bits</p> | Decimal Value | Full Network IDs |
| --------------------------------------------------- | ------------- | ---------------- |
| 00 000000                                           | 0             | 192.168.1.0      |
| 01 000000                                           | 64            | 192.168.1.64     |
| 10 000000                                           | 128           | 192.168.1.128    |
| 11 000000                                           | 192           | 192.168.1.192    |

Method 2:\
When you are working with several bits, using the above method can be complicated. A shortcut method is to fine the network IDs using the formula of subtracting the new subnet from 256. This value gives you the range for each new network. For our scenario, this is calculated as follows:

|  256 |                                              |
| ---: | -------------------------------------------- |
| -192 |                                              |
|   64 | The network IDs will be in increments of 64. |

Using this number, you simply start with your assigned subnet number (as the first network ID) and then add the value (64 in this example) to find each new network ID.

|                           |               | Network ID                                        | Full Network IDs |
| ------------------------- | ------------- | ------------------------------------------------- | ---------------- |
| <p>First network<br> </p> | <p>0<br> </p> | <p>0<br>(This was the assigned<br>network ID)</p> | 192.168.1.0      |
| Second network            | 0 + 64 =      | 64                                                | 192.168.1.64     |
| Third network             | 64 + 64 =     | 128                                               | 192.168.1.128    |
| Fourth network            | 128 + 64 =    | 192                                               | 192.168.1.192    |

Find the Usable IP Address Ranges for Each Subnet

The last step is to find the IP addresses that can be assigned to host. As you begin, remember that the first and last IP addresses in the range cannot be assigned to hosts. The first available address is the host ID ( 0, 64, 128, 192 in our example), and the last IP address is used for broadcast messages.

To find the usable IP addresses, use the following rules:

* To find the starting IP address, add 1 to the network ID.
* To find the last usable IP address, subtract 2 from the network ID following the ID you are working on.\
  To complete this step for the last range, add the base network range (in our example, 64) to the last network ID and then complete this step on the number that addition produces.
*
* The broadcast address for each network is always the last IP address in the range.

| Network ID     | Math      | <p>First Available<br>Host IP Address</p> | Math      | <p>Last Available<br>Host IP Address</p> | Broadcast Address |
| -------------- | --------- | ----------------------------------------- | --------- | ---------------------------------------- | ----------------- |
| 192.168.1.0    | 0 + 1 =   | 192.168.1.1                               | 64 - 2 =  | 192.168.1.62                             | 192.168.1.63      |
| 192.168.1.64   | 64 + 1 =  | 192.168.1.65                              | 128 - 2 = | 192.168.1.126                            | 192.168.1.127     |
| 192.168.1.128  | 128 + 1 = | 192.168.1.129                             | 192 - 2 = | 192.168.1.190                            | 192.168.1.191     |
| 192.168.1.192  | 192 + 1 = | 192.168.1.193                             | 256 - 2 = | 192.168.1.254                            | 192.168.1.255     |
| 192 + 64 = 256 |           |                                           |           |                                          |                   |

Useful Charts

The following charts can be helpful when working with IPv4 network addresses and subnets.

|                      | Values for Single Octet |        |        |        |        |        |        |        |
| -------------------- | ----------------------- | ------ | ------ | ------ | ------ | ------ | ------ | ------ |
| Exponential Notation | 27                      | 26     | 25     | 24     | 23     | 22     | 21     | 20     |
| Decimal Value        | 128                     | 64     | 32     | 16     | 8      | 4      | 2      | 1      |
| Decimal Value        | 0 or 1                  | 0 or 1 | 0 or 1 | 0 or 1 | 0 or 1 | 0 or 1 | 0 or 1 | 0 or 1 |

&#x20;

| Subnet Mask Values | Decimal Equivalent |
| ------------------ | ------------------ |
| 00000000           | 0                  |
| 10000000           | 128                |
| 11000000           | 192                |
| 11100000           | 224                |
| 11110000           | 240                |
| 11111000           | 248                |
| 11111100           | 252                |
| 11111110           | 254                |
| 11111111           | 255                |

Use the following table as a shortcut guide to subnetting.

Look for patterns in the table so you can easily reproduce the table at any time. The number of subnets is the number of subnets you get by subnetting a default network address (either class B or class C in this table). For example, if you subnet a class B network using a /24 mask, you would have 256 subnets. To identify the actual number of hosts per subnet, use the formula 2n - 2, where n is the number of unmasked bits in the subnet mask.

| Masked Bits | Mask Value      | Number of Subnets | Number of Hosts per Subnet |      |
| ----------- | --------------- | ----------------- | :------------------------: | ---- |
| Approximate | Actual (2n - 2) |                   |                            |      |
| /20         | 255.255.240.0   | 16                |            4000            | 4094 |
| /21         | 255.255.248.0   | 32                |            2000            | 2046 |
| /22         | 255.255.252.0   | 64                |            1000            | 1022 |
| /23         | 255.255.254.0   | 128               |             500            | 510  |
| /24         | 255.255.255.0   | 1 or 256          |         256 or 250         | 254  |
| /25         | 255.255.255.128 | 2                 |         128 or 125         | 126  |
| /26         | 255.255.255.192 | 4                 |          64 or 60          | 62   |
| /27         | 255.255.255.224 | 8                 |          32 or 30          | 30   |
| /28         | 255.255.255.240 | 16                |          16 or 15          | 14   |
| /29         | 255.255.255.248 | 32                |              8             | 6    |
| /30         | 255.255.255.252 | 64                |              4             | 2    |

## IPV4 Configuration&#x20;

Actions you were required to perform:![Incorrect](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAsAAAALCAYAAACprHcmAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyJpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMy1jMDExIDY2LjE0NTY2MSwgMjAxMi8wMi8wNi0xNDo1NjoyNyAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNiAoV2luZG93cykiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6MTU0MzEyOTA5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6MTU0MzEyOTE5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDoxNTQzMTI4RTk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIgc3RSZWY6ZG9jdW1lbnRJRD0ieG1wLmRpZDoxNTQzMTI4Rjk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PvDFWeEAAAEASURBVHjabI+9agJBFIXvDhZC6uA2WgaSLpDnsREszCYgKvGnjqvYmc0W1oLPkyIJpAlosy8QSDMzOWe4S6bwwrfn/nHnbHIcj1siUoElWLQ3G6njNJlQnsEcpMY7VwEBc/B0HI3CIpW19plXxjo3A6KswP33cJhQta5ns4azdoVDP2CrrxdgAG7kPx7BS+K9l68BZ5IBGm5GS7+AxourspSwzPjs94NV0I6WT6BzvduFwvDz3usJ7GTgEkgE64xzRvLW7VIfIs+Mj3OeG9baKZI8GtB7qT9ZaI+HLgyWcyDKFLze7veeqnU9yw08pepvCdZ3h0M4RWWtfebpnwADAAUyxgiIGBh2AAAAAElFTkSuQmCC)Fix the subnet mask on Exec![Incorrect](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAsAAAALCAYAAACprHcmAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyJpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMy1jMDExIDY2LjE0NTY2MSwgMjAxMi8wMi8wNi0xNDo1NjoyNyAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNiAoV2luZG93cykiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6MTU0MzEyOTA5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6MTU0MzEyOTE5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDoxNTQzMTI4RTk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIgc3RSZWY6ZG9jdW1lbnRJRD0ieG1wLmRpZDoxNTQzMTI4Rjk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PvDFWeEAAAEASURBVHjabI+9agJBFIXvDhZC6uA2WgaSLpDnsREszCYgKvGnjqvYmc0W1oLPkyIJpAlosy8QSDMzOWe4S6bwwrfn/nHnbHIcj1siUoElWLQ3G6njNJlQnsEcpMY7VwEBc/B0HI3CIpW19plXxjo3A6KswP33cJhQta5ns4azdoVDP2CrrxdgAG7kPx7BS+K9l68BZ5IBGm5GS7+AxourspSwzPjs94NV0I6WT6BzvduFwvDz3usJ7GTgEkgE64xzRvLW7VIfIs+Mj3OeG9baKZI8GtB7qT9ZaI+HLgyWcyDKFLze7veeqnU9yw08pepvCdZ3h0M4RWWtfebpnwADAAUyxgiIGBh2AAAAAElFTkSuQmCC)Fix the default gateway on Exec![Incorrect](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAsAAAALCAYAAACprHcmAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyJpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMy1jMDExIDY2LjE0NTY2MSwgMjAxMi8wMi8wNi0xNDo1NjoyNyAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNiAoV2luZG93cykiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6MTU0MzEyOTA5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6MTU0MzEyOTE5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDoxNTQzMTI4RTk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIgc3RSZWY6ZG9jdW1lbnRJRD0ieG1wLmRpZDoxNTQzMTI4Rjk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PvDFWeEAAAEASURBVHjabI+9agJBFIXvDhZC6uA2WgaSLpDnsREszCYgKvGnjqvYmc0W1oLPkyIJpAlosy8QSDMzOWe4S6bwwrfn/nHnbHIcj1siUoElWLQ3G6njNJlQnsEcpMY7VwEBc/B0HI3CIpW19plXxjo3A6KswP33cJhQta5ns4azdoVDP2CrrxdgAG7kPx7BS+K9l68BZ5IBGm5GS7+AxourspSwzPjs94NV0I6WT6BzvduFwvDz3usJ7GTgEkgE64xzRvLW7VIfIs+Mj3OeG9baKZI8GtB7qT9ZaI+HLgyWcyDKFLze7veeqnU9yw08pepvCdZ3h0M4RWWtfebpnwADAAUyxgiIGBh2AAAAAElFTkSuQmCC)Enable the scope on the DHCP Server![Incorrect](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAsAAAALCAYAAACprHcmAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyJpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMy1jMDExIDY2LjE0NTY2MSwgMjAxMi8wMi8wNi0xNDo1NjoyNyAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNiAoV2luZG93cykiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6MTU0MzEyOTA5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6MTU0MzEyOTE5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDoxNTQzMTI4RTk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIgc3RSZWY6ZG9jdW1lbnRJRD0ieG1wLmRpZDoxNTQzMTI4Rjk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PvDFWeEAAAEASURBVHjabI+9agJBFIXvDhZC6uA2WgaSLpDnsREszCYgKvGnjqvYmc0W1oLPkyIJpAlosy8QSDMzOWe4S6bwwrfn/nHnbHIcj1siUoElWLQ3G6njNJlQnsEcpMY7VwEBc/B0HI3CIpW19plXxjo3A6KswP33cJhQta5ns4azdoVDP2CrrxdgAG7kPx7BS+K9l68BZ5IBGm5GS7+AxourspSwzPjs94NV0I6WT6BzvduFwvDz3usJ7GTgEkgE64xzRvLW7VIfIs+Mj3OeG9baKZI8GtB7qT9ZaI+HLgyWcyDKFLze7veeqnU9yw08pepvCdZ3h0M4RWWtfebpnwADAAUyxgiIGBh2AAAAAElFTkSuQmCC)Fix the 003 Router option on the DHCP Server![Incorrect](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAsAAAALCAYAAACprHcmAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyJpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMy1jMDExIDY2LjE0NTY2MSwgMjAxMi8wMi8wNi0xNDo1NjoyNyAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNiAoV2luZG93cykiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6MTU0MzEyOTA5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6MTU0MzEyOTE5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDoxNTQzMTI4RTk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIgc3RSZWY6ZG9jdW1lbnRJRD0ieG1wLmRpZDoxNTQzMTI4Rjk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PvDFWeEAAAEASURBVHjabI+9agJBFIXvDhZC6uA2WgaSLpDnsREszCYgKvGnjqvYmc0W1oLPkyIJpAlosy8QSDMzOWe4S6bwwrfn/nHnbHIcj1siUoElWLQ3G6njNJlQnsEcpMY7VwEBc/B0HI3CIpW19plXxjo3A6KswP33cJhQta5ns4azdoVDP2CrrxdgAG7kPx7BS+K9l68BZ5IBGm5GS7+AxourspSwzPjs94NV0I6WT6BzvduFwvDz3usJ7GTgEkgE64xzRvLW7VIfIs+Mj3OeG9baKZI8GtB7qT9ZaI+HLgyWcyDKFLze7veeqnU9yw08pepvCdZ3h0M4RWWtfebpnwADAAUyxgiIGBh2AAAAAElFTkSuQmCC)Configure Exec for DHCPExplanation

Complete this lab as follows:

1. From CorpServer, verify the networking configuration as follows:
   1. In the notification area of CorpServer, notice that the Network icon appears normal.
   2. Select the Network icon.\
      Notice that this machine is connected to CorpNet.com and has a connection to the internet.
   3. Right-click the Network icon and select Open Network and Sharing Center.\
      The information from this dialog confirms that CorpServer is connected to the local network and the internet.
2. From CorpServer, use ping to verify that the CorpServer and the ISP can be reached as follows:
   1. In the Search field on the taskbar, enter cmd.
   2. Under Best match, right-click Command Prompt and select Run as Administrator.
   3. At the command prompt, type ping corpserver and press Enter.\
      A successful reply is received.
   4. Type ping 65.86.1.1 to ping the ISP and press Enter.\
      A successful reply is received.
3. From CorpServer, use ipconfig and tracert to examine the networking information for the vEthernet (External) and verify that the path to the ISP is using the same default gateway as follows:
   1. At the command prompt, type ipconfig /all and press Enter.
   2. Maximize the command prompt window.
   3. From the information shown regarding the vEthernet (External) card, you learn the following:
      * DHCP Enabled: No\
        This indicates that the server is configured with a static IP address and is not enabled for DHCP
      * IPv4 address: 192.168.0.10
      * Subnet mask: 255.255.255.00\
        The server is using the default subnet mask for the Class C IP address range.
      * Default gateway: 192.168.0.5\
        The router's internal interface is configured as the default gateway.
   4. Type tracert 65.86.1.1 and press Enter.\
      This verifies a path to the ISP through the default gateway of 192.168.0.5.
4. From Exec, verify the status of the networking configuration as follows:
   1. From the top navigation tabs, select Floor 1 Overview.
   2. Under Executive Office, select Exec.
   3. In the notification area, notice that the Network icon has a yellow warning sign with an exclamation point. This indicates a connection to the local network, but no access to the internet.
   4. Select the Network icon.\
      The network card is attached to an unidentified network and has no internet connection.
   5. Right-click the Network icon and select Open Network & Internet settings.\
      This confirms that Exec is connected to the local network, but has no internet access.
   6. Close Network & Internet Settings.
5. Use ping to test the connections between CorpServer and the ISP as follows:
   1. In Search field on the taskbar, enter cmd.
   2. Under Best match, right-click Command Prompt and select Run as Administrator.
   3. At the command prompt, type ping exec and press Enter.\
      A successful reply is received.
   4. Type ping 65.86.1.1 and press Enter.\
      The request timed out.
   5. Type ping corpserver and press Enter.\
      The request timed out.\
      These ping tests indicate that although Exec has a valid connection to the network, it can't communicate with CorpServer or the ISP.
6. Using ipconfig, determine if any problems may exist as follows:
   1.  From the command prompt, type ipconfig /all and press Enter.\
       The following information about the Ethernet connection on Exec is given:

       * DHCP Enabled: No
       * IPv4 Address: 192.168.0.62
       * Subnet Mask: 255.255.255.240
       * Default Gateway: 192.168.0.4

       \
       This information provides you with at least two clues to the problem:

       * Although DHCP is being used on the network, ipconfig is showing that this workstation is not getting its IP address from the DHCP server.
       * The subnet mask reveals that the IPv4 IP address is not on the same network as the the default gateway.
       * In addition, the subnet mask is not the default subnet mask for the Class C IP address range being used. With 255.255.255.240 as a subnet mask, the network would only include addresses from 192.168.0.48 to 192.168.0.63. The IP address for CorpServer (192.168.0.10) and the ISP (65.86.1.1) fall outside of this range. The information received in step 3 confirms that the subnet mask for the Class C IP address range is 255.255.255.0.
7. Use ping to provide the correct subnet mask for Exec and retest the machines network connections as follows:
   1. Right-click the Network icon and select Open Network & Internet settings.
   2. Select Change adapter options.
   3. Right-click Ethernet and select Properties.
   4. Select Internet Protocol Version 4 (TCP/IP).
   5. Select Properties.
   6. In the Subnet mask field, enter 255.255.255.0 as the subnet.
   7. Click OK.
   8. Leave all other windows open.
   9. At the command prompt, type ping exec and press Enter.\
      A successful reply is received.
   10. Type ping corpserver and press Enter.\
       A successful reply is received.
   11. Type ping 65.86.1.1 and press Enter.\
       The request timed out for the ISP.\
       Notice that there are no changes to the Network icon. This indicates that you only have local connectivity.
8. Use tracert to determine what the issue is as follows:
   1. At the command prompt, type tracert 65.86.1.1 and press Enter.\
      The request timed out indicates the following:
      * The ICMP packets are not returning from the first hop (gateway) in its path to the ISP. In other words, Exec is not finding the gateway.
      * The gateway address on Exec is not configured correctly. The gateway address (router) on the network diagram is 192.168.0.5.
9. Enter the correct gateway address on Exec, verify the internet connection is available, and use tracert to test the connection as follows:
   1. Return to the Ethernet Properties dialog.
   2. Make sure Internet Protocol Version 4 (TCP/IP) is selected.
   3. Select Properties.
   4. In the Default gateway field, enter 192.168.0.5
   5. Click OK.
   6. Click Close.\
      Notice that the Network icon indicates a connection to the internet is established.
   7. At the command prompt, type tracert 65.86.1.1 and press Enter.\
      tracert now returns a path to the ISP through the gateway. Since you have established a valid connection to the internet, leave Exec configured to use a static address for now so you can turn your attention to troubleshooting the computer in Office 1.
10. From Office1, use ping to test network connections to Office1, CorpServer, and the ISP as follows:
    1. From the top navigation tabs, select Floor 1 Overview.
    2. Under Office 1, select Office1.
    3. Select the Network icon.\
       Office1 is connected to the unidentified network and has no internet access.
    4. In Search field on the taskbar, enter cmd.
    5. Under Best match, right-click Command Prompt and select Run as Administrator.
    6. At the command prompt, type ping Office1 and press Enter.\
       A successful reply is received.
    7. Type ping corpserver and press Enter.\
       The request times out.
    8. Type Ping 65.86.1.1 and press Enter.\
       The request times out.\
       These tests indicate that Office1 has a valid connection to the local network but not to any computer on other networks.
11. Use ipconfig to help determine what the issue may is as follows:
    1. At the command prompt, type ipconfig /all and press Enter.\
       The following information about the Ethernet connection is provided:
       * DHCP Enabled: Yes\
         This workstation is configured to use a DHCP server.
       * Autoconfiguration IPv4 Address: An address is shown.\
         The address shown is in the Automatic Private IP Addressing (APIPA) range of 169.254.0.1 to 169.254.255.254. This means that the workstation is not receiving an IP address from the DHCP server. Therefore, the workstation can only communicate with other hosts on the local network that are using APIPA.
       * Subnet mask: 255.255.0.0\
         This is the default subnet mask for the APIPA address and is different from the subnet mask being used on CorpServer.
       * Default gateway: (blank).\
         This means that communication is limited to workstations on the local network.
       * DHCP Server line is not shown. This means that the workstation was unable to contact the DHCP server.
       * DNS Servers line is not shown for IPv4.
       * Since DHCP is enabled, the rest of the information should have come from the DHCP server. Therefore, you can conclude that there is an issue with the DHCP server.
12. From CorpServer, connect to CorpDHCP as follows:
    1. From the top navigation tabs, select Floor 1 Overview.
    2. Under Networking Closet, select CorpServer.
    3. In Hyper-V Manager, select CORPSERVER.
    4. Maximize the window for easier viewing.
    5. Under Virtual Machines, right-click CorpDHCP and select Connect.
13. Activate Scope \[192.168.0.1] Subnet1 as follows:
    1. In Server Manager, select Tools > DHCP.
    2. In the left pane, expand CorpDHCP.CorpNet.com.
    3. Expand IPv4.\
       Notice that the scope folder shows a down arrow indicating that the scope is not active.
    4. Right-click Scope \[192.168.0.1] Subnet1 and select Activate.\
       The down arrow is removed from the folder icon.
    5. Leave the DHCP console open.
14. From Office1, renew the network card's setting using ipconfig as follows:
    1. From the top navigation tabs, select Floor 1 Overview.
    2. Under Office 1, select Office1.
    3. At the command prompt, type ipconfig /renew and press Enter.\
       Since this machine is configured to get its networking information from the DHCP and the scope is active, a new IP address and networking information is received for the Ethernet connection.
    4. Type ipconfig /all and press Enter.\
       Examine the results of the Ethernet configuration.\
       You should notice a line for the default gateway, DNS server, and DHCP server, along with a new IP address that is now within the DHCP scope for the local network.
15. Use ping and tracert to test the connections to CorpServer and the ISP as follows:
    1. At the command prompt, type ping corpserver and press Enter.\
       A successful reply is received.
    2. Type ping 65.86.1.1 and press Enter.\
       The request times out.
    3. Type tracert 65.86.1.1 and press Enter.\
       The request times out.\
       From this, you see that although the computer can now communicated with other devices on the same network, it still cannot communicate with the ISP.
16. Use ipconfig to find the next issue as follows:
    1. At the command prompt, type ipconfig /all and press Enter.\
       As you examine the results, you notice that the default gateway is set to 192.168.0.2, but you know it should be 192.168.0.5.\
       Since this address is coming from DHCP, you need to check the DHCP server.
17. From CorpDHCP, change the IP address for the default gateway to 192.168.0.5 as follows:
    1. From the top navigation tabs, select Floor 1 Overview.
    2. Under Networking Closet, select CorpServer.
    3. In the DHCP console, expand Scope \[192.168.0.1] Subnet1.
    4. From the right pane, right-click Scope Options and select Configure Options.
    5. Select 003 Router.
    6. From the bottom pane, select 192.168.0.2.
    7. Select Remove.
    8. In the IP Address field, enter 192.168.0.5.
    9. Select Add.
    10. Click OK.
18. From Office1, renew and test the IP address information as follows:
    1. From the top navigation tabs, select Floor 1 Overview.
    2. Under Office 1, select Office1.
    3. At the command prompt, type ipconfig /renew and press Enter.\
       New IP address information is received from the DHCP server, reconfiguring the settings for the Ethernet connection.
    4. Type ipconfig /all and press Enter.\
       Check the Ethernet configuration and notice the line for the default gateway is now configured correctly to 192.168.0.5.
    5. Verify that the Network icon and Network & Internet settings both indicate that Office1 is connected to the local network and the internet.
    6. At the command prompt, type ping 65.86.1.1 and press Enter.\
       A successful reply is received from the ISP.
19. From Exec, reconfigure the Ethernet connection to use DHCP as follows:
    1. From the top navigation tabs, select Floor 1 Overview.
    2. Under Executive Office, select Exec.
    3. Right-click the Network icon and select Open Network & Internet settings.
    4. Select Change adapter options.
    5. Right-click Ethernet and select Properties.
    6. Select Internet Protocol Version 4 (TCP/IP).
    7. Select Properties.
    8. Select Obtain an IP address automatically.
    9. Select Obtain DNS server address automatically.
    10. Click OK.
    11. Click Close.
20. Verify the network settings for Exec as follows:
    1. In Search field on the taskbar, enter cmd.
    2. Under Best match, right-click Command Prompt and select Run as Administrator.
    3. At the command prompt, type ipconfig /all and press Enter.\
       The results show that the IP address, default gateway, DNS Server, and DHCP Server are provided by the DHCP server.\
       The Network icon and Network & Internet settings indicate that Exec is connected to the corporate network with full internet access.
    4. At the command prompt, type tracert 65.86.1.1 and press Enter.\
       A successful route to the ISP is returned through the gateway. The network is now fully functional, and your troubleshooting is complete.



## Configure IPv4 part 2

Actions you were required to perform:![Incorrect](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAsAAAALCAYAAACprHcmAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyJpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMy1jMDExIDY2LjE0NTY2MSwgMjAxMi8wMi8wNi0xNDo1NjoyNyAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNiAoV2luZG93cykiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6MTU0MzEyOTA5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6MTU0MzEyOTE5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDoxNTQzMTI4RTk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIgc3RSZWY6ZG9jdW1lbnRJRD0ieG1wLmRpZDoxNTQzMTI4Rjk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PvDFWeEAAAEASURBVHjabI+9agJBFIXvDhZC6uA2WgaSLpDnsREszCYgKvGnjqvYmc0W1oLPkyIJpAlosy8QSDMzOWe4S6bwwrfn/nHnbHIcj1siUoElWLQ3G6njNJlQnsEcpMY7VwEBc/B0HI3CIpW19plXxjo3A6KswP33cJhQta5ns4azdoVDP2CrrxdgAG7kPx7BS+K9l68BZ5IBGm5GS7+AxourspSwzPjs94NV0I6WT6BzvduFwvDz3usJ7GTgEkgE64xzRvLW7VIfIs+Mj3OeG9baKZI8GtB7qT9ZaI+HLgyWcyDKFLze7veeqnU9yw08pepvCdZ3h0M4RWWtfebpnwADAAUyxgiIGBh2AAAAAElFTkSuQmCC)Configure the server with a manual IP address![Incorrect](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAsAAAALCAYAAACprHcmAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyJpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMy1jMDExIDY2LjE0NTY2MSwgMjAxMi8wMi8wNi0xNDo1NjoyNyAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNiAoV2luZG93cykiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6MTU0MzEyOTA5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6MTU0MzEyOTE5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDoxNTQzMTI4RTk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIgc3RSZWY6ZG9jdW1lbnRJRD0ieG1wLmRpZDoxNTQzMTI4Rjk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PvDFWeEAAAEASURBVHjabI+9agJBFIXvDhZC6uA2WgaSLpDnsREszCYgKvGnjqvYmc0W1oLPkyIJpAlosy8QSDMzOWe4S6bwwrfn/nHnbHIcj1siUoElWLQ3G6njNJlQnsEcpMY7VwEBc/B0HI3CIpW19plXxjo3A6KswP33cJhQta5ns4azdoVDP2CrrxdgAG7kPx7BS+K9l68BZ5IBGm5GS7+AxourspSwzPjs94NV0I6WT6BzvduFwvDz3usJ7GTgEkgE64xzRvLW7VIfIs+Mj3OeG9baKZI8GtB7qT9ZaI+HLgyWcyDKFLze7veeqnU9yw08pepvCdZ3h0M4RWWtfebpnwADAAUyxgiIGBh2AAAAAElFTkSuQmCC)Configure 192.168.10.10 as the IP address![Incorrect](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAsAAAALCAYAAACprHcmAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyJpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMy1jMDExIDY2LjE0NTY2MSwgMjAxMi8wMi8wNi0xNDo1NjoyNyAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNiAoV2luZG93cykiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6MTU0MzEyOTA5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6MTU0MzEyOTE5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDoxNTQzMTI4RTk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIgc3RSZWY6ZG9jdW1lbnRJRD0ieG1wLmRpZDoxNTQzMTI4Rjk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PvDFWeEAAAEASURBVHjabI+9agJBFIXvDhZC6uA2WgaSLpDnsREszCYgKvGnjqvYmc0W1oLPkyIJpAlosy8QSDMzOWe4S6bwwrfn/nHnbHIcj1siUoElWLQ3G6njNJlQnsEcpMY7VwEBc/B0HI3CIpW19plXxjo3A6KswP33cJhQta5ns4azdoVDP2CrrxdgAG7kPx7BS+K9l68BZ5IBGm5GS7+AxourspSwzPjs94NV0I6WT6BzvduFwvDz3usJ7GTgEkgE64xzRvLW7VIfIs+Mj3OeG9baKZI8GtB7qT9ZaI+HLgyWcyDKFLze7veeqnU9yw08pepvCdZ3h0M4RWWtfebpnwADAAUyxgiIGBh2AAAAAElFTkSuQmCC)Configure 255.255.255.0 as the mask![Incorrect](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAsAAAALCAYAAACprHcmAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyJpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMy1jMDExIDY2LjE0NTY2MSwgMjAxMi8wMi8wNi0xNDo1NjoyNyAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNiAoV2luZG93cykiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6MTU0MzEyOTA5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6MTU0MzEyOTE5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDoxNTQzMTI4RTk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIgc3RSZWY6ZG9jdW1lbnRJRD0ieG1wLmRpZDoxNTQzMTI4Rjk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PvDFWeEAAAEASURBVHjabI+9agJBFIXvDhZC6uA2WgaSLpDnsREszCYgKvGnjqvYmc0W1oLPkyIJpAlosy8QSDMzOWe4S6bwwrfn/nHnbHIcj1siUoElWLQ3G6njNJlQnsEcpMY7VwEBc/B0HI3CIpW19plXxjo3A6KswP33cJhQta5ns4azdoVDP2CrrxdgAG7kPx7BS+K9l68BZ5IBGm5GS7+AxourspSwzPjs94NV0I6WT6BzvduFwvDz3usJ7GTgEkgE64xzRvLW7VIfIs+Mj3OeG9baKZI8GtB7qT9ZaI+HLgyWcyDKFLze7veeqnU9yw08pepvCdZ3h0M4RWWtfebpnwADAAUyxgiIGBh2AAAAAElFTkSuQmCC)Configure 192.168.10.5 as the default gateway![Incorrect](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAsAAAALCAYAAACprHcmAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyJpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMy1jMDExIDY2LjE0NTY2MSwgMjAxMi8wMi8wNi0xNDo1NjoyNyAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNiAoV2luZG93cykiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6MTU0MzEyOTA5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6MTU0MzEyOTE5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDoxNTQzMTI4RTk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIgc3RSZWY6ZG9jdW1lbnRJRD0ieG1wLmRpZDoxNTQzMTI4Rjk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PvDFWeEAAAEASURBVHjabI+9agJBFIXvDhZC6uA2WgaSLpDnsREszCYgKvGnjqvYmc0W1oLPkyIJpAlosy8QSDMzOWe4S6bwwrfn/nHnbHIcj1siUoElWLQ3G6njNJlQnsEcpMY7VwEBc/B0HI3CIpW19plXxjo3A6KswP33cJhQta5ns4azdoVDP2CrrxdgAG7kPx7BS+K9l68BZ5IBGm5GS7+AxourspSwzPjs94NV0I6WT6BzvduFwvDz3usJ7GTgEkgE64xzRvLW7VIfIs+Mj3OeG9baKZI8GtB7qT9ZaI+HLgyWcyDKFLze7veeqnU9yw08pepvCdZ3h0M4RWWtfebpnwADAAUyxgiIGBh2AAAAAElFTkSuQmCC)Configure the server with a manual DNS server address![Incorrect](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAsAAAALCAYAAACprHcmAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyJpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMy1jMDExIDY2LjE0NTY2MSwgMjAxMi8wMi8wNi0xNDo1NjoyNyAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNiAoV2luZG93cykiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6MTU0MzEyOTA5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6MTU0MzEyOTE5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDoxNTQzMTI4RTk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIgc3RSZWY6ZG9jdW1lbnRJRD0ieG1wLmRpZDoxNTQzMTI4Rjk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PvDFWeEAAAEASURBVHjabI+9agJBFIXvDhZC6uA2WgaSLpDnsREszCYgKvGnjqvYmc0W1oLPkyIJpAlosy8QSDMzOWe4S6bwwrfn/nHnbHIcj1siUoElWLQ3G6njNJlQnsEcpMY7VwEBc/B0HI3CIpW19plXxjo3A6KswP33cJhQta5ns4azdoVDP2CrrxdgAG7kPx7BS+K9l68BZ5IBGm5GS7+AxourspSwzPjs94NV0I6WT6BzvduFwvDz3usJ7GTgEkgE64xzRvLW7VIfIs+Mj3OeG9baKZI8GtB7qT9ZaI+HLgyWcyDKFLze7veeqnU9yw08pepvCdZ3h0M4RWWtfebpnwADAAUyxgiIGBh2AAAAAElFTkSuQmCC)Configure 192.168.10.11 as the preferred DNS server![Incorrect](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAsAAAALCAYAAACprHcmAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyJpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMy1jMDExIDY2LjE0NTY2MSwgMjAxMi8wMi8wNi0xNDo1NjoyNyAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNiAoV2luZG93cykiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6MTU0MzEyOTA5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6MTU0MzEyOTE5ODJBMTFFMzgwODNFNTQ3M0NFMzNBRTQiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDoxNTQzMTI4RTk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIgc3RSZWY6ZG9jdW1lbnRJRD0ieG1wLmRpZDoxNTQzMTI4Rjk4MkExMUUzODA4M0U1NDczQ0UzM0FFNCIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PvDFWeEAAAEASURBVHjabI+9agJBFIXvDhZC6uA2WgaSLpDnsREszCYgKvGnjqvYmc0W1oLPkyIJpAlosy8QSDMzOWe4S6bwwrfn/nHnbHIcj1siUoElWLQ3G6njNJlQnsEcpMY7VwEBc/B0HI3CIpW19plXxjo3A6KswP33cJhQta5ns4azdoVDP2CrrxdgAG7kPx7BS+K9l68BZ5IBGm5GS7+AxourspSwzPjs94NV0I6WT6BzvduFwvDz3usJ7GTgEkgE64xzRvLW7VIfIs+Mj3OeG9baKZI8GtB7qT9ZaI+HLgyWcyDKFLze7veeqnU9yw08pepvCdZ3h0M4RWWtfebpnwADAAUyxgiIGBh2AAAAAElFTkSuQmCC)Configure 192.168.0.11 as the alternate DNS serverExplanation

Complete this lab as follows:

1. From the taskbar, right-click the Network icon and select Open Network and Sharing Center.
2. On the left, select Change adapter settings.
3. Right-click vEthernet (External) and select Properties.
4. Select Internet Protocol Version 4 (TCP/IPv4).
5. Select Properties.
6. Select Use the following IP address.
7. In the IP address field, enter 192.168.10.10.
8. Click in the Subnet mask field to allow the default subnet mask to populate the field.
9. In the Default gateway field, enter 192.168.10.5.
10. Make sure Use the following DNS server addresses is selected.
11. In the Preferred DNS server field, enter 192.168.10.11.
12. In the Alternate DNS server field, enter 192.168.0.11.
13. Click OK.
14. Click Close.
15. In the Search the web and Windows field, enter cmd.
16. Under Best match, right-click Command Prompt and select Run as Administrator.
17. At the command prompt, type ipconfig /all and press Enter.
18. Make sure vEthernet (external) is configured as specified above.

