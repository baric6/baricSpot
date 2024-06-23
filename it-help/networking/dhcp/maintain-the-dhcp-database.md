# Maintain the DHCP Database

* Back up a DHCP database.

Key terms for this section include the following:

| Term          | Definition                                                                                                                                                   |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| DHCP Database | DHCP servers store DHCP lease and reservation information in database files. By default, these files are stored in the %SystemRoot%\System32\DHCP directory. |

* DHCP database file types
* Removing a DHCP database
* Backup interval
* Moving a DHCP database

You must stop the DHCP service when manually modifying the database.

DHCP Database File Types

| File     | Description                                                               |
| -------- | ------------------------------------------------------------------------- |
| dhcp.mdb | This is the primary file for dhcp and contains all the scope information. |
| dhcp.tmp | This is a backup copy of the dhcp that is created during indexing.        |
| J50.log  | This file contains changes to the dhcp database before they are written.  |
| J50.chk  | This file tells dhcp which log files are needed for recovery purposes.    |

Remove a DHCP Database

Following are steps that can be taken to remove the DHCP database.

* Open a command prompts and stop the DHCP service by typing net stop dhcpserver.
* Remove all the files from C:\Windows\System32\DHCP.
* From the command prompt, restart the service by typing net start dhcpserver.
* Reconcile the DHCP scope to check for errors.

DHCP Backup Interval

There are several things you should be aware of concerning the DHCP Backup Interval.

* The DHCP Database backs up every 60 minutes by default.
* DHCP scopes, reservations, active leases, server options, and scope options are stored in backups.
* You can change the backup interval by modifying the registry key. HKEY\_LOCAL\_MACHINE\SYSTEM\CurrentControlSet\Services\DHCPServer\Parameters.

Move a DHCP Database

You may find it necessary to move the DHCP service to another server. If your DHCP has a complex configuration, you may find it easier to move the DHCP database than to manually configure the new server. This is especially true if your DHCP has a complex configuration or a large number of reservations. Moving the database eliminates the errors that are inherent when manually typing DHCP reservations, exclusions, and filters.
