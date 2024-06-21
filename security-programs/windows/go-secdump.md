# Go-Secdump

Package go-secdump is a tool built to remotely extract hashes from the SAM registry hive as well as LSA secrets and cached hashes from the SECURITY hive without any remote agent and without touching disk.

The tool is built on top of the library [go-smb](https://github.com/jfjallid/go-smb) and use it to communicate with the Windows Remote Registry to retrieve registry keys directly from memory.

It was built as a learning experience and as a proof of concept that it should be possible to remotely retrieve the NT Hashes from the SAM hive and the LSA secrets as well as domain cached credentials without having to first save the registry hives to disk and then parse them locally.

The main problem to overcome was that the SAM and SECURITY hives are only readable by NT AUTHORITY\SYSTEM. However, I noticed that the local group administrators had the WriteDACL permission on the registry hives and could thus be used to temporarily grant read access to itself to retrieve the secrets and then restore the original permissions.

Download

{% embed url="https://github.com/jfjallid/go-secdump" %}
