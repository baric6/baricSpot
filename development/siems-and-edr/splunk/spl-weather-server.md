# SPL weather server

#### Snow and Rain by Inches

```splunk
index=hourly_weather
| eval _time=strptime(ran_at, "%Y-%m-%dT%H:%M:%S.%6NZ")
| eval temp_f=tonumber('current.temp_f'), precip_mm=tonumber('current.precip_mm')
| eval rain_mm=if(precip_mm>0 AND temp_f>32, precip_mm, 0)
| eval snow_mm=if(precip_mm>0 AND temp_f<=32, precip_mm, 0)
| timechart span=1h sum(rain_mm) AS "Rain (mm)" sum(snow_mm) AS "Snow (mm)"
```

