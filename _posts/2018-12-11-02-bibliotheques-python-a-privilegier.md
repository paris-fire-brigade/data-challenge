---
layout: post
comments: true
title: "02 - Bibliothèques Python à privilégier"
categories: [post]
author: "Benjamin Berhault"
lang: fr
---

<div class="row">
  <div class="col grid s12 m6 l3">
    <img src="{{ '/images/libraries.jpg' | relative_url }}" class="responsive-img">
  </div>
  <div class="col grid s12 m6 l9 ">
    <ul>
      <li>L'incontournable ipyleaflet</li>
      <li>Majeures bibliothèques Python de data visualization
        <ul>
          <li>Matplotlib</li>
          <li>Seaborn</li>
          <li>Bokeh</li>
        </ul>
      </li>
      <li>OSMnx - Analyse de réseau routier en Python</li>
    </ul>
  </div>
</div>

##  L'incontournable ipyleaflet
<b>ipyleaflet</b> est une bibliothèque facilitant la création de cartes interactives, l'insertion et manipulation d'objets et formes géométriques.

<div class="row">
  <div class="col grid s12 m4 l3">
    <ul>
      <li><a href="https://ipyleaflet.readthedocs.io/en/latest/">Documentation</a></li>
      <li><a href="https://github.com/jupyter-widgets/ipyleaflet">Répertoire GitHub</a></li>
    </ul>
  </div>
  <div class="col grid s12 m8 l9">
    Installation
    <pre class="language-console"><code class="language-console">conda install -c conda-forge ipyleaflet</code></pre>
  </div>
</div>

Exemple d'utilisation
<center><img src="{{ '/images/01-libraries/05-libraries.png' | relative_url }}" class="responsive-img"></center>
<br>

## Majeures bibliothèques Python de data visualization

### Matplotlib
Matplotlib est probablement le package Python le plus utilisé pour la représentation de données en 2 dimensions.

<div class="row">
  <div class="col grid s12 m4 l3">
    <ul>
      <li><a href="https://matplotlib.org/tutorials/index.html">Tutoriels</a></li>
      <li><a href="https://matplotlib.org/gallery/index.html">Galerie</a></li>
    </ul>
  </div>
  <div class="col grid s12 m8 l9">
    Installation
    <pre class="language-console"><code class="language-console">conda install -c conda-forge matplotlib</code></pre>
  </div>
</div>

Exemple d'utilisation
<center><img src="{{ '/images/01-libraries/02-libraries.png' | relative_url }}" class="responsive-img"></center>

### Seaborn
Seaborn est une bibliothèque de data visualisation basée sur matplotlib.

<div class="row">
  <div class="col grid s12 m4 l3">
    <ul>
      <li><a href="https://seaborn.pydata.org/tutorial.html">Tutoriels</a></li>
      <li><a href="https://seaborn.pydata.org/examples/index.html">Galerie</a></li>
    </ul>
  </div>
  <div class="col grid s12 m8 l9">
    Installation
    <pre class="language-console"><code class="language-console">conda install -c conda-forge seaborn</code></pre>
  </div>
</div>

Exemple d'utilisation
<center><img src="{{ '/images/01-libraries/03-libraries.png' | relative_url }}" class="responsive-img"></center>

### Bokeh
Bokeh permet la création de visuels intéractifs de représentation de données en exploitant les dernières innovations dont bénéficient les navigateurs web.

<div class="row">
  <div class="col grid s12 m4 l3">
    <ul>
      <li><a href="https://hub.mybinder.org/user/bokeh-bokeh-notebooks-su7mtuxo/notebooks/tutorial/00%20-%20Introduction%20and%20Setup.ipynb">Tutoriels</a></li>
      <li><a href="https://bokeh.pydata.org/en/latest/docs/gallery.html">Galerie</a></li>
    </ul>
  </div>
  <div class="col grid s12 m8 l9">
    Installation
    <pre class="language-console"><code class="language-console">conda install -c conda-forge bokeh</code></pre>
  </div>
</div>
<br>

Exemple d'utilisation
<center><img src="{{ '/images/01-libraries/04-libraries.png' | relative_url }}" class="responsive-img"></center>

## OSMnx - Analyse de réseau routier en Python (potentiellement intéressant)

OSMnx permet de récupérer, construire, analyser et visualiser les réseaux de rues issus de données OpenStreetMap.

<div class="row">
  <div class="col grid s12 m4 l3">
    <ul>
      <li><a href="https://github.com/gboeing/osmnx">Repo GitHub</a></li>
      <li><a href="https://github.com/gboeing/osmnx/tree/master/examples">Exemples</a></li>
    </ul>
  </div>
  <div class="col grid s12 m8 l9">
    Installation
    <pre class="language-console"><code class="language-console">conda install -c conda-forge osmnx</code></pre>
  </div>
</div>

<center><img src="{{ '/images/01-libraries/06-libraries.png' | relative_url }}" class="responsive-img"></center>

[04 - Jupyter et les commandes magiques <i class="material-icons" style="vertical-align:middle">fast_forward</i>]({{ site.baseurl }}{% post_url 2018-12-11-04-jupyter-et-les-commandes-magiques %})
{: .align-right}

