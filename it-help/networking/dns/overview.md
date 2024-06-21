# Overview

As you study this section, answer the following questions:

* What are the primary functions of a Domain Name System?
* In what way is DNS a distributed database?
* In what way is DNS a hierarchical database?
* What are the parts of an FQDN?
* How does an FQDN identify a host?
* What are the advantages of installing DNS on a Nano Server?

Key terms for this section include the following:

| Term                                          | Definition                                                                                                                                                                                                                                                                                                                                                                            |
| --------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>Domain Name System<br>(DNS)</p>            | A service that resolves fully qualified domain names (FQDNs) to IP addresses and IP addresses to FQDNs.                                                                                                                                                                                                                                                                               |
| . (dot) Domain                                | The root domain, or root of the DNS domain tree, denotes a fully qualified unambiguous domain name.                                                                                                                                                                                                                                                                                   |
| <p>Fully Qualified Domain Names<br>(FQDN)</p> | The FQDN includes the host name and all domain names separated by periods. The final period, which is for the root domain, is normally omitted and only implied.                                                                                                                                                                                                                      |
| <p>Top-Level Domain<br>(TDL)</p>              | Sometimes known as a first-level domain, a TDL is the last part of a domain name (.com, .edu, .gov). TDLs are managed by the Internet Corporation of Assigned Names and Numbers (ICANN).                                                                                                                                                                                              |
| Second-Level Domain                           | Additional domains, or second-level domains, are registered to an individual or organization for use on the internet.                                                                                                                                                                                                                                                                 |
| Third-Level Domain                            | Third-level domains are only used in the United Kingdom (UK) and are associated with the co.uk first- and second-level name domains. Third-level domains are registered to individuals or organizations for use on the internet in the same way second-level domains are registered in the rest of the world. An example of a third-level domain in the DNS domain tree is bbc.co.uk. |
| Hostname                                      | The hostname is the part of a FQDN that represents a specific host. It is the left-most name in an FQDN. For example, "www" is the hostname of www.example.com.                                                                                                                                                                                                                       |
| Sub-Domain                                    | In an FQDN, any domain between the hostname and the second-level domain is a sub-domain. Sub-domains are not registered. Responsibility for sub-domains lies with the individual or organization that registered the second-level domain. Docs.microsoft.com and news.google.com are examples of sub-domains in the DNS domain tree.                                                  |

DNS, the Domain Naming System, is a service that resolves fully qualified domain names (FQDNs) to IP addresses and IP addresses to FQDNs.

This lesson covers the following topics:

* General DNS concepts
* FQDNs and DNS domains
* Installing DNS
* Installing DNS on Nano Server

General DNS Concepts

DNS can be a difficult topic to master. Understanding a few general concepts will help when you encounter more complex DNS issues.

* DNS is an abbreviation for Domain Name System.
* Users identify computers by their name, but computers use IP addresses when communicating with other computers.
* DNS maps recognizable FQDNs to numerical IP addresses.
  * For example, DNS translates the FQDN www.yahoo.com to the IP address 98.137.246.8.
* DNS is a database that is:
  * Distributed
    * Each DNS server maintains only a portion of the DNS database.
    * An authoritative DNS maintains original and definitive database records for computers in it's DNS domain.
  * Hierarchical
    * DNS domains are nodes in an inverted tree structure.
    * The single DNS domain at the top is the root or . (dot) domain.
    * Each DNS domain has only one parent domain, but can have multiple child domains.

FQDNs and DNS Domains

The following graphic and terms provide an explanation of FQDNs and DNS domains.

