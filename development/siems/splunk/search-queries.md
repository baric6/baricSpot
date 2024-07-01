# Search Queries

## Useful search commands

Count by tag you are searching for like "Message" will bring a count of like messages

`| stats count by <tag>`



Rex is regex that you can replace a string like below replace a space with a underscore&#x20;

`| rex field=_raw "Account Name:\s+(?<Account_Name>[^\s]+)" | stats count by Account_Name`&#x20;



Pulls data from fields and organizes it into a table view

`| table UserId, SourceFileName, UserAgent, CreationTime`
