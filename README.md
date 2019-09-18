[![DOI](https://zenodo.org/badge/208208313.svg)](https://zenodo.org/badge/latestdoi/208208313)

# KLUM: Karlsruhe Library of Urban Materials
This repository contains an urban material spectral library that contains 181 material samples and consists of 12 materials and 33 subclasses.

**License:** [GNU GPLv2](https://www.gnu.org/licenses/old-licenses/gpl-2.0.html)

Contact: 
- [Rebecca Ilehag, M.Sc.](rebecca.ilehag@kit.edu)

If you use the dataset, please cite:

	@article{ilehag2019KLUM
	title={{KLUM: An Urban VNIR and SWIR Spectral Library Consisting of Building Materials}},
	author={Ilehag, Rebecca and Schenk, Andreas and Huang, Yilin and Hinz, Stefan},
	journal={Remote Sensing},
	volume={11},
	number={18},
	pages={2149},
	year={2019},
	}
	
Link to paper:
https://doi.org/10.3390/rs11182149

## Description
The KLUM spectral library was acquired during the summer of 2018 in Karlsruhe, Germany. It contains 181 urban material samples that consists of 12 materials and 33 subclasses. 
For additional information regarding i.e. the post-processing or the labelling, please refer to the article.

The following data is available for download:
- **\Images:** Folder containing images of each material sample
- **KLUM.pdf:** Document providing an overview of the material samples
- **KLUM_metadata.x:** File containing the essential metadata and spectra
	- **index:** Unique material label
	- **class:** Material class
	- **subclass:** Material subclass
	- **usage** Description of the material's usage (e.g. Facade, ground or roof)
	- **color:** Description of the material's color
	- **surface_structure_texture_coating:** Description of the material's surface structure, texture and coating
	- **status:** Description of the sample’s status (e.g. Weathered or New)
	- **effective_solar_incidence_angle:** Effective Solar Incidence Angle at time of acquisition
- **KLUM_spectra.x:** File containing the spectra
	- **index:** Unique material label
	- **spectra:** 1x2151 vector containing the spectral reflectance in %
	- Row 2 contains the hyperspectral bands in nm (350-2500 nm)
- **KLUM_quality.x:** File containing additional information about the quality of the post-processing
	- **index:** Unique material label
	- **notes_VNIR:** Information about any changes in the corresponding part of the spectrum (350-1000 nm)
	- **notes_SWIR1:** Information about any changes in the corresponding part of the spectrum (1001-1800 nm) 
	- **notes_SWIR2:** Information about any changes in the corresponding part of the spectrum (1801-2500 nm) 
		- 0: Removed data 
		- 10: Original data
		- 20: Processed data
	- **quality:** 1x2151 vector containing potential measure of processing quality
		- 0: Removed data
		- 0 < x < 5: Quality measure
		- 10: Original data

## Example script for reading the data
Matlab 2018a

	KLUM_quality_file = csvread('KLUM_quality.csv',1,1);
	KLUM_spectra_file = csvread('KLUM_spectra.csv',1,1);
	KLUM_metadata = readtable('KLUM_metadata.csv');

	quality = KLUM_quality_file(:,4:end);
	notes = KLUM_quality_file(:,1:3);

	lambda = KLUM_spectra_file(1,:);
	spectra = KLUM_spectra_file(2:end,:);
