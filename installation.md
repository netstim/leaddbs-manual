# Installation

## Prerequisite

* Recommended RAM size: 32GB or more
* MATLAB: R2021a or later
* MATLAB Image Processing Toolbox
* MATLAB Signal Processing Toolbox
* MATLAB Statistics and Machine Learning Toolbox
* MATLAB Curve Fitting Toolbox (optional)
* MATLAB Parallel Computing Toolbox (optional)
* [SPM12](https://www.fil.ion.ucl.ac.uk/spm/software/spm12/)

## Normal installation

1. Download Lead-DBS from [here](https://www.lead-dbs.org/download/).
2. Extract the downloaded zip into your MATLAB toolbox folder. For example, it can be in your home folder under `Documents/MATLAB/toolbox`.  Please avoid extracting Lead-DBS into MATLAB installation folder or other folder which requires `sudo` or `administrator` permission.
3. Add SPM12 in your MATLAB search path: right-click on the SPM12 folder and choose `Add to Path` -> `Selected Folders` (**NOT** `Selected Folders and Subfolders`).
4. Add Lead-DBS in your MATLAB search path: right-click on the Lead-DBS folder and choose `Add to Path` -> `Selected Folders and Subfolders` .

Once Lead-DBS is added to your MATLAB search path, you can run Lead-DBS by entering the command `lead dbs` into the MATLAB Command Window.

If you used previous versions of Lead-DBS before and see errors when you run it after you install a new version, can run `ea_restoreprefs(1,1)` to reset the preferences and try again.

If Lead-DBS subfolders are somehow not completely added to MATLAB search path, you can run \`ea\_setpath\` to update the path.

## Installation via Github

For more experienced users or developers who'd also wish to modify the code and potentially improve Lead-DBS, there is an alternative way of installation:

1. Clone the Lead-DBS repository from [here](https://github.com/leaddbs/leaddbs).
2. Download the necessary [data](http://www.lead-dbs.org/release/download.php?id=data\_pcloud) and unzip it into the cloned git repository.
3. Set MATLAB search path as described in [#normal-installation](installation.md#normal-installation "mention").

This alternative way of installation can also be interesting to receive quicker (most often daily) hotfixes or updates and helps us to assist you in a more flexible way.

We'd love to implement your improvements into Lead-DBS – feel free to submit pull requests or contact us for direct push access.

## Installing additional content

Several add-ons are available which can be installed manually from inside Lead-DBS. For most cases, Lead-DBS will try to auto-install these when needed. You can also take a look at the `Install` menu within the main Lead-DBS GUI to install custom items.

## Disclaimer

We try to maintain compatibility to Windows, Unix and macOS, but given our small team, not all functions are well tested on all OSs ([fork us on github and join our team to improve that](http://www.github.com/leaddbs/leaddbs)).

## **Useful tools**

DICOM viewer [Aliza](https://www.aliza-dicom-viewer.com)

NIfTI viewer [MRIcron](https://www.nitrc.org/projects/mricron/), [Mango](https://mangoviewer.com/mango.html)

[DTI-TK Quicklook plugin](http://dti-tk.sourceforge.net/pmwiki/pmwiki.php?n=QuicklookPlugin.Main) (macOS)

[3D Slicer](https://www.slicer.org)

[FSL](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/)

[DSI-Studio](https://dsi-studio.labsolver.org/)

[TrackVis](https://trackvis.org/)

