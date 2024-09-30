# Monitoring domain controller with TIG suite

<figure><img src="../../.gitbook/assets/image (380).png" alt=""><figcaption></figcaption></figure>

### Setup

{% embed url="https://youtu.be/lJBGwzfGhwI" %}

### Github

{% embed url="https://65007.github.io/TIG/" %}

### NOTE

If you get a powershell exec issue on windows mean that windows blocked the file and you have to unblock it with:

`Unblock-File -Path C:\Users\Administrator\Documents\scripts\PowerShellTips.chm`

### Restart the program if crashed

go to

```
C:\Program Files\telegraf
```

run

```
 .\telegraf --config-directory 'C:\Program Files\telegraf\telegraf.conf'
```
