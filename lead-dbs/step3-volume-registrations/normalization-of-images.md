# Normalizing the Images

| **Context**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <ul><li><em>Normalization wraps native patient images into standard stereotactic (MNI) space. All templates can be found in your installation under <code>lead_dbs/templates/</code>. For ANTs-based and Schönecker normalizations, the</em> <a href="http://www.bic.mni.mcgill.ca/ServicesAtlases/ICBM152NLin2009"><em>ICBM 152 2009b Nonlinear Asymmetric</em></a> <em>is used (<code>mni_hires.nii</code>). ANTs with the default Lead-DBS settigns is recommended, see</em> <a href="https://doi.org/10.1016/j.neuroimage.2018.09.061"><em>Ewert et al. (2019)</em></a><em>.</em></li><li><em>For DARTEL, a DARTEL template was generated based on the ICBM 152 2009c series and is supplied within Lead-DBS (<code>dartel/dartelmni_*.nii</code>). The New Segment algorithm uses the enhanced tissue probability map by Lorio et al. (<code>TPM_Lorio_Draganski.nii</code> file located under <code>lead_dbs/templates/</code>.</em></li><li><em>During normalization, native patient images are transformed to MNI space non-linearly, allowing the deformation of different brain regions in different ways. After coregistration, both images (pre-and post-operative) are in the same space, and we can use the transformation matrix gained by normalizing our pre-operative image. Then we apply it to our post-operative image (or rather, the electrodes in the post-operative image). That way, the electrodes are localized within the MNI space, and we can assess their spatial relationship to their respective targets.</em></li></ul> |

## Built-in normalization protocols

<details>

<summary>Advanced Normalization Tools (ANTs)</summary>

This protocol uses the nonlinear diffeomorphic normalization algorithms referred to as SyN or BSplineSyN (e.g. [Avants 2011](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3065962/) or [Tustison 2013](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3870320/)). The deformation field is estimated based on a series of preoperative acquisitions (these can include any number of preoperative images, e.g. `anat_t2.nii`, `anat_t1.nii`, `anat_pd.nii, anat_fgatir.nii` etc. as well as `dti.nii`which will then produce `fa2anat.nii`) and applied to all (co-registered) postoperative images later on. Please note that the dti.nii is used to export an fa.nii image which is subsequently co-registered to the anat.nii as fa2anat.nii.

</details>

<details>

<summary>FSL FNIRT</summary>

This protocol uses the [FSL FNIRT](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/FNIRT/UserGuide) routine. There is no multispectral normalization support, meaning it will only use the anchor modality (usually the `anat_t1.nii` volume depending on the space configuration).

</details>

<details>

<summary>SPM DARTEL</summary>

This protocol uses the Diffeomorphic Anatomical Registration Through Exponentiated Lie Algebra (DARTEL, Ashburner 2007) approach supplied with SPM12 to normalize the preoperative MR-image directly to the ICBM template (in MNI space). The estimated DARTEL flowfields are then applied to the coregistered postoperative versions. A DARTEL template was generated based on the `ICBM 152 2009b` series and is supplied within Lead-DBS. Thus, other than the standard DARTEL workflow (which aims at generating a group-template and affine-registering that to MNI space), the DARTEL template used in the Lead-DBS setting is defined by the nonlinear MNI templates, directly. As pointed out in Klein 2009, DARTEL seems to perform equally well in pair-wise and group-wise normalizations.

</details>

<details>

<summary>SPM Segment</summary>

This protocol uses the SPM12 "Segment" approach to segment and normalize the pre-operative image to the ICBM template (in MNI space). The estimated deformation fields are then applied to the coregistered postoperative versions. Lead-DBS uses a slightly modified version of the New Segment approach in that it uses a higher spatial resolution of the warps. This leads to a higher processing time.

</details>

<details>

<summary><em><strong>Three-step affine normalization (Schönecker 2009)</strong></em></summary>

This protocol is based on the approach described in [Schönecker 2009](https://www.ncbi.nlm.nih.gov/pubmed/19713324). It uses ANTs to linearly coregister the pre- or postoperative images into MNI space in three consecutive steps, each focusing more on the subcortical target region. The last step spares the ventricles, which may largely vary in the subject-specific anatomy. This is the only normalization routine that can handle the situation where you don't have pre-operative images and still should give precise results.

You can select the protocol depending on the image files that are available for processing.

If applicable, Lead-DBS also gives you the option to normalize fiber tracking images into MNI space. For processing of these images, the option `[] Normalize Fibers` under the `Lead-Connectome` panel should be checked.

</details>

## How to

<figure><img src="../../.gitbook/assets/UI_normalization (1).png" alt="" width="375"><figcaption><p> UI settings for normalization.</p></figcaption></figure>

1. This step follows after coregistration. Select your patient and make sure `Normalize Volumes` and `Check Results` is selected (arrows 1 and 2).
2. If normalization has been run before, select `Retouch/overwrite approved results` (arrow 4) to get a new instance of coregistration results.
3. By clicking on `Settings` (arrow 5), you can select from the normalization protocols implemented in Lead. More details can be found here: [#built-in-normalization-protocols](normalization-of-images.md#built-in-normalization-protocols "mention"). Usually, the default settings work well.
4. Press `Run`. Normalization is computationally the most intense step and can take more than an hour, depending on the method chosen and your computer. Once it is done, you must assess the quality of the results. For more information on that, please consult [checking-the-coregistration.md](checking-the-coregistration.md "mention").
5. The atlas fit and results of the normalization can be manually edited. For a thorough tutorial on how to, follow the instructions in [refine-atlas-fit-with-warpdrive.md](refine-atlas-fit-with-warpdrive.md "mention").

| **Output**                                                                                                                                                                                                                                                                        |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <ul><li>A pop-up window with information about methods and references. If this information is not needed, the window can be closed.</li><li>New normalization data will appear in the selected file, under <code>derivatives/leaddbs/patient_name/normalization</code>.</li></ul> |
