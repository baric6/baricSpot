# Microsoft .net 3.5 keeps popping up and wont install

## Documentation

{% embed url="https://learn.microsoft.com/en-us/troubleshoot/windows-client/application-management/dotnet-framework-35-installation-error" %}

## Fix - Use Windows installation media

You can use the Windows installation media as the file source when you enable the .NET Framework 3.5 feature. To do this, follow these steps:&#x20;

1\. Insert the Windows installation media.&#x20;

2\. At an elevated command prompt, run the following command:&#x20;

_**note**_ Source:D: maybe different depending on PC. After you plug in the media look what drive it is in

```
Dism /online /enable-feature /featurename:NetFx3 /All /Source:D:\sources\sxs /LimitAccess
```
