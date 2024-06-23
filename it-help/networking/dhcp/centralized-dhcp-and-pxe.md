# Centralized DHCP and PXE

| Term                   | Definition                                                                                                                                                                                                          |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DHCP Relay Agent       | A device that listens for broadcast DHCPDISCOVER and DHCPREQUEST messages and forwards them to a DHCP server on another subnet.                                                                                     |
| DHCP IP Helper Address | The IP Helper address lets routers relay User Datagram Protocol (UDP) requests when necessary. It makes the router a middleman and allows a broadcast to pass through a router to its destination.                  |
| PXE                    | Preboot execution environment (PXE) allows computers to boot remotely through a network interface. PXE enables a client machine to boot from a server independent of the hard disks and installed operating system. |

* DHCP Relay Agent
* DHCP IP Helper Table

DHCP Relay Agent and IP Helper Table

Because a DHCP client doesn't have an IP address assigned when it initially boots, it must use broadcast frames to communicate with a DHCP server. If the server is on a different subnet than the client, then the DHCP requests sent by the client will not reach the server because broadcast frames are dropped by network routers. If your network is configured in this manner, you can implement one of the following mechanisms to forward DHCP broadcasts through network routers to a remote DHCP server on a different subnet.

The following table provides details about Relay Agent and the IP Helper Table.

| Option                                              | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| --------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DHCP Relay Agent                                    | <p>If you use a Windows server in your network, then you can install the Routing and Remote Access service (RRAS) role on the server and enable the DHCP Relay Agent Role service. The DHCP Relay Agent service sends the DHCP packets it receives to a remote DHCP server on a different subnet. To configure the DHCP Relay service, you must:</p><ul><li>Specify which server network interface the agent listens on for DHCP messages.</li><li>Specify the IP address of the remote DHCP server the agent should forward DHCP messages to.</li></ul> |
| <p>IP Helper Table<br>RFC 1542 Compliant Router</p> | <p>An RFC 1542-compliant router listens for DHCP traffic and routes any received DHCP frames to the appropriate subnet. For example, on a Cisco router, you can enable this functionality by using the ip helper-address command. The syntax for this command is:</p><p>ip helper-address <em>[server_address]</em></p><p>Replace <em>[server_address]</em> with the IP address of the remote DHCP server.</p>                                                                                                                                           |

* PXE on the same server as DHCP
* PXE when DHCP is on another server

PXE on the Same Server as DHCP

When a Microsoft DHCP server and Windows Deployment Services (WDS) are on the same server and all WDS clients are on the same network as the WDS server, you don’t have to change any DHCP settings.

PXE when DHCP is on Another Server

When you are using Windows Deployment Services (WDS) to install Windows OSs on computers over the network with DHCP is on one server and your image file is on another server, you have to configure additional DHCP options.

| DHCP Option | Description                                                                                        |
| ----------- | -------------------------------------------------------------------------------------------------- |
| Option 60   | PXE-enabled network cards add the DHCP option 60 to their DHCP Discover packets.                   |
| Option 66   | Boot Server Host Name supplies the WDS server’s IP address or server name.                         |
| Option 67   | Bootfile Name is the name and path the boot file WDS clients need to start remote OS installation. |

## Config a DHCP relay agent

1. Add the DHCP relay agent protocol as follows:
   1. From Server Manager, select Tools > Routing and Remote Access.
   2. From the left pane, expand IPv4.
   3. Right-click General and select New Routing Protocol.
   4. Select DHCP Relay Agent.
   5. Click OK.
2. Add and configure a relay agent interface as follows:
   1. From the left pane, right-click DHCP Relay Agent and select New Interface.
   2. Select Ethernet.
   3. Click OK.
   4. Make sure Relay DHCP packets is selected.
   5. In the Boot threshold field, enter 0.
   6. Click OK.
3. Identify the DHCP server as follows:
   1. From the left pane, right-click DHCP Relay Agent and select Properties.
   2. In the Server address field, enter 192.168.0.14.
   3. Select Add.
   4. Click OK.
4. Renew the TCP/IP address as follows:
   1. From the location tabs at the top, select Building B.
   2. Under Building B, select Inside.
   3. Under Manager Office, select Exec2.
   4. In the Search the web and Windows field, enter command and press Enter.
   5. In the command prompt, type ipconfig /renew and press Enter.\
      The computer should receive an address on the 192.168.10 network.
   6. In the navigation area, select the Network icon to view the connection status and verify that CorpNet.com is connected.
