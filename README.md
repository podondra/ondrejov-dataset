# Ondřejov Spectra Dataset

Code used for generation of this dataset is in
[podondra/ondrejov-dataset](https://github.com/podondra/ondrejov-dataset)
GitHub repository.

[Ondřejov Perek 2m Telescope](https://stelweb.asu.cas.cz/~slechta/2m/)

Consisting of 12936 labeled spectra.

## Context

TODO
How was the data collected and why?

## Contents

TODO
What fields are in your data?
What are their units of measurement?
Are there missing values or other recording flaws?

The dataset is released as a CSV file containing the following columns for each
spectrum:

- *id*
- *label*
- *object*: Title of observation
- *ra*
- *dec*
- *expval*: Exposure value in photon counts [Mcounts]
- *gratang*
- *detector*: Name of the detector
- *chipid*: Name of CCD chip
- *specfilt*: Spectral filter
- *date-obs*: UTC date start of observation
- *dichmir*: Dichroic mirror number
- *fluxes*: 140 columns of fluxes sampled uniformly between 6519 and 6732
  Angstroms

### Classes

Ondřejov dataset includes total number of 3 classes:

- *absorption*
- *emission*
- *double-peak*

## Preprocessing

TODO
describe preprocessing

## Goals

TODO
Do you have any objectives in mind in making your data open?

## Contact

Ondřej Podsztavek <ondrej.podsztavek@gmail.com>

## Acknowledgements

TODO
Who do you owe thanks for sharing this dataset?
Provide details on the datasets’s provenance.
This is not only important in collaborative social data science,
but may also be a part of respecting the dataset owner’s license.

## TODO List

- complete this README.md
    - cannot provide the original data
- publish on Zenodo (README.md, ondrejov-dataset.csv, LICENSE)
