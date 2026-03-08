# Make a Audit Report



#### User Analysis (hybrid check local and azure)

{% columns %}
{% column %}
* AD users Enabled/Disabled
* Local users Enabled/Disabled
* Detect local accounts&#x20;
* last login/use
{% endcolumn %}

{% column %}
* Password never expires
* Password Last set
* Password Expires
* Enumerate OU and Security Groups&#x20;
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

#### FSMO Role Analyst&#x20;

* Schema Master - forest - Modifies AD structure
* Domain naming Master - forest - Adds/removes Domains
* PCD Emulator - Domain - Syncs time, Manages Passwords
* RID Master -  Domain - Allocates object ID's
* Infrastructure Master - Domain - Updates cross domain references&#x20;
