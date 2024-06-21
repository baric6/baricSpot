# SCShell

SCShell is a fileless lateral movement tool that relies on ChangeServiceConfigA to run commands. The beauty of this tool is that it does not perform authentication against SMB. Everything is performed over DCERPC.

The utility can be used remotely WITHOUT registering a service or creating a service. It also doesn't have to drop any file on the remote system\* (Depend on the technique used to execute)

Capable of Pass the hash&#x20;

Download

{% embed url="https://github.com/Mr-Un1k0d3r/SCShell" %}
