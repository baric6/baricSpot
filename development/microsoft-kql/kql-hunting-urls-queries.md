# KQL Hunting URLS Queries

Gets URLS that contain the word "click" in it

```kusto
UrlClickEvents
| where Url matches regex @"(?i)click"
| project Url, AccountUpn
```

Gets URLS that have random letters in it

```kusto
UrlClickEvents
| where Url matches regex @"https?://(?:www\.)?[a-zA-Z0-9]+\.[a-zA-Z0-9]+.*"
| project Url, AccountUpn
```
