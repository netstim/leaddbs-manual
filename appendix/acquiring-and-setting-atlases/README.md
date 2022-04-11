# Acquiring and Installing Atlases

Lead-DBS comes pre-installed with a list of different atlas sets (see [here for an overview](https://www.lead-dbs.org/helpsupport/knowledge-base/atlasesresources/atlases/)). However, depending on the needs of your study, other subcortical atlases may be installed.  Atlases that are available in standard NIfTI format (.nii or .nii.gz extensions) and are available in MNI space can be used within Lead-DBS with little to no effort. If atlases come in a different space, you may need to dig into the spaces feature of Lead-DBS (unfortunately documentation on this is scarce. Contact us on [Slack](https://leadsuite.slack.com) and/or [see this page for more information](https://www.lead-dbs.org/about-the-mni-spaces/)).

On [this page](http://www.lead-dbs.org/?page\_id=45) you can find information about how and where to obtain other subcortical atlases suitable for 2D/3D-visualization using Lead-DBS.

If an atlas you know of is missing on this page, please contact us so we can add it to our list. If possible, we are also interested in distributing other subcortical atlases alongside the toolbox if they are made available for distribution.

## Installing additional atlases

### Atlases with a NIfTI file for each structure

To install an atlas that is available within MNI space, create a blank folder within

```
leaddbs/templates/space/MNI_ICBM_2009b_NLIN_ASYM/atlases/
```

For instance, let's call it 'my\_atlas'. Next, in this folder create subfolders named `lh` `rh` `midline` and `mixed`. The structure of your directory should be like this:

```
leaddbs/templates/space/MNI_ICBM_2009b_NLIN_ASYM/atlases/
leaddbs/templates/space/MNI_ICBM_2009b_NLIN_ASYM/atlases/my_atlas/lh
leaddbs/templates/space/MNI_ICBM_2009b_NLIN_ASYM/atlases/my_atlas/rh
leaddbs/templates/space/MNI_ICBM_2009b_NLIN_ASYM/atlases/my_atlas/midline
leaddbs/templates/space/MNI_ICBM_2009b_NLIN_ASYM/atlases/my_atlas/mixed
```

Note that not all of those subfolders are needed – but for now let's just create them.

Next, place NIfTI files of the different structures in these folders. For instance, if you have a NIfTI file that shows the left STN, place it into this subfolder:

```
leaddbs/templates/space/MNI_ICBM_2009b_NLIN_ASYM/atlases/my_atlas/lh/STN.nii.gz
```

These files can be either compressed (.nii.gz) or uncompressed (.nii). Usually, it is not necessary to call the structures "left" or "right". For instance, something like `STN_lh.nii.gz` is not necessary. This is especially not intended, if the same structure appears in both `lh` and `rh` subfolders. In that case, the filenames should be identical. Place structures that exist only once in the brain (such as the hypophysis) or midline structures (like the fornix) into the `midline` subfolder. In case you have one NIfTI file for a bilateral structure (such as one file showing left and right STN) into the `mixed` subfolder.

NIfTI files can be either binary (0 vs. 1) or probabilistic. See [Customizing Atlas Visualization](customizing-atlas-visualization.md) for more details on the latter.

To finalize the atlas, open up Lead-DBS, select the atlas from the dropdown menu, check `Render 3D` and press `Run`. The first run takes long, be patient. The reason is that Lead-DBS needs to aggregate all information into a single file (`atlas_index.mat`) and creates a gray matter mask for VTA calculations (`gm_mask.nii.gz`).

### Atlases with one NIfTI file for all structures

Sometimes, atlases are stored within one NIfTI file with an accompanying .txt or .csv file that describes them. For instance, structure one could be defined by all voxels in the NIfTI that has a certain integer value (say the voxel-intensity for the Putamen could be 5). In this case, you can either break the NIfTI file up into multiple files (e.g. using SPM's Image Calculator or similar tools) if you know how to. Alternatively, you can first store the atlas as a `labeling` atlas and then use the `ea_labeling2atlas`function to convert the file into a Lead-DBS atlas.

To do the latter, first place the NIfTI file into

```
leaddbs/templates/space/MNI_ICBM_2009b_NLIN_ASYM/labeling/my_atlas.nii
leaddbs/templates/space/MNI_ICBM_2009b_NLIN_ASYM/labeling/my_atlas.txt
```

The .txt file needs to be .txt and has a simple format such as

```
1 Subthalamic_Nucleus
2 Globus_Pallidus
3 Putamen
4 Red_Nucleus
5 Thalamus
```

Note that the numbers (1-5) refer to voxel intensities that define the structures, they are separated from the structure labels by a simple blank and the structure labels cannot contain blanks (substitute blanks with underscores).

To convert this `labeling` into an atlas, now run`ea_labeling2atlas('my_atlas');`

This will automatically create all necessary subfolders in the `/atlases` subdirectory. Usually, you can delete the .nii and .txt files from the `/labeling` folder after converting them to an atlas.

To finalize the atlas, open up Lead-DBS, select the atlas from the dropdown menu, check `Render 3D` and press `Run`. The first run takes long, be patient. The reason is that Lead-DBS needs to aggregate all information into a single file (`atlas_index.mat`) and creates a gray matter mask for VTA calculations (`gm_mask.nii.gz`).

### What is the difference between a "labeling" and an "atlas" in Lead-DBS?

If you're now confused about what we did up there, here's what's the difference:

In Lead-DBS, "labelings" are usually used for connectomic analyses. Most of them cover the whole brain or larger parts of the brain and parcellate it into smaller regions. For instance, we may want to use labelings to see whether electrodes of top-responding PD-patients are preferentially connected to the supplementary motor area (instead of the primary motor cortex) and define these regions by "labelings". A limitation of labelings is that the same voxel cannot define multiple brain regions – it is hard-assigned to one specific structure (or to none).

Instead, "atlases" are usually used to define the subcortex, or in the broader sense DBS targets, their surrounding structures of key structures of interest. With atlases, it is possible to assign the same voxel to two structures (such as the STN and the motor-part of the STN) and each structure can be probabilistic.

This is why we use two different formats to store anatomical information. The "hack" above is used to convert one to the other – and there is a `ea_atlas2labeling`function, as well. However, be aware that since the two formats have different capabilities and limitations, converting from one to the other isn't always straight-forward and results should be carefully checked.

### Modifying atlases with MATLAB or code

By now, you may have noticed, that upon the first visualization, Lead-DBS creates two additional files, namely `ea_atlas.index` and `gm_mask.nii.gz`. The former can be modified (using MATLAB) to change colors of the atlas or to group entries to "presets" that can be easily toggled on or off. For instance, you may take a closer look on the `DISTAL (Ewert 2017)` in the 3D viewer to understand what possibilities are there. In the Atlas control figure, you can choose useful presets to visualize (such as `Primary DBS targets`. By choosing either `STN: Solid` or `STN: Subzones` the STN will be shown as a single structure or divided into motor, associative or limbic functional domains.

To see how this is stored, load in the `atlas_index.mat` file of the DISTAL atlas into MATLAB:

```
load(fullfile(ea_space,'atlases','DISTAL (Ewert 2017)','atlas_index.mat'));
```

Then type:

```
atlases.presets(1)
```

which will show:

```
struct with fields:
  label: 'Primary DBS targets'
   show: [1 5 14 15 36 41 47 64 69 72 82]
   hide: [1×90 double]
default: 'absolute'
```

This is the first "preset", which is also the default preset (specified by `atlases.defaultset` ). The "default" entry can be `absolute` (meaning the preset will only show structures defined in the `show` entry and hide structures defined in the `hide` field) or `relative` (in which case the currently visible set of structures will not be altered if not explicitly mentioned).

You can change the color of atlases by changing the `atlases.colors` fields and the colormap to use by adding an `atlases.colormap` field (if not already present). For instance

```
atlases.colormap=ea_redblue;
```

will result in Lead-DBS mapping entries in `atlases.colors` ascendingly from red over white to blue.

For more options on [how to customize atlas visualizations, see the next page](customizing-atlas-visualization.md).

{% hint style="info" %}
For a whole commented example script of how to install and modify a custom atlas, [see this page](../useful-command-line-tools/installing-an-atlas-from-a-repository.md).
{% endhint %}
