# Server Properties

| Term            | Definition                                                             |
| --------------- | ---------------------------------------------------------------------- |
| DNS Logging     | The ability to configure the type of events to include in the DNS log. |
| Zone Scavenging | The process of eliminating obsolete DNS records.                       |

* DNS server properties dialog
* DNS logging
* Recursion settings
* Zone scavenging settings
* DNS client global settings

DNS Server Properties Dialog

There are several important settings in the properties dialog of the DNS server. This dialog is opened in the DNS Manager utility by right-clicking the DNS server and selecting Properties.

* Interfaces tab
  * Specifies which network cards or IP addresses that will serve DNS requests
  * Can be set to all IP addresses or a selection of IP addresses
* Debug Logging tab
  * Specifies additional DNS events to be logged for troubleshooting.
* Monitoring tab
  * Allows the user to run test queries against the DNS server to verify the configuration of the server
* Advanced tab
  * Allows the disabling of recursion
  * Allows the enabling of BIND secondaries for integration with Unix and Linux DNS
  * Allows the enabling of round robin
  * Allows the enabling of netmask ordering
  * Allows the DSN server to secure its cache against pollution

DNS Logging

By default, a DNS server is set to log any major events.

* Logging is set under the Event Logging and Debug Logging tabs in the DNS server properties.
* Event Logging can be set to log all events, errors only, errors and warnings, or no events.
* Debug Logging allows extra logging that is helpful for troubleshooting the DNS server. The collecting of information can be limited by selecting:
  * Outgoing, Incoming or both.
  * UDP, TCP or both.
  * Queries/Transfers, Updates, Notifications or any combination.
* Debug logging can be configured in PowerShell. The commandlet is Set-DnsServerDiagnostics. Important switches for this command are:
  * SendPackets
  * TcpPackets
  * Answers

Recursion Settings

DNS servers can send out two types of queries.

* Iterative queries request authoritative information only.
* Recursive queries allow the queried DNS server to contact other DNS servers when it does not have the requested information.

Recursion is configured by adding forwarders.

* Recursion can be disabled using the setting under the Advanced tab in the DNS server properties.
* Disabling recursion disables forwarders.
* Recursion can be disabled at the command prompt. The command is:\
  C:\\>dnscmd \<server name> /config /norecursion 1
* Recursion can be disabled in PowerShell. The commandlet is:\
  PS C:\\>Set-DnsServerRecursion -Enable $false

Zone Scavenging Settings

DNS records that are dynamically created by clients may become obsolete after time. Zone aging and scavenging settings control how stale records are removed from a DNS zone.

* Static DNS records are not subject to zone scavenging.
* Aging and scavenging is configured in two places.
  * Set Enable automatic scavenging of stale records under the Advanced tab of the DNS server properties. The default scavenging period is every seven days.
  * Configure each zone by clicking Aging under the General tab of the zone properties.
    * Mark Scavenge stale resource records.
    * Configure the No-refresh interval and Refresh interval settings.
* Zone scavenging can be configured from the command prompt. The commands are:\
  C:\\>dnscmd \<server name> /config \<zone name> /aging 1 /refreshinterval \<number of hours> /norefreshinterval \<number of seconds>\
  C:\\>dnscmd \<server name> /config /defaultagingstate 1 /defaultnorefreshinterval \<number of hours>
* Zone scavenging can be configured from PowerShell. The commandlets are:\
  PS C:\\>Set-DnsServerZoneAging \<zone name> -Aging $true\
  PS C:\\>Set-DnsServerScavenging -ComputerName \<server> -ScavengingState $true -RefreshInterval \<dd:hh:mm:ss format> -NoRefreshInterval \<dd:hh:mm:ss format> -ScavengingInterval \<dd:hh:mm:ss format>
* PS C:\\>Set-DnsServerResourceRecordAging -ZoneName \<zone> -Force -Recurse

DNS Client Global Settings

DNS client settings can be divided into two primary groups.

* Interface settings are specific to a network interface.
* Global settings apply to the protocols as a whole and are applied across all network interfaces.

DNS client global settings can be configured in two ways.

* In an Active Directory domain, DNS client global settings are best configured with group policies.
*   DNS client global settings can be configured using PowerShell.

    * DSN client global setting are viewed using:\
      PS C:\\>Get-DnsClientGlobalSetting
    * DSN client global setting are configured using:\
      Set-DnsClentGlobalSetting -UseDevolution <$true or $false> -SuffixSearchList (\<list of DNS domains>)
    * A group policy will overwrite any PowerShell configurations.

