# Installation

## Prerequisite

* Recommended RAM size: 32GB or more
* MATLAB: R2022a or later
* MATLAB Image Processing Toolbox
* MATLAB Signal Processing Toolbox
* MATLAB Statistics and Machine Learning Toolbox
* MATLAB Curve Fitting Toolbox (optional)
* MATLAB Parallel Computing Toolbox (optional)
* [SPM12](https://www.fil.ion.ucl.ac.uk/spm/software/spm12/)

## Normal installation

1. Download Lead-DBS from [here](https://www.lead-dbs.org/download/).
2. Extract the downloaded zip into your MATLAB toolbox folder. For example, it can be in your home folder under `Documents/MATLAB/toolbox`. Please avoid extracting Lead-DBS into MATLAB installation folder or other folder which requires `sudo` or `administrator` permission. An installation directory path with spaces should also be avoided.
3. Add SPM12 in your MATLAB search path: right-click on the SPM12 folder and choose `Add to Path` -> `Selected Folders` (**NOT** `Selected Folders and Subfolders`).
4. Add Lead-DBS in your MATLAB search path: right-click on the Lead-DBS folder and choose `Add to Path` -> `Selected Folders and Subfolders` .

Once Lead-DBS is added to your MATLAB search path, you can start it by running `lead dbs` in MATLAB Command Window.

## Installation via GitHub

For more experienced users or developers who'd also wish to modify the code and potentially improve Lead-DBS, there is an alternative way of installation:

1. Clone the Lead-DBS repository from [here](https://github.com/netstim/leaddbs) and switch to `develop` branch.
2. Download the necessary [data](https://www.lead-dbs.org/release/download.php?id=data\_pcloud) and unzip it into the cloned git repository.
3. Add SPM12 in your MATLAB search path: right-click on the SPM12 folder and choose `Add to Path` -> `Selected Folders` (**NOT** `Selected Folders and Subfolders`).
4. Add Lead-DBS in your MATLAB search path: right-click on the Lead-DBS folder, choose `Add to Path` -> `Selected Folders` (**NOT** `Selected Folders and Subfolders`) and then run `ea_setpath` in MATLAB Command Window to set the path.

This alternative way of installation can also make it easy to receive quicker (most often daily) hotfixes or updates and helps us to assist you in a more flexible way.

We'd love to implement your improvements into Lead-DBS – feel free to submit pull requests or contact us for direct push access.

## Tips

{% hint style="info" %}
If you have used previous versions of Lead-DBS, but encounter errors when running a new version, you can run `ea_restoreprefs(1,1)` in MATLAB Command Window to reset the preferences and try again.
{% endhint %}

{% hint style="info" %}
If Lead-DBS subfolders are somehow not completely added to MATLAB search path (in such case you may see `Unrecognized function or variable` error), you can run `ea_setpath` in MATLAB Command Window to update the search path.
{% endhint %}

{% hint style="info" %}
If you have GitHub installation of Lead-DBS and want to switch between `develop` and `classic` branches, you would also need to download the classic [data](https://www.lead-dbs.org/release/download.php?id=data\_classic\_pcloud) and unzip it into Lead-DBS folder. To switch the branch, you can use the MATLAB helper functions`ea_switch2classic` and `ea_switch2dev`. This way the prefs and recent patient/group histories for the two branches will be preserved properly.
{% endhint %}

{% hint style="info" %}
On macOS, Lead-DBS version < 3.0 and the classic branch on GitHub only support MATLAB version <= R2023a.
{% endhint %}

## Installing additional content

Several add-ons are available which can be installed manually from inside Lead-DBS. For most cases, Lead-DBS will try to auto-install these when needed. You can also take a look at the `Install` menu within the main Lead-DBS GUI to install custom items.

## Disclaimer

We try to maintain compatibility to Linux, masOS and Windows, but given our small team, not all functions are well tested on all OSs ([fork us on GitHub and join our team to improve that](https://www.github.com/netstim/leaddbs)).

## **Useful tools**

DICOM viewer [Aliza](https://www.aliza-dicom-viewer.com)

NIfTI viewer [MRIcron](https://www.nitrc.org/projects/mricron/), [Mango](https://mangoviewer.com/mango.html)

[DTI-TK Quicklook plugin](https://dti-tk.sourceforge.net/pmwiki/pmwiki.php?n=QuicklookPlugin.Main) (macOS)

[3D Slicer](https://www.slicer.org)

[FSL](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/)

[DSI-Studio](https://dsi-studio.labsolver.org/)

[TrackVis](https://trackvis.org/)
