---
description: >-
  We are happy to answer any questions related to BIDS migration in our Slack
  support channel.
---

# Importing a classic Lead-DBS dataset to BIDS version

If you have patient data processed using the classic version of Lead-DBS (<=v2.6), importing them into a BIDS dataset is quite easy. Simply click the `Add patient to dataset` button and choose the classic (or 'legacy') patient folder. This will automatically run the import process.&#x20;

In case you run into problems, here is a more detailed explanation of file types produced by the classic version of Lead-DBS and how they will be processed during the import.&#x20;

### Raw Images and Preprocessing Files

* `raw_anat*.nii` -> These are the raw images. These will be stored under "derivatives/rawimages/sub-patientID" in BIDS structure.
* `tp_*` images are the tone mapped images, i.e. copies of the images with tone mapping applied for better contrast.
*   `ea_precoregtransformation`: in Lead-DBS, preprocessing does alignment of

    anchor image (i.e., the T1w image) to the template, this is the transformation for that.

### Coregistration Files

* `anat_*.nii` -> preprocessed, coregistered images. These will be stored under "derivatives/leaddbs/sub-patientID/coregistration/anat" folder.
* `postop_tra` -> coregistered post-op MRI images. These will be stored under "derivatives/leaddbs/sub-patientID/coregistration/anat" folder.
* `rpostop_ct`-> co-registered postoperative CT images. These will be stored under "derivatives/leaddbs/sub-patientID/coregistration/anat" folder.
* `anat_t12postop_ct_ants1.mat` and `postop_ct2anat_t1_ants.mat` -> These are the inverse and forward transformations between CT and T1w images. These will be stored under "derivatives/leaddbs/sub-patientID/coregistration/transformations" folder.&#x20;

{% hint style="info" %}
In case patient has **post-op CT** and multiple coregistration attempts were made in the classic patient folder, there might be more than one transformations named as "anat\_t12postop\_ct\_ants**2**", "anat\_t12postop\_ct\_ants**3**"... etc. In this case, Lead-DBS will only migrate the last one (the one in use).
{% endhint %}

{% hint style="info" %}
In case patient has **post-op MRI**, there are **no transformations stored for the coregistration**, this is normal because for post-op MRI, electrode localization is done on the coregistered image directly. Transformations were not necessary and not stored.
{% endhint %}

### Normalization Files

* `glpostop_ct`-> normalized post-op CT image. These will be stored under "derivatives/leaddbs/sub-patientID/normalization/anat" folder.
* `glanatComposite` and `glanatInverseComposite` -> transfomation files for normalization if **ANTs** was used as method of normalization. They can be either \*.h5 or \*.nii.gz files depending on when the normalization was done. In recent version of Lead-DBS, we store the transformations in \*.nii.gz format. These will be stored under "derivatives/leaddbs/sub-patientID/normalization/transformations"
* `y_ea_(inv_)normparams` -> transformation files for normalization if SPM was used as method of normalization. These will be stored under "derivatives/leaddbs/sub-patientID/normalization/transformations"

{% hint style="info" %}
You can check `ea_normmethod_applied` in the legacy patient folder to know which method was used for normalization.
{% endhint %}

### Log Files

*   `ea_coreg_approved`->stores approval status of coregistration, brainshift correction and

    normalization. It will automatically be transfered to BIDS format. **If this file is not present, everything will be set to approved by default when importing. In this case we recommend you to double check your coregistration, normalization and brainshift correction results.**
*   `ea_coregmrmethod_applied` and `ea_normmethod_applied` -> stores info about

    which methods were used. The contents will be moved under "derivatives/leaddbs/sub-patientID/coregistration/logs/" and "derivatives/leaddbs/sub-patientID/normalization/logs/" respectively.
* `ea_ui`-> stores the options set in the GUI. This will be moved under "derivatives/leaddbs/sub-patientID/prefs" folder

### Reconstruction Files

* `ea_reconstruction:` stores the electrode reconstructions. This will be stored under "derivatives/leaddbs/sub-patientID/reconstruction" folder.
* `ct_mask`: CT mask for localization when using PaCER as reconstruction method, rct\_mask is the same but based on co-registered CT

### Brainshift Correction Files

* `scrf` folder -> scrf stands for subcortical refine. The contents of this folder will be moved under "derivatives/leaddbs/sub-patientID/brainshift" folder.

### Stimulation Volume Files

* `headmodel`  folder -> stores the head model for VTA calculation
* `stimulations` folder -> contains the files for VTA and e-field models. These will be moved under "derivatives/leaddbs/sub-patientID/stimulations"
  * In very old patient folders, stimulations were stored directly under `stimulations` (i.e., no `native` or `MNI*` subfolder is present). This is becuase stimulation calculation was done before native space VTA calculation was introduces. Therefore, BIDS import will move these old folders under "derivatives/leaddbs/sub-patientID/stimulations/MNI\*" subfolder.&#x20;
*   Subfolders under the `stimulations` folder with the connectome name (e.g.

    PPMI74 or HCP1000…) contain results from `Lead Mapper`. If you want to reuse previously calculated fingerprint maps, the legacy folders should be renamed to the correct connectome name before migration (since all connectomes were renamed). Otherwise, they will be skipped and you will see warnings in MATLAB Command Window.

### Miscellaneous Files

* Other relevant files that might be present in the legacy folder will be moved to "derivatives/leaddbs/sub-patientID/miscellaneous" folder.

### Essential files in a legacy folder of a patient with postoperative CT scan

<figure><img src="../../.gitbook/assets/Screen Shot 2023-08-25 at 18.16.32.png" alt=""><figcaption></figcaption></figure>

### Essential files in a legacy folder of a patient with a postoperative MRI scan

<figure><img src="../../.gitbook/assets/Screen Shot 2023-08-25 at 18.18.20.png" alt=""><figcaption></figcaption></figure>
