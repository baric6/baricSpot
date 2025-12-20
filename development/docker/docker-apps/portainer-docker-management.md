# Portainer Docker Management

<figure><img src="../../../.gitbook/assets/portainer-container-list-screen.webp" alt=""><figcaption></figcaption></figure>

{% embed url="https://docs.portainer.io/start/intro" %}

#### Add a volume to Docker

```
sudo docker volume create portainer_data
```

When creating a new container it is always good to add a volume before, this goes for all containers you create in the future &#x20;

#### Quick-Start Docker

```
sudo docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
```

{% embed url="https://docs.portainer.io/start/install-ce/server/docker" %}

#### Install docker Portainer and run a small docker through Portainer

{% embed url="https://www.youtube.com/watch?v=qmkAu2e9nS0" %}
