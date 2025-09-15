# Server Search Management

#### Find Expensive Searches

```
index=_internal sourcetype=scheduler component=SavedSplunker 
| eval runtime=round(run_time,2) 
| stats avg(runtime) max(runtime) count by savedsearch_name
| sort - max(runtime)
```

#### To many concurrent Searches

```
index=_internal sourcetype=splunkd component=DispatchManager
| timechart count by status
```

