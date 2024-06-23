# DHCP Policies

| Term          | Definition                                                                                                                                      |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| DHCP policies | A feature in Windows Server 2016 that gives administrators the ability to customize IP address lease options with conditions based on criteria. |

* DHCP Policy scenarios
* DHCP Policy conditions

DHCP Policy Scenarios

Granular control of DHCP scopes provides several benefits. With granular control, you can create policies that:

* Use a block of IP addresses for a specific client types, such as desktops, printers, or VOIP phones.
* Hand out shorter lease times to mobile devices compared to wired devices.

DHCP Policy Conditions

You can apply DHCP policies based on certain conditions. The following table describes some common conditions.

<table><thead><tr><th width="86">Condition</th><th width="936">Description</th></tr></thead><tbody><tr><td>User Class</td><td>All the computers located in the accounting department of an organization is an example of a user class.</td></tr><tr><td>MAC Address</td><td>MAC addresses from the same manufacturer often have the same prefix. Wildcards can identify a group of computers based on MAC address. For example, 12ab34* identifies all devices that start with that MAC address.</td></tr><tr><td>Client Identifier</td><td>Client Identifier is usually based on the MAC address, but could include other identifiers.</td></tr><tr><td>Domain Name</td><td>You can use the Fully Qualified Domain Name as a condition. For example, all the computers in accounting.corpnet.xyz might have a condition.</td></tr><tr><td>Relay Agent</td><td>DHCP requests that are forwarded by a DHCP agent can have a condition. For example, you might want those clients to have a shorter lease time than other clients on a network.</td></tr></tbody></table>
