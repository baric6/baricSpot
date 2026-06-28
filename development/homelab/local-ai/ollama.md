# Ollama

#### Exposing API for agent development

You can not edit the config directly you have to create a override file to change it, keep Ollama running for this and do it in a separate terminal&#x20;

To view config&#x20;

```
sudo systemctl cat ollama.service
```

Run the command&#x20;

```
ss -tlnp | grep 11434
```

When the output look likes below that means api is only accessible on local host&#x20;

```
LISTEN 0      4096       0.0.0.0:11434      0.0.0.0:*
```

To make it viewable on all machines on the network

Makes a directory

```
sudo mkdir -p /etc/systemd/system/ollama.service.d
```

Makes a blank file you will edit&#x20;

```
sudo nano /etc/systemd/system/ollama.service.d/override.conf
```

In the blank file paste

```
[Service]
Environment="OLLAMA_HOST=0.0.0.0"
```

Save the file and run&#x20;

```
ss -tlnp | grep 11434
```

Now you should see&#x20;

```
LISTEN 0      4096               *:11434            *:*   
```

That means you will be able to connect to the api on any computer on the network
