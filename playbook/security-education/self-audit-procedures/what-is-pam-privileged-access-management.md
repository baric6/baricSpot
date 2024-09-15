# What is PAM (Privileged access management)

{% embed url="https://www.beyondtrust.com/resources/glossary/privileged-access-management-pam" %}

Privileged access management (PAM) is an identity security solution that helps protect organizations against cyber threats by monitoring, detecting, and preventing unauthorized privileged access to critical resources.

* cybersecurity strategies and technologies for exerting control over the elevated (“privileged”) accounts
* a central goal is the enforcement of least privilege
* a PAM best practice is to only use these administrator accounts when absolutely necessary
* Privileged account passwords are often referred to as “the keys to the IT kingdom,”

**types of privileged accounts**

* Local administrative accounts: Non-personal accounts providing administrative access to the local host or instance only.
* Domain administrative accounts: Privileged administrative access across all workstations and servers within the domain.
* Break glass (also called emergency or firecall) accounts: Unprivileged users with administrative access to secure systems in the case of an emergency.
* Service account: Privileged local or domain accounts that are used by an application or service to interact with the operating system.
* Active Directory or domain service accounts: Enable password changes to accounts, etc.
* Application accounts: Used by applications to access databases, run batch jobs or scripts, or provide access to other applications.

**why need pam**

* Lack of visibility and awareness of of privileged users, accounts, assets, and credentials
* Over-provisioning of privileges : IT admins traditionally provision end users with broad sets of privileges.
* Shared accounts and passwords or decentralized credential management
* or decentralized credential management
* Lack of visibility into application and service account privileges

**best practices**

* Establish and enforce a comprehensive privilege management policy: how accounts are provisioned/de-provisioned
* Identify and bring under management all privileged accounts and credentials
* Enforce least privilege over end users, endpoints, accounts, applications, services, systems, etc
  * Remove admin rights on endpoints
  * Remove all root and admin access rights to servers and reduce every user to a standard user
  * Remove unnecessary privileges
  * Eliminate standing privileges (privileges that are “always-on”) wherever possible
    * Privileged access for human users should always expire
  * Limit privileged account membership to as few people as possible
  * Minimize the number of rights for each privileged account
* Enforce separation of privileges and separation of duties: read, edit, write, execute, etc
* Segment systems and networks
* Enforce password security best practices
* Monitor and audit all privileged activity
* Implement dynamic, context-based access
  * determine how much and for how long privilege can be provisioned
* Implement privileged threat/user analytics
