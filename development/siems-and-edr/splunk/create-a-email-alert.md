# Create a email alert

## Server Setup

<figure><img src="../../../.gitbook/assets/image (292).png" alt=""><figcaption></figcaption></figure>

## Create a alert&#x20;

<figure><img src="../../../.gitbook/assets/image (294).png" alt=""><figcaption></figcaption></figure>

Resources&#x20;

{% embed url="https://support.servicenow.com/kb?id=kb_article_view&sysparm_article=KB0749544" %}

## Troubleshooting

<figure><img src="../../../.gitbook/assets/image (295).png" alt=""><figcaption></figcaption></figure>



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
