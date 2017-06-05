# SciPy 2017 ChiantiPy Talk
All materials for my talk on ChiantiPy at the 2017 SciPy conference

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
