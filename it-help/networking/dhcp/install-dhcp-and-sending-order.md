# Install DHCP and Sending Order



| Terms                                      | Definitions                                                                                                                                                                                                             |
| ------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Dynamic Host Configuration Protocol (DHCP) | A component of the TCP/IP protocol suite used to assign an IP address to a host automatically from a preconfigured pool of addresses.                                                                                   |
| DHCP Server Authorization                  | The process of enabling a DHCP server in a domain environment to prevent rogue DHCP servers from functioning on the network.                                                                                            |
| DHCP Server                                | A computer that runs the DHCP Server service, holds information about available IP addresses and related configuration information as defined by the systems administrator, and responds to requests from DHCP clients. |
| DHCP Client                                | A computer that gets its IP configuration information using DHCP from a DHCP server.                                                                                                                                    |
| Address Pool                               | Available IP addresses form an address pool within the DHCP scope. The pooled addresses are available for the DHCP server to dynamically assign to DHCP clients.                                                        |
| Broadcast                                  | A packet addressed to all computers on the network.                                                                                                                                                                     |

Dynamic Host Configuration Protocol (DHCP) centralizes IP address assignment management by allowing a server to dynamically assign IP addresses to clients. DHCP also allows users who move from network to network to easily obtain an IP address appropriate for the subnet they are connected to.\
The DHCP server and the client use broadcasts to communicate with each other. An easy way to remember how DHCP works is to use the acronym DORA. DORA stands for discover, offer, request, and acknowledge.\
\
The table below describes the method clients use to obtain an address from a DHCP server.

<table><thead><tr><th width="196">Broadcast</th><th width="888">Description</th></tr></thead><tbody><tr><td>DHCP Discover (D)</td><td>The client begins by sending out a DHCP Discover broadcast to identify DHCP servers on the network.</td></tr><tr><td>DHCP Offer (O)</td><td>A DHCP server that receives a Discover advertisement from a client responds with a DHCP offer. The offer contains a proposed IP address lease. If more than one DHCP server sends an offer packet, the client usually responds to the first DHCP offer that it receives.</td></tr><tr><td>DHCP Request (R)</td><td>The client accepts the offered address lease by responding with a DHCP request broadcast.</td></tr><tr><td>DHCP ACK (A)</td><td>The DHCP server responds to the request by sending a DHCP ACK (acknowledgement) broadcast. At this point, the IP address lease is established between the client and server.</td></tr></tbody></table>

DHCP Installation

DHCP is installed by adding the DHCP role. This is done using Server Manager and will add the DHCP service along with the DHCP Snap-in. Before you can use DHCP, you need to complete its installation and authorize its use. This process also creates the DHCP user groups that will be required. After installation is complete, you access DHCP by going to Administrative Tools and selecting DHCP from the list.

The DHCP server must be assigned a static IP address.

DHCP Authorization

Authorization is necessary to keep unauthorized DHCP servers off the network. Unauthorized DHCP servers can cause problems such as handing out wrong addresses and keeping a user from accessing network resources.\
The following table discusses facts related to the DHCP authorization process.

| DHCP Authorization | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Requirements       | <p>Authorization requirements for a DHCP server include the following:</p><ul><li>Authorization is required if you are using Active Directory; no authorization is required for a standalone server.</li><li>If you use Active Directory, DHCP servers must either be domain controllers or domain member servers to be authorized.</li><li>When you authorize a DHCP server, its IP address is added to a list of authorized DHCP servers maintained in Active Directory.</li></ul> |

| <ul><li>To authorize a DHCP server, you must be logged in as a member of the Enterprise Admins group. If you install a DHCP server as an enterprise admin, the server is automatically authorized.</li></ul> |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Verification                                                                                                                                                                                                 | <p>Keep in mind the following about DHCP server authorization verification:</p><ul><li>You can authorize a server before or after DHCP is installed.</li><li>When a DHCP server starts, its IP address is compared to the Active Directory list. If it is found, the server is allowed to issue IP addresses. If it is not found, the server automatically shuts down before completing the startup process.</li><li>A Windows DHCP server checks for authorization when it boots and reauthorizes every five minutes.</li><li>DHCP servers running other operating systems, such as Linux or Unix, do not check for authorization with a domain controller before assigning addresses.</li></ul> |

Keep in mind the following when configuring a DHCP server:

* It is beneficial to configure the DHCP service to auto-start.
* The DHCP server must be assigned a static IP address.
* When you set up DHCP on a member server and add a user to the DHCP Administrators group, that user has DHCP Administrator rights only on the member server. If you delegate administration on a domain controller, the DHCP administrator has rights on all DHCP servers in the domain.

## Lab install DHCP

1. Install a DHCP role as follows:
   1. From Hyper-V Manager, select CORPSERVER.
   2. Maximize the window to view all virtual machines.
   3. Right-click CorpDCHP and select Connect.
   4. From Server Manager, select Manage > Add Roles and Features.
   5. In the Add Roles and Features wizard, click Next.
   6. Make sure Role-based or feature-based installation is selected; then click Next.
   7. Make sure CorpDHCP.CorpNet.com is selected in the Server Pool area; then click Next.
   8. Select the DHCP Server role.
   9. Select Add Features.
   10. Click Next.
   11. Click Next because no additional features are required for the DHCP Server.
   12. In the DHCP Server window, click Next.
   13. Select Install to add the selected role.
2. Authorize CorpDHCP as a DHCP server as follows:
   1. In the center area, select Complete DHCP configuration to begin the DHCP Post-Install configuration wizard.
   2. In the DHCP Post-Install configuration wizard, click Next.
   3. Verify the _credentials_; then select Commit.
   4. Click Close to close the DHCP Post-Install configuration wizard.
   5. Click Close to close the Add Roles and Features wizard.
3. Configure and activate a DHCP Scope as follows:
   1. From Server Manager, select Tools > DHCP.
   2. Expand CorpDHCP.CorpNet.com.
   3. Right-click IPv4 and select New Scope.
   4. In the New Scope wizard, click Next.
   5. In the Name field, enter the _name_ of the _scope_ and then click Next.
   6. Enter the _start IP address_.
   7. Enter the _end IP address_.
   8. Make sure the subnet is 255.255.255.0.
   9. Make sure the length is 24; then click Next.
4. Click Next to ignore any exclusions and delays.
5. Enter 5 days as the lease duration and then click Next.
6. Select No, I will configure these options later to postpone configuring other DHCP options and then click Next.
7. Click Finish to close the wizard and create the scope.

* Activate the DHCP scope as follows:

1. Expand IPv4.
2. Right-click Scope \[192.168.0.1] Subnet1 and select Activate.



discover, offer, request, ack

Ask a member of the Enterprise Admins group to authorize the server.

DHCP server

Authorize Srv11.

The DHCP server responds with a DHCP Offer.
