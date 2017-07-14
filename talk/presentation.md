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
## Will Barnes<sup id="rice">1</sup>, Ken Dere<sup id="gm">2</sup>
### 14 July 2017
##### <sup id="rice">1</sup> Dept. of Physics & Astronomy, Rice University, Houston, TX 
##### <sup id="gm">2</sup> Dept. of Physics & Astronomy, George Mason University, Fairfax, VA  
###### Built with [backslide](https://github.com/sinedied/backslide) and [Remark.js](https://github.com/gnab/remark)

???
Thank organizers for giving me a talk

Thank donors for financial support to attend

Info about me

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

???
Mention URL at bottom of the page to find slides at

solar physicist, intro to images
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
### Collaboration between:
#### George Mason University
#### University of Michigan
#### University of Cambridge

???
High-temperature, low-density optically-thin plasmas (EUV and x-ray)

---
class: full,middle,center
background-image: url("img/all_lines.png")
background-size: contain

???
CHIANTI "Periodic table" &ndash; charge state on x, elements on y, color/text show # of levels

Currently 1.7 GB of ASCII text files

Thousands of levels for ions of elements H through Zn

Sometimes hundreds of thousands of transitions, e.g. Fe IX

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
  * Origins in Arcetri spectral code
  * CHIANTI name not an acronym, but rather because of connection to Arcetri and Tuscany (mention Brunella)
  * What role it has played in interpreting data from instruments in solar physics, use in astrophysics
  * Basically, make the point that CHIANTI has been an integral part of solar
  * Papers(~15) have over 3000 combined citations (a lot for astro/solar)

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

# What is ChiantiPy?

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

Organized around several core modules (others too but we will focus on these ~~four~~ three)
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
class:middle,center
background-image: url("img/OA_logo.png")
background-size: contain

---

# Installation
#### GitHub (recommended)
```bash
$ git clone https://github.com/chianti-atomic/ChiantiPy.git
$ cd ChiantiPy && python setup.py install
```
#### PyPI: 
```bash 
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
* *Line emission* from (primarily) collisions between ions and free electrons

```python
import numpy as np
import ChiantiPy.core as ch
T = np.logspace(4,8,100)
n = 1e9
fe5 = ch.ion('fe_5',temperature=T,
             eDensity=n)
fe5.Abundance
fe5.Elvlc
fe5.Wgfa
```

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
class: middle

* For a transition between levels `\(i\)` and `\(j\)` in ion `\(X_k\)`,

$$ I = \frac{1}{4\pi}0.83\mathrm{Ab}(X)f\_{X,k}n\_j\frac{1}{N\_e}\frac{hc}{\lambda\_{ij}}\mathrm{EM} $$

* Main concern is `\(n_j\)`, the level population as a function of temperature/density,

$$ 
\sum\_{k>j}n\_kA\_{kj} + n\_e\sum\_{i=j}n\_jC\_{ij} - \left(\sum\_{i<j}n\_jA{ji} + n\_e\sum\_{k=j}n\_jC\_{jk}\right) = 0 
$$

* **Source:** collisional exictation from lower levels, radiative decay from upper levels
* **Sink:** excitation to higher levels, decay to lower levels

---

```python
fe5.populate()
fe5.popPlot(top=50)
plt.ylim([1e-3,0.5])
```
<img src="img/pop_plot_fe5.png" style="margin:auto;display:block;" width="650px">

???
Code and figures, just use figure output from plotting routines in ChiantiPy to show that capability
---
class: middle

```python
import ChiantiPy.tools.filters as ch_filters
wavelength = np.arange(2600,2900,0.1)
fe5.spectrum(wavelength,filter=(ch_filters.lorentz,5))
fe5.spectrumPlot(index=np.argmax(fe5.IoneqOne))
plt.ylim([0,3.1e-27])
```
<img src="img/spec_plot_fe5.png" style="margin:auto;display:block;" width="550px">

???
Mention that `spectrum` module can be used to create composite spectrum along with continuum
Combine line + continuum for many ions, transitions

---
# `Continuum` Module
* **Free-free** (*bremsstrahlung*)

\begin{align}
\frac{dW}{dtdVd\lambda} =& \frac{c}{3m\_e}\left(\frac{\alpha h}{\pi}\right)^3\left(\frac{2\pi}{3m\_ek\_B}\right)^{1/2}\frac{Z^2}{\lambda^2T^{1/2}}\bar{g}\_{ff} \\\\
&\times\exp{\left(-\frac{hc}{\lambda k\_BT}\right)},\quad [\mathrm{erg}\,\mathrm{cm}^3\,\mathrm{s}^{-1}\,\mathrm{\mathring{A}}^{-1}\,\mathrm{str}^{-1}]
\end{align}

* **Free-bound**

\begin{align}
\frac{dW}{dtdVd\lambda} =& \frac{1}{4\pi}\frac{2}{hk\_Bc^3m\_e\sqrt{2\pi k\_Bm\_e}}\frac{E^5}{T^{3/2}}\sum\_i\frac{\omega\_i}{\omega\_0}\sigma\_i^{bf} \\\\
&\times\exp\left(-\frac{E - I\_i}{k_BT}\right),\quad [\mathrm{erg}\,\mathrm{cm}^3\,\mathrm{s}^{-1}\,\mathrm{\mathring{A}}^{-1}\,\mathrm{str}^{-1}]
\end{align}

???
*Continuous* function of wavelength and temperature/density

Physics of continuum radiation: free-free, free-bound

In this equations, nearly everything is a constant
* Important stuff is Gaunt factor, ionization potential, photoionization cross-section, statistical weights
* ChiantiPy, using CHIANTI data, takes care of this for you
* Approximations from literature in cases of GF and cross-section

Code examples and plots

Note this module has been redesigned in 0.7.1
---
class: middle

```python
wavelength = np.logspace(0,3,100)
temperature = np.logspace(6,8.5,100)
fe18continuum = ch.Continuum('fe_18',temperature)
fe18continuum.calculate_free_free_emission(wavelength)
fe18continuum.calculate_free_bound_emission(wavelength)
```
<img src="img/continuum.png" width="850px">

---
# `ioneq` Module

* Ion charge state (primarily) a function of *temperature*
* Assuming *ionization equilibrium*, population fraction of ion `\(i\)` of element `\(X\)` given by,

$$ I\_{i−1}f\_{X,i−1} + R\_if\_{X,i+1} = I\_if\_{X,i} + R\_{i−1}f\_{X,i} $$

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
class:middle,center
# Applications

---
class:middle,center

<img src="img/github_pr_snapshot.png" width="800px">
<img src="img/response_211.png" width="800px">

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
  * Ken Dere (George Mason)
  * Giulio Del Zanna (Cambridge)
  * Peter Young (GSFC)
  * and many more...
* <img src="img/sunpy_logo.svg" width="60px"> SunPy project
  * Stuart Mumford (NSO/DKIST)
  * David Pérez-Suárez (UCL/MSSL)
* <img src="img/astropy_logo.svg" width="40px"> Astropy project
* Stephen Bradshaw (Rice)

