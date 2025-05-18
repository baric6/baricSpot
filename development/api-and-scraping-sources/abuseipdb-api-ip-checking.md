# AbuseIPDB API IP checking

### Home Page

{% embed url="https://www.abuseipdb.com/" %}

### API Documentation

{% embed url="https://docs.abuseipdb.com/#introduction" %}

In order to get a API key you need to make a account with AbuseIPDB

### Basics

This is a quick start to call API in python

```python
import requests
import json

ip_address = '<IP Address>'

headers = {
    'Accept': 'application/json',
    'Key': '<your key here>'
}

# -------- 1. /check endpoint --------
check_url = 'https://api.abuseipdb.com/api/v2/check'
check_params = {
    'ipAddress': ip_address,
    'maxAgeInDays': '90'
}

check_response = requests.get(url=check_url, headers=headers, params=check_params)

check_data = check_response.json()
print(json.dumps(check_data, indent=4, sort_keys=True))
```
