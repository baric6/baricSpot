# Remap Ports

{% embed url="https://forums.docker.com/t/port-mapping-in-docker-compose/115018/3" %}

#### Notes

```
-p 8000:8000
```

The above ports are mapped 1:1 and will work but if you have multiple containers fighting for ports it can get messy

* The first number is the one to change&#x20;
* the second number is the container number keep that default

```
-p 8003:8000
```

Above means that the user will be able to access the box on :8003 and the container is mapping its internal :8000 to the users :8003
