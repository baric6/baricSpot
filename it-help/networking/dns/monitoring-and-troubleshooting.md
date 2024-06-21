# Monitoring and Troubleshooting

Key terms for this section include the following:

| Term                   | Definition                                                                                                                                                                                        |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DNS Performance Alerts | A feature added to Server Manager when the DNS role is added to send alerts when CPU usage and available memory cross a configurable threshold.                                                   |
| DNS Performance Tuning | The process of monitoring and configuring the DNS server's critical resources to optimize DNS performance.                                                                                        |
| PowerShell             | An automated task framework provided by Microsoft with a command line shell and scripting language. There are several DNS cmdlets that can be uses to set up, configure, and manage a DNS server. |
| dnscmd                 | A command line utility used for routine DNS setup, configuration, and management.                                                                                                                 |

* DNS monitoring tools
* DNS troubleshooting tools

DNS Monitoring Tools

There are several tools that can monitor the health of a DNS server.

| Tool                   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DNS Performance Alerts | <p>The DNS tab in Server Manager has a performance pane containing a graph that monitors CPU and memory.</p><ul><li>Performance alert thresholds control when alerts are triggered.</li><li>The CPU usage alert is measured in percentage.</li><li>The available memory alert is measured in MBs.</li></ul>                                                                                                                                                                                                                                                                            |
| Automated DNS Testing  | <p>Within the DNS Manager utility, there is a Test Now button under the Server properties' Monitoring tab. When you select it:</p><ul><li>A query is sent to the DNS server.</li><li>The status of the test is either Pass or Fail.</li><li>You can configure options to automate the testing.<br> </li></ul>                                                                                                                                                                                                                                                                          |
| Dnsperf                | <p>Dnsperf is an industry standard tool that measures the performance of a DNS server by sending a measured number of queries. Dnsperf:</p><ul><li>Helps determine the query load that a DNS server can handle.</li><li>Tests generally focus on cached lookups.</li><li>Tests can be configured to determine how the server responds to recursive and root hint lookups.</li><li>Can analyze how your server responds to a measured number of dynamic updates.</li></ul>                                                                                                              |
| DNS Log File           | <p>DNS log entries are found in the DNS log file.</p><ul><li><p>The dns.log file is located in the %systemroot%\System32\dns folder. It contains:</p><ul><li>Queries</li><li>Notification messages from other servers</li><li>Dynamic updates</li></ul></li><li>The level of information written to the log file is configured in the DNS Manager utility.</li></ul>                                                                                                                                                                                                                   |
| Event Viewer           | <p>There are three DNS event logs.</p><ul><li>The DNS Server event log tracks the DNS service. It contains entries for when the service starts and stops and when the DNS service loads each DNS zone.</li><li><p>Two event logs are found under DNS-Server:</p><ul><li>The Audit log shows events such as when DNS records and zones are updated. It also tracks user actions, such as when the debug log levels are changed.</li><li>The Analytical log tracks DNS queries, when a zone lookup is performed and when a query is forwarded to another DNS server.</li></ul></li></ul> |

DNS Troubleshooting Tools

DNS problems usually fall into two categories.

* When there is no response to a DNS query, the problems may be related to the DNS server itself.
* When the DNS service either gives a negative response to a host that does exist or responds with incorrect information, diagnosing the problem can be more challenging.

There are several command line tools that can help troubleshoot name resolution problems.

