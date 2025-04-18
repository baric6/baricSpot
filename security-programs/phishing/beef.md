# BeEF

**BeEF** is short for **The Browser Exploitation Framework**. It is a penetration testing tool that focuses on the web browser.

Amid growing concerns about web-borne attacks against clients, including mobile clients, BeEF allows the professional penetration tester to assess the actual security posture of a target environment by using client-side attack vectors. Unlike other security frameworks, BeEF looks past the hardened network perimeter and client system, and examines exploitability within the context of the one open door: the web browser. BeEF will hook one or more web browsers and use them as beachheads for launching directed command modules and further attacks against the system from within the browser context.

{% embed url="https://github.com/beefproject/beef" %}

## Install&#x20;

{% embed url="https://www.developsec.com/2018/06/22/installing-beef-on-ubuntu-18-04/" %}

To start the beef server go to the location of where you cloned it&#x20;

ex.. desktop/beef/beef (for me)

```
./beef
```



To Dashboard&#x20;

```
http://127.0.0.1:3000/ui/panel
```



When everything is successful, you have a a Apache server up (not needed to go to)

```
http://127.0.0.1:3000
```



Open a new tab

```
http://127.0.0.1:3000/demos/butcher/index.html
```



When going to that page on the dashboard you should see that endpoint populate

<figure><img src="../../.gitbook/assets/image (428).png" alt=""><figcaption></figcaption></figure>