![Explanation of FQDNs and DNS domains - including host name, sub-domain, second-level domain, and top-level domain](https://cdn.testout.com/\_version\_405/serverpro2016network-741v4-en-us/en-us/resources/text/t\_dns\_install\_spn4/fqdn\_example.png)

| DNS Term                                     | Description                                                                                                                                                                                                                                                                                                                                                                                |
| -------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| . (dot) Domain                               | The root domain, or root of the DNS domain tree, denotes a fully qualified unambiguous domain name.                                                                                                                                                                                                                                                                                        |
| <p>Fully Qualified<br>Domain Name (FQDN)</p> | The FQDN includes the host name and all domain names separated by periods. The final period, which is for the root domain, is normally omitted and only implied.                                                                                                                                                                                                                           |
| Top-Level Domain (TDL)                       | Sometimes known as a first-level domain, a TDL is the last part of a domain name (.com, .edu, .gov). TDLs are managed by the Internet Corporation of Assigned Names and Numbers (ICANN).                                                                                                                                                                                                   |
| Second-Level Domain                          | Additional domains, or second-level domains, are registered to an individual or organization for use on the internet. These domains are registered using an appropriate top-level domain, which is normally chosen to suit the organization or geographic location where the domain will be used. Yahoo.com and microsoft.com are examples of second-level domains in the DNS domain tree. |
| Third-Level Domain                           | Third-level domains are only used in the United Kingdom (UK) and are associated with the co.uk first and second level-name domains. Third-level domains are registered to individuals or organizations for use on the internet in the same way second-level domains are registered in the rest of the world. An example of a third-level domain in the DNS domain tree is bbc.co.uk.       |
| Hostname                                     | The hostname is the part of a FQDN that represents a specific host. It is the left-most name in an FQDN. For example, "www" is the hostname of www.example.com.                                                                                                                                                                                                                            |
| Sub-Domain                                   | In an FQDN, any domain between the hostname and the second-level domain is a sub-domain. Sub-domains are not registered. Responsibility for sub-domains lies with the individual or organization that registered the second-level domain. Docs.microsoft.com and news.google.com are examples of sub-domains in the DNS domain tree.                                                       |

Don't confuse a DNS domain with an Active Directory domain.

* A DNS domain is a section of the DNS tree.
* A DNS domain is not an Active Directory domain.
* For example, CorpNet.com may be one Active Directory domain, but is two DNS domains, CorpNet and com.

Installing DNS

A  Windows 2016 server with DNS can be a domain controller, a domain member, or a stand-alone server.

* On a domain controller, you can install DNS as part of the Active Directory Domain Controller Installation wizard or DC promo. The wizard will prompt you to install DNS.
* Whether the Windows 2016 server is a domain controller, member server, or standalone, you can install DNS by:
  * Adding the DNS role from Server Manager.
    * Use the Manage > Add Roles and Features menu item.
    * Select the DNS Server role.
    * If desired, include the features that install the DNS management tools.
  * Adding the DNS role using PowerShell.
    * Use the Install-WindowsFeatures -Name DNS -IncludeAllSubFeature -IncludeManagementTools command.

Installing DNS on Nano Server

Windows Server 2016 offers a new Nano Server installation option.\
\
Nano Server:

* Is similar to Server Core mode
* Has a significantly smaller footprint
* Uses less disk space
* Installs quickly
* Has fewer patches and reboots than the fully featured Windows Server

These feature make Nano Server and ideal platform for a DNS server.

While you can deploy Nano Server to a physical computer, the tasks for creating a Nano Server as a virtual machine and installing DNS are as follows:

1. Create a virtual disk that includes the files needed to install the DNS role.
   1. Copy the NanoServerImageGenerator folder from the Windows Server 2016 ISO to a local folder.
   2. From PowerShell:
      1. Import the Nano image creation modules and functions using the Import-Module .\NanoServerImageGeneration -Verbose command.
      2. Create a virtual disk using the New-NanoServerImage command and the following options:
         * \-Edition Standard
         * \-DeploymentType Guest
         * \-MediaPath \<path to Windows Server 2016 installation disk>
         * \-BasePath \<working folder>
         * \-TargetPath \<file name that will be the virtual disk, either vhd or vhdx>
         * \-ComputerName \<computer name>
         * \-DomainName \<domain name>
         * \-Package Microsoft-NanoServer-DNS-Package
2. Use Hyper-V Manager to create a virtual machine.
   1. Choose Generation 2 if the virtual disk file has a vhdx extension.
   2. Add a disk using the virtual disk file previously created.
3. Start the virtual machine and add the DNS role in one of two ways:
   * Use PowerShell remoting to connect to the Nano Server. Then using the Install-WindowsFeature command to install DNS.
   * Use Server Manager to add the role:
     * Use Manage > Add Servers to add the Nano Server to Server Manager.
     * Use Manage > Add Roles and Features to add the DNS Role.

The steps for installing Nano Server and DNS on a physical machine are similar to installing the program on a virtual machine. The challenge is to deploy the disk image (as a VHD, VHDX, or WIM file) to the physical disk. One way to deploy the image is to boot the physical machine into WinPE and deploy the disk from a WIM file.

Once DNS is installed on the Nano server, you can manage the DNS role using PowerShell or the DNS Manager tool.
