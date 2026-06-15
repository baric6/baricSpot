# Add an email as a proxy address

#### Attaching Email

**(Email must not be active on any other employee or in a soft delete status)**

Log on to your main Domain controller as administrator

Open Active Directory Users and Computers

Find the user that will be getting the proxy address

Right click on the user and go to properties

Click Attribute Editor

Scroll down to proxy-address then select and edit

value to add: smtp:(email address to add) click add

\*\*important - the smtp value has to be all lower case, only the primary smtp value is all upper case for smtp\*\*

Click Ok and Ok

#### Force Sync

On your main Domain controller

Open Powershell as Administrator

run the following&#x20;

```
Start-ADSyncSyncCycle -PolicyType Delta
```

This will force a sync to Entra

Open Synchronization Service and check the latest export value for any errors.

If no errors, go to admin.microsoft.com and check the user account for the new alias

#### Remove Email

Follow the same steps to remove the address

In AD on your Main Domain Controller&#x20;

proxyAddress select the value added and remove

Click OK and Apply then OK

&#x20;

On your main Domain controller

Run the same powershell as above

```
Start-ADSyncSyncCycle -PolicyType Delta
```

Verify in admin.microsoft.com that the alias is now gone from the user

&#x20;

