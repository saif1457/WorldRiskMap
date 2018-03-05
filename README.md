# WorldRiskMap
A portal to view World Risk analytics from causes ranging from natural incidents (earthquakes, weather) to economic events (stock market crash, commodity price crash), etc. Website is live at www.saifbhatti.com/worldrisk.

Map preview:

![WorldRiskMap](http://res.cloudinary.com/dcl78rpmg/image/upload/c_limit,q_10,w_819/v1517327976/worldrisk_hvizxz.png "World Risk Map")

## Implemented Technologies
The map autoupdates natural disaster information using `jquery`'s `getJSON()` function within JavaScript. This is then implemented using [LeafletJS](http://leafletjs.com) and HTML5/CSS3 on my website.

Currently there is no back-end database connection.

### Earthquakes

All earthquake data is brought in using the following API call to the [United States Geological Survey](https://earthquake.usgs.gov):

`https://earthquake.usgs.gov/fdsnws/event/1/query?format=geojson&starttime=2018-01-01&minmagnitude=6`

With the risk profile, I was particularly concerned with the most significant events, as many small earthquakes occur daily which cause little to no harm. Within the API call, I specified that the only events in 2018 with `starttime=2018-01-01` and only earthquakes with `minmagnitude=6`.

### Freak Weather

In order to determine that constituted an `freak weather event`, first needed to compile a database of historial highs and low for the cities being considered. 

An example table:

| Cities   | Historial Low °C | Historical High |
|----------|------------------|-----------------|
| London   |        -5        |        35       |
| Paris    |                  |        32       |
| New York |                  |        34       |

Basic  logic for determining a `freak weather event`:

```
if City_Temp falls within 25% of Historial_High 

  freak_weather_event = Heatwave

if City_Temp falls within 25% of Historial_Low

  freak_weather_event = Freeze

if City_Wind_Speed exceeds 40mph

  freak_weather_event = Windstorm
```

## Upcoming Additions

- Adding a changelog sidebar on the website
- Adding a timesweep bar to allow user to move through time and see events occur
- Adding Weather API and `heatwave`, `freeze` and `windstorm` Icons


