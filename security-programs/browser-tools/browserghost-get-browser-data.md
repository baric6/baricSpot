# BrowserGhost get browser data

<figure><img src="../../.gitbook/assets/image (68).png" alt=""><figcaption></figcaption></figure>

Realize that the system grabs the browser passwords of other users on the machine (to facilitate quick credential collection when moving laterally)

Use .net2 to achieve compatibility with most windows, and remove dependencies (no need for System.Data.SQLite.dll, which is cumbersome)

Can decrypt the full version password of chrome (the encryption method has changed after chrome80 version)

Chrome can already get login data, cookie, history, book

IE supports obtaining bookmarks, passwords, and history (.Net2 extracting passwords is too complicated for code reference to

{% embed url="https://github.com/djhohnstein/SharpWeb/raw/master/Edge/SharpEdge.cs" %}

{% embed url="https://github.com/QAX-A-Team/BrowserGhost" %}
