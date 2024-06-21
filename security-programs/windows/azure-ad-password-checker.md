# Azure AD password checker

In an Azure AD environment, it's possible to determine whether a user has Multi-Factor Authentication (MFA) disabled without requiring any special privileges. This can be accomplished by analyzing the account's creation date and last password change date. If these dates match and there has been no human interaction since the account was created, it's possible that the user has not been able to enable MFA or change their password. This information can be useful for identifying potential security risks designed for use by both red and blue teams. The roadrecon database file is needed for this tool. Roadrecon tool is developed by dirkjanm and can be download on github https://github.com/dirkjanm/ROADtools or pip install roadrecon.

Download

{% embed url="https://github.com/quahac/Azure-AD-Password-Checker" %}
