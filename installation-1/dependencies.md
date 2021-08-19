# Dependencies

// TO BE UPDATED \(e.g., include PaCER\). Currently this is not a dependency list as I am used to in the Linux world \(Khoa\).

Lead-DBS is a collection of  tools for the purpose of DBS electrode reconstructions and related processing. The core job of our development team is to find and integrate the best neuroimaging tools available within the open-source community and develop our own code where no good code can be found. Three dimensional visualizations and electrode reconstruction algorithms \([TRAC/CORE](http://www.sciencedirect.com/science/article/pii/S1053811914009938)\) have been built by ourselves. As for other parts of the toolbox, we aim at incorporating the best tools available. 

For instance, normalizations into MNI space can be done from Lead-DBS by either [DARTEL](http://www.fil.ion.ucl.ac.uk/spm/software/spm12/) or [ANTs](http://stnava.github.io/ANTs/), both of which demonstrated superior results against twelve competing algorithms in [Klein 2009](http://www.ncbi.nlm.nih.gov/pubmed/19195496). For Fibertracking Lead-DBS uses, among other routines, the [Gibbs' tracking algorithm](https://www.uniklinik-freiburg.de/mr-en/research-groups/diffperf/fibertools.html), which showed superior results against nine competing algorithms in [Fillard 2011](http://www.ncbi.nlm.nih.gov/pubmed/21256221). 

Thus, Lead-DBS heavily depends on shared libraries and other tools that should be referenced properly if used for research projects. Please find a list of tools used by Lead-DBS [here](http://www.lead-dbs.org/?page_id=1126).

**Depends**

MATLAB. Version 2020b is currently recommended as some recent tools such as the Sweetspot Explorer were built with MATLAB's app designer. 

MATLAB toolboxes. Image Processing Toolbox.

Statistical Parametric Mapping 12 from their [website](https://www.fil.ion.ucl.ac.uk/spm/software/spm12/) or [Github repository](https://github.com/spm/spm12). Add the SPM12 folder to the Matlab path \(see [Setting the MATLAB Path](installation/setting-a-path-for-_lead-dbs_-in-matlab.md)\) or copy it into the Lead-DBS's ext\_lib folder.

**Recommends**

**Suggests**

