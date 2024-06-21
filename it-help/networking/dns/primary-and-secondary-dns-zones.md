# Primary and Secondary DNS Zones

As you study this section, answer the following questions:

* What is the difference between forward lookup and reverse lookup zones?
* How are reverse lookup zones named?
* What is the difference between a standard zone and an Active Directory-integrated zone?
* What is the difference between a primary zone and a secondary zone?
* What events trigger a zone transfer?
* Why are Active Directory-integrated zones transfers considered to be secure?
* What are the differences between the four Active Directory-integrated zone replication scope options?

Key terms for this section include the following:

| Term                                       | Definition                                                                                                                                 |
| ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------ |
| DNS Zone                                   | Any distinct, contiguous portion of the domain name space in the Domain Name System.                                                       |
| Forward Lookup Zone                        | A DNS zone containing records used to resolve FQDNs to IP addresses.                                                                       |
| Reverse Lookup Zone                        | A DNS zone containing records used to resolve IP addresses to FQDNs.                                                                       |
| Standard Zone                              | A DNS zone where DNS records are stored in text files.                                                                                     |
| Primary (Master) Zone                      | A standard read-write zone that contains original, authoritative DNS records.                                                              |
| Secondary (Slave) Zone                     | A standard read-only zone that contains a copy of the records contained in a primary zone and used for fault tolerance and load balancing. |
| Zone Transfer                              | The transfer of records from a primary zone to a secondary zone.                                                                           |
| <p>Active Directory<br>Integrated Zone</p> | A DNS zone where DNS records are stored in Active Directory data structures.                                                               |
| Replication Scope                          | An Active Directory-integrated zone option that controls how records are replicated between domain controllers.                            |

* Forward lookup and reverse lookup zones
* Standard primary and standard secondary zones
* Zone transfers
* Active Directory-Integrated zones
* Replication Scopes

Forward Lookup and Reverse Lookup Zones

All zones are either forward lookup or reverse lookup.

* Forward lookup zones resolve FQDNs to IP addresses.
  * The name of the zone is the DNS domain. Example: east.CorpNet.com
* Reverse lookup zones resolve IP addresses to FQDNs.
  * Reverse lookup zone names are IP addresses written in reverse order. Example: 1.169.192.in-addr.arpa

Standard Primary and Standard Secondary Zones

Standard zones are stored in text files. They can be primary or secondary.

* Standard primary zones are the only read/write copy of the zone.
* Standard secondary zones are copies of primary zones and are read-only.
  * Secondary zones are used for fault tolerance and load balancing.
* Modifications must be done on the primary zone.

Zone Transfers

Zone transfers are associated with standard zones. Information is transferred from a primary zone to a secondary zone. Zone transfers are:

* Initiated by the secondary zone.
* Triggered in two ways:
  * The secondary zone requests a zone transfer at the end of a configurable refresh interval.
  * The primary zone sends a notification to the secondary zone that a change has been made.
    * The secondary zone then requests a zone transfer.
* Secured through permissions.
  * A primary zone must be configured to allow the transfer to secondary zones.
* Transmitted across the network in cleartext.

Active Directory-Integrated Zones

Active Directory-Integrated (ADI) zones are stored in Active Directory data structures instead of text files.

* ADI zones are multi-master primary zones.
  * Any change to any copy of the ADI zone is propagated to all other copies of the zone.
* ADI zone transfers are secure since they are accomplished through encrypted Active Directory replication.
* ADI zones have secure dynamic updates.
  * Clients can securely update DNS when their IP address changes.

Replication Scopes

ADI zones can be replicated according to one of four replication scope settings:

* To all DNS severs running on domain controllers in this forest.
* To all DNS servers running on domain controllers in this domain.
* To all domain controllers in this domain (whether or not they run DNS).
* To all domain controllers in the scope of this directory partition.
  * You must first create the Active Directory partition using dnscmd /createdirectorypartition and then dnscmd /enlistdirectorypartition.



