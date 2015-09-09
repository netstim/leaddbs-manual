## Renaming the Image Files

_Lead-DBS_ can process different image views. However, the image files must have a **specific name format** for them to be recognized. The naming scheme can be changed in the _**ea_prefs.m**_ file within the LEAD installation directory. If you use the built-in DICOM import function, you are asked to specify the type of each acquisition within a GUI and thus don't have to do the naming manually.

#### File Naming Format

**MR imaging** files within each folder must have the following format:
- Pre-operative images:
 - `anat.nii`
 - `dti.nii`for fiber tracking images*
 - `dti.bvec`for dti bvec table*
 - `dti.bval`for dti bval table*
 - *these three files are automatically generated if you convert DICOM to nifti using the popular [dcm2nii software](http://www.mccauslandcenter.sc.edu/mricro/mricron/dcm2nii.html)

- Post-operative images:
 - `postop_tra.nii` for transversal images
 - `postop_cor.nii` for coronal images
 - `postop_sag.nii` for sagittal images

**CT imaging** files within each folder must have the following format:

- Pre-operative MR images:
 - `anat.nii`
- Post-operative images:
 - `rpostop_ct.nii` (if CT images have already been coregistered to the `anat.nii` file) or
 - `postop_ct.nii`(if CT images have not been coregistede to the `anat.nii` file – but please note that coregistration between CT and MR does not yet robustly works from within LEAD-DBS. Please use Software such as 3DSlicer or the Yale bioimage suite to do so.

You can download a Nifti-Viewing software such as [MRIcron](http://www.mccauslandcenter.sc.edu/mricro/mricron/) to view the different image files and help in correct naming. [SPM8](http://www.fil.ion.ucl.ac.uk/spm/software/spm8/) needs to be installed (this program can also be used to visualize the images).

