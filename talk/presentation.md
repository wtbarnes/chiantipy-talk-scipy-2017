title: ChiantiPy
class: animation-fade
layout: true

<!-- This slide will serve as the base layout for all your slides -->
.colorstrip[
]
.bottom-bar[
    <a href="https://wtbarnes.github.io/chiantipy-talk-scipy-2017/">
    wtbarnes.github.io/chiantipy-talk-scipy-2017
    </a>
    <img src="img/gm_logo_white_190.gif" class="school-logo">
    <img src="img/rice_owl_logo.transparent.png" class="school-logo">
]

---

class: impact

<h1><img src="img/chiantipy-logo.png" height="150px" style="vertical-align:bottom">{{title}}</h1>
## A Python Package for Astrophysical Spectroscopy
### 2017 SciPy Conference &ndash; Austin, TX
## Will Barnes<sup id="rice">1</sup>, Kenneth Dere<sup id="gm">2</sup>
### 14 July 2017
###### <sup id="rice">1</sup> Department of Physics & Astronomy, Rice University, Houston, TX 
###### <sup id="gm">2</sup> Deptartment of Physics & Astronomy, George Mason University, Fairfax, VA  

---


# Contact Info
.col-2[
&zwnj;
]
.col-8[
<i class="fa fa-github-alt fa-3x" aria-hidden="true" style="vertical-align:middle; padding-right:10px;"></i>
<a href="https://github.com/wtbarnes">wtbarnes</a>

<i class="fa fa-twitter fa-3x" aria-hidden="true" style="vertical-align:middle; padding-right:10px;"></i>
<a href="https://twitter.com/wtbarnes_">wtbarnes_</a>

<i class="fa fa-globe fa-3x" aria-hidden="true" style="vertical-align:middle; padding-right:10px;"></i>
<a href="http://wtbarnes.github.io/">wtbarnes.github.io</a>

<i class="fa fa-envelope fa-3x" aria-hidden="true" style="vertical-align:middle; padding-right:10px;"></i>
<a href="mailto:will.t.barnes@gmail.com">
will.t.barnes@gmail.com
</a>
]

.col-2[
&zwnj;
]

---
# What is CHIANTI?

---
background-image: url("img/chianti_tree.png")
background-size: contain

# The CHIANTI Project

???
Explain chart, hierarchy

Efforts of the CHIANTI team over the years have been focused on database and IDL code

ChiantiPy developed by Ken Dere

Solar physics slow to adopt Python so IDL still primary interface to the data
---
class: full,middle,center
background-image: url("img/chianti_team.png")

---
Quotes with pictures from a few team members

CHIANTI consolidated many atomic datasets from the literature

Goal was to have single, well-maintained, and freely-available database

CHIANTI name not an acronym, but rather because of connection to Arcetri and Tuscany

What role it has played in interpreting data from instruments in solar physics, use in astrophysics

Basically, make the point that CHIANTI has been an integral part of solar 

???
Note from paper reviewer:
However, for your talk, I would like to recommend to discuss more about your insights about development in Python and less about equations and too detailed physics. This will be more appealing to the audience.
---

# Development and Infrastructure
[![Build Status](https://travis-ci.org/chianti-atomic/ChiantiPy.svg?branch=master)](https://travis-ci.org/chianti-atomic/ChiantiPy)
[![Documentation Status](http://readthedocs.org/projects/chiantipy/badge/?version=latest)](http://chiantipy.readthedocs.io/en/latest/?badge=latest)
[![Coverage Status](https://coveralls.io/repos/github/chianti-atomic/ChiantiPy/badge.svg?branch=master)](https://coveralls.io/github/chianti-atomic/ChiantiPy?branch=master)

* All development done in the open on GitHub
* Automatic builds on Travis CI
  * Python 2.7, 3.4, 3.5 (3.6 coming soon!)
  * PRs not
  * Documentation builds with Sphinx
  * Minimal test suite, but this is a big `TODO`
* Automatic documentation builds on Read the Docs
* Test coverage reports via Coveralls
* Follow Astropy package template
* Testing and docs infrastructure provided by [astropy-helpers](https://github.com/astropy/astropy-helpers)

---
# Resources

.col-2[&zwnj;]
.col-8[
<i class="fa fa-github-alt fa-3x" aria-hidden="true" style="vertical-align:middle; padding-right:10px;"></i>
<a href="https://github.com/chianti-atomic/ChiantiPy">chianti-atomic/ChiantiPy</a>

<i class="fa fa-book fa-3x" aria-hidden="true" style="vertical-align:middle; padding-right:10px;"></i>
<a href="http://chiantipy.readthedocs.io/en/latest/">chiantipy.readthedocs.io</a>

<i class="fa fa-globe fa-3x" aria-hidden="true" style="vertical-align:middle; padding-right:10px;"></i>
<a href="http://www.chiantidatabase.org/">CHIANTI Webpage</a>

<i class="fa fa-google fa-3x" aria-hidden="true" style="vertical-align:middle; padding-right:10px;"></i>
<a href="https://groups.google.com/forum/#!forum/chianti">CHIANTI Mailing List</a>
]
.col-2[&zwnj;]

---
class: middle

# Acknowledgement
* CHIANTI team 
  * Helen Mason (Cambridge)
  * Giulio Del Zanna (Cambridge)
  * Peter Young (GSFC)
  * and many more...
* SunPy project
  * Stuart Mumford (NSO/DKIST)
  * David Pérez-Suárez (UCL)
* Astropy project
* Stephen Bradshaw (Rice)

---

# The basics

## Getting started

Use [Markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) to write your slides. Don't be afraid, it's really easy!

--

## Making points

Look how you can make *some* points:
--

- Create slides with your **favorite text editor**
--

- Focus on your **content**, not the tool
--

- You can finally be **productive**!

---

# There's more

## Syntax highlighting

You can also add `code` to your slides:
```html
<div class="impact">Some HTML code</div>
```

## CSS classes

You can use .alt[shortcut] syntax to apply .big[some style!]

...or just <span class="alt">HTML</span> if you prefer.

---

# And more...

## 12-column grid layout

Use to the included **grid layout** classes to split content easily:
.col-6[
  ### Left column

  - I'm on the left
  - It's neat!
]
.col-6[
  ### Right column

  - I'm on the right
  - I love it!
]

## Learn the tricks

See the [wiki](https://github.com/gnab/remark/wiki) to learn more of what you can do with .alt[Remark.js]
