# Kali in the browser

#### Runs laggy and no network (could be my hardware)

Try with caution&#x20;

* runs without systemd

```
sudo docker run -d \
--name=kali-linux \
--security-opt seccom=unconfined \
-e PUID=1000 \
-e PGID=1000 \ 
-e TZ=Etc/UTC \
-e SUBFOLDER=/ \
-e TITLE="Kali Linux"  \
-p 3011:3000 \
-p 3009:3001
--device /dev/dri:/dev/dri  \
--shm-size="1gb" \
--restart unless-stopped \
lscr.io:/linuxserver/kali-linux:latest

```

