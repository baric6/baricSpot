# Search Queries

## Useful search commands

Count by tag you are searching for like "Message" will bring a count of like messages

`| stats count by <tag>`



Rex is regex that you can replace a string like below replace a space with a underscore&#x20;

`| rex field=_raw "Account Name:\s+(?<Account_Name>[^\s]+)" | stats count by Account_Name`&#x20;



Pulls data from fields and organizes it into a table view

`| table UserId, SourceFileName, UserAgent, CreationTime`



lookup a uploaded csv table by file name&#x20;

`| inputlookup <filename.csv>`



Compare IP data in file with splunk logs

`* | lookup c2cisp.csv ip as d_ip OUTPUT ip as c2cisp | search c2cisp=*`

{% embed url="https://community.splunk.com/t5/Splunk-Search/How-to-search-a-lookup-table-to-find-any-IP-addresses-that-match/m-p/175026" %}
