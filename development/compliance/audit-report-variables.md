# Audit Report Variables



#### User Analysis (hybrid check local and azure)

{% columns %}
{% column %}
* AD users Enabled/Disabled
* last login/use(inactive users)
* Audit privileged Groups
* Admins w/o MFA
* Users with AdminCount = 1
* Accounts with No Password Required
* Orphaned SIDs for folders
{% endcolumn %}

{% column %}
* Password never expires
* Password Last set
* Password Expires
* Enumerate OU and Security Groups&#x20;
* Direct permissions for folder access
* Users w/o MFA&#x20;
* Users in Too Many Groups
* GPO audit
{% endcolumn %}
{% endcolumns %}

#### Computer Analysis

{% columns %}
{% column %}
* Detect Domain Controllers
* Detailed Domain Controller Event log Analysis
* Internet domain analysis
* Detect Local mail servers
* Detect time servers
* Network discovery for non AD devices
* Serial Number&#x20;
* CPU/RAM/NIC
* DNS Entries&#x20;
* Scheduled tasks
* CPU/CORE count
* OS version/Model
{% endcolumn %}

{% column %}
* Discover Network shares
* Detect added or removed computers
* Web server discovery and Identification
* Missing security updates&#x20;
* System by system event logs
* Internet access and speed test
* HDD storage/Used/Free
* Last Login
* Last 5 Event viewer Errors&#x20;
* Listening ports&#x20;
* Windows Key
* Antivirus/Anti spyware/Firewall
* Local users Enabled/Disabled
* Detect local accounts&#x20;
{% endcolumn %}
{% endcolumns %}

#### Computer Application analysis

{% columns %}
{% column %}
* Detect major applications
* SQL Server Analysis
{% endcolumn %}

{% column %}
* Internet access and speed test
* external security vulnerabilities&#x20;
{% endcolumn %}
{% endcolumns %}
