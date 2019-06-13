---
layout: post
comments: true
title: "04 - Jupyter et les commandes magiques"
categories: [post]
author: "Benjamin Berhault"
lang: fr
---

<div class="row">
  <div class="col grid s12 m6 l3" height>
    <img src="{{ '/images/magic-wand.jpg' | relative_url }}" class="responsive-img" style="padding-top: 20px">
  </div>
  <div class="col grid s12 m6 l9 ">
    Jupyter dispose d'un système de commandes dites « magiques » offrant un langage de commande minimaliste et extensible.
  </div>
</div>

<b>Références</b>
* [Jupyter Notebook documentation](https://ipython.org/ipython-doc/3/interactive/tutorial.html#magic-functions)
* [The cell magics in IPython](http://nbviewer.jupyter.org/github/ipython/ipython/blob/1.x/examples/notebooks/Cell%20Magics.ipynb)

<b>2 types de fonctions magiques sont à distinguer :</b>

* <b>Line magics</b> : il s'agit de commandes précédées d'un caractère `%` et dont les arguments ne s'étendent que jusqu'à la fin de la ligne courante. Par exemple, `%matplotlib inline` permet l'affichage des figures directement au sein du notebook.
* <b>Cell magics</b> : il s'agit de commandes précédées des caractères `%%` et prendra en compte les instructions de toute la cellule.

<b>Exemple :</b>

<center><img src="{{ '/images/02-magic/01-magic.png' | relative_url }}" class="responsive-img"></center>

[05 - Exploitation des données à partir d'une base de données <i class="material-icons" style="vertical-align:middle">fast_forward</i>]({{ site.baseurl }}{% post_url 2018-12-14-05-exploitation-des-donnees-au-sein-d-une-bdd %})
{: .align-right}