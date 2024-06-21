# kernal coff loader

Jormungandr is a kernel implementation of a COFF loader, allowing kernel developers to load and execute their COFFs in the kernel. The only supported type of COFF is an x64 kernel COFF (meaning, a COFF that uses functions from either NTOSKRNL or SSDT). This project is not supported to run with VBS enabled because it is using pools with execute permissions but this project should work for any version of Windows starting from Windows 7.

##

Download&#x20;

{% embed url="https://github.com/Idov31/Jormungandr" %}
