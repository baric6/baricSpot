# Pi Weather Station

<figure><img src="../../.gitbook/assets/91359998-4625bb80-e7bb-11ea-937e-c87eede41f35.JPG" alt=""><figcaption></figcaption></figure>

A server that Run a weather map and accessible from a web UI

The documentation is saying put on a raspberry pie but I used Ubuntu server with node installed

Out of the box it wont show up on your network but will if you remove "localhost"

```
app.listen(PORT, "localhost", async () => {
```

&#x20;So it will look like

```
app.listen(PORT, async () => {
```

{% embed url="https://github.com/elewin/pi-weather-station" %}
