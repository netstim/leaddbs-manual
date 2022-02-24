# Normalizing the Images

_Lead-DBS_ allows you to automatically normalize the patient images into standard stereotactic (MNI) space. All templates can be found in your installation under\
`lead_dbs/templates/`. For ANTs-based and Schönecker normalizations, the [_ICBM 152 2009b Nonlinear Asymmetric_](http://www.bic.mni.mcgill.ca/ServicesAtlases/ICBM152NLin2009) is used (`mni_hires.nii`). In case of DARTEL, a DARTEL template was generated based on the ICBM 152 2009c series and is supplied within Lead-DBS (`dartel/dartelmni_*.nii`). The New Segment algorithm uses the enhanced tissue probability map by Lorio et al. (`TPM_Lorio_Draganski.nii` file located under `lead_dbs/templates/`.

There are several approaches to achieve a precise normalization of pre- and post-operative images. In most of the routines that come pre-installed with LEAD, post-operative images are first coregistered with each other and then coregistered to the pre-operative images. Finally, all coregistrations are normalized into the MNI space based on the transformation parameters found when co-registering the pre-operative image to the template.

_Lead-DBS_ comes with the following built-in normalization protocols:

*   \_Advanced Normalization Tools (ANTs):

    \_This protocol uses the nonlinear diffeomorphic normalization algorithms referred to as SyN or BSplineSyN (e.g. [Avants 2011](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3065962/) or [Tustison 2013](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3870320/)). The deformation field is estimated based on a series of preoperative acquisitions (these can include any number of preoperative images, e.g. `anat_t2.nii`, `anat_t1.nii`, `anat_pd.nii, anat_fgatir.nii` etc. as well as `dti.nii`which will then produce `fa2anat.nii`) and applied to all (co-registered) postoperative images later on. Please note that the dti.nii is used to export an fa.nii image which is subsequently co-registered to the anat.nii as fa2anat.nii.
*   FSL FNIRT:

    This protocol uses the [FSL FNIRT](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/FNIRT/UserGuide) routine. There is no multispectral normalization support, meaning it will only use the anchor modality (usually the `anat_t1.nii` volume depending on the space configuration).
*   \_SPM DARTEL:

    \_This protocol uses the Diffeomorphic Anatomical Registration Through Exponentiated Lie Algebra (DARTEL, Ashburner 2007) approach supplied with SPM12 to normalize the preoperative MR-image directly to the ICBM template (in MNI space). The estimated DARTEL flowfields are then applied to the coregistered postoperative versions. A DARTEL template was generated based on the `ICBM 152 2009b` series and is supplied within Lead-DBS. Thus, other than the standard DARTEL workflow (which aims at generating a group-template and affine-registering that to MNI space), the DARTEL template used in the Lead-DBS setting is defined by the nonlinear MNI templates, directly. As pointed out in Klein 2009, DARTEL seems to perform equally well in pair-wise and group-wise normalizations.
*   \_SPM Segment:

    \_This protocol uses the SPM12 "Segment" (In SPM8 referred to as "New Segment") approach to segment and normalize the pre-operative image to the ICBM template (in MNI space). The estimated deformation fields are then applied to the coregistered postoperative versions. LEAD uses a slightly modified version of the New Segment approach in that it uses a higher spatial resolution of the warps. This leads to a higher processing time.
* _Three step affine normalization (Schönecker 2009):_  \
  __\
  __This protocol is based on the approach described in [Schönecker 2009](https://www.ncbi.nlm.nih.gov/pubmed/19713324). It uses ANTs to linearly coregister the pre- or postoperative images into MNI space in three consecutive steps, each focusing more on the subcortical target region. The last step spares the ventricles, which may largely vary in the subject-specific anatomy. This is the only normalization routine that can handle the situation where you don't have pre-operative images and still should give precise results.
* You can select the protocol to run depending on the image files that are available for processing.

After loading the patient directory and choosing the imaging technique (see **Section 2**), check the option `[] Normalize` and press `Run`.

When available, _Lead-DBS_ also gives you the option of normalizing fiber tracking images into MNI space. For processing of these images, the option `[] Normalize Fibers` under the `Lead-Connectome` panel should be checked.

The option `[] Check Normalization` opens several viewers that are built to check co-registration of the normalized images with the MNI space at the end of the process.
