# Wazuh email notification

the program to send email notifations is called postfix email server

Wazuh email alerts does not support SMTP servers with authentication such as Gmail. However, you can use a server relay, like Postfix, to send these emails. Follow this guide for instructions on configuring Postfix with Gmail.

{% embed url="https://documentation.wazuh.com/current/user-manual/manager/manual-email-report/smtp-authentication.html" %}

**Restart postfix**

```
systemctl restart postfix
```
