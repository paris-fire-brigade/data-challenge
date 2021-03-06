---
layout: post
comments: true
title: "01 - Data Analysis Challenge"
categories: [challenge]
author: "Benjamin Berhault"
lang: en
---

<div class="row">
  <div class="col grid s12 m6 l3">
    <center><a href="{{ '/docs/affiche_data_challenge_bspp.pdf' | relative_url }}"><img src="{{ '/images/affiche_data_challenge_bspp_preview.png' | relative_url }}" class="responsive-img" title="Download the challenge poster"></a></center>
  </div>
  <div class="col grid s12 m6 l9 "><p>This challenge is organized as part of the <b>recruitment</b>, in early 2019, of 2 to 3 <b>trainees</b> in the Paris fire service seeking to work in <b>in data analysis, data science and / or business intelligence</b>. Any other participant is however welcome.</p>
      <p>The challenge concerns an operational problem of the rescue service of the Paris Fire Brigade. The anonymised data of the service are made available.</p>
      <p>Candidates must conduct in a <a href="https://jupyter.org/">Jupyter Notebook</a> the analysis of the dataset and answer the problem even extend it. We will pay close attention to the graphical transcription of data, comments and conclusions. A geographical representation is unavoidable.</p>

      <ul>
        <li>Challenge opening date: <b> Friday 14 December 2018</b></li> 
        <li>Challenge closing date: <b> Sunday 20 January 2019</b></li>
      </ul>
  </div>
</div>

<div class="card-panel teal lighten-4">
<h4>Retained candidate</h4>
<div class="row">
  <div class="col grid s12 m6 l3">
    <center><a href="https://www.linkedin.com/in/geoffrey-chetcuti-9a4114164"><img src="{{ '/images/05-candidats/geoffrey_chetcuti.png' | relative_url }}" class="responsive-img"></a></center>
  </div>
  <div class="col grid s12 m6 l9 "><big><b>Geoffrey Chetcuti</b></big> <script src="//platform.linkedin.com/in.js" type="text/javascript"></script>
            <script type="IN/MemberProfile" data-id="http://www.linkedin.com/in/geoffrey-chetcuti-9a4114164" data-format="hover" data-related="false"></script><br>
  Student in the Institut supérieur d’électronique de Paris / ISEP.<br>
  Business Intelligence Specialization<br>
  <br>
  ISEP is a French Grande école located in Paris. It specializes in electronics, telecommunication and computer science.<br>
  <a href="https://www.isep.fr/cycle-ingenieur/parcours-ingenieur-en-business-intelligence/">Specialization details</a>
  </div>
</div>
</div>
<br>

<h3>Problem</h3>
<div class="card-panel amber lighten-4">
<big>Some road sections and periods of traffic in Paris, the departments of 92, 93 and 94 are problematic <u>during</u> the delivery of emergency relief, will you be able to identify them?</big>
</div>

<p>The vehicle movements we are interested in for this analysis are those that occurred during the transit to a place of emergency request, that is to say movements between the <b>Departed</b> and <b>Presented</b> positions. (see Operational Status)</p>

<p>Note that some emergency vehicles do not transmit their GPS positions.</p>

<h5>Other optional issues</h5>
<ul>
  <li>Estimate the <a href="https://fr.wikipedia.org/wiki/Zone_de_chalandise">catchment areas</a> 10 minutes from the rescue centers, for different time slots of the day (you do not need the location of the rescue centers to evaluate these areas).</li>
  <li>The current dispatch system uses a model of estimation of the transit times for emergency vehicles very rigid, would you be able to elaborate a more relevant estimate using for example: the time of the day, day of the week or day of the weekend, road traffic mearsures or weather conditions.</li>
  <li>Are you able to extend the spectrum of your analysis leading to findings that managers of a rescue service might be interested in.</li>
</ul>

<h3>Tutorials</h3>
A consultation of the <a href="{{site.baseurl}}/tutorials.html">tutorials</a> is highly recommended. They are here to help you.

<h3>Works submission</h3>
<ul>
  <li>The works will necessarily be restored within one or more Jupyter Notebook (file .ipynb) in Python 3 preferably, however R will be tolerated.</li>
  <li>Must be sent <b>no later than the 20th of January 2019</b> by email to <a href="mailto:benjamin.berhault@pompiersparis.fr?subject=Soumission%20relative%20au%20Paris%20Fire%20Brigade%20Data%20Challenge&amp;body=Bonjour%E2%80%9A%0AVeuillez%20trouver%20en%20pièce%20jointe%20le%20Notebook%20résultant%20de%20mon%20travail%20concernant%20le%20mini%20challenge%20des%20pompiers%20de%20Paris%20d%C2%B4exploitation%20de%20données.">benjamin.berhault@pompiersparis.fr</a></li>
  <li>We will pay close attention to the graphical transcription of data and conclusions.</li>
  <li>Geographical rendering is strongly recommended.</li>
