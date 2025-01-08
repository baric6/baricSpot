# Queries

### Search for all logs

```
tag=*
```

### Count all logs

```
tag=* | stats count
```

### count by search word

```
tag=* words admin | stats count
```
