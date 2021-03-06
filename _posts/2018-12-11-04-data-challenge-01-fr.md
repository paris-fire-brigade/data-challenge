---
layout: post
comments: true
title: "Challenge"
categories: [challenge]
author: "Benjamin Berhault"
lang: fr
---

<div class="section no-pad-bot" id="index-banner">
  <div class="container">

    <h1 class="header center black-text">{{ page.title | escape }}</h1>
    
    <br>
  </div>
</div>

<div class="row">
  <div class="col grid s12 m6 l3">
    <img src="{{ '/images/data_challenge.jpg' | relative_url }}" class="responsive-img">
  </div>
  <div class="col grid s12 m6 l9 ">
    <big><b>Contenu de la page</b></big>
      <ul>
        <li>Problématique à traiter</li>
        <li>Tutoriels</li>
        <li>Restitution des travaux</li>
        <li>Données</li>
        <li>Sources externes de données potentiellement pertinentes</li>
      </ul>
  </div>
</div>

La Brigade de Sapeurs-Pompiers de Paris assure les missions de secours à victimes et de protection contre l'incendie sur Paris, le 92, 93 et 94.

<h2>Problématique à traiter</h2>
<div class="card-panel amber lighten-4"><big>Certains tronçons routiers et périodes de circulation sur Paris, les départements du 92, 93 et 94 sont problématiques <u>lors</u> de l'engagement des secours, serez-vous capable de les identifier ?</big></div>

<p>Les déplacements de véhicules nous intéressant pour cette analyse sont ceux ayant lieux lors du transit vers un lieu de demande de secours, c'est-à-dire les déplacements entre les positions <b>Parti</b> et <b>Présenté</b>. (cf. Statuts opérationnels)</p>

<p>A noter que certains véhicules de secours ne remontent pas de positions GPS.</p>

<p><b>Echéance :</b> le 20 janvier 2019</p>

<h4>Autres problématiques optionnelles</h4>
<ul>
  <li>Estimer les <a href="https://fr.wikipedia.org/wiki/Zone_de_chalandise">zones de chalandises</a> à 10 minutes des centres de secours, pour différentes tranches horaires de la journée (vous n'avez pas besoin de l'emplacement des centres de secours pour évaluer ces zones).</li>
  <li>Le système actuel d'engagement du service de secours utilise un modèle d'estimation des temps de transit des véhicules de secours très rigide, seriez-vous capable d'en élaborer un plus pertinent fonction par exemple: de l'heure de la journée, jour de la semaine ou jour du weekend, période de l'année ou conditions météorologiques.</li>
  <li>Etes-vous capable d'étendre le spectre de votre analyse menant à des trouvailles pouvant potentiellement intéresser les gestionnaires du service de secours.</li>
</ul>

<h2>Tutoriels</h2>
Une consultation des <a href="{{ '/tutoriels.html' | relative_url }}">tutoriels</a> mis à disposition est fortement recommandé. Ils sont là pour vous aider.

<h2>Restitution des travaux</h2>
<ul>
  <li>Les travaux seront obligatoirement restitués au sein d'un ou plusieurs Jupyter Notebook (fichier .ipynb) en Python 3 de préférence, R sera cependant toléré.</li>
  <li>A transmettre <b>au plus tard le 20 janvier 2019</b> par mail à <a href="mailto:benjamin.berhault@pompiersparis.fr?subject=Soumission%20relative%20au%20Paris%20Fire%20Brigade%20Data%20Challenge&amp;body=Bonjour%E2%80%9A%0AVeuillez%20trouver%20en%20pièce%20jointe%20le%20Notebook%20résultant%20de%20mon%20travail%20concernant%20le%20mini%20challenge%20des%20pompiers%20de%20Paris%20d%C2%B4exploitation%20de%20données.">benjamin.berhault@pompiersparis.fr</a></li>
  <li>Nous porterons une grande attention à la transcription graphique des données et conclusions.</li>
  <li>Un rendu géographique est fortement conseillé.</li>
</ul>

<h2>Données</h2>
<div style="display: flex; align-items:center; text-align: center;"><img src="{{ '/images/csv_icon.png' | relative_url }}"> <a href="{{ '/data/data.zip' | relative_url }}">Télécharger le jeu de données</a></div>
<br>
Les données s'étendent sur une période allant du <b>lundi 5 septembre 2016</b> au <b>dimanche 30 octobre 2016</b> inclus, soit 8 semaines.

