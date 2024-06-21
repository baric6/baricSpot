# Rancher Kubernetes cluster

<figure><img src="../../.gitbook/assets/kind-of-excited-that-i-finally-went-this-route-rancher-for-v0-hi93qqref87c1.webp" alt=""><figcaption></figcaption></figure>

Docker Quick-start

```
docker run -d --restart=unless-stopped \
  -p 80:80 -p 443:443 \
  --privileged \
  rancher/rancher:latest
```

{% embed url="https://ranchermanager.docs.rancher.com/getting-started/installation-and-upgrade/other-installation-methods/rancher-on-a-single-node-with-docker" %}
