# Search Queries

## Useful search commands

#### Count by tag you are searching for like "Message" will bring a count of like messages

```
| stats count by ip
```

```
| stats count by userName, ip
```

#### Rex is regex that you can replace a string like below replace a space with a underscore&#x20;

```
| rex field=_raw "Account Name:\s+(?<Account_Name>[^\s]+)" | stats count by Account_Name   
```



#### Pulls data from fields and organizes it into a table view

```
| table UserId, SourceFileName, UserAgent, CreationTime
```

#### lookup a uploaded csv table by file name&#x20;

```
| inputlookup <filename.csv>
```

#### Compare IP data in file with splunk logs

* lookup c2cisp.csv ip  - calls the file and uses the ip column
* matches the ip to the the data set d\_ip
* outputs the matched in a var named c2cisp

```
* | lookup c2cisp.csv ip as d_ip OUTPUT ip as c2cisp | search c2cisp=*
```

{% embed url="https://community.splunk.com/t5/Splunk-Search/How-to-search-a-lookup-table-to-find-any-IP-addresses-that-match/m-p/175026" %}

Find IPs that are not in the csv or 123.123.123.123

```
* | lookup IP.csv ip AS ipAdd OUTPUT ip AS match_ip
| where isnull(match_ip) | where ipAdd != "123.123.123.123"
| stats count by userDisplayName, ipAdd | sort - count
```

#### lookup Resources

For reference: the docs have a page for each command: [lookup](https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Flinkprotect.cudasvc.com%2Furl%3Fa%3Dhttp%253a%252f%252fdocs.splunk.com%252fDocumentation%252fSplunk%252flatest%252fSearchReference%252flookup%26c%3DE%2C1%2C9WdqfdRfM0wEV\_Qnll6u4oBZHKTTvtQhTrcqBQPvue3crYzZ5LGmx33Mcm\_T1VPSqXJxHtYvRz9C0m9\_wyG9\_Su1VbB5JSvUHjEzpyXZ9mKADgto2nhsA1A%2C%26typo%3D1\&data=05%7C02%7Cj.hollon%40gesmv.org%7C957c925c683d49a425a908dcbc67cda4%7C28083ef1d541442f8571ff507e065abf%7C0%7C0%7C638592401318082814%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C\&sdata=VM%2BEuWCD2e9zIoLKbJw7%2BvR8JJ2%2Fgu%2FhFGLvA7B87o0%3D\&reserved=0), [inputlookup](https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Flinkprotect.cudasvc.com%2Furl%3Fa%3Dhttp%253a%252f%252fdocs.splunk.com%252fDocumentation%252fSplunk%252flatest%252fSearchReference%252finputlookup%26c%3DE%2C1%2C\_RriEuStr5fUqhhcdL9ktqZlefHk3PxVSHx5SWFKC\_k5D5yQf9aTz7EGnY30hW4NUuFgXpMes3uj22gLmqWSILsODRT0lkoXyGuCDWOwrCGQjha2urXf9YnrDNZx%26typo%3D1\&data=05%7C02%7Cj.hollon%40gesmv.org%7C957c925c683d49a425a908dcbc67cda4%7C28083ef1d541442f8571ff507e065abf%7C0%7C0%7C638592401318096900%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C\&sdata=iCD29NMcBYPKDfJpksPdxjHETg%2BSUIrf9UOgaCOdQEo%3D\&reserved=0), and [outputlookup](https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Flinkprotect.cudasvc.com%2Furl%3Fa%3Dhttp%253a%252f%252fdocs.splunk.com%252fDocumentation%252fSplunk%252flatest%252fSearchReference%252foutputlookup%26c%3DE%2C1%2Csk5ByITxaEoeA0li5naNbLhGxogdYvKGvJs\_0hqxkd1fmA5nFyu72K6K0Mbw7lSDryeY184W-bIjbUA-CocNsaZbKDYKKc6j5L17doKgwFJL\_qA%2C%26typo%3D1\&data=05%7C02%7Cj.hollon%40gesmv.org%7C957c925c683d49a425a908dcbc67cda4%7C28083ef1d541442f8571ff507e065abf%7C0%7C0%7C638592401318102398%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C\&sdata=eVEjixid3N1X7PMv1%2FDQgfwwPoWEv6pfu889YwzbJ7k%3D\&reserved=0).

In short:

* `lookup` **adds data** to each _existing_ event in your result set based on a field existing in the event matching a value in the lookup
* `inputlookup` takes the the table of the lookup and **creates new events** in your result set (either created completely or added to a prior result set)
* `outputlookup` takes the current event set and writes it to a CSV or KVStore.

