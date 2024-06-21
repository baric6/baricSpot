# Portainer Docker Management

<figure><img src="../../.gitbook/assets/portainer-container-list-screen.webp" alt=""><figcaption></figcaption></figure>

{% embed url="https://docs.portainer.io/start/intro" %}

Quick-Start Docker

`docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest`

{% embed url="https://docs.portainer.io/start/install-ce/server/docker" %}
