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
##### <sup id="rice">1</sup> Dept. of Physics & Astronomy, Rice University, Houston, TX 
##### <sup id="gm">2</sup> Dept. of Physics & Astronomy, George Mason University, Fairfax, VA  
###### Built with [backslide](https://github.com/sinedied/backslide) and [Remark.js](https://github.com/gnab/remark)
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
class: middle, center
# What is ChiantiPy?
--

## A Python interface to the CHIANTI atomic database

---
class: middle, center

# ~~What is ChiantiPy?~~
## A Python interface to the CHIANTI atomic database

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
class: middle,full
# What is ChiantiPy

???
Return to original question

Basic description before launching into details of the code
---

# Development and Infrastructure
[![Build Status](https://travis-ci.org/chianti-atomic/ChiantiPy.svg?branch=master)](https://travis-ci.org/chianti-atomic/ChiantiPy)
[![Documentation Status](http://readthedocs.org/projects/chiantipy/badge/?version=latest)](http://chiantipy.readthedocs.io/en/latest/?badge=latest)
[![Coverage Status](https://coveralls.io/repos/github/chianti-atomic/ChiantiPy/badge.svg?branch=master)](https://coveralls.io/github/chianti-atomic/ChiantiPy?branch=master)

* All development done in the open on GitHub
  * 17 open issues
  * 0 to 1 PRs per week (99 merged)
  * PRs merged only when tests passed, informal review
* Automatic builds on Travis CI
  * Python 2.7, 3.4, 3.5 (3.6 coming soon!)
  * Minimal test suite, but this is a big `TODO`
* Automatic documentation builds on Read the Docs
* Test coverage reports via Coveralls
* Follow Astropy package template
* Testing and docs infrastructure provided by [`astropy-helpers`](https://github.com/astropy/astropy-helpers)

???
Small developement community &ndash; Dere, Barnes, a few other minor contributors

Established infrastructure, but release schedule needs work

---
# The `ion` Object

???
Talk about ion object

Information stored on the object

Emissivity and level population calculations

Some equations, code examples, plots

Basic physics of line emission
---
# `Continuum` Module

???
Physics of continuum radiation: free-free, free-bound

Code examples and plots

Note this module has been redesigned in 0.7.1

---
# `spectrum` Module

???
Combine line + continuum for many ions, transitions
---
# Resources
* GitHub (recommended)
  * `git clone https://github.com/chianti-atomic/ChiantiPy.git`
  * `cd ChiantiPy && python setup.py install`
* PyPI: `pip install ChiantiPy`
* conda/conda-forge
  * Work in progress
  * Difficulty is the database &ndash; how to make 1.7 GB of data a dependency?
  * Suggestions welcome!
* Release schedule not yet well established
  * Currently v0.7
  * v0.7.1 to be released soon

---
# Resources

<i class="fa fa-github-alt fa-3x" aria-hidden="true" style="vertical-align:middle; padding-right:10px;"></i>
<a href="https://github.com/chianti-atomic/ChiantiPy">chianti-atomic/ChiantiPy</a>

<i class="fa fa-book fa-3x" aria-hidden="true" style="vertical-align:middle; padding-right:10px;"></i>
<a href="http://chiantipy.readthedocs.io/en/latest/">chiantipy.readthedocs.io</a>

<i class="fa fa-globe fa-3x" aria-hidden="true" style="vertical-align:middle; padding-right:10px;"></i>
<a href="http://www.chiantidatabase.org/">CHIANTI Webpage</a>

<i class="fa fa-google fa-3x" aria-hidden="true" style="vertical-align:middle; padding-right:10px;"></i>
<a href="https://groups.google.com/forum/#!forum/chianti">CHIANTI Mailing List</a>

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
* Built with [backslide](https://github.com/sinedied/backslide) and [Remark.js](https://github.com/gnab/remark)


