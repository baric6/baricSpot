# powershell - MFASweep

<figure><img src="../../.gitbook/assets/image (172).png" alt=""><figcaption></figcaption></figure>

MFASweep is a PowerShell script that attempts to log in to various Microsoft services using a provided set of credentials and will attempt to identify if MFA is enabled. Depending on how conditional access policies and other multi-factor authentication settings are configured some protocols may end up being left single factor. It also has an additional check for ADFS configurations and can attempt to log in to the on-prem ADFS server if detected.

* Microsoft Graph API
* Azure Service Management API
* Microsoft 365 Exchange Web Services
* Microsoft 365 Web Portal w/ 6 device types (Windows, Linux, MacOS, Android Phone, iPhone, Windows Phone)
* Microsoft 365 Active Sync
* ADFS

Download&#x20;

{% embed url="https://github.com/dafthack/MFASweep" %}
