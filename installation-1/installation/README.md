# Installation

_Lead-DBS_ is a toolbox that works in the [MATLAB](http://www.mathworks.de/products/matlab/) environment \([The Mathworks](http://www.mathworks.com/)\). The optimal recommended version to use is ML 2019a. A version ≥2016b is needed for some functions & visualizations. We try to maintain compatibility to all three OSs, but given our small team, not all functions are well tested on all OSs \([fork us on github and join our team to improve that](http://www.github.com/leaddbs/leaddbs)\). The best-tested setting is running Lead-DBS on a Macintosh on ML 2019b.

Yet, there are some required steps before you can use the toolbox:

1. After downloading the folder containing _Lead-DBS_, you should set the MATLAB path to include the toolbox folder \(for help on setting a path in MATLAB, go to **Section 1.1**\).
2. You need _SPM12_ for normalization and file handling installed and included to your MATLAB path as well.

Once LEAD is added to your Matlab path, you can run _Lead-DBS_ by entering the command `lead dbs` into the MATLAB Command Window.

## Installation via Github

For more experienced users or developers who'd also wish to modify the code and potentially improve _Lead-DBS_, there is an alternative way of installation:

1. Clone the Lead-DBS repository from [here](https://github.com/leaddbs/leaddbs).
2. Download the necessary datafiles using this [link](http://www.lead-dbs.org/release/download.php?id=data) and unzip the downloaded folder into the cloned git repository.
3. We'd love to implement your improvements into _Lead-DBS_ – please contact us for direct push access to Github or feel free to add pull-requests to the _Lead-DBS_ repository.

This alternative way of installation can also be interesting to receive quicker \(most often daily\) updates on the code and helps us to assist you in a more flexible way.

## Installing additional content

Several add-ons are available which can be installed manually from inside Matlab. For most cases, Lead-DBS will try to auto-install these assets when needed and you can take a look at the `Install` menu within the main Lead-DBS GUI to install custom items.

## Further dependencies

The FEM-based VTA model \(Horn et al. 2017\) needs Fortran dependencies since it uses the [SimBio toolbox](https://www.mrt.uni-jena.de/simbio/index.php/Main_Page) that is partially based on Fortran code. [Please see this page](../../appendix/troubleshooting-specific-help/adding-fortran-dependencies-for-vta-modeling.md) for instructions to install dependencies if needed.

