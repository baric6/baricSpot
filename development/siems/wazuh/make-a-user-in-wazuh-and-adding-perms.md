# Make a user in wazuh and adding perms

{% embed url="https://documentation.wazuh.com/current/cloud-service/your-environment/manage-auth.html" %}

## Back end roles

admin

## In server

server users

Wazuh OVA, you can change the password for your machines system user wazuh-user from default password wazuh to any custom one just by running the **passwd** command in your OVA while logged in with wazuh-user and providing current and new password.

#### wazuh web interface / indexer users

The passwords tool is embedded in the Wazuh indexer under

&#x20;`/usr/share/wazuh-indexer/plugins/opensearch-security/tools/`

You can use the embedded version or download it with the following command:

```
curl -so wazuh-passwords-tool.sh https://packages.wazuh.com/4.4/wazuh-passwords-tool.sh
```

**when running make sure to be in the**

[ **`/usr/share/wazuh-indexer/plugins/opensearch-security/tools/`** ](#user-content-fn-1)[^1]

**directory or it will fail**

```
bash wazuh-passwords-tool.sh -u admin -p AbCF12*
```

## Documentation

{% embed url="https://documentation.wazuh.com/current/user-manual/user-administration/password-management.html" %}

[^1]: 
