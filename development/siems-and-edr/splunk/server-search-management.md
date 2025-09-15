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



Quick fixes

* Kill runaway searches in **Activity → Jobs**.
* Extend default search time window (don’t allow users to query “All time”).
* Throttle scheduled searches to run less often.
* Review CIM/data model accelerations you don’t actually use.
