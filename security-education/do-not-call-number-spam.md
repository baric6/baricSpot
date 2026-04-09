# Do not call number spam

Go to [ Call.gov](http://www.donotcall.gov/) or call 1-888-382-1222 (TTY: 1-866-290-4236) from the phone you want to register. It’s free.

Your phone number should show up on the Registry the next day, but it can take up to 31 days for sales calls to stop. You can check whether your number is on the Registry at [DoNotCall.gov](http://www.donotcall.gov/) or by calling 1-888-382-1222 from the number you want to verify.

#### API

base url

[https://api.ftc.gov/v0/dnc-complaints?api\_key=](https://api.ftc.gov/v0/dnc-complaints?api_key=iqjr4eaydtvGmVolNeAUSl15bWaAg00wLK8E5jXJ)\<your key>

#### PARMS

\&created\_date="2020-04-09 04:30:00"

\&created\_date\_from="2020-04-09 04:30:00"

\&created\_date\_to="2020-04-12 04:30:00"

\&violation\_date="2020-02-26"

\&violation\_date\_from="2020-02-26"

\&violation\_date\_to="2020-02-27"

\&state="Idaho"

\&state="Arizona"

\&city="Phoenix"

\&area\_code=360

\&is\_robocall=true

\&sort\_order=ASC

\&items\_per\_page=10

\&offset=10

#### How to get multiple pages within dates&#x20;

Note (

* only get 50 per request
* default items\_per\_page is 50 so you don't have to put that in the URL if you want 50 per page&#x20;

)

Below will get you 51-100 or page 2, removing the offset will get you 0-50 or page 1

[https://api.ftc.gov/v0/dnc-complaints?api\_key=\<your key >\&created\_date\_from=%222020-04-01%2004:10:00%22\&created\_date\_to=%222020-04-09%2004:30:00%22&](https://api.ftc.gov/v0/dnc-complaints?api_key=iqjr4eaydtvGmVolNeAUSl15bWaAg00wLK8E5jXJ\&created_date_from=%222020-04-01%2004:10:00%22\&created_date_to=%222020-04-09%2004:30:00%22\&items_per_page=50)offset=50

