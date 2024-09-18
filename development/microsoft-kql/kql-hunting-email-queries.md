# KQL hunting email Queries

#### Look for a certain email

```kusto
EmailEvents
| where SenderFromAddress contains "Boltinc8@gmail.com"
| project RecipientEmailAddress, Subject
```

#### Get email with lab in the name

```kusto
EmailEvents
| where RecipientEmailAddress matches regex "^lab\\d{1,2}@.+$"
| project SenderFromAddress, RecipientEmailAddress
```

Get all emails that have a attachment with said name

```kusto
EmailAttachmentInfo
| where FileName contains "INV9783.pdf"
| project RecipientEmailAddress, FileName, Timestamp, SenderDisplayName, SenderFromAddress
```

#### Get all emails from Gmail and count

```kusto
EmailEvents
| where SenderFromAddress  contains "@gmail.com"
| summarize Count = count() by SenderFromAddress
| project SenderFromAddress, Count
```

#### Get all emails with Gmail

```kusto
EmailEvents
| where SenderFromAddress contains "@gmail.com" 
| project SenderFromAddress, RecipientEmailAddress, Subject
```

#### Hunt emails except

```kusto
EmailEvents
| where not(SenderFromAddress has_any("@yahoo.com", "@gmail.com", "@outlook.com", "@aol.com", "icloud.com"))
| summarize Count = count() by SenderFromAddress
| project SenderFromAddress, Count
```

#### Regex pattern matches any character that is not an ASCII character

```kusto
EmailEvents
| where Subject matches regex @"[^\x00-\x7F]"
| project RecipientEmailAddress, Subject, EmailAction
```

#### Finding Chinese character&#x20;

```kusto
EmailEvents
| where Subject matches regex @"[\u4E00-\u9FFF]"
| project Timestamp, RecipientEmailAddress, Subject, SenderFromAddress
```

#### Finding Spanish character&#x20;

```kusto
EmailEvents
| where Subject matches regex @"[áéíóúüñÁÉÍÓÚÜÑ]"
| project Timestamp, RecipientEmailAddress, Subject, SenderFromAddress
```

All Languages that are not English&#x20;

```kusto
EmailEvents
| where isnull(EmailLanguage) or EmailLanguage != "en" // Include emails with no language specified or not in English
| order by EmailLanguage asc // Sort by language in ascending order
| project RecipientEmailAddress, Subject, SenderFromAddress, EmailLanguage
```

#### Finding attachments sent from Gmail

```kusto
EmailAttachmentInfo
| where SenderFromAddress contains "gmail"
| project RecipientEmailAddress, SenderFromAddress, FileName
```

#### Finding attachments that are PDF sent from Gmail with a certain size

```kusto
EmailAttachmentInfo
| where FileType has "pdf"
| where SenderFromAddress contains "gmail"
| where FileSize > 40000 and FileSize < 50000
| extend FileSizeKB = FileSize / 1024.0
| project RecipientEmailAddress, SenderFromAddress, FileName, FileSize, FileSizeKB 
```

Attachments type count

```kusto
EmailAttachmentInfo
| summarize Count = count() by FileType
| order by Count desc
```
