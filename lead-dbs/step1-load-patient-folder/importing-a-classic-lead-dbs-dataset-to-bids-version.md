---
description: >-
  We are happy to answer any questions related to BIDS migration in our Slack
  support channel.
---

# Importing a classic Lead-DBS dataset to BIDS version

If you have a dataset already set up with the classic version, importing them into the BIDS version is quite easy. <mark style="background-color:yellow;">Simply click the add patients button and choose the classic (or 'legacy') patient folder. This will automatically run the legacy import process</mark>.&#x20;

In case you run into problems, here is a more detailed explanation of the classic lead dbs file types and how they will be processed during the BIDS import.&#x20;

### Raw Images and Preprocessing Files

* `raw_anat*.nii` -> These are the raw images. These will be stored under "derivatives/rawimages/patientID" in BIDS structure.
*   `tp_*` images are the tonemapped images, i.e. copies of the images with a better

    contrast
*   `ea_precoregtransformation`: in Lead-DBS, preprocessing does alignment of

    anchor image (i.e., the t1) to MNI template, this is the transformation for that.

### Coregistration Files

* `anat_*.nii` -> preprocessed, coregistered images. These will be stored under "derivatives/leaddbs/patientID/coregistration/anat" folder.
* `postop_tra` -> coregistered post-op MRI images. These will be stored under "derivatives/leaddbs/patientID/coregistration/anat" folder.
* `rpostop_ct`-> co-registered postoperative CT images. These will be stored under "derivatives/leaddbs/patientID/coregistration/anat" folder.
* `anat_t12postop_ct_ants1.mat` and `postop_ct2anat_t1_ants.mat` -> These are the forward and inverse coregistration transfomation files. These will be stored under "derivatives/leaddbs/patientID/coregistration/transformations" folder.&#x20;

{% hint style="info" %}
If multiple coregistration attempts were made in the classic folder, there might be more files named as "anat\_t12postop\_ct\_ants**2,** anat\_t12postop\_ct\_ants**3..** etc. In this case, Lead-DBS will migrate the last one.&#x20;
{% endhint %}

{% hint style="info" %}
When there is a **post-op MRI**, there are **no transforms stored for the**

**coregistration**, this is normal because for MRI, electrode localization is done on the

coregistered scan directly. anat\_t2 to t1 transformations are also not stored.
{% endhint %}

### Normalization Files

* `glpostop_ct`-> normalized postoperative images. These will be stored under "derivatives/leaddbs/patientID/normalization/anat" folder.
* `glanatComposite` and `glanatInverseComposite` -> transfomation files for normalization if **ANTs** was used as method of normalization. They can be \*.h5 or \*.nii.gz depending on when the normalization was done. These will be stored under "derivatives/leaddbs/patientID/normalization/transformations"
* `y_ea_(inv_)normparams` -> transformation files for normalization if SPM was used as method of normalization. These will be stored under "derivatives/leaddbs/patientID/normalization/transformations"

{% hint style="info" %}
You can check `ea_normmethod_applied` to learn which method was preferred for normalization.
{% endhint %}

### Log Files

*   `ea_coreg_approved`->stores approval status of coregistration, brainshift and

    normalization. It will automatically be transfered to BIDS format. **If this file is not present, everything will be set to approved when importing by default. In this case we recommend you to double check your coregistration, normalization and brainshift correction results.**
*   `ea_coregmrmethod_applied` and `ea_normmethod_applied` -> stores info about

    which algorithms were used. The contents will be moved under "derivatives/leaddbs/patientID/coregistration/logs/" and "derivatives/leaddbs/patientID/normalization/logs/" respectively.
* `ea_ui`-> stores the options used in the GUI. This will be moved under "derivatives/leaddbs/patientID/prefs" folder

### Reconstruction Files

* `ea_reconstruction:` stores the electrode reconstructions. This will be stored under "derivatives/leaddbs/patientID/reconstruction" folder.
* `ct_mask`: used to do localization, rct\_mask is the same but co-registered

### Brainshift Correction Files

* `scrf` folder -> scrf stands for subcortical refine. The contents of this will be moved under "derivatives/leaddbs/patientID/brainshift" folder.

### Stimulation Volume Files

* `headmodel`  folder -> stores the head model for VTA computation
* `stimulations` folder -> contains the files for VTA and e-field models. These will be moved under "derivatives/leaddbs/patientID/stimulations"
  *   In very old patient folders, the `gs_*` folders in stimulations are stored directly under

      stimulations (i.e., no native or MNI… subfolder is present). This may be becuase stimulation calculation was done before native space VTA calculation was introduces. Therefore, BIDS import will move these old folders under "derivatives/leaddbs/patientID/stimulations/MNI..." subfolder.&#x20;
*   Subfolders under the stimulation/gs\_ folders with the connectome name (e.g.

    PPMI74…) should be deleted. Or if you want to reuse previously calculated fingerprint maps, the legacy folders should be renamed to the correct connectome name before migration (since all connectomes were renamed)

### Miscellaneous Files

* Other files that might be present in the legacy folder will be moved to "derivatives/leaddbs/patientID/miscellaneous" folder.

{% hint style="info" %}
Files such as `tmp`, `v_rc…` , `grid`, `lanat` (this is just a zoomed image, i.e. different field of view) can be deleted before import.
{% endhint %}

### Essential files in a legacy folder of a patient with postoperative CT scan

<figure><img src="../../.gitbook/assets/Screen Shot 2023-08-25 at 18.16.32.png" alt=""><figcaption></figcaption></figure>

### Essential files in a legacy folder of a patient with a postoperative MRI scan

<figure><img src="../../.gitbook/assets/Screen Shot 2023-08-25 at 18.18.20.png" alt=""><figcaption></figcaption></figure>