</ul>

<h3>Data</h3>
<div style="display: flex; align-items:center; text-align: center;">
  <img src="{{ '/images/csv_icon.png' | relative_url }}"><a href="{{ '/data/data.zip' | relative_url }}">Download the dataset</a>
</div>
  <br>
The data cover a period from <b>Monday, September 5, 2016</b> to <b>Sunday, October 30, 2016</b> inclusive, or 8 weeks.

<h5>Dataset columns</h5>
<ul>
  <li><b>Date</b> - Date time of the observed value</li>
  <li><b>Longitude</b> - Longitude of the emergency vehicle GPS position</li>
  <li><b>Latitude</b> - Latitude of the emergency vehicle GPS position</li>
  <li><b>Véhicule de secours</b> - Emergency Vehicle Identifier</li>
  <li><b>Famille de véhicule de secours</b> - Family of emergency vehicle</li>
  <li><b>Statut opérationnel</b> - Operational status of the emergency vehicle, manually entered by crew</li>
  <li><b>Numéro intervention</b> - Identifier of the rescue request to which the emergency vehicle has been allocated</li>
  <li><b>Type intervention</b> - Color referring to an emergency request category</li>
  <li><b>Availability</b> - Emergency vehicle availability based on status (0: unavailable, 1: available)</li>
  <li><b>Centre de secours</b> - Identifier of the fire station from which the emergency vehicle came</li>
</ul>

<h5>Operational statutes</h5>
A emergency vehicle transmits various radio statutes during an intervention for a rescue request, within the dataset these have been reduced to the essential information:
<ul>
  <li><b>Sélection</b> - selection of rescue vehicle in the dispatch application</li>
  <li><b>Parti (Departed)</b> - the vehicle begins its route leading to emergency request place</li>
  <li><b>Présenté (Presented)</b> - the vehicle arrives at the place of the emergency request</li>
  <li><b>Transport hôpital</b> - the vehicle starts transporting a victim to a hospital</li>
  <li><b>Arrivée hôpital</b> - the vehicle arrives at the hospital</li>
  <li><b>Quitte hôpital</b> - the vehicle leaves the hospital</li>
  <li><b>Rentré</b> - the vehicle has returned positioned at its parking spot (a fire station)</li>
  <li><b>Quitte les lieux</b> - because the vehicle can also simply leave the scene of an intervention without having to carry a victim</li>
  <li><b>Indisponible</b> - for various reasons the vehicle can be put in the unavailable position</li>
  <li><b>Non pertinent</b> - statutes without interest for that study</li>
</ul>

<h3>External sources of potentially relevant data</h3>
<ul>
  <li><a href="https://download.geofabrik.de/europe/france/ile-de-france.html">OpenStreetMap data of the region Ile-de-France</a> (nevertheless the <a href="{{ site.baseurl }}{% post_url 2019-06-13-06-set-up-an-osrm-server-on-ubuntu %}">API</a> available can also provide you with a lot of relevant information for your analysis)</li>
  <li>Atmospheric parameters measured or observed (data source: <a href="https://donneespubliques.meteofrance.fr/?fond=produit&id_produit=90&id_rubrique=32">https://donneespubliques.meteofrance.fr</a>)
    <ul>
      <li><a href="{{ '/data/meteo_synop.201609.csv.gz' | relative_url }}">Data from September 2016</a></li>
      <li><a href="{{ '/data/meteo_synop.201610.csv.gz' | relative_url }}">Data from October 2016</a></li>
    </ul>
  </li>
  <li><a href="https://opendata.paris.fr/explore/dataset/comptages-routiers-permanents/information/">Paris traffic data from permanent sensors</a>
    <ul>
      <li><a href="https://opendata.paris.fr/api/datasets/1.0/comptages-routiers-permanents/attachments/2016_paris_donnees_trafic_capteurs_zip/">2016 data</a></li>
      <li><a href="https://opendata.paris.fr/explore/dataset/referentiel-comptages-routiers/download/?format=csv&timezone=Europe/Berlin&use_labels_for_header=true">Geographical repository for traffic data from permanent sensors</a></li>
    </ul>
  </li>
</ul>

<br>