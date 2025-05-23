# Connect Splunk Enterprise With SOAR

### Start here

This Tutorial is meant to be setup where Splunk and SOAR is on the same internal net. If you are setting up cloud instances where your data is going over the public net don't use this tutorial&#x20;

{% embed url="https://www.youtube.com/watch?v=36RjwmJ_Ee4" %}

### Instructions

Make sure you grab the right app, in the video he sets up the wrong app up at first but all the steps leading to it is the same no matter what app&#x20;

{% embed url="https://splunkbase.splunk.com/app/3411" %}

Go into the Splunk App for SOAR Export, you should see the below image to make sure you are in the right place

**Note** - _you will have HTTPS enabled at first, I am setting up the soar on the same internal internet as Splunk is on and is not facing the internet. If your Splunk and soar is facing the internet Https should be on_&#x20;

Click on configurations and click Create Server&#x20;

<figure><img src="../../../../.gitbook/assets/image (435).png" alt=""><figcaption></figcaption></figure>

### Second - turn off HTTP certs

In the Splunk server:

in windows location

```
\Splunk\etc\apps\phantom\phantom.conf
```

in this folder you should see a entry in the file that looks like

```
[Verify_certs]
value = true
```

Do not change this value in here, create a new folder named "local" in:

```
\Splunk\etc\apps\phantom\
```

With in the local folder create a phantom.conf and add:

```
[Verify_certs]
value = false
```

We have to do it in one more folder



### Third

You will see the below Image

<figure><img src="../../../../.gitbook/assets/image (436).png" alt=""><figcaption></figcaption></figure>

* Authorization Configuration = you will get a Json Object that will connect you to the SOAR
* Name = can be anything
* Proxy = if you are using a proxy&#x20;
* Adaptive Response Relay&#x20;

For these selections all we will be filling in Authorization Configuration and Name
