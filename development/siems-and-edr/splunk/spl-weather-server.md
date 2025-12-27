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

<figure><img src="../../../.gitbook/assets/image (463).png" alt=""><figcaption></figcaption></figure>

#### Chances of a Tornado

This looks at

* current temp
* current dew-point
* current humidity
* current pressure
* current wind and gusts
* current precipitation

Gives a score from 0-100 to try to predict tornado type conditions&#x20;

```splunk
index=hourly_weather
| eval _time=strptime(ran_at, "%Y-%m-%dT%H:%M:%S.%6NZ")
| eval temp_f=tonumber('current.temp_f')
| eval dewpoint_f=tonumber('current.dewpoint_f')
| eval humidity=tonumber('current.humidity')
| eval pressure=tonumber('current.pressure_mb')
| eval wind=tonumber('current.wind_kph')
| eval gust=tonumber('current.gust_kph')
| eval precip=tonumber('current.precip_mm')
| sort 0 _time
| streamstats current=f last(pressure) AS prev_pressure
| eval pressure_drop=prev_pressure-pressure
| eval spread=temp_f-dewpoint_f
| eval pressure_score=case(
    pressure_drop>=5,30,
    pressure_drop>=3,20,
    pressure_drop>=2,10,
    true(),0
)
| eval spread_score=case(
    spread<=2,25,
    spread<=4,20,
    spread<=6,10,
    true(),0
)
| eval wind_score=case(
    gust>=50,20,
    gust>=40,15,
    wind>=25,10,
    true(),0
)
| eval humidity_score=case(
    humidity>=75,15,
    humidity>=65,10,
    humidity>=55,5,
    true(),0
)
| eval precip_score=if(precip>0,10,0)
| eval tornado_risk_percent=pressure_score+spread_score+wind_score+humidity_score+precip_score
| timechart span=30m max(tornado_risk_percent) AS "Tornado Risk (%)"
```

Anything that has a 70% or greater is a cause for concern

<figure><img src="../../../.gitbook/assets/image (464).png" alt=""><figcaption></figcaption></figure>
