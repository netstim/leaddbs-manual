---
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Using Normative Connectomes

{% hint style="info" %}
This page is under construction
{% endhint %}

## Context

Normative connectomes are brain connectivity profiles that are represented in a common (template) space. Such connectomes form the basis of several further analyses, including discriminative fibertract analysis, as well as networkmapping analysis. There are both advantages and disadvantages of using normative connectomes. For instance, one primary advantage of using normative connectome is that these connectomes are often prepared from a large number of patients, and are processed with state of the art preprocessing pipelines (e.g., HCP1064 connectome, HCP1200 subjects connectome). This ensures that data quality are high. One potential disadvantage could be that the influence of a disease on the structural and functional patterns may not be adequtly represented in normative connectomes, given that it is usually based on healthy patients. However, Wang et al performed a quantitative analysis comparing normative and patient specific  connectomes to show that patient-specific diffusion-MRI data, age- and disease-matched or normative group connectome data show very similar optimal connectivity profile when analysis stimulation dependent connectivity profiles.&#x20;



## How To

Connectomes can be structural (tract based) or functional (fMRI based). For structural connectomes, the basic building block is a "tract file", whose data structure is specific for Lead DBS. These tract files can be in `.trk` format and then converted to Lead-DBS specific `.mat` format using the function `ea_trk2ftr` . Briefly, a Lead-DBS specific tract file is a struct which contans the variables:\


* fibers - n x 4 array, where column 1,2 and 3 represents the x,y,z coordinates of each point in a streamline and column 4 represents which fiber bundle the streamline belongs to.
* idx - number of streamlines in one fiber bundle, used to index the fiber.
* voxmm - 'mm'
* mirrored - whether the fiber is mirrored or not
* ea\_fibformat - string, version of the fiber format

For functional connectomes, the basic building block is a "time series" file, in `.mat` format.&#x20;

All structural connectomes in Lead-DBS must be present under `leaddbs/connectomes/dMRI` and functional connectomes must be present under `leaddbs/connectomes/fMRI`. To change this location, you use use the prefs entry, `prefs.lc.datadir` to define a different path. Note that all paths defined in this entry must contain a filesep \['/' or '\\'] at the end of the path.

### dMRI connectomes

To construct a dMRI connectome, use the following command:

`ea_atlas2conn(input_atlas,connectome_name)`

Where the `input_atlas`  is a folder containing subfolders `lh/` and `rh/` and optionally, `midline` Note that there should be equal number of tracts on the left and right hemisphere else this function will error out.

The atlas2conn function aggregates the tracts in the input atlas starting from the left hemisphere and then the right hemisphere. Midline tracts can also be added.&#x20;



### dMRI Multitract connectomes

To construct a dMRI multitract connectome, follow these steps:

* Perform whatever actions you need on your tracts, for example flipping. You can use `ea_connectome_filter_downsample_flip.m` to perform operations such as filtering per ROI, downsampling, or flipping on your tracts.
* Both the left and right files can be placed inside one main subbfolder, but each tract name should contain a suffix `_left` or `_right`, and should be contained within one folder.
* Please be sure to name your tracts with the same name except the suffix `'_left'` or `'_right'`. Please do not use special characters for naming tracts, including `'-'` . Further analysis requires that this is correctly indexed across hemispheres and therefore, they need to matched correctly.
* Your connectome should be finally have this format: `leaddbs/connectomes/dMRI_multitract<connnectome_name>/{`_`_left.mat,`_`._right.mat}`
* Additional note on mirroring: fiber filtering and many further tools require the presence of boolean flag 'mirrored' for enabling mirroring functions. This flag can be added manually to each tract or can be added automatically by the script `ea_connectome_filter_downsample_flip.m` when flipping is performed.



## References

1. Wang Q, Akram H, Muthuraman M, Gonzalez-Escamilla G, Sheth SA, Oxenford S, Yeh FC, Groppa S, Vanegas-Arroyave N, Zrinzo L, Li N, Kühn A, Horn A. Normative vs. patient-specific brain connectivity in deep brain stimulation. Neuroimage. 2021 Jan 1;224:117307. doi: 10.1016/j.neuroimage.2020.117307. Epub 2020 Aug 28. PMID: 32861787.



