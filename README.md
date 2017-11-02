# Ondrejov Spectra Dataset

Code used for generation of this dataset is in
[podondra/ondrejov-dataset](https://github.com/podondra/ondrejov-dataset)
GitHub repository.

## Context

TODO
How was the data collected and why?

## Contents

TODO
What fields are in your data?
What are their units of measurement?
Are there missing values or other recording flaws?

### Preprocessing

TODO
describe preprocessing

### Columns

TODO
id, label, fluxes

Extracted metadata from FITS files:

- OBJECT: Title of observation
- RA
- DEC
- EXPVAL: Exposure value in photon counts [Mcounts]
- GRATANG
- DETECTOR: Name of the detector
- CHIPID: Name of CCD chip
- SPECFILT: Spectral filter
- DATE-OBS: UTC date start of observation
- DICHMIR: Dichroic mirror number

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

- add comments to the Jupyter notebook
- complete this README.md
    - cannot provide the original data
- publish on Zenodo (README.md, ondrejov-dataset.csv, LICENSE)
