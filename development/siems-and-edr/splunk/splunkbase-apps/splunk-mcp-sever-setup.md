# Splunk MCP Sever - setup

{% embed url="https://splunkbase.splunk.com/app/7931" %}

MCP Server for Splunk Platform The Model Context Protocol (MCP) server provides a standardized, secure, and scalable interface for connecting AI assistants, agents, and other intelligent systems with data in the Splunk platform.

1. Download Splunk MCP Server
   1. Download this first it will bring a role you need for the user&#x20;
2. Make a role
   1. Under Settings > Roles > New Role&#x20;
      1. Name your role
      2. Under the Capabilities find mcp\_tool\_execute and check it
      3. Save Role
3. Make a user
   1. Under Settings > Users > New User
      1. &#x20;Name your user
      2. Set Password
      3. Add role you just created and the user role
      4. Everything else can be default
4. create a token
   1. Under Settings > Tokens > New New Token
      1. User - is the user you created above&#x20;
      2. Audience - Description
      3. Expiration - +30d - will make it last for 30days without renew
      4. Not before - +30d - makes it a month (not sure I put 30 and i have for a month)
      5. token - will appear when you hit create
         1. This is what you use in your AI agents&#x20;
         2. This is the only time it will appear then it is gone forever so save it&#x20;
5. add the token to AI client&#x20;
   1. Depends on the AI you are using look at their docs&#x20;
