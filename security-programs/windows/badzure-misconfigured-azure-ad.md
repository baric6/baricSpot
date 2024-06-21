# BadZure misconfigured Azure AD

BadZure is a PowerShell script that leverages the Microsoft Graph SDK to orchestrate the setup of Azure Active Directory tenants, populating them with diverse entities while also introducing common security misconfigurations to create vulnerable tenants with multiple attack paths.

Specifically, BadZure automates the process of creating multiple entities such as: users, groups, application registrations, service principals and administrative units. To simulate common security misconfigurations in real environments, it randomly assigns Azure AD roles, Graph permissions and application ownership privileges to randomly picked security principals enabling the creation of unique attack paths. In line with the 'Assume Breach' principle, BadZure provides users with two methods of initial access to the vulnerable tenants it creates thereby simulating account takeover scenarios.

The key advantage of BadZure lies in its ability to rapidly populate and purge existing Azure AD tenants with randomly generated vulnerable configurations and pre-configured initial access facilitating continous and iterative attack simulation (red team) and detection development (blue team) experimentation. It is designed for security practitioners with an interest in exploring and understanding Azure AD security.

Download&#x20;

{% embed url="https://github.com/mvelazc0/BadZure" %}
