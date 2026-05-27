# Entra ID: Disable User Password Expiration

This is good for if your change password policy is on the DC and you don't want users to change their password remotely.

{% embed url="https://www.daveherrell.com/entra-id-disable-user-password-expiration/" %}

If you are running a [Hybrid AD](https://www.spiceworks.com/tech/cloud/articles/legacy-ad-hybrid-ad-and-azure-ad-difference/) environment with Active Directory Syncing to Entra ID (Azure AAD).  You may run into issues where the password expires on the Active Directory account, but the password still works within MS365 for users.  &#x20;

You need to disable the Entra ID password expiration so they stay in sync.  You can easily do this per user by running the following PowerShell script.&#x20;

First, connect to AzureAD via PowerShell:

```
Connect-AzureAD -Confirm
```

Next, run one of the scripts below to verify or update the Entra ID profile. Make sure you update the ObjectID with the person you wish to update.

```
#Ok Let's Check Users Policy
Check users policy:
Get-AzureADUser -ObjectId 'dave@daveherrell.com' | Select-Object @{N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}}

#Setting all users to expire in Azure AD
Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies None

#Setting single user to expire in Azure AD
Set-AzureADUser -ObjectId 'dave@daveherrell.com' -PasswordPolicies DisablePasswordExpiration

#To re-enable for all
Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies DisablePasswordExpiration
```

That’s all there is to it.  If you are a visual person, as myself, you can verify this within the [**Azure Portal**](https://portal.azure.com/#view/Microsoft_AAD_UsersAndTenants/UserManagementMenuBlade/~/AllUsers), under the users account you just updated.  Search for the user, click their Properties tab on the account, under Assigned licenses in the list should be a “**Password policies**” attribute that now says “**DisablePasswordExpiration**“.&#x20;

<figure><img src="../../../.gitbook/assets/image (472).png" alt=""><figcaption></figcaption></figure>
