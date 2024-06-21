# DHCP Options

| Term              | Definition                                                                                              |
| ----------------- | ------------------------------------------------------------------------------------------------------- |
| DHCP Option Types | Client configuration parameters a DHCP server can assign when offering an IP address lease to a client. |
| DHCP Option Class | A way for the DHCP server to customize option types provided to clients.                                |

* Option assignments
* Common DHCP options

Option Assignments

In addition to providing an IP address, the DHCP server can also assign DHCP clients with additional IP configuration parameters using options. Commonly used DHCP options include the subnet mask, the default gateway router address, and one or more DNS server addresses. You can configure four option levels:

<table><thead><tr><th>Option</th><th width="918">Description</th></tr></thead><tbody><tr><td>Server Options</td><td>Server options are applied to all computers that get an IP address from the DHCP server, regardless of which scope they obtain the address from. For example, if your organization has only one DNS server, then all DHCP clients need the same DNS server address. You can accomplish this task most efficiently with a server option.</td></tr><tr><td>Scope Options</td><td>Scope options are applied to all computers that get an IP address from a particular scope on the DHCP server. For example, each scope may need to be configured with a default gateway address option that is appropriate for the scope's subnet.</td></tr><tr><td>Class Options</td><td>Class options are applied to all computers that are members of a particular class. To do this, you must first configure the class individually on each computer so the DHCP server knows what class it belongs to. For example, you may want all your older operating systems to receive different options than your newer operating systems. Class options are not commonly implemented.</td></tr><tr><td>Client Options</td><td>Client options are applied to a specific DHCP client. The client's MAC address is used to identify which system receives the option. A client option will override all other options.</td></tr></tbody></table>

Common DHCP Options

There are many options you can configure in DHCP. The following table describes some of the most popular options.

<table><thead><tr><th>Option</th><th width="506">Description</th></tr></thead><tbody><tr><td>Options 3<br>Router</td><td>Option 3 specifies the IP address of the default gateway you want assigned to clients.</td></tr><tr><td>Option 6<br>DNS Servers</td><td>Options 6 specifies which DNS name servers are assigned to clients.</td></tr><tr><td>Option 15<br>Domain Name</td><td>Option 15 specifies the DNS domain name that your clients will receive.</td></tr></tbody></table>

## DHCP Configure Options

1. Connect to the CorpDHCP virtual machine as follows:
   1. From Hyper-V Manager, select **CORPSERVER**.
   2. To view all of the virtual machines, maximize Hyper-V Manager.
   3. From the Virtual Machines pane, right-click **CorpDCHP** and select **Connect.** The virtual machine is opened.
2. Configure the DHCP server options as follows:
   1. From Server Manager, select Tools > DHCP.
   2. From the left pane, expand CorpDHCP.CorpNet.com.
   3. Expand IPv4.
   4. Right-click Server Options and select Configure Options.
   5. Under Available Options, mark 006 DNS Servers.
   6. In the IP Address field, enter the _IP address_ as found in the scenario.
   7. Click Add to add the IP address to the list.
   8. Repeat steps 1i-1j to add additional IP addresses.
   9. Click Apply.
   10. Under Available Options, mark 015 DNS Domain Name.
   11. In the String value field, enter CorpNet.com.
   12. Click OK to save the options you have defined.
3. Configure the DHCP scope options as follows:
   1. Expand Scope \[192.168.0.1] Subnet1.
   2. Right-click Scope Options and select Configure Options.
   3. Under Available Options, mark 003 Router.
   4. In the IP address field, enter 192.168.0.5.
   5. Click Add to add the IP address to the list.
   6. Click OK to save the options you defined.

> Server options apply to every scope on the server. Scope options override the server settings for a specific scope.

