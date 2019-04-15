# Ondřejov Spectra Dataset

Ondřejov dataset contains 12936 labeled stellar spectra from
[Ondřejov CCD700 archive](http://voarchive.asu.cas.cz/ccd700/q/web/form).
The spectra were observed with
[Ondřejov Perek 2m Telescope](https://stelweb.asu.cas.cz/web/index.php?pg=2m_telescope).

Code used for generation of this dataset is in
[podondra/ondrejov-dataset](https://github.com/podondra/ondrejov-dataset)
GitHub repository.

## Context

The dataset was created to support the discovery of emission-line spectra in the
[Large Sky Area Multi-Object Fibre Spectroscopic Telespcope](http://www.lamost.org)
(LAMOST) survey.
The main idea was to use Ondřejov dataset to train a machine learning algorithm
and (in combination with domain adaption) find interesting objects in the large
spectral archive.

## Contents

The dataset is released as a CSV file containing the following columns for each
spectrum:

- *id*: a unique identifier (FITS file name)
- *label*: assigned class
- *object*: title of observation
- *ra*: right ascension
- *dec*: declination
- *expval*: exposure value in photon counts [Mcounts]
- *gratang*: diffraction grating angle
- *detector*: name of the detector
- *chipid*: name of CCD chip
- *specfilt*: spectral filter
- *date-obs*: UTC date start of the observation
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

### Air to Vacuum Wavelength Conversion

Spectra from Ondřejov CCD700 archive are in air wavelength, but LAMOST spectra
use vacuum wavelength. Therefore, a conversion of Ondřejov spectra was made
according to formulas provided on
[Vienna Atomic Line Database Wiki](http://www.astro.uu.se/valdwiki/Air-to-vacuum%20conversion).

### Gaussian Blur

LAMOST spectrograph spectral resolving power is between 500-1800 which is much
smaller than spectral resolving power 13000 in H-alpha of Ondřejov spectrograph.
To overcome this difference spectra from the dataset were blurred with Gaussian
filter with a standard deviation of value 7.

### Resampling

Machine learning algorithms require their inputs to be a set of
features. To have the same features for all spectra, they need to be
resampled to get measurements in the same wavelength across all spectra.
Then it is easy to create a design matrix where each row is a spectrum
and columns contain fluxes in specified wavelengths between 6519 and 6732
Angstroms.

## Contact

- Ondřej Podsztavek <podszond@fit.cvut.cz>
- Petr Škoda <skoda@sunstel.asu.cas.cz>
