# Introduction

The _Lead Toolbox_ is a **MATLAB**-based toolbox with several subparts that work ideally together. _Lead-DBS_ is a toolbox that allows the user to **localize** and **visualize** in a 3D model electrodes in patients treated with _**deep brain stimulation**_. _Lead-Connectome_ is a toolbox entailed with functional and structural whole-brain connectome analyses.

This manual focuses on the _Lead-DBS_ subpart of the toolbox.

## Key Features

* Linear and nonlinear normalization of MRI and CT images to MNI space
* Reconstruction of the electrode trajectories
* Manual correction of the electrode localization
* Visualization of results in 2D slice views
* Visualization of a 3D model showing DBS electrodes and their target areas
* Calculation of the Volume of Activated Tissue \(VAT\) and visualization of the structural connectivity from the VAT to other brain areas

## Quick-Start primers

If you're looking for a quick start to try it out, [click here if you have postoperative CT data](http://www.lead-dbs.org/?page_id=220) or [here if you have postoperative MR data](http://www.lead-dbs.org/?page_id=225).

## Dependencies

_Lead-DBS_ can be seen as a collection of useful tools that have been gathered together for the purpose of DBS electrode reconstructions and related processing. The core job of our development team is to find and plug in the best neuroimaging tools available within the open-source community and write bits of pieces of own code where no good code can be found. 3D-visualizations and electrode reconstruction algorithms \([TRAC/CORE](http://www.sciencedirect.com/science/article/pii/S1053811914009938)\) have been built by ourselves. As for other parts of the toolbox, we aim at incorporating the best tools available. For instance, normalizations into MNI space can be done from within _Lead-DBS_ by either [DARTEL](http://www.fil.ion.ucl.ac.uk/spm/software/spm12/) or [ANTs](http://stnava.github.io/ANTs/), both of which have shown superior to all 12 competing algorithms in [Klein 2009](http://www.ncbi.nlm.nih.gov/pubmed/19195496). As for Fibertracking, _Lead-DBS_ among other routines uses the [Gibbs' tracking algorithm](https://www.uniklinik-freiburg.de/mr-en/research-groups/diffperf/fibertools.html), which showed superior to all 9 competing algorithms in [Fillard 2011](http://www.ncbi.nlm.nih.gov/pubmed/21256221). Thus, _Lead-DBS_ heavily depends on shared libraries and other tools that should be referenced properly if used for research projects. Please find a list of tools used by _Lead-DBS_ [here](http://www.lead-dbs.org/?page_id=1126).