<h4>Colonnes du jeu de données</h4>
<ul>
  <li><b>Date</b> - Date heure de l'information relevée</li>
  <li><b>Longitude</b> - Longitude de la position du véhicule de secours</li>
  <li><b>Latitude</b> - Latitude de la position du véhicule de secours</li>
  <li><b>Véhicule de secours</b> - Identifiant du véhicule de secours</li>
  <li><b>Famille de véhicule de secours</b></li>
  <li><b>Statut opérationnel</b> - Statut opérationnel du véhicule de secours saisi manuellement par l'équipage</li>
  <li><b>Numéro intervention</b> - Identifiant de la demande de secours à laquelle a été alloué le véhicule de secours</li>
  <li><b>Type intervention</b> - Couleur faisant référence à une catégorie d'intervention</li>
  <li><b>Disponibilité</b> - Disponibilité du moyen de secours découlant des statuts (0 : indisponible, 1 : disponible)</li>
  <li><b>Centre de secours</b> - Identifiant du centre de secours dont est issu le véhicule de secours</li>
</ul>

<h4>Statuts opérationnels</h4>
Un véhicule transmet divers statuts lors d'une intervention pour une demande de secours, au sein du jeu de données ces derniers ont été regroupés aux informations essentielles :
<ul>
  <li><b>Sélection</b> - sélection du véhicule de secours par l'application d'engagement des secours</li>
  <li><b>Parti</b> - le véhicule débute son itinéraire vers le lieu de la demande de secours</li>
  <li><b>Présenté</b> - le véhicule arrive sur le lieu de la demande de secours</li>
  <li><b>Transport hôpital</b> - le véhicule débute le transport d'une victime vers un hôpital</li>
  <li><b>Arrivée hôpital</b> - le véhicule arrive à l'hôpital</li>
  <li><b>Quitte hôpital</b> - le véhicule quitte l'hôpital</li>
  <li><b>Rentré</b> - le véhicule est revenu positionné à son lieu de stationnement</li>
  <li><b>Quitte les lieux</b> - car le véhicule peut également simplement quitter les lieux d'une intervention sans avoir à transporter une victime</li>
  <li><b>Indisponible</b> - pour diverses raisons le véhicule peut être mis en position d'indisponibilité</li>
  <li><b>Non pertinent</b> - statuts sans intérêt</li>
</ul>

<h2>Sources externes de données potentiellement pertinentes</h2>
<ul>
  <li><a href="https://download.geofabrik.de/europe/france/ile-de-france.html">Données OpenStreetMap Ile-de-France</a> (néanmoins l'<a href="{{ site.baseurl }}{% post_url 2019-06-13-06-set-up-an-osrm-server-on-ubuntu %}">API</a> mise à disposition peut également vous fournir beaucoup d'information pertinente pour vos analyses)</li>
  <li>Paramètres atmosphériques mesurés ou observés (source de données : <a href="https://donneespubliques.meteofrance.fr/?fond=produit&id_produit=90&id_rubrique=32">https://donneespubliques.meteofrance.fr</a>)
    <ul>
      <li><a href="{{ '/data/meteo_synop.201609.csv.gz' | relative_url }}">Données de septembre 2016</a></li>
      <li><a href="{{ '/data/meteo_synop.201610.csv.gz' | relative_url }}">Données d'octobre 2016</a></li>
    </ul>
  </li>
  <li><a href="https://opendata.paris.fr/explore/dataset/comptages-routiers-permanents/information/">Données trafic de la ville de Paris issues de capteurs permanents</a>
    <ul>
      <li><a href="https://opendata.paris.fr/api/datasets/1.0/comptages-routiers-permanents/attachments/2016_paris_donnees_trafic_capteurs_zip/">Données de 2016</a></li>
      <li><a href="https://opendata.paris.fr/explore/dataset/referentiel-comptages-routiers/download/?format=csv&timezone=Europe/Berlin&use_labels_for_header=true">Référentiel géographique pour les données trafic issues des capteurs permanents</a></li>
    </ul>
  </li>
</ul>
<br>