# Windows

Documentation

{% embed url="https://www.zabbix.com/documentation/current/en/manual/guides/monitor_windows" %}

Download

{% embed url="https://www.zabbix.com/download_agents" %}

{% embed url="https://www.youtube.com/watch?v=1zIZ__cHv48" %}

## Agent install&#x20;

1. download the version of MSI file you want
   1. NOTE some are zip files, i haven't had luck doing that way&#x20;
2.  When it hits the page that asks for a host-name&#x20;

    1. add the host name of the PC
       1. you can add whatever you want but only the passive scan will not need it, other scans may and not putting your host name may become a problem
    2. when it asks for the first IP this is your zabbix server IP
    3. it will prefill the port needed -> 10050
    4. the next port is the proxy address you can enter the IP of the zabbix server and you will be fine
    5. install


3. if you want to see if the service is running, search for zabbix in the windows services&#x20;
4.  #### Find agent in windows files

    `C:\Program Files\Zabbix Agent\Zabbix_agentd`



## Connecting Agent to the server

1. in the zabbix web UI go to the configuration tab and click on hosts
2. click create hosts
3. under the host tab
   1. add the host-name, you should put the pc host-name but it can be anything
   2. add to a group, find the best template that fits the machine&#x20;
   3. add a agent interface
      1. put the IP of client machine
      2. dns can be left blank
      3. it should auto prefill the port 10050
   4. everything else can be default, don't hit add
   5. go to the templates tab on the top of the page
   6. under link new templates&#x20;
      1. search for "Template OS Windows by zabbix agent"
   7. click add, and PC should be added

## Viewing alerts from Zabbix Dashboard

OPTIONAL: Run queries to update data. zabbix will auto update at a set time as set by the server

go back to all host find your server name and click the item link. on the bottom of this menu you will see check boxes select all of them by the top most check box. on the bottom of menu there is a "check now button"

You should see numbers by the links that means you have data flowing in





