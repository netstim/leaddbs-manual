# Table of contents

* [Introduction](README.md)
* [How to contribute to Lead-DBS](ways-to-contribute-to-lead-dbs.md)

## Installation <a id="installation-1"></a>

* [Dependencies](installation-1/dependencies.md)
* [Installation](installation-1/installation/README.md)
  * [Setting the MATLAB Path to include Lead-DBS](installation-1/installation/setting-a-path-for-_lead-dbs_-in-matlab.md)
  * [Acquiring and Installing Atlases](installation-1/installation/acquiring_and_setting_atlases/README.md)
    * [Customizing Atlas Visualization](installation-1/installation/acquiring_and_setting_atlases/customizing_atlas_visualization.md)

## Lead-DBS

* [Overview](lead-dbs/0.-overview.md)
* [1. Load Patient Folder](lead-dbs/1.-load-patient-folder.md)
* [2. Image Import](lead-dbs/2.-image-import/README.md)
  * [File Naming Format](lead-dbs/2.-image-import/file-naming-format.md)
* [3. Volume Registrations](lead-dbs/3.-volume-registrations/README.md)
  * [Normalizing the Images](lead-dbs/3.-volume-registrations/normalization-of-images/README.md)
    * [Checking the Coregistrations and Normalizations](lead-dbs/3.-volume-registrations/normalization-of-images/checking_the_coregistration.md)
  * [Brain shift Correction](lead-dbs/3.-volume-registrations/subcortical-refine-post-to-pre-transforms.md)
* [4. \(optional\) Surface Reconstruction](lead-dbs/4.-optional-surface-reconstruction/README.md)
  * [Lead Mapper](lead-dbs/4.-optional-surface-reconstruction/lead-mapper.md)
* [5. \(optional\) Reconstruction of Electrode Trajectories](lead-dbs/5.-optional-reconstruction-of-electrode-trajectories/README.md)
  * [Pre-reconstructing the Electrode Trajectory](lead-dbs/5.-optional-reconstruction-of-electrode-trajectories/reconstruction-of-electrode-trajectory.md)
  * [Manual Correction of Electrode Localization](lead-dbs/5.-optional-reconstruction-of-electrode-trajectories/manual_correction_of_electrode_localization/README.md)
    * [How are reconstructions stored?](lead-dbs/5.-optional-reconstruction-of-electrode-trajectories/manual_correction_of_electrode_localization/how-are-reconstructions-stored.md)
  * [Orientation of Directional Leads](lead-dbs/5.-optional-reconstruction-of-electrode-trajectories/determining-the-orientation-of-directional-leads/README.md)
    * [Prerequisites](lead-dbs/5.-optional-reconstruction-of-electrode-trajectories/determining-the-orientation-of-directional-leads/prerequisites.md)
    * [Automatic Algorithm](lead-dbs/5.-optional-reconstruction-of-electrode-trajectories/determining-the-orientation-of-directional-leads/automatic-algorithm.md)
    * [Possible Problems with the Automatic Algorithm](lead-dbs/5.-optional-reconstruction-of-electrode-trajectories/determining-the-orientation-of-directional-leads/possible-problems-with-the-automatic-algorithm.md)
    * [User-Assisted Algorithm \(Manual Refine\)](lead-dbs/5.-optional-reconstruction-of-electrode-trajectories/determining-the-orientation-of-directional-leads/user-assisted-algorithm-manual-refine.md)
* [6. \(optional\) Perform Connectivity Analysis](lead-dbs/6.-optional-perform-connectivity-analysis.md)
* [7. Visualization](lead-dbs/7.-visualization/README.md)
  * [MER analysis](lead-dbs/7.-visualization/mer-analysis.md)
  * [Writing 2D Images](lead-dbs/7.-visualization/writing_2d_images.md)
  * [Creating the 3D Scene](lead-dbs/7.-visualization/creating-the-3d-scene.md)
* [Reconstruction Statistics](lead-dbs/reconstruction_statistics.md)
* [Untitled](lead-dbs/untitled.md)

## Lead-Group

* [Group analyses with Lead-DBS](lead-group/group_analyses_with_lead-dbs.md)
* [Setup Analysis](lead-group/setup-analysis.md)
* [General Settings](lead-group/general-settings.md)
* [Group Visualization](lead-group/group-visualization.md)
* [Calculate VTA and Stats](lead-group/calculate-vta-and-stats.md)
* [Sweetspot Explorer](lead-group/sweetspot-explorer.md)

## Appendix

* [Code Backbone](appendix/code-backbone.md)
* [Troubleshooting / Specific Help](appendix/troubleshooting-specific-help/README.md)
  * [Adding Fortran dependencies for VTA modeling](appendix/troubleshooting-specific-help/adding-fortran-dependencies-for-vta-modeling.md)
* [Command line interface](appendix/command-line-interface/README.md)
  * [Command line options](appendix/command-line-interface/command-line-options.md)
* [Matlab scripting examples](appendix/useful-command-line-tools/README.md)
  * [Installing an atlas from an online repository](appendix/useful-command-line-tools/installing-an-atlas-from-a-repository.md)
  * [Warping a normative connectome to native subject space](appendix/useful-command-line-tools/warping-a-normative-connectome-to-native-subject-space.md)
* [Connectomics](appendix/connectomic_analyses/README.md)
  * [Diffusion MRI: Patient Specific Processing](appendix/connectomic_analyses/dmri.md)
  * [fMRI-Analysis: Patient Specific Processing](appendix/connectomic_analyses/fmri_analysis.md)
  * [Using Normative Connectomes](appendix/connectomic_analyses/using-normative-connectomes/README.md)
    * [Discriminative Fibertracts analysis](appendix/connectomic_analyses/using-normative-connectomes/discriminative-fibertracts-analysis.md)

