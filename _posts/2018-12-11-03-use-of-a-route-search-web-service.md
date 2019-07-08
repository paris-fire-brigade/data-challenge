---
layout: post
comments: true
title: "03 - Use of a route search web service"
categories: [post]
author: "Benjamin Berhault"
lang: en
published: false
---

<div class="row">
  <div class="col grid s12 m6 l3">
    <img src="{{ '/images/osrm.png' | relative_url }}" class="responsive-img">
  </div>
  <div class="col grid s12 m6 l9 ">To extend your analysis perspectives, a route search service from the OSRM project has been deployed with <a href="https://download.geofabrik.de/europe/france/ile-de-france.html">OpenStreetMap data from Ile-de-France</a>.
    <ul>
    	<li><a href="http://project-osrm.org/docs/v5.15.2/api/#services">Official documentation of use of the API</a></li>
    	<li>URL of the service deployed for this challenge: <a href="http://209.97.130.63:5000">http://209.97.130.63:5000</a></li>
    </ul>
  </div>
</div>

<b>Services provided by the OSRM engine:</b>
<ul>
	<li><a href="http://project-osrm.org/docs/v5.5.1/api/#nearest-service">Nearest service</a> - Snaps a coordinate to the street network and returns the nearest n matches.</li>
	<li><a href="http://project-osrm.org/docs/v5.5.1/api/#tile-service">Route service</a> - Finds the fastest route between coordinates in the supplied order.</li>
	<li><a href="http://project-osrm.org/docs/v5.5.1/api/#table-service">Table service</a> - Computes the duration of the fastest route between all pairs of supplied coordinates.</li>
	<li><a href="http://project-osrm.org/docs/v5.5.1/api/#match-service">Match service</a> - Map matching matches/snaps given GPS points to the road network in the most plausible way.</li>
	<li><a href="http://project-osrm.org/docs/v5.5.1/api/#trip-service">Trip service</a> - The trip plugin solves the Traveling Salesman Problem using a greedy heuristic (farthest-insertion algorithm). The returned path does not have to be the fastest path, as TSP is NP-hard it is only an approximation. </li>
	<li><a href="http://project-osrm.org/docs/v5.5.1/api/#tile-service">Tile service</a> - This service generates Mapbox Vector Tiles that can be viewed with a vector-tile capable slippy-map viewer.</li>
</ul>

## Retrieving the route of a vehicle corresponding to a sequence of GPS tracks

Having available GPS recording of the rescue vehicles, you might want to retrieve information about the routes taken.

Let's take an example with the following sequence of geolocations (longitude, latitude, longitude, latitude, ...):</i> :

```console
2.341618,48.908885;2.343194,48.905945;2.344167,48.911415;2.341778,48.918194;2.342972,48.922474;2.343090,48.922413
```

To retrieve the route corresponding to these GPS positions via the service available, you can use the following code:

```python
import json
import requests
from pprint import pprint

url = 'http://209.97.130.63:5000/route/v1/car/'
url += '2.341618,48.908885;2.343194,48.905945;2.344167,48.911415;2.341778,48.918194;2.342972,48.922474;2.343090,48.922413'
url += '?alternatives=false&steps=false&geometries=polyline&overview=simplified&annotations=false'

response = requests.get(url)
json_data = json.loads(response.text)
```

The `pprint` module (for pretty print) allows the display of self-indented python data structures.

```python
pprint(json_data)
```
```console
{
   "code":"Ok",
   "routes":[
      {
         "geometry":"wkoiHmkhMdAqDbDbE~EoHfCyDee@G{h@W?lMQp@S^wJoM[iB_A@Kp@{ElBj@hBGp@mDdDIuD?W",
         "legs":[
            {
               "steps":[

               ],
               "distance":359.3,
               "duration":50.2,
               "summary":"",
               "weight":50.2
            },
            [...]
         ],
         "distance":2846.7,
         "duration":273.6,
         "weight_name":"routability",
         "weight":273.6
      }
   ],
   "waypoints":[
      {
         "hint":"2-AEgP___39_AAAAfwAAAAkAAAAAAAAAWTypQgAAAAD04LtAAAAAAH8AAAB_AAAACQAAAAAAAAD1BAAAwbsjAPtH6gLyuiMAVUrqAgEArwKra8kH",
         "distance":68.644532,
         "name":"Rue des Entrepreneurs",
         "location":[
            2.341825,
            48.908283
         ]
      },
      [...]
```
You can retrieve the geometry of the evaluated route with the following parameters:

```python
json_data["routes"][0]["geometry"]
```
Geometry returned:
```console
wkoiHmkhMdAqDbDbE~EoHfCyDee@G{h@W?lMQp@S^wJoM[iB_A@Kp@{ElBj@hBGp@mDdDIuD?W
```

You can check the received response with the [Google Interactive Polyline Encoder Utility](https://developers.google.com/maps/documentation/utilities/polylineutility). To do this copy / paste the geometry into the <b>Encoded Polyline</b> and click <b>Decode polyline</b>. In my case, I get the exact polyline expected corresponding to transmitted GPS tracks.

<center>
	<img src="{{ '/images/08-OSRM/01-OSRM.png' | relative_url }}" class="responsive-img">
</center>

<div class="card-panel teal lighten-4">If you feel the need to quickly visualize coordinates on a map you can use:  <a href="https://www.darrinward.com/lat-long/">https://www.darrinward.com/lat-long/</a></div>

[04 - Jupyter and magic commands <i class="material-icons" style="vertical-align:middle">fast_forward</i>]({{ site.baseurl }}{% post_url 2018-12-11-04-jupyter-and-magic-commands %})
{: .align-right}
