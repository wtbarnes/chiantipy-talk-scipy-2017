# SciPy 2017 ChiantiPy Talk
[![Build Status](https://travis-ci.org/wtbarnes/chiantipy-talk-scipy-2017.svg?branch=master)](https://travis-ci.org/wtbarnes/chiantipy-talk-scipy-2017)

All materials for my talk on ChiantiPy at the [2017 SciPy conference](https://scipy2017.scipy.org/ehome/220975/493388/)

## Outline
* Introduction
* History of CHIANTI database and ChiantiPy
  * In astronomy, everything is remote sensing--photons hitting your detector
  * Need a way to interpret signal from the detector
  * Need for consolidated atomic database
  * Early CHIANTI team, impact on field of solar physics
  * Primary interaction with CHIANTI is through IDL, via SolarSoft
  * ChiantiPy created in 2010(?, check this)
  * Solo effort, not a lot of momentum, support from community (
* Database Structure
  * How is it structured
  * What kinds of data does it contain
* ChiantiPy capabilities
  * Line Emission
    * Mention ionization equilibrium here
  * Continuum
  * Spectra
  * Radiative Losses (if time permits)
* Infrastructure
  * Packaging--using Astropy package template, working towards availability on conda (database dependency is an issue)
  * Documentation--automatic docs builds on Read the Docs 
  * Testing--automatic builds and tests run on Travis CI at every commit (cover is still low though...)
  * Membership in OpenAstronomy
* Future: Roadmap and Goals
  * Integration with SunPy
  * Packaging, distribution via conda
  * Cleanup and speedup
  * Encourage more widespread use in the community
* Concluding remarks
  
## Misc. Notes

##  Interview Questions for CHIANTI Team
* What are the main sources of atomic data that CHIANTI pulls from?
* How did you go about collecting all of this information initially?
* What were the challenges in distributing and packaging this data?
* Were there other similar databases at that time?
* What is the funding like for a project like CHIANTI?
* What impact has the CHIANTI project had on the field of solar physics?
* How widely used is CHIANTI by those outside of solar physics? Any users outside of astrophysics?
* How can community better support the CHIANTI project?
* How can community better support the ChiantiPy project?

## Notes from Interview with CHIANTI Team

### H. Mason

1. How did the idea for the database come about?

   > CHIANTI was started by Ken, Brunella Monsignori-Fossi (Arcetri Observatory) and me.

   > Ken and I had been working together on Skylab and later on HRTS data. I come from an atomic physics background (University College London) and had been calculating atomic data for coronal ions. Ken had been asked to produce/revise a huge compilation of atomic data. Brunella had been working on solar and stellar spectra, and had developed and Arcteri spectral code.

   > We were all at a conference (in Elba?) having lunch, that is when we got the idea of setting up an atomic database, with a spectral analysis wrapper.

   > Giulio and Enrico both worked with Brunella as students. Peter was my grad student.

2. Why name the database "CHIANTI"? 

   > The name CHIANTI is not an acronym, we thought about a few possibilities but they were all contrived. We chose the name because of the close connection with Italy, in particular Arcetri, Tuscany, where the CHIANTI team met of several occasions.

3. How did you go about collecting all of the data? 

   > We searched the literature and also produced new atomic data ourselves, using various codes from UCL and Queens University Belfast, QUB, Atomic Structure and electron scattering codes. More recently we (Giulio and I) have been collaborating with Prof Nigel Badnell (Strathclyde) to provide highly accurate atomic data. Ken gathered, assessed and has calculated data for ionisation and recombination.

   > It is REALLY important for scientists to acknowledge the original data sources, so much hard work, often unappreciated.

4. Were there other similar databases at that time? 

   > Yes, there were a few spectral analysis codes. Besides Arcetri, there was one called MEKAL, developed by Mewe in Holland (?), also one at Harvard, and in Boulder. Most of these used approximate methods to estimate the atomic data. Also there as a database, ADAS, developed by Hugh Summers, for fusion research, but you had to busy in to this. None of them were or are as accurate, complete or up-to-date as CHIANTI. Also we wanted CHIANTI to be accessible and freely-available to the hole community.

5. What are the main sources of the atomic data included in CHIANTI? 

   > Up-to-date assessed published data, plus some calculations the CHIANTI team have carried out, to supplement what is available in the literature.

6. What are/were the challenges in distributing and packaging this data? 

   > It is a MASSIVE amount of data. Initially we fitted the electron excitation rates, to reduce all published data to the same format, check all the data (convergence at high energy etc) and to store it more compactly. We used a five point spline to fit the data, but for some cases, this was not sufficient, so we increased the number of spline points. Now we have the option of including the data as it is produced. Obviously the CHIANTI dataset has increased dramatically with time, which is a challenge for data storage, but also for the time individual calculations take, for example to simulate spectral lines.

   > Each new release is accompanied by a publication, so providing the data, s/w and documentation is a challenge.

6. How is CHIANTI funded? 

   > In the USA, by NSF and NASA. In the UK, by STFC. We also held some NATO grants which allowed us travel funds to meet and collaborate.

7. How has the CHIANTI project impacted solar physics? astrophysics? 

   > It has enabled scientists to analyse spectroscopic data, in particular SoHO/CDS and SUMER, Hinode/EIS, SDO/EVE also astro instruments. This is a service to the community and in 2010 (?) the CHIANTI team were awarded the Group Achievement Award for Geophysics by the Royal Astronomical Society. It has also contributed greatly to the analysis of imaging instruments, such as SDO. Also it is used a lot when designing new instruments, and now in forward modelling, eg FROMO and other codes.


8. How widely used is CHIANTI by those outside of solar physics? 

   > CHIANTI has been integrated into many other spectral codes, eg CLOUDY, APED, Pint-of-Ale etc..which are widely used for astrophysics. The solar physics community uses IDL, but this is not the case for astrophysics. However, the database can still be imported into other codes.

   Any users outside of astrophysics? 

   > It has been made more widely available via European databases. Giulio could say more about that.

9. How can the community better support the CHIANTI/ChiantiPy project?

   > Funding??!! We often struggle to get the funding we need to carry on. Recognition of all the hard work that has been put into CHIANTI, as a service to the community. Collaborations which could improve CHIANTI, eg non-equilibrium versions, non-Maxwellian (a Kappa version is available using v7.1, but funding is needed to keep this updated). Steve at al have been working with a time-dep-ionisation version.

   > We have plans for the future to deal with non-equilibrium processes, electron density effects, but we need support (mainly funding) to take this forward.

   > Ken and I are both getting older, both still scientifically active, but the younger members of the team need to work together to take CHIANTI forward. They may even need to look for some younger collaborators to bring into the team. This itself is a challenge.

   > Feedback from USERs has always been good, and helps to improve CHIANTI.

### K. Dere
Regarding the beginnings of ChiantiPy,

> Did some hunting around to see when I did begin ChiantiPy.  The earliest files I found were from 2003, just to try reading the files and learn Python on my own time.  At that time we had numarray instead of numpy and I think, some version of scipy.  Also had Konrad Hinsen's scientific package.  In 2009 I had just received a grant from NASA astrophysics to develop ChiantiPy which was already far from the beginnings in 2003.

> Well, I started in 2003, as I said. It was mostly a way to learn Python but I kept it and it got to  the point that I was far enough along to write a proposal to NASA in 2008 and that was accepted. A significant part of the proposal was to make the Python web interface and one of the reviewers liked that. Then in 2009 I put it on Sourceforge and released v 0.1. I am sure some of the earliest stuff was pretty ugly.

Regarding use by other fields,

> As for use by astrophysicists, my ADS reports shows a considerable number but I would be hard to categorize them.  We get comments from a few laboratory users but, aside from the data itself, I am not sure how well we match their needs.

### P. Young
> The paper [Young et al., (2016)](http://adsabs.harvard.edu/abs/2016JPhB...49g4009Y) which has some background information about CHIANTI. For funding, currently Ken, Enrico and myself receive funding through NASA Astrophysics (ADAP program).

### G. Del Zanna
> Within the UK, we received some funding from STFC only in the last two grant proposals, they are mainly to include new atomic data into new versions, not about mantaining  current versions
