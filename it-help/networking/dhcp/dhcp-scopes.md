# DHCP Scopes

| Term                | Definition                                                                                                                                                                                                                               |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DHCP Scopes         | A pool of IP addresses and other IP configuration parameters from which a DHCP server leases addresses to DHCP scopes.                                                                                                                   |
| DHCP Lease Duration | A parameter of a DHCP IP address lease that specifies how long a DHCP client can keep an address.                                                                                                                                        |
| DHCP Lease Renewal  | The process of a DHCP client renewing its IP address lease by using unicast DHCPREQUEST messages.                                                                                                                                        |
| DHCP Filter         | A DHCP server feature that allows administrators to restrict which computers on a network are leased IP addresses.                                                                                                                       |
| DHCP Reservation    | An IP address associated with reserving DHCP clients' MAC addresses to ensure that when a client requests an IP address, it always receives the same one with any configured options.                                                    |
| DHCP Exclusions     | One or more IP addresses within a DHCP scope that are not allocated by the DHCP Server service. Exclusions ensure that the specified IP addresses will not be offered to clients by the DHCP server as part of the general address pool. |

* DHCP server status
* Scopes
* Exclusions
* Reservations
* Filters

DHCP Status

The DHCP console provides context-sensitive icons to reflect DHCP server status as follows:

| Status                                                                                                                                                                                                                                                                                                | Description                                                                                                                                                                                |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| ![Server icon indicating that a DHCP server has been added to the console](https://cdn.testout.com/\_version\_405/serverpro2016network-741v4-en-us/en-us/resources/text/t\_dhcp\_scopes\_spn4/dhcp\_console.png)                                                                                      | A DHCP server has been added to the console.                                                                                                                                               |
| ![An icon with a check mark in a green circle indicates that the DHCP server is connected and authorized](https://cdn.testout.com/\_version\_405/serverpro2016network-741v4-en-us/en-us/resources/text/t\_dhcp\_scopes\_spn4/dhcp\_authorized.png)                                                    | A check mark in a green circle indicates that the DHCP server is connected and authorized.                                                                                                 |
| ![An icon with a red down arrow indicates that the DHCP server is connected but not authorized](https://cdn.testout.com/\_version\_405/serverpro2016network-741v4-en-us/en-us/resources/text/t\_dhcp\_scopes\_spn4/dhcp\_not\_authorized.png)                                                         | A red down arrow indicates that the DHCP server is connected but not authorized.                                                                                                           |
| ![An icon with a horizontal white line inside red circle indicates that the DHCP server is connected, but the user does not have administrative credentials](https://cdn.testout.com/\_version\_405/serverpro2016network-741v4-en-us/en-us/resources/text/t\_dhcp\_scopes\_spn4/dhcp\_not\_admin.png) | A horizontal white line inside a red circle indicates that the DHCP server is connected, but the current user does not have the administrative credentials necessary to manage the server. |
| ![An icon with an exclamation sign inside a yellow triangle indicates that 90 percent of available addresses for server scopes are either in use or leased](https://cdn.testout.com/\_version\_405/serverpro2016network-741v4-en-us/en-us/resources/text/t\_dhcp\_scopes\_spn4/dhcp\_90\_percent.png) | An exclamation sign inside a yellow triangle indicates that 90 percent of available addresses for server scopes are either in use or leased.                                               |
| ![An icon with an exclamation sign inside a blue circle indicates that 100 percent of available addresses for server scopes are either in use or leased](https://cdn.testout.com/\_version\_405/serverpro2016network-741v4-en-us/en-us/resources/text/t\_dhcp\_scopes\_spn4/dhcp\_no\_addresses.png)  | An exclamation sign inside a blue circle indicates that 100 percent of available addresses for server scopes are either in use or leased.                                                  |

DHCP Scopes

To configure a DHCP server to deliver IP addresses, you must configure the scope. A _scope_ is the range of IP addresses that the DHCP server can assign to clients. Be aware of the following when working with scopes:

* There is only one scope allowed per network segment.
* The scope must be activated before the DHCP server will assign addresses to clients. After you activate a scope, do not change its range of IP addresses.
* A scope has a subnet mask that determines the subnet for a given IP address. You cannot change the subnet mask in an existing DHCP scope. To change the subnet mask used by a scope, you must delete and recreate the scope.
* Lease duration values are part of the scope properties and determine the length of time a client can use the IP address leased through DHCP.

DHCP Exclusions

A DHCP scope defines a range of IP addresses that the DHCP server can assign to clients on a subnet. You can use exclusions to prevent the DHCP server from assigning certain IP addresses within the range specified in the scope.

| Mechanism | Description                                                                                                                                                                                                                                          |
| --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Exclusion | <ul><li>Exclusions identify IP addresses within the range that are excluded from assignment, such as an address statically assigned to a server or router.</li><li>Set exclusions by right-clicking Address Pool and selecting Exceptions.</li></ul> |

DHCP Reservations

Use reservations to make sure a specific client always receives the same IP address from the DHCP server. For example, you could configure a reservation to ensure a network printer is always assigned the same IP address.

| Mechanism   | Description                                                                                                                                                                                                                                                                                                  |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Reservation | <ul><li>The reservation associates the client's MAC address with the IP address the client should receive.</li><li>You can use the ipconfig /all command to determine the computer's MAC address.</li><li>You can configure client options for the individual computers listed under reservations.</li></ul> |

DHCP Filters

Filters control which computers can be DHCP server clients. Filters use the computer's MAC address.

| Mechanism | Description                                                                                                                                                                                                                                                                  |
| --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Filter    | <p>There are two filter types:</p><ul><li>Allow specifies the computers that can be DHCP server clients.</li><li>Deny specifies the computers that cannot be DHCP server clients.</li></ul><p>Enable the Allow or Deny filter and then specify the MAC and IP addresses.</p> |

## Setting a new Address Pool scope

Following are steps an expert might take to complete this lab:

1. From Hyper-V Manager, select CORPSERVER.
2. Expand the window to view all virtual machines.
3. Right-click CorpDCHP and select Connect.
4. From Server Manager, select Tools > DHCP.
5. In the left pane, expand CorpDHCP.CorpNet.com.
6. Expand the IPv4 protocol.
7. Expand the Scope folder.
8. Right-click the Address Pool node and select New Exclusion Range.
9. In the Start IP address field, enter the _starting IP address_.
10. In the End IP address field, enter the _ending IP address_.
11. Click Add.
12. Click Close to close the Add Exclusion Range dialog.

## DHCP Reservations

Following are steps an expert might use to complete this lab:

1. From Hyper-V Manager, select CORPSERVER.
2. Expand the window to view all virtual machines.
3. Right-click CorpDCHP and select Connect.
4. From Server Manager, select Tools > DHCP.
5. In the left pane, expand CorpDHCP.CorpNet.com.
6. Expand the IPv4 protocol.
7. Expand the Scope folder.
8. Right-click Reservations and select New Reservation.
9. In the Reservation name field, enter a _reservation name_ (such as the computer name).
10. In the IP address field, enter the _IP address_.
11. In the MAC address field, enter the _MAC address_. For Ethernet, the MAC address will look like c8ba99cd8012 or c8-ba-99-cd-80-12.
12. Under Supported types, select DHCP only as needed.
13. Select Add to create the client reservation.
14. Repeat steps 9-  13 for additional reservations.
15. Select Close.

