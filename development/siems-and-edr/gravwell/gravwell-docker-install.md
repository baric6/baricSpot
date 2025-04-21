# Gravwell Docker Install

### Install

Note

* I had to change the port to 8081 because i already had a docker listening 8080
* I also took out --net gravnet option because i didn't care it is on another network

```
docker run -p 8081:80 -p 4023:4023 -p 4024:4024 -d -e GRAVWELL_INGEST_SECRET=MyIngestSecret -e GRAVWELL_INGEST_AUTH=MyIngestSecret -e GRAVWELL_CONTROL_AUTH=MyControlSecret -e GRAVWELL_SEARCHAGENT_AUTH=MySearchAgentAuth --name gravwell gravwell/gravwell:latest
```

Default web portal Creds:  admin / changeme
