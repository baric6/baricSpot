# Template for python data pusher

#### Init

On the splunk side you have to set up a index once you have made a index you need to configure it with the index it will be one of the options when setting up a HEC

1. set up a index
2. setup a HEC&#x20;

#### Scripts

The script below is a template to test if any data will push. I am doing it with a weather API&#x20;

There is some data that needs to be set up

* splunk\_url is the IP of the server
* splunk\_token is the token that gets generated with when creating a HEC server

```python
splunk_url = "https://<splunk-ip>:8088/services/collector/event"
splunk_token = "<generated-token-from-HEC>"  # HEC HTTP token
```

For this instance you need to go to:

{% embed url="https://weatherapi.com" %}

Make a free account and put the API key and zip code to make this work&#x20;

<pre class="language-python"><code class="lang-python"><strong># only runs once
</strong><strong>import json
</strong>import requests

# --- Splunk Config ---
splunk_url = "https://&#x3C;splunk-ip>:8088/services/collector/event"
splunk_token = "&#x3C;generated-token-from-HEC>"  # HEC HTTP token

headers = {
    "Authorization": f"Splunk {splunk_token}"
}

# --- Weather API Config (WeatherAPI.com) ---
weather_api_key = "&#x3C;weather-api-key>"   # replace with your key
zip_code = "&#x3C;zip-code>"  # Example: New York zip code
weather_url = f"http://api.weatherapi.com/v1/current.json?key={weather_api_key}&#x26;q={zip_code}&#x26;aqi=no"

# --- Get weather data ---
try:
    weather_response = requests.get(weather_url)
    weather_response.raise_for_status()
    weather_data = weather_response.json()

    # Build Splunk event
    event = {
        "event": weather_data,       # the JSON from WeatherAPI
        "sourcetype": "_json",
        "index": "python_weather",
        "host": "weather_app"
    }

    # Send to Splunk
    response = requests.post(
        splunk_url,
        headers=headers,
        data=json.dumps(event),
        verify=False  # disable SSL verification if self-signed cert
    )

    if response.status_code == 200:
        print("✅ Weather data successfully sent to Splunk")
    else:
        print(f"❌ Failed: {response.text}")

except requests.exceptions.RequestException as e:
    print(f"Error fetching weather data: {e}")

</code></pre>

The below script set to run every hour the script above only will run once

```python
# runs every hour
import json
import requests
import time
from datetime import datetime

# --- Splunk Config ---
splunk_url = "https://<splunk-ip>:8088/services/collector/event"
splunk_token = "<generated-token-from-HEC>"  # HEC HTTP token
headers = {
    "Authorization": f"Splunk {splunk_token}"
}

# --- Weather API Config ---
weather_api_key = "<weather-api-key>"   # replace with your key
zip_code = "<zip-code>"  # Example: New York zip code
weather_url = f"http://api.weatherapi.com/v1/current.json?key={weather_api_key}&q={zip_code}&aqi=no"

def send_weather():
    try:
        weather_response = requests.get(weather_url)
        weather_response.raise_for_status()
        weather_data = weather_response.json()

        weather_data["ran_at"] = datetime.utcnow().isoformat() + "Z"

        event = {
            "event": weather_data,
            "sourcetype": "_json",
            "index": "python_weather",
            "host": "weather_app"
        }

        response = requests.post(
            splunk_url,
            headers=headers,
            data=json.dumps(event),
            verify=False
        )

        if response.status_code == 200:
            print(f"✅ Weather data sent to Splunk at {weather_data['ran_at']}")
        else:
            print(f"❌ Failed: {response.text}")

    except requests.exceptions.RequestException as e:
        print(f"Error fetching weather data: {e}")

# --- Run every hour ---
while True:
    send_weather()
    time.sleep(3600)  # 3600 sec = 1 hour

```
