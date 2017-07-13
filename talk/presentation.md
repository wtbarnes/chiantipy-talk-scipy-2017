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

???
Thank organizers for giving me a talk

Thank donors for financial support to attend 
---
class: middle

# Contact Info
.col-1[
  &zwnj;
]
.col-4[
<a href="https://github.com/wtbarnes">
<i class="fa fa-github-alt fa-3x" aria-hidden="true" style="vertical-align:middle; padding-right:10px;"></i>wtbarnes</a>

<a href="https://twitter.com/wtbarnes_">
<i class="fa fa-twitter fa-3x" aria-hidden="true" style="vertical-align:middle; padding-right:10px;"></i>
wtbarnes_</a>
]
.col-7[
<a href="http://wtbarnes.github.io/">
<i class="fa fa-globe fa-3x" aria-hidden="true" style="vertical-align:middle; padding-right:10px;"></i>wtbarnes.github.io</a>

<a href="mailto:will.t.barnes@gmail.com">
<i class="fa fa-envelope fa-3x" aria-hidden="true" style="vertical-align:middle; padding-right:10px;"></i>will.t.barnes@gmail.com</a>
]

---
class:full,middle,center
background-image: url("img/sdo_aia_211.png")
background-size: contain
---
class:full,middle,center
background-image: url("img/iris_20150428_100823_0.gif")
background-size: contain
---
class:full,middle,center
background-image: url("img/hinode_eis_fe12_195.png")
background-size: contain
---
class: middle,center
# CHIANTI
## "An Atomic Database for Diagnostics of Astrophysical Plasmas"
---
class: full,middle,center
background-image: url("img/all_lines.png")
background-size: contain

???
Currently 1.7 GB of ASCII text files

Thousands of  transitions for ions of elements H through Zn

Very useful for calculating optically thin emission/intensity

Compiled primarily for analysis of solar spectra

---
background-image: url("img/timeline.png")
background-size: contain

# Some history...

???
Quick description of CHIANTI

Cover first two points, flip to team picture, flip back and then...

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

# Installation
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

# The `ion` Object

.col-8[
* Ion &ndash; "building block" of database
* Energy levels (`.elvlc`)
* Transitions between levels (`.wgfa`)
* *Line emission* from (primarily) 
]
.col-4[
  <img src="img/filetree.png" width="275px">
]
???
ChiantiPy objects can be placed into two categories: per ion and composite ion

Talk about ion object

Information stored on the object (elvlc, wgfa, scups)

Abundance

Emissivity and level population calculations

Some equations, code examples, plots

Basic physics of line emission
---
# The `ion` Object
---
# `Continuum` Module
* Free-free (*bremsstrahlung*)
* Free-bound

???
Physics of continuum radiation: free-free, free-bound

Code examples and plots

Note this module has been redesigned in 0.7.1
---
# `ioneq` Module

* Ion charge state (primarily) a function of *temperature*
* Assuming *ionization equilibrium*, population fraction of ion `\(i\)` of element `\(X\)` given by,

$$ I\_{i−1}X\_{i−1} + R\_iX\_{i+1} = I\_iX\_i + R\_{i−1}X\_i $$

* **Sink:** ionization from lower levels, recombination from upper levels
* **Source:** recbombination to lower levels, ionization to upper levels
* Solve iteratively using ionization (`\(I_i\)`) and recombination (`\(R_i\)`) from CHIANTI
* Use data to solve *non-equilibrium ionization* equations as well

???
Brief example of ionization equilibrium calculation, physics behind it, some plots
---

```python
ioneq_chianti = ch.ioneq('Fe')
ioneq_chianti.load()
```
or
```python
temperature = np.logspace(3.5,9.5,500)
ioneq_custom = ch.ioneq('Fe')
ioneq_custom.calculate(temperature)
```
<img src="img/fe_ioneq.png" width="830px">

???
Explain different curves

Say where the data goes, e.g. Temperature and Ioneq attributes on the classes
---
# `spectrum` Module

???
Combine line + continuum for many ions, transitions

Only code plus figures, no equations

Just explain composite of line emission from many ions+continuum

Discuss different 
---
# Applications

???
AIA Response functions--show transitions for a few Fe ions superimposed on 1-2 AIA wavelength passbands side-by-side with temperature response function
---
class:middle,center,full
background-image: url("img/hinode_eis_fe12_195.gif")
background-size: contain
---
class:middle

# Resources
.col-6[
<a href="https://github.com/chianti-atomic/ChiantiPy">
<i class="fa fa-github-alt fa-3x" aria-hidden="true" style="vertical-align:middle; padding-right:10px;"></i>chianti-atomic/ChiantiPy</a>

<a href="http://chiantipy.readthedocs.io/en/latest/">
<i class="fa fa-book fa-3x" aria-hidden="true" style="vertical-align:middle; padding-right:10px;"></i>chiantipy.readthedocs.io</a>

<a href="http://www.chiantidatabase.org/">
<i class="fa fa-globe fa-3x" aria-hidden="true" style="vertical-align:middle; padding-right:10px;"></i>CHIANTI Webpage</a>
]
.col-6[
<a href="https://groups.google.com/forum/#!forum/chianti">
<i class="fa fa-google fa-3x" aria-hidden="true" style="vertical-align:middle; padding-right:10px;"></i>CHIANTI Mailing List</a>

<a href="http://conference.scipy.org/proceedings/scipy2017/will_barnes.html">
<i class="fa fa-file-text-o fa-3x" aria-hidden="true" style="vertical-align:middle; padding-right:10px;"></i>2017 SciPy Proceedings</a>
]
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
* <img src="img/astropy_logo.svg" width="40px"> Astropy project
* Stephen Bradshaw (Rice)

