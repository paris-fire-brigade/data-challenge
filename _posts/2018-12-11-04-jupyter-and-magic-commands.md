---
layout: post
comments: true
title: "04 - Jupyter and magic commands"
categories: post
author: "Benjamin Berhault"
lang: en
---

<div class="row">
  <div class="col grid s12 m6 l3" height>
    <img src="{{ '/images/magic-wand.jpg' | relative_url }}" class="responsive-img" style="padding-top: 20px">
  </div>
  <div class="col grid s12 m6 l9 ">
    Jupyter has a system of so-called « magic » commands with a minimalist and extensible control language.
  </div>
</div>

<b>References</b>
* [Jupyter Notebook documentation](https://ipython.org/ipython-doc/3/interactive/tutorial.html#magic-functions)
* [The cell magics in IPython](http://nbviewer.jupyter.org/github/ipython/ipython/blob/1.x/examples/notebooks/Cell%20Magics.ipynb)

<b>There are two types of magic functions to distinguish:</b>

* <b>Line magics</b>: These are commands preceded by a `%` character and whose arguments extend only to the end of the current line. For example, `%matplotlib inline` allows displaying figures directly within the notebook.
* <b>Cell magics</b>:  These are commands preceded by the characters `%%` and will take into account the instructions of the entire cell.

<b>Example :</b>

<center><img src="{{ '/images/02-magic/01-magic.png' | relative_url }}" class="responsive-img"></center>

[05 - Using data from a database <i class="material-icons" style="vertical-align:middle">fast_forward</i>]({{ site.baseurl }}{% post_url 2018-12-14-05-using-data-from-a-database %})
{: .align-right}

