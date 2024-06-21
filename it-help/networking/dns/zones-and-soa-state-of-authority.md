# Zones and SOA(state of Authority)

Key terms for this section include the following:

| Term                             | Definition                                                                                                                                                             |
| -------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Start of Authority (SOA) Records | A record in a DNS zone that is integrated into the zone properties dialog box that contains the name of the DNS server, the zone administrator and other key settings. |
| Stub Zones                       | A DNS zone that contains information used to directly forward queries to a specific external DNS zone.                                                                 |
| GlobalNames Zones                | A DNS zone used to resolve single label names in a domain to IP addresses.                                                                                             |

Start of Authority (SOA) Records

The SOA record exists in a DNS zone, but is integrated into the Properties dialog box. The SOA contains:

* The name of the DNS server
* The zone administrator
* Key settings:
  * How often zone transfers occur
  * The wait time before failed zone transfers are retried
  * The time that data can be used on a secondary DNS server before it expires
  * The default time-to-live on resource records

Stub Zones

Stub Zones are often used when a child zone is located on a different DNS server. For example:

* One DNS server is authoritative for the CorpNet.xyz zone.
* Another DNS server is authoritative for east.CorpNet.xyz.

A stub zone:

* Contains a copy of selected records from the primary zone.
  * The SOA record.
  * Host records for the DNS servers in the primary zone.
  * Records that identify the servers as DSN servers.
* Behaves like a Conditional Forwarder.
  * Forwards queries to DNS server identified in the stub zone.

Stub zones can be created using the DNS Manager utility or with command prompt and PowerShell commands.

| Utility        | Steps or Commands                                                                                                                                                               |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DNS Manager    | <ul><li>Create the zone using the New Zone wizard.</li><li>Choose Stub zone.</li><li>Enter the IP address or FQDN of the Master DNS server where primary zone exists.</li></ul> |
| Command Prompt | C:\\>dnscmd <_DSN server_> /zoneadd <_name of zone_> /stub <_master DNS_>                                                                                                       |
| PowerShell     | PS C:\\>Add-DnsServerStubZone -Name <_DSN server_> -MasterServers <_Master DNS_> -PassThru -ZoneFile "<_file name_>"                                                            |

GlobalNames Zones

The GlobalNames zone is used to resolve single label names in a domain for older Windows NT hosts and hosts supported by WINS.

Create a GlobalNames zone as follows:

1. Create a zone.
   1. Create the zone using the New Zone wizard.
   2. Choose Primary zone.
   3. Name it GlobalNames.
2. Enable GlobalNames from the command prompt as follows:\
   C:\\>dnscmd <_DNS server_> /config /enableglobalnamessupport 1

