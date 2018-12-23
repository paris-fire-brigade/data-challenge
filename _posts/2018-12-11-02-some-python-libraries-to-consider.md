---
layout: post
comments: true
title: "02 - Some Python libraries to consider"
categories: post
author: "Benjamin Berhault"
lang: en
---

<div class="row">
  <div class="col grid s12 m6 l3">
    <img src="{{ '/images/libraries.jpg' | relative_url }}" class="responsive-img">
  </div>
  <div class="col grid s12 m6 l9 ">
    <ul>
      <li>Ipyleaflet</li>
      <li>Major Python libraries for data visualization
        <ul>
          <li>Matplotlib</li>
          <li>Seaborn</li>
          <li>Bokeh</li>
        </ul>
      </li>
      <li>OSMnx - Road Network Analysis</li>
    </ul>
  </div>
</div>

##  Ipyleaflet
<b>ipyleaflet</b> is a library facilitating the creation of interactive maps, the insertion and manipulation of objects and geometric shapes.

<div class="row">
  <div class="col grid s12 m4 l3">
    <ul>
      <li><a href="https://ipyleaflet.readthedocs.io/en/latest/">Documentation</a></li>
      <li><a href="https://github.com/jupyter-widgets/ipyleaflet">GitHub repo</a></li>
    </ul>
  </div>
  <div class="col grid s12 m8 l9">
    Installation
    <pre class="language-console"><code class="language-console">conda install -c conda-forge ipyleaflet</code></pre>
  </div>
</div>

Example
<center><img src="{{ '/images/01-libraries/05-libraries.png' | relative_url }}" class="responsive-img"></center>
<br>

## Major Python libraries for data visualization

### Matplotlib
Matplotlib is probably the most used Python package for 2-dimensional data representation.

<div class="row">
  <div class="col grid s12 m4 l3">
    <ul>
      <li><a href="https://matplotlib.org/tutorials/index.html">Tutorials</a></li>
      <li><a href="https://matplotlib.org/gallery/index.html">Gallery</a></li>
    </ul>
  </div>
  <div class="col grid s12 m8 l9">
    Installation
    <pre class="language-console"><code class="language-console">conda install -c conda-forge matplotlib</code></pre>
  </div>
</div>

Example
<center><img src="{{ '/images/01-libraries/02-libraries.png' | relative_url }}" class="responsive-img"></center>

### Seaborn
Seaborn is a data visualization library based on matplotlib.

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

Example
<center><img src="{{ '/images/01-libraries/03-libraries.png' | relative_url }}" class="responsive-img"></center>

### Bokeh
Bokeh enables the creation of interactive visual representations of data by exploiting the latest innovations enjoyed by web browsers.

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

Example
<center><img src="{{ '/images/01-libraries/04-libraries.png' | relative_url }}" class="responsive-img"></center>

## OSMnx - Road Network Analysis (potentially interesting)

OSMnx allows you to retrieve, build, analyze and visualize street networks from OpenStreetMap data.

<div class="row">
  <div class="col grid s12 m4 l3">
    <ul>
      <li><a href="https://github.com/gboeing/osmnx">Repo GitHub</a></li>
      <li><a href="https://github.com/gboeing/osmnx/tree/master/examples">Examples</a></li>
    </ul>
  </div>
  <div class="col grid s12 m8 l9">
    Installation
    <pre class="language-console"><code class="language-console">conda install -c conda-forge osmnx</code></pre>
  </div>
</div>

<center><img src="{{ '/images/01-libraries/06-libraries.png' | relative_url }}" class="responsive-img"></center>

[03 - Use of a route search web service <i class="material-icons" style="vertical-align:middle">fast_forward</i>]({{ site.baseurl }}{% post_url 2018-12-11-03-use-of-a-route-search-web-service %})
{: .align-right}