| Command Line Tool | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ping              | <p>A ping gives a quick indication of any DNS problems.</p><ul><li>When an FQDN is used in a ping, a name translation is performed in the background by requesting the IP address from the DNS server.</li><li>A "Could not find host" response may indicate a DNS lookup problem.</li><li>An incorrect IP address in the ping output may indicate faulty DNS host records or faulty DNS settings.</li></ul>                                                                                                                                             |
| ipconfig          | <p>The ipconfig command can be used to view your DNS client settings to make sure they’re correct.</p><ul><li>The results include a list of DNS servers the client sends name queries to.</li><li>The /displaydns option displays the contents of the client’s cache.</li><li>The /flushdns option clears the local cache and forces the DNS client to query the DNS server for new address translations.</li><li>The /registerdns option not only refreshes the DHCP lease, but registers the host’s name and IP address with the DNS server.</li></ul> |
| nslookup          | <p>The nslookup command is a simple way to run queries against a DNS server.</p><ul><li>It may indicate that the query has timed out because the DNS service could not be contacted.</li><li>It may indicate that an authoritative DNS was contacted, but the queried hostname doesn’t exist.</li></ul>                                                                                                                                                                                                                                                  |

Other utilities can also be used to review and configure DNS settings.

* The dnscmd command can be run from the command prompt.
  * You can run several options with this command, including /clearcache, which clears the lookup cache on the DNS server.
* There is a long list of PowerShell cmdlets that can be used to troubleshoot a DNS server.\
  For example:
  * Clear-DNSServerCache clears the DNS server lookup cache.
  * Get-DnsServer retrieves configuration information.
  * Get-DnsServerStatistics gives statistics about DNS record types, zone queries, zone transfers, and zone updates along with other useful troubleshooting information.



## Troubleshooting dynamic DNS

Complete this lab as follows:

1. Connect to the CorpDC virtual machine as follows:
   1. From Hyper-V Manager, select **CORPSERVER**.
   2. To view all of the virtual machines, maximize Hyper-V Manager.
   3. From the Virtual Machines pane, right-click on **CorpDC** and select Connect.
2. Create the reverse lookup zone as follows:
   1. From Server Manager, select Tools > DNS.
   2. From the left pane, expand CORPDC.
   3. Select Reverse Lookup Zones.\
      Notice that there is no reverse lookup zone for the 192.168.0.x network.
   4. Right-click Reverse Lookup Zones and select New Zone.
   5. Click Next to begin the New Zone wizard.
   6. Make sure the Primary zone and Store the zone in Active Directory options are selected.
   7. Click Next.
   8. Select how you want to replicate data and click Next.
   9. Make sure that IPv4 Reverse Lookup Zone is selected and click Next.
   10. In the Network ID field, enter 192.168.0 and click Next.
   11. Specify the type of dynamic updates that will be accepted for the DNS zone.
   12. Click Next.
   13. Click Finish.



## Troubleshooting DNS records

Create an A record for CorpWeb using 192.168.0.15Explanation

Complete this lab as follows:

1. From CorpServer, use the ping command to troubleshoot the connection to the CorpWeb server as follows:
   1. In the Search the web and Windows field, enter cmd.
   2. Under Best match, right-click Command Prompt and select Run as Administrator.
   3. At the command prompt, type ping corpweb.corpnet.local and press Enter.\
      Notice that the ping is unable to find CorpWeb.
   4. At the command prompt, type ping 192.168.0.15 and press Enter. The ping succeeds using the IP address, indicating a problem with the CorpWeb DNS record.
2. Create the host record for CorpWeb as follows:
   1. In Hyper-V Manager, select CORPSERVER.
   2. Under Virtual Machines, right-click CorpDC and select Connect.
   3. In Server Manager, select Tools > DNS.
   4. In the left pane, expand CORPDC.
   5. Expand Forward Lookup Zones.
   6. Right-click CorpNet.local and select New Host (A or AAAA).
   7. In the Name field, enter CorpWeb.
   8. In the IP address field, enter 192.168.0.15.
   9. Select Create associated pointer (PTR) record to automatically create the PTR record for the new host.
   10. Select Add Host.
   11. Click OK.
   12. Click Done to close the New Host dialog.
3. From CorpServer, verify that the new host record fixed the connection issue as follows:
   1. At the command prompt on CorpServerping, type ping corpweb.corpnet.local and press Enter. The ping now succeeds.
