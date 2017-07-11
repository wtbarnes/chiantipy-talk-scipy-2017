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
class: middle,center
# What is CHIANTI?
---
Placeholder: put energy level/ion/element table graphic (Fig 1 from paper) here

???
Currently 1.7 GB of ASCII text files

Thousands of transitions for ions of elements H through Zn
---
background-image: url("img/timeline.png")
background-size: contain

# Some history...

???
Quick description of CHIANTI

Progress from CHIANTI to ChiantiPy

* CHIANTI
  * CHIANTI consolidated many atomic datasets from the literature
  * Goal was to have single, well-maintained, and freely-available database
  * CHIANTI name not an acronym, but rather because of connection to Arcetri and Tuscany (mention Brunella)
  * What role it has played in interpreting data from instruments in solar physics, use in astrophysics
  * Basically, make the point that CHIANTI has been an integral part of solar 


* ChiantiPy
  * Efforts of the CHIANTI team over the years have been focused on database and IDL code
  * ChiantiPy developed by Ken Dere
  * Solar physics slow to adopt Python so IDL still primary interface to the data


Note from paper reviewer:
However, for your talk, I would like to recommend to discuss more about your insights about development in Python and less about equations and too detailed physics. This will be more appealing to the audience.
---
class: full,middle,center
background-image: url("img/chianti_team.png")

???
Explain who members are, where they are currently located

Backdrop

Point out K. Dere

Helen --> Steve --> Me
---

# What is ChiantiPy

* Python interface to the CHIANTI atomic database
* Perform common calculations with data
  * Line emission (`ion`)
  * Continuum emission (`Continuum`)
  * Ionization equilibrium (`ioneq`)
  * Composite Spectra (`spectrum`)
* **NOT** a direct translation of the IDL code, but provides the same capabilities
* Move from *freely available* to truly *open source*
  * Make development a community effort, e.g. SunPy and Astropy
  * Embrace modern developement practices
* Leverage full power of Python and SciPy stack

???
Return to original question

Basic description before launching into details of the code

* A replacement for the IDL client, but not a direct translation
* Develop Python in the open (GitHub) to encourage many contributors from the community
* Relieve burden from CHIANTI developers (time and money in short supply), push towards Python adoption by solar community

Organized around several core modules (others too but we will focus on these four)
---

# Development and Infrastructure
[![Build Status](https://travis-ci.org/chianti-atomic/ChiantiPy.svg?branch=master)](https://travis-ci.org/chianti-atomic/ChiantiPy)
[![Documentation Status](http://readthedocs.org/projects/chiantipy/badge/?version=latest)](http://chiantipy.readthedocs.io/en/latest/?badge=latest)
[![Coverage Status](https://coveralls.io/repos/github/chianti-atomic/ChiantiPy/badge.svg?branch=master)](https://coveralls.io/github/chianti-atomic/ChiantiPy?branch=master)

* Currently **v0.7**, v0.7.1 coming soon
* Licensed under ISC Software License
* All development done in the open on GitHub
  * 17 open issues
  * 0 to 1 PRs per week (~100 merged in past year)
* Automatic builds on Travis CI
  * Python 2.7, 3.4, 3.5 (3.6 coming soon!)
  * Minimal test suite, but this is a big `TODO`
* Automatic documentation builds on Read the Docs
* Test coverage reports via Coveralls
* Testing and docs infrastructure provided by [`astropy-helpers`](https://github.com/astropy/astropy-helpers)

???
Small developement community &ndash; Dere, Barnes, a few other minor contributors

Established infrastructure, but release schedule needs work

Follow Astropy package template

PRs merged only when tests passed, informal review

---

# The `ion` Object

.col-8[
* Ion &ndash; "building block" of database
* Energy levels (`.elvlc`)
* Transitions between levels (`.wgfa`)
]
.col-4[
  <img src="img/filetree.png" width="275x">
]
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
# `ioneq` Module

???
Brief example of ionization equilibrium calculation, physics behind it, some plots
---
# `spectrum` Module

???
Combine line + continuum for many ions, transitions
---
# Applications

???
AIA Response functions

Forward modeling -- movie showing EIS lines/maps of an AR from our synthesizAR code
---
# Resources
#### GitHub (recommended)
```shell
$ git clone https://github.com/chianti-atomic/ChiantiPy.git
$ cd ChiantiPy && python setup.py install
```
#### PyPI: 
```shell 
$ pip install ChiantiPy
```
#### conda/conda-forge
* Work in progress
* Difficulty is the database &ndash; how to make 1.7 GB of data a dependency?

???
Release schedule not yet well established

Suggestions welcome on how to deal with database as a dependency in conda/conda-forge
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
* <img src="img/sunpy_logo.svg" width="60px"> SunPy project
  * Stuart Mumford (NSO/DKIST)
  * David Pérez-Suárez (UCL/MSSL)
* <img src="img/astropy_logo.svg" width="50px"> Astropy project
* Stephen Bradshaw (Rice)

