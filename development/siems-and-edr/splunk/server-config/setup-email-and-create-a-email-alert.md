# Setup email and Create a email alert

#### Note

Email should be configured on the search head, not the indexer, because the search head is responsible for handling alerts and user-facing functionalities, including the UI that sends email notifications.

## Server Setup

<figure><img src="../../../../.gitbook/assets/image (292).png" alt=""><figcaption></figcaption></figure>

#### Troubleshooting:&#x20;

If you have setup the email part of it but you are still not getting emails

1. \<Splunk Home>/etc/system/local there should be a file called "alert\_action.conf". If there is no file called that in the local folder. Create it.&#x20;
   1. anything in the local folder overrides the default settings
   2. \[email]\
      mailserver = smtp.gmail.com:587 _// your mail server_\
      use\_tls = true\
      auth\_username = [splunk@mydomin.](mailto:splunk@gesmv.org)com _// make sure this matches from=_\
      auth\_password = \<Your Password>\
      from = [splunk@mydomain.](mailto:splunk@gesmv.org)com _// make sure this matches auth\_username=_
   3. restart the server&#x20;
2. After adding the details in the UI, go to the server and search for any file named alert\_action to see if you details saved. it should look like the above file but in a different location&#x20;

## Create a alert&#x20;

<figure><img src="../../../../.gitbook/assets/image (294).png" alt=""><figcaption></figcaption></figure>

Resources&#x20;

{% embed url="https://support.servicenow.com/kb?id=kb_article_view&sysparm_article=KB0749544" %}

## Troubleshooting

<figure><img src="../../../../.gitbook/assets/image (295).png" alt=""><figcaption></figcaption></figure>



## How to setup email alerts results

You can display Basic values you can put in the Subject or Body

Example:

```
$name$ // Gives you the name of the alert, ex. "Sign in out of US"
```



#### Custom values

The best way i found it to work is make the result query return a table. Splunk will look at the first entry to pull the values from.(ex..if you are returning multi rows it will only read the first for values)

```
| table _time, "User", "Client IP", City, Country
```

In the email you would access the values by

```
Email: $result.User$
IP: $result.Client IP$
City: $result.City$
Country: $result.Country$
```
