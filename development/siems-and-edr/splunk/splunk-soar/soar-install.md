# SOAR Install

### Install Splunk Soar Video

{% embed url="https://www.youtube.com/watch?v=uLXUE6oTuNA" %}

### Dependencies

Red hat 8 (not gotten the soar to work on red hat 9)

* Account needed register or login
* [https://developers.redhat.com/products/rhel/download](https://developers.redhat.com/products/rhel/download)

Splunk Soar (I am using the trial for this)

* Account needed register or login
* [https://www.splunk.com/en\_us/download/soar-free-trial.html](https://www.splunk.com/en_us/download/soar-free-trial.html)



### Install Red Hat

I am going to assume you have created a VM and installed Linux before it is very cut and dry. The only thing different is licensing Red Hat. In the install GUI of red hat under license you just put the same user email and password you have made for the site. If your having trouble follow this:

{% embed url="https://developers.redhat.com/rhel8/install-rhel8-vbox#create_the_vm" %}

It is pretty much the same for any VM provider you use&#x20;

After the Install of Red Hat

### Install Splunk Soar

In red hat OS go to this link sign-in  and grab the wget link for:

Splunk SOAR On-premises Unprivileged Oracle Linux/ RHEL 8

{% embed url="https://www.splunk.com/en_us/download/soar-free-trial.html" %}

Change to root

```
sudo -i
```

Under your home folder for example

<figure><img src="../../../../.gitbook/assets/image (429).png" alt=""><figcaption></figcaption></figure>

After that is done downloading&#x20;

Change to the /opt/ directory&#x20;

```
cd /opt/
```

Now extract the Soar tar to the /opt/ directory

```
tar -xzvf <location of the file>
```

After install you should see this folder on /opt/

CD into the folder

<figure><img src="../../../../.gitbook/assets/image (430).png" alt=""><figcaption></figcaption></figure>

Within that folder prepare the SOAR by

```
./soar-prepare-system --splunk-soar-home /opt/splunk-soar/ --https-port 8443
```

Hit "Y" for everything for defaults

Towards the end of the install it will ask for a password for the phantom user create one, you will need it later

Go back to the root directory

```
cd /
```

Change ownership to /opt/ directory to phantom (this worked for me if you get a perm denied doing it the video way)

```
chown phantom: /opt/
```

Now go back into the splunk-soar folder

```
cd /opt/splunk-soar/
```

Change to phantom user

```
su phantom
```

Once in the splunk-soar folder, run the soar-install

```
./soar-install --splunk-soar-home /opt/splunk-soar/ --https-port 8443
```

Its is good to follow what the warnings say, I am going to ignore the warnings and press "y"

Next it will ask if everything is correct hit "y"

After it is done installing (i was in the /opt/splunk-soar/ folder) switch to the bin folder

```
cd bin
```

In the bin menu there is a script you need to run to start the server

Run

```
./start_phantom
```

The server is running now

Go to the webapp by (the HTTPS:// is important, HTTP will take you no where):

```
https://localhost:8443 or <ip>:8443
```

### How to use Splunk Soar Video

{% embed url="https://www.tiktok.com/@gavrisec/video/7360502027358702890" %}

Video for Installing Splunk Soar on red hat 8 in case video is taken down&#x20;

{% file src="../../../../.gitbook/assets/Download.mp4" %}

