# Table of contents

* [Introduction](README.md)
* [How to contribute to Lead-DBS](ways-to-contribute-to-lead-dbs.md)

## Installation

* [Dependencies](installation/dependencies.md)
* [Installation](installation/installation.md)

## Lead-DBS

* [Overview](lead-dbs/step0-overview.md)
* [1. Load Patient Folder](lead-dbs/step1-load-patient-folder.md)
* [2. Image Import](lead-dbs/step2-image-import/README.md)
  * [Converting NIfTI-images into BIDS](lead-dbs/step2-image-import/converting-nifti-images-into-bids.md)
  * [Converting DICOM files into BIDS](lead-dbs/step2-image-import/converting-dicom-files-into-bids.md)
* [3. Volume Registrations](lead-dbs/step3-volume-registrations/README.md)
  * [Coregister Volumes](lead-dbs/step3-volume-registrations/coregister-volumes.md)
  * [Normalizing the Images](lead-dbs/step3-volume-registrations/normalization-of-images.md)
  * [Brainshift Correction](lead-dbs/step3-volume-registrations/subcortical-refine-post-to-pre-transforms.md)
  * [Checking the Coregistration and Normalization](lead-dbs/step3-volume-registrations/checking-the-coregistration.md)
  * [Refine Atlas Fit with WarpDrive](lead-dbs/step3-volume-registrations/refine-atlas-fit-with-warpdrive.md)
* [4. (optional) Surface Reconstruction](lead-dbs/step4-optional-surface-reconstruction.md)
* [5. (optional) Reconstruction of Electrode Trajectories](lead-dbs/step5-optional-reconstruction-of-electrode-trajectories/README.md)
  * [Orientation of Directional Leads](lead-dbs/step5-optional-reconstruction-of-electrode-trajectories/determining-the-orientation-of-directional-leads/README.md)
    * [Prerequisites](lead-dbs/step5-optional-reconstruction-of-electrode-trajectories/determining-the-orientation-of-directional-leads/prerequisites.md)
    * [Automatic Algorithm](lead-dbs/step5-optional-reconstruction-of-electrode-trajectories/determining-the-orientation-of-directional-leads/automatic-algorithm.md)
    * [Possible Problems with the Automatic Algorithm](lead-dbs/step5-optional-reconstruction-of-electrode-trajectories/determining-the-orientation-of-directional-leads/possible-problems-with-the-automatic-algorithm.md)
    * [User-Assisted Algorithm (Manual Refine)](lead-dbs/step5-optional-reconstruction-of-electrode-trajectories/determining-the-orientation-of-directional-leads/user-assisted-algorithm-manual-refine.md)
  * [TRAC/CORE Details](lead-dbs/step5-optional-reconstruction-of-electrode-trajectories/trac-core-details.md)
  * [Reconstruction File](lead-dbs/step5-optional-reconstruction-of-electrode-trajectories/reconstruction-file.md)
  * [Manual Reconstruction](lead-dbs/step5-optional-reconstruction-of-electrode-trajectories/manual-reconstruction.md)
* [6. (optional) Perform Connectivity Analysis](lead-dbs/step6-optional-perform-connectivity-analysis.md)
* [7. Visualization](lead-dbs/step7-visualization/README.md)
  * [MER Analysis](lead-dbs/step7-visualization/mer-analysis.md)
* [Reconstruction Statistics](lead-dbs/reconstruction-statistics.md)
* [Untitled](lead-dbs/untitled.md)

## Lead-Group

* [Group analyses with Lead-DBS](lead-group/group-analyses-with-lead-dbs.md)
* [Setup Analysis](lead-group/setup-analysis.md)
* [General Settings](lead-group/general-settings.md)
* [Group Visualization](lead-group/group-visualization.md)
* [Calculate VTA and Stats](lead-group/calculate-vta-and-stats.md)
* [Sweetspot Explorer](lead-group/sweetspot-explorer.md)

## Connectomics

* [Connectomics](connectomics/connectomic-analyses/README.md)
  * [Diffusion MRI: Patient Specific Processing](connectomics/connectomic-analyses/dmri.md)
  * [fMRI-Analysis: Patient Specific Processing](connectomics/connectomic-analyses/fmri.md)
  * [Using Normative Connectomes](connectomics/connectomic-analyses/using-normative-connectomes/README.md)
    * [Discriminative Fibertracts analysis](connectomics/connectomic-analyses/using-normative-connectomes/discriminative-fibertracts-analysis.md)
* [Lead Connectome Mapper](connectomics/lead-mapper.md)

## Lead-OR

* [Imaging setup](lead-or/imaging-setup.md)
* [Electrophysiology setup](lead-or/electrophysiology-setup.md)
* [Using the platform](lead-or/using-the-platform.md)

## Appendix

* [Code Backbone](appendix/code-backbone.md)
* [Acquiring and Installing Atlases](appendix/acquiring-and-setting-atlases/README.md)
  * [Customizing Atlas Visualization](appendix/acquiring-and-setting-atlases/customizing-atlas-visualization.md)
* [Troubleshooting / Specific Help](appendix/troubleshooting-specific-help/README.md)
  * [Adding Fortran dependencies for VTA modeling](appendix/troubleshooting-specific-help/adding-fortran-dependencies-for-vta-modeling.md)
  * [VTA Calculation Troubleshoot](appendix/troubleshooting-specific-help/vta-calculation-troubleshoot.md)
* [WarpDrive](appendix/warpdrive.md)
* [Command line interface](appendix/command-line-interface/README.md)
  * [Command line options](appendix/command-line-interface/command-line-options.md)
* [Matlab scripting examples](appendix/useful-command-line-tools/README.md)
  * [Installing an atlas from an online repository](appendix/useful-command-line-tools/installing-an-atlas-from-a-repository.md)
  * [Warping a normative connectome to native subject space](appendix/useful-command-line-tools/warping-a-normative-connectome-to-native-subject-space.md)
* [Using Slicer](appendix/using-slicer/README.md)
  * [Sweet-sour spot](appendix/using-slicer/sweet-sour-spot.md)
