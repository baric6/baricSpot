# Monitoring a file from a PC

## Manual by editing agent on the machine you want to monitor

#### File location

`C:\Program Files\SplunkUniversalForwarder\etc\apps\SplunkUniversalForwarder\local\input.config`

If in the installer you have it monitoring the event viewer alerts the file should contain

<figure><img src="../../../.gitbook/assets/image (296).png" alt=""><figcaption></figcaption></figure>

To monitor the file location add this to the above file

`[monitor://C:\Users\j.hollon\Desktop\moniterMe]`&#x20;

`disabled = false`&#x20;

`index = <name me>`

`sourcetype = <anything>`

`recursive = true`

## Log to see if it is sending to splunk indexer

`C:\Program Files\SplunkUniversalForwarder\var\log\splunk\splunkd.log`

## Resources

{% embed url="https://www.splunk.com/en_us/blog/tips-and-tricks/audit-file-access-and-change-in-windows.html" %}

{% embed url="https://docs.splunk.com/Documentation/SplunkCloud/9.2.2403/Data/MonitorfilesystemchangesonWindows#Examples_of_file_system_change_monitoring" %}
