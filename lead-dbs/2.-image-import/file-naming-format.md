# File Naming Format

Lead-DBS can process different image views. However, the image files must have a **specific name format** for them to be recognized. The naming scheme can be changed in the **ea\_prefs.m** preference file within the LEAD installation directory. If you use the built-in DICOM import function, you are asked to specify the type of each acquisition within a GUI and thus don't have to do the naming manually. 

You should decide whether you have postoperative MRI or CT. If both acquisitions were taken from a patient, you need to choose which one you prefer, i.e. combining both is not \(yet\) possible in _Lead-DBS_.

Pre-operative images:

* * `anat_t2.nii` / `anat_t1.nii` / `anat_pd.nii`
    * if you name your file `anat_t2.nii`, _Lead-DBS_ assumes that it is a T2-weighted image. If you instead name it `anat_t1.nii`, it assumes that it is a T1-weighted image \(`anat_pd.nii` for the rare case of proton density imaging\).
    * You can also use several \(e.g. T2 and T1 weighted images\) for combined normalizations using the ANTs multimodal normalization or all SPM based approaches.
  * `anat_*.nii` images
    * These could e.g. be special acquisitions that could help highlight the basal ganglia \(like FGATIR/QSM or similar\). These will be used as additional spectrums to segment grey from white matter in all SPM based normalization algorithms \(i.e. SPM Segment, SPM DARTEL and SPM SHOOT\).
  * `dti.nii`for fiber tracking images\*
  * `dti.bvec`for dti bvec table\*
  * `dti.bval`for dti bval table\*
  * _these three files are automatically generated if you convert DICOM to nifti using the popular_ [_dcm2nii_](https://www.nitrc.org/projects/mricron) _software \(part of MRIcron\) , or newer_ [_dcm2niix_](https://www.nitrc.org/projects/mricrogl/)
* Post-operative images:
  * _Either_ you use **MR imaging** files within each folder must have the following format:
    * `postop_tra.nii` for transversal images
    * `postop_cor.nii` for coronal images
    * `postop_sag.nii` for sagittal images
  * _Or_ you use **CT imaging** files within each folder must have the following format:
    * `postop_ct.nii`\(if CT images have not been coregistered to the `anat.nii` file\).
    * `rpostop_ct.nii` \(if CT images have already been coregistered to the `anat.nii` file\)

You can download a Nifti-Viewing software such as [MRIcron](https://www.nitrc.org/projects/mricron) to view the different image files and help in correct naming. [SPM12](http://www.fil.ion.ucl.ac.uk/spm/software/spm12/) needs to be installed \(this program can also be used to visualize the images\).

For Mac users, [the DTI-TK Quicklook plugin](http://dti-tk.sourceforge.net/pmwiki/pmwiki.php?n=QuicklookPlugin.Main) is extremely helpful when dealing with NIfTI data on a mac, in general. I'd even say it's **a must have** \(and really easy to install\).

