---
description: >-
  This page might be outdated. We continuously work on updating our
  documentation, thank you for your patience.
---

# Reconstruction File

The data is stored

* for BIDS version, under: derivatives/leaddbs/patientID/reconstructions/sub-patientID\_desc-reconstruction.mat&#x20;
* for classic version under the `ea_reconstruction.mat` file inside the patient directory.

There is a single variable `reco`. For instance, `reco.native.coords_mm{2}(3,:)` is the left (`{2}`) third lowest (`(3,:)`) contact coordinates in x, y, z in native postoperative space (i.e., `postop_tra.nii` , `postop_cor.nii`, `postop_sag.nii` or `rpostop_ct.nii`). This space is similar to the preop space except for brainshift effects. If brainshift is minimal, coordinates could thus also be used in `anat_*.nii` spaces. However, if you ran brainshift correction, there is a fourth entry called `reco.scrf` which is more precisely in `anat_*.nii` space.

`reco.mni` are coordinates in MNI space. Similarly, `reco.acpc` is an automatic transform to AC/PC space (see [Horn et al., 2017](https://doi.org/10.1016/j.neuroimage.2017.02.004) or [this summary](https://www.lead-dbs.org/?p=2467)).
