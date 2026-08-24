# SPL Threat-hunting

#### IDSLocked Spike on any single account

```splunk
index=365 Operation=UserLoginFailed LogonError=IdsLocked
| bucket _time span=1h
| stats count BY _time, UserId
| where count > 10
| eval alert="Account locked " + tostring(count) + " times in 1hr: " + UserId
```

#### Password spray or Brute force&#x20;

```
index=<Your Index> Operation=UserLoginFailed
| bucket _time span=30m
| stats 
    dc(UserId)    AS unique_targets 
    values(UserId) AS targets
    count          AS total_failures 
    BY _time, ClientIP
| where unique_targets >= 3 OR total_failures >= 25
| where ClientIP != "<Your IP>"
| eval alert="Spray candidate" + ClientIP + " | targets=" + tostring(unique_targets) + " failures=" + tostring(total_failures)
```
