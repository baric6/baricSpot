# Cisco Meraki using API to to set "VPN Exclusion Rules"

#### Read and Write the VPN Exclusion Rules

In the Meraki portal add all the VPN exclusions to a location for the program below to copy and it will write a JSON

```python
import requests
import json

API_KEY = "< meraki api key >"
ORG_ID = < meraki org key >
NETWORK_ID = "< location network id >"

url = f'https://api.meraki.com/api/v1/organizations/{ORG_ID}/appliance/trafficShaping/vpnExclusions/byNetwork'
headers = {
    'X-Cisco-Meraki-API-Key': API_KEY,
    'Content-Type': 'application/json'
}
params = {
    'networkIds[]': NETWORK_ID
}

response = requests.get(url, headers=headers, params=params)
# print(response.json())
data = response.json()

with open("output.json", "w") as f:
    json.dump(data, f, indent=2)

print("Saved to output.json")
```

#### Example output

```json
{
    "items":[
        "networkID": "dummy data"
        "networkName": "dummy data"
        "custom": [
            {
                "protocol": "tcp",
                "destination": "< ip >",
                "port": "any"
            }
        ]
    ],
    "majorApplications": []
}
```

#### Push the VPN Exclusion Rules

```python
import requests
import json

API_KEY = "< meraki api key >"
ORG_ID = < meraki org key >

# Put Your network_id of the location or locations
NETWORK_IDS = [
    " < location network id 1 > ",
    " < location network id 2 > "
]

with open("output.json", "r") as f:
    source_data = json.load(f)

payload = {"custom": source_data["items"][0]["custom"]}

headers = {
    'X-Cisco-Meraki-API-Key': API_KEY,
    'Content-Type': 'application/json'
}

for network_id in NETWORK_IDS:
    url = f'https://api.meraki.com/api/v1/networks/{network_id}/appliance/trafficShaping/vpnExclusions'
    response = requests.put(url, headers=headers, json=payload)
    if response.status_code == 200:
        print(f"{network_id} - Updated successfully.")
    else:
        print(f"{network_id} - Error {response.status_code}: {response.text}")
```
