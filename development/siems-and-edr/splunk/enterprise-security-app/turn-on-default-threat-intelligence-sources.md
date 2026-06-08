# Turn on default Threat Intelligence Sources



{% embed url="https://help.splunk.com/en/splunk-enterprise-security-8/administer/8.1/threat-intelligence/overview-of-threat-intelligence-in-splunk-enterprise-security" %}

* All sources turned on makes a lookup folder where you can search to match manually or if your data is CIM compliant it will auto create alerts via mission control
* Some of the urls on the default sources start with lookup:// these are local files only to splunk

#### Default Sources&#x20;

alexa\_top\_one\_million\_sites

* Alexa top 1 mil sites
* [https://s3.amazonaws.com/alexa-static/top-1m.csv.zip](https://s3.amazonaws.com/alexa-static/top-1m.csv.zip)
* nothing is in the file :/

cisco\_top\_one\_million\_sites

* Cisco Umbrella Top 1 Million Sites, copyright 2018, Cisco Umbrella
* [https://s3-us-west-1.amazonaws.com/umbrella-static/top-1m.csv.zip](https://s3-us-west-1.amazonaws.com/umbrella-static/top-1m.csv.zip)&#x20;
* list of urls&#x20;

emerging\_threats\_compromised\_ip\_blocklist

* [https://rules.emergingthreats.net/blockrules/compromised-ips.txt](https://rules.emergingthreats.net/blockrules/compromised-ips.txt)&#x20;
* list of ip addresses&#x20;

emerging\_threats\_ip\_blocklist

* [https://rules.emergingthreats.net/fwrules/emerging-Block-IPs.txt](https://rules.emergingthreats.net/fwrules/emerging-Block-IPs.txt)&#x20;
* list of ip addresses&#x20;

hailataxii\_malware

* Hail a TAXII.com malware domain host list
* [http://hailataxii.com/taxii-data](http://hailataxii.com/taxii-data)&#x20;
* URL don't exists&#x20;

iblocklist\_logmein

* Addresses that are used by the LogMeIn product to enable unauthorized remote access
* [https://list.iblocklist.com/?list=logmein](https://list.iblocklist.com/?list=logmein)&#x20;
* short list of ip addresses

iblocklist\_piratebay

* Addresses that are commonly associated with known PirateBay sites
* [https://list.iblocklist.com/?list=nzldzlpkgrcncdomnttb](https://list.iblocklist.com/?list=nzldzlpkgrcncdomnttb)&#x20;
* short list of ip addresses

iblocklist\_proxy

* Addresses that are commonly associated with known traffic-proxy sites
* [https://list.iblocklist.com/?list=bt\_proxy](https://list.iblocklist.com/?list=bt_proxy)&#x20;
* list of ip

iblocklist\_rapidshare

* Addresses that are commonly associated with known RapidShare sites
* [https://list.iblocklist.com/?list=zfucwtjkfwkalytktyiw](https://list.iblocklist.com/?list=zfucwtjkfwkalytktyiw)&#x20;
* short list of ip addresses

iblocklist\_spyware

* Addresses that are commonly associated with known spyware sites
* [https://list.iblocklist.com/?list=bt\_spyware](https://list.iblocklist.com/?list=bt_spyware)&#x20;
* urls and ip addresses

iblocklist\_tor

* Addresses that are commonly associated with known Tor sites
* [https://list.iblocklist.com/?list=tor](https://list.iblocklist.com/?list=tor)&#x20;
* medium list of ip addresses

iblocklist\_web\_attacker

* Addresses that are commonly associated with known malicious attacker sites
* [https://list.iblocklist.com/?list=ghlzqtqxnzctvvajwwag](https://list.iblocklist.com/?list=ghlzqtqxnzctvvajwwag)
* range of ip addresses 124.42.34.172-124.42.34.172&#x20;

icann\_top\_level\_domain\_list

* ICANN Top-level Domains List
* [https://data.iana.org/TLD/tlds-alpha-by-domain.txt](https://data.iana.org/TLD/tlds-alpha-by-domain.txt)
* top level domains - AAA, AARP, ABB, ...&#x20;

maxmind\_geoip\_asn\_ipv4 and maxmind\_geoip\_asn\_ipv6

* MaxMind GeoIP ASN IPv4 database
* [https://download.maxmind.com/app/geoip\_download?edition\_id=GeoLite2-ASN-CSV\&license\_key=YOUR\_LICENSE\_KEY\&suffix=zip](https://download.maxmind.com/app/geoip_download?edition_id=GeoLite2-ASN-CSV\&license_key=YOUR_LICENSE_KEY\&suffix=zip)
* need a license key

mitre\_attack

* MITRE ATT\&CK framework
* [https://raw.githubusercontent.com/mitre/cti/master/enterprise-attack/enterprise-attack.json](https://raw.githubusercontent.com/mitre/cti/master/enterprise-attack/enterprise-attack.json)&#x20;
* json

mozilla\_public\_suffix\_list

* Mozilla Public Suffix List
* [https://publicsuffix.org/list/effective\_tld\_names.dat](https://publicsuffix.org/list/effective_tld_names.dat)&#x20;
* ex .. safey.aero, gov.al

phishtank

* Phishtank Database
* [https://data.phishtank.com/data/online-valid.csv.gz](https://data.phishtank.com/data/online-valid.csv.gz)
* phishing urls

sans

SANS blocklist

* [https://isc.sans.edu/block.txt](https://isc.sans.edu/block.txt)
* short list of urls



&#x20;
