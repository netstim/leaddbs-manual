# How are reconstructions stored?

the `ea_reconstruction.mat` file inside the patient directory stores the data \(if you use `lead group,` the `LEAD_groupanalysis.mat` file stores a copy of all patient reconstructions\).

There is a single variable `reco` inside the file that stores the data.

For instance,

`reco.native.coords_mm{2}(3,:)`

will be the left \(`{2}`\) third lowest \(`(3,:)`\) contact coordinates \(in x, y, z order\) in native postoperative \(i.e. `postop_tra.nii` , `postop_cor.nii`, `postop_sag.nii` or `rpostop_ct.nii`\) space. This space is similar to the preop space except for brainshift effects. If brainshift is minimal, coordinates could thus also be used in `anat_*.nii` spaces. However, if you did run brainshift correction, there will be a fourth entry called `reco.scrf` which will be in more precisely in `anat_*.nii` space.

`reco.mni` are coordinates in MNI space.

Similarly, `reco.acpc` is an automatic \([Horn et al. 2017](https://www.ncbi.nlm.nih.gov/pubmed/28163141), also [see this summary](http://www.lead-dbs.org/?p=2467)\) transform to AC/PC space.

