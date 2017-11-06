# Ondřejov Spectra Dataset

Ondřejov dataset contains 12936 labeled stellar spectra from Ondřejov CCD700
archive. The spectra were obsered with
[Ondřejov Perek 2m Telescope](https://stelweb.asu.cas.cz/~slechta/2m/).

Code used for generation of this dataset is in
[podondra/ondrejov-dataset](https://github.com/podondra/ondrejov-dataset)
GitHub repository.

## Context

The dataset was created to support discovery of emission-line spectra in the
[Large Sky Area Multi-Object Fibre Spectroscopic Telespcope](http://www.lamost.org)
(LAMOST) survey.
The main idea was to use Ondřejov dataset to train a machine learning algorithm
and (in combination with domain adaption) find interesting objects in the large
archive.

## Contents

The dataset is released as a CSV file containing the following columns for each
spectrum:

- *id*: unique identifier (FITS file name)
- *label*: assigned class
- *object*: title of observation
- *ra*: right ascension
- *dec*: declination
- *expval*: exposure value in photon counts [Mcounts]
- *gratang*: diffraction grating angle
- *detector*: name of the detector
- *chipid*: name of CCD chip
- *specfilt*: spectral filter
- *date-obs*: UTC date start of observation
- *dichmir*: dichroic mirror number
- *fluxes*: 140 columns of fluxes sampled uniformly between 6519 and 6732
  Angstroms

### Classes

Spectra are divided into 3 classes according to profile of the H-alpha spectral
line:

- *absorption*: 6102 spectra (47.17%)
- *emission*: 5301 spectra (40.98%)
- *double-peak*: 1533 spectra (11.85%)

## Preprocessing

In this section all the preprocessing methods applied to each spectrum are
described, because it is not possible to provide original FITS files which
contains raw spectra.

### Air to Vacuum Wavelenght Conversion

Spectra from Ondřejov CCD700 archive are in air wavelenght but LAMOST spectra
use vacuum wavelenght. Therefore a conversion of Ondřejov spectra was made
according to formulas provided on
[Vienna Atomic Line Database Wiki](http://www.astro.uu.se/valdwiki/Air-to-vacuum%20conversion).

### Gaussian Blur

LAMOST spectrograph spectral resolving power is between 500-1500 which is much
smaller than spectral resolving power 13000 in H-alpha of Ondřejov spectrograph.
To overcome this difference spectra from dataset were blurred with Gaussian
filter with standard deviation of value 7.

### Resampling

Machine learning algorithms requires their inputs to be a set of
features. In order to have same features for all spectra they need to be
resampled to get measurement in same wavelength across all spectra.
Then it is easy to create design matrix where each row is a spectrum
and columns contain fluxes in specified wavelengths between 6519 and 6732
Angstroms.

## Contact

Ondřej Podsztavek <podszond@fit.cvut.cz>
