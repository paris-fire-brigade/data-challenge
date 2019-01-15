---
layout: post
comments: true
title: "03 - Utilisation d'un service web de recherche d'itinéraire"
categories: post
author: "Benjamin Berhault"
lang: fr
---

<div class="row">
  <div class="col grid s12 m6 l3">
    <img src="{{ '/images/osrm.png' | relative_url }}" class="responsive-img">
  </div>
  <div class="col grid s12 m6 l9 ">Pour étendre vos perspectives d'analyse, un service de recherche d'itinéraire issu du projet <a href="http://project-osrm.org/">OSRM</a> a été déployé avec les <a href="https://download.geofabrik.de/europe/france/ile-de-france.html">données OpenStreetMap d'Ile-de-France</a>.
    <ul>
    	<li><a href="http://project-osrm.org/docs/v5.15.2/api/#services">Documentation officielle d'utilisation de l'API</a></li>
    	<li>URL du service déployé pour ce challenge : <a href="http://209.97.130.63:5000">http://209.97.130.63:5000</a></li>
    </ul>
  </div>
</div>

<b>Services fournis par le moteur OSRM :</b>
<ul>
	<li><a href="http://project-osrm.org/docs/v5.5.1/api/#nearest-service">Nearest service</a> - Snaps a coordinate to the street network and returns the nearest n matches.</li>
	<li><a href="http://project-osrm.org/docs/v5.5.1/api/#tile-service">Route service</a> - Finds the fastest route between coordinates in the supplied order.</li>
	<li><a href="http://project-osrm.org/docs/v5.5.1/api/#table-service">Table service</a> - Computes the duration of the fastest route between all pairs of supplied coordinates.</li>
	<li><a href="http://project-osrm.org/docs/v5.5.1/api/#match-service">Match service</a> - Map matching matches/snaps given GPS points to the road network in the most plausible way.</li>
	<li><a href="http://project-osrm.org/docs/v5.5.1/api/#trip-service">Trip service</a> - The trip plugin solves the Traveling Salesman Problem using a greedy heuristic (farthest-insertion algorithm). The returned path does not have to be the fastest path, as TSP is NP-hard it is only an approximation. </li>
	<li><a href="http://project-osrm.org/docs/v5.5.1/api/#tile-service">Tile service</a> - This service generates Mapbox Vector Tiles that can be viewed with a vector-tile capable slippy-map viewer.</li>
</ul>

## Récupération de l'itinéraire d'un véhicule correspondant à une suite de traces GPS

Ayant à disposition les traces GPS des véhicules de secours, vous pourriez vouloir récupérer des infomations relatives aux parcours empruntés. 

Prenons un exemple avec la suite de géolocalisations suivante <i>(longitude,latitude;longitude,latitude;...)</i> :

```console
2.341618,48.908885;2.343194,48.905945;2.344167,48.911415;2.341778,48.918194;2.342972,48.922474;2.343090,48.922413
```

Pour récupérer l'itinéraire correspondant à ces positions GPS via le service à disposition, vous pouvez utiliser le code suivant :

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

Le module `pprint` (pour pretty print) permet l'affichage de structures de données Python auto-indentées.

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
Vous pouvez récupérer la géométrie de l'itinéraire évalué avec les paramètres suivants :

```python
json_data["routes"][0]["geometry"]
```
Géométrie retournée :
```console
wkoiHmkhMdAqDbDbE~EoHfCyDee@G{h@W?lMQp@S^wJoM[iB_A@Kp@{ElBj@hBGp@mDdDIuD?W
```

Vous pouvez vérifier la réponse obtenue avec la [Google Interactive Polyline Encoder Utility](https://developers.google.com/maps/documentation/utilities/polylineutility). Pour cela copier/coller la géométrie dans le champ <b>Encoded Polyline</b> et cliquez sur <b>Decode polyline</b>. Dans mon cas, j'obtiens l'exacte polyline attendue correspondant aux traces GPS transmises.

<center>
	<img src="{{ '/images/08-OSRM/01-OSRM.png' | relative_url }}" class="responsive-img">
</center>

<div class="card-panel teal lighten-4">Si vous ressentez le besoin de visualiser très rapidement des coordonées sur une carte vous pouvez utiliser : <a href="https://www.darrinward.com/lat-long/">https://www.darrinward.com/lat-long/</a></div>

[04 - Jupyter et les commandes magiques <i class="material-icons" style="vertical-align:middle">fast_forward</i>]({{ site.baseurl }}{% post_url 2018-12-11-04-jupyter-et-les-commandes-magiques %})
{: .align-right}
