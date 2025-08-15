# email2phonenumber

This tool helps automate discovering someone's phone number by abusing password reset design weaknesses and publicly available data. It supports 3 main functions:

{% embed url="https://www.martinvigo.com/email2phonenumber/" %}

* "scrape" - scrapes websites for phone number digits by initiating password reset using the target's email address
* "generate" - creates a list of valid phone numbers based on the country's Phone Numbering Plan publicly available information
* "bruteforce" - iterates over a list of phone numbers and initiates password reset on different websites to obtain associated masked emails and correlate it to the victim's one

{% embed url="https://github.com/martinvigo/email2phonenumber" %}

#### Demo

{% embed url="https://www.youtube.com/watch?v=dfvqhDUn81s" %}
