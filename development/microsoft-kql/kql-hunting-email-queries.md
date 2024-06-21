# KQL hunting email Queries

#### Look for a certain email

```
EmailEvents
| where SenderFromAddress contains "Boltinc8@gmail.com"
| project RecipientEmailAddress, Subject
```

#### Get email with lab in the name

```
EmailEvents
| where RecipientEmailAddress matches regex "^lab\\d{1,2}@.+$"
| project SenderFromAddress, RecipientEmailAddress
```

Get all emails that have a attachment with said name

```kql
EmailAttachmentInfo
| where FileName contains "INV9783.pdf"
| project RecipientEmailAddress, FileName, Timestamp, SenderDisplayName, SenderFromAddress
```

#### Get all emails from gmail and count

```
EmailEvents
| where SenderFromAddress  contains "@gmail.com"
| summarize Count = count() by SenderFromAddress
| project SenderFromAddress, Count
```

#### Get all emails with gmail

```
EmailEvents
| where SenderFromAddress contains "@gmail.com" 
| project SenderFromAddress, RecipientEmailAddress, Subject
```

#### Hunt emails except

```
EmailEvents
| where not(SenderFromAddress has_any("@yahoo.com", "@gmail.com", "@outlook.com", "@aol.com", "icloud.com", "@gesmv.org"
, "@crayonstoclassrooms.org", "@info.dot.ohio.gov", "@amazon.com","@voicemail.goto.com", "@dayforce.com", "@sharepointonline.com"
, "@shopgoodwill.com", "@shopgoodwill.com","@sharepointonline.com", "@ceridian.com", "@brittcosoftware.com", "@alerts.reliaslearning.com"
))
| summarize Count = count() by SenderFromAddress
| project SenderFromAddress, Count
```
