# Search Queries

## Useful search commands

#### Count by tag you are searching for like "Message" will bring a count of like messages

```
| stats count by <tag>
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

```
* | lookup c2cisp.csv ip as d_ip OUTPUT ip as c2cisp | search c2cisp=*
```

{% embed url="https://community.splunk.com/t5/Splunk-Search/How-to-search-a-lookup-table-to-find-any-IP-addresses-that-match/m-p/175026" %}

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