As an aside, when getting started with SPL commands, the [Quick Reference Guide](https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Flinkprotect.cudasvc.com%2Furl%3Fa%3Dhttps%253a%252f%252fwww.splunk.com%252fen\_us%252fresources%252fsplunk-quick-reference-guide.html%253f\_gl%253d1%252afyrfu%252a\_ga%252aMTM1MDE5NjQxOS4xNzE2NDkwNTkz%252a\_ga\_GS7YF8S63Y%252aMTcyMDU0NTkxNi41MC4xLjE3MjA1NDYwNDguNjAuMC4w%252a\_gcl\_aw%252aR0NMLjE3MTk5NDgwODUuQ2p3S0NBand5bzYwQmhCaUVpd0FIbVZMSmNici10RkRUOU1HcnNIQmFSTlVKNEMxNHNFeDFodWlGZzlzeFJxVUNWT0pJY3pWUUlkRUJ4b0NaN2NRQXZEX0J3RQ..%252a\_gcl\_au%252aNDc2NzA2MzM4LjE3MTk1MTAyOTc.%252aFPAU%252aNDc2NzA2MzM4LjE3MTk1MTAyOTc.%252a\_ga\_5EPM2P39FV%252aMTcyMDU0NTkxMC42MS4xLjE3MjA1NDYwOTQuMC4wLjg5NzY5NjQ4MQ..%2526\_ga%253d2.112675780.1326565181.1720446000-1350196419.1716490593%2526\_gac%253d1.162205518.1719948090.CjwKCAjwyo60BhBiEiwAHmVLJcbr-tFDT9MGrsHBaRNUJ4C14sEx1huiFg9sxRqUCVOJIczVQIdEBxoCZ7cQAvD\_BwE%26c%3DE%2C1%2CEfqycHdjyslu-vDjblfaAaXzZJWwxpiV-Y6iYoqbWDihlODdZW3opDAlRZGGE-wuus35hySy9hEUJFiolFssSMCus7G5wx-CMrE9Bm9LFVeYZBoqfQg%2C%26typo%3D1\&data=05%7C02%7Cj.hollon%40gesmv.org%7C957c925c683d49a425a908dcbc67cda4%7C28083ef1d541442f8571ff507e065abf%7C0%7C0%7C638592401318107293%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C\&sdata=BKaQZnWjZTD01AvS6zWAx2n4zvcrap%2FIF56as%2BxvW0Q%3D\&reserved=0) is the holy grail IMO for learning all about Splunk key concepts and common commands, along with different examples. Make sure you've got this one in your back pocket, as well as the [Search Reference Docs](https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Flinkprotect.cudasvc.com%2Furl%3Fa%3Dhttps%253a%252f%252fdocs.splunk.com%252fDocumentation%252fSplunk%252f9.3.0%252fSearchReference%252fWhatsInThisManual%26c%3DE%2C1%2CLvqq-cM4stNxqpHx9sm\_tXCm0d3gO5qd3na1JxkgHeypdDhX3aQ-jP-5taeav8eSfCu0mksrZxZ6lFk\_z3u5EWW5sFIAXWk1e5p8IPnz-pNnBhXHyY9EmLawEuXy%26typo%3D1\&data=05%7C02%7Cj.hollon%40gesmv.org%7C957c925c683d49a425a908dcbc67cda4%7C28083ef1d541442f8571ff507e065abf%7C0%7C0%7C638592401318115115%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C\&sdata=qwP0DazyibF2ZaB%2BCZYuAg4KODUWk60UarXtKoEmVZs%3D\&reserved=0).\
Yes, you can lookup two tables in the came command. You can even join the two tables together. It really depends on what you're trying to do with the lookup (whether you're trying to use multiple inputlookup calls, or multiple lookup calls).

*   The former requires the use of append or join:\


    > \| inputlookup lookup1| append \[|inputlookup lookup2]| join ip \[|inputlookup lookup3]\
    > \
    >
*   The latter is just sequential:\


    > index=\<index> sourcetype=\<sourcetype>\
    > |lookup lookup1 ip\
    > |lookup lookup2 host\
    > \
    > OR\
    > \
    > |inputlookup3\
    > |lookup lookup1 ip\
    > |lookup lookup2 host

#### Using Sort

```
your search....| sort -count
```

```
your search....| sort -_time
```

{% embed url="https://community.splunk.com/t5/Splunk-Search/How-do-I-sort-this-stats-count/m-p/362536" %}

#### Using where

```
 where ClientIP IN ("86.48.9.97", "92.119.17.191")
```

{% embed url="https://docs.splunk.com/Documentation/SCS/current/SearchReference/WhereCommandExamples" %}

#### Using maps with Location of IP

Cluster map

```
| iplocation ipAdd 
| geostats latfield=lat longfield=lon count by userName
```

<figure><img src="../../../../.gitbook/assets/image (307).png" alt=""><figcaption></figcaption></figure>

Choropleth Map&#x20;

```
| iplocation ip
| stats count by Country 
| rename Country AS country count as numb 
| sort -numb 
| geom geo_countries featureIdField=country
```

<figure><img src="../../../../.gitbook/assets/image (306).png" alt=""><figcaption></figcaption></figure>
