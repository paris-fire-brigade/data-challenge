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
2.25975,48.923557;2.248389,48.922695;2.235361,48.916889;2.2255,48.91325;2.225833,48.914028;2.225861,48.914001;2.225833,48.914055;2.225861,48.914055;2.226417,48.914333;2.230083,48.91486;2.23725,48.917557;2.242917,48.920029;2.24775,48.922417;2.249278,48.922749;2.252528,48.922916;2.256556,48.923054;2.261778,48.922779;2.262389,48.922638;2.262333,48.922611;2.262361,48.922611;2.262194,48.922585;2.262194,48.922585;2.262194,48.922585;2.262167,48.922585;2.262139,48.922585;2.262167,48.922585;2.262167,48.922554;2.262194,48.922554
```

Pour récupérer l'itinéraire correspondant à ces positions GPS via le service à disposition, vous pouvez utiliser le code suivant :

```python
import json
import requests
from pprint import pprint

url = 'http://209.97.130.63:5000/trip/v1/driving/'
url += '2.25975,48.923557;2.248389,48.922695;2.235361,48.916889;2.2255,48.91325;2.225833,48.914028;2.225861,48.914001;2.225833,48.914055;2.225861,48.914055;2.226417,48.914333;2.230083,48.91486;2.23725,48.917557;2.242917,48.920029;2.24775,48.922417;2.249278,48.922749;2.252528,48.922916;2.256556,48.923054;2.261778,48.922779;2.262389,48.922638;2.262333,48.922611;2.262361,48.922611;2.262194,48.922585;2.262194,48.922585;2.262194,48.922585;2.262167,48.922585;2.262139,48.922585;2.262167,48.922585;2.262167,48.922554;2.262194,48.922554'
url += '?source=first&destination=last'

response = requests.get(url)
json_data = json.loads(response.text)
```

Le module `pprint` (pour pretty print) permet l'affichage de structures de données Python auto-indentées.

```python
pprint(json_data)
```
```console

{'code': 'Ok',
 'trips': [{'distance': 6372.6,
            'duration': 632.3,
            'geometry': 'gkriHmjxLp@zE_@xGhAvCh@vC{@hLHvEMDPxJv@jG`@hDh@jC~M`]rF|M|FjShCtJpK``@p@nE~BfFnDbLe@d@{AvA{@cC??AC?Cs@sBuCiI~BkD}T{x@sDkMgVem@wAgPGuHNiAHg@k@iEl@{KqBwG^yGy@uExCqBBiHFqANg@??????????????????W~ACbIqCjB',
            'legs': [{'distance': 266.3,
                      'duration': 24.1,
                      'steps': [],
                      'summary': '',
                      'weight': 24.1},
                     {'distance': 551.4,
                      'duration': 50.4,
                      'steps': [],
                      ...
```
Vous pouvez récupérer la géométrie de l'itinéraire évalué avec les paramètres suivants :

```python
json_data["trips"][0]["geometry"]
```
Géométrie retournée :
```console
gkriHmjxLp@zE_@xGhAvCh@vC{@hLHvEMDPxJv@jG`@hDh@jC~M`]rF|M|FjShCtJpK``@p@nE~BfFnDbLe@d@{AvA{@cC??AC?Cs@sBuCiI~BkD}T{x@sDkMgVem@wAgPGuHNiAHg@k@iEl@{KqBwG^yGy@uExCqBBiHFqANg@??????????????????W~ACbIqCjB
```

Vous pouvez vérifier la réponse obtenue avec la [Google Interactive Polyline Encoder Utility](https://developers.google.com/maps/documentation/utilities/polylineutility). Pour cela copier/coller la géométrie dans le champ <b>Encoded Polyline</b> et cliquez sur <b>Decode polyline</b>. Dans mon cas, j'obtiens l'exacte polyline attendue correspondant aux traces GPS transmises.

<center>
	<img src="{{ '/images/08-OSRM/01-OSRM.png' | relative_url }}" class="responsive-img">
</center>

<div class="card-panel teal lighten-4">Si vous ressentez le besoin de visualiser très rapidement des coordonées sur une carte vous pouvez utiliser : <a href="https://www.darrinward.com/lat-long/">https://www.darrinward.com/lat-long/</a></div>

[04 - Jupyter et les commandes magiques <i class="material-icons" style="vertical-align:middle">fast_forward</i>]({{ site.baseurl }}{% post_url 2018-12-11-04-jupyter-et-les-commandes-magiques %})
{: .align-right}
