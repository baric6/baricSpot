# Respotter

<figure><img src="../../.gitbook/assets/respotter_demo.gif" alt=""><figcaption></figcaption></figure>

This application detects active instances of Responder by taking advantage of the fact that **Responder will respond to any DNS query**. Respotter uses LLMNR, mDNS, and NBNS protocols to search for a bogus hostname that does not exist (default: Loremipsumdolorsitamet). If any of the requests get a response back, then it means Responder is probably running on your network.

{% embed url="https://github.com/lawndoc/Respotter" %}
