# Importing a classic Lead-DBS dataset to BIDS version

If you have a dataset already set up with the classic version, importing them into the BIDS version is quite easy. Simply click the add patients button and choose the classic (or 'legacy') patient folder. This will automatically start the legacy import process.&#x20;

Here are some examples of legacy folders:

#### 1) Patient with Post-operative CT Images

<figure><img src="../../.gitbook/assets/image (24).png" alt=""><figcaption><p>Here is how a legacy folder for a patient with postoperative CT images looks like.</p></figcaption></figure>

Here are some common files and how they will be converted into BIDS.

* `raw_anat*.nii` -> These are the raw images. These will be stored under "derivatives/rawimages/patientID" in BIDS structure.
* `anat_*.nii` -> preprocessed, coregistered images. These will be stored under "derivatives/leaddbs/coregistration/anat" folder.
* &#x20;`postop_tra` -> coregistered post-op MRI images. These will be stored under "derivatives/leaddbs/coregistration/anat" folder.
* `rpostop_ct`-> co-registered postoperative CT images. These will be stored under "derivatives/leaddbs/coregistration/anat" folder.
* `glpostop_ct`-> normalized postoperative images. These will be stored under "derivatives/leaddbs/normalization/anat" folder.
*   `ea_coreg_approved`->stores approval status of coregistration, brainshift and

    normalization. It will automatically be transfered to BIDS format. **If this file is not present, everything will be set to approved when importing by default. In this case we recommend you to double check your coregistration, normalization and brainshift correction results.**
*   `ea_coregmrmethod_applied` and `ea_normmethod_applied:` stores info about

    which algorithms were used
*   `ea_precoregtransformation`: in Lead-DBS, preprocessing does alignment of

    anchor image (i.e., the t1) to MNI template, this is the transformation for that
* `ea_ui`: stores the options used in the GUI
* `ea_reconstruction:` stores the electrode reconstructions. This will be stored under "derivatives/leaddbs/patientID/reconstruction" folder.
* `scrf` folder -> scrf stands for subcortical refine. The contents of this will be moved under "derivatives/leaddbs/patientID/brainshift" folder.&#x20;
* `headmode`l  folder -> stores the head model for VTA computation
* `stimulations` folder -> will be moved under "derivatives/leaddbs/patientID/stimulations"
  *   In very old patient folders, the `gs_*` folders in stimulations are stored directly under

      stimulations (i.e., no native or MNI… subfolder is present). This may be becuase stimulation calculation was done before native space VTA calculation was introduces. Therefore, BIDS import will move these old folders under "derivatives/leaddbs/patientID/stimulations/MNI..." subfolder.&#x20;
* ct\_mask: used to do localization, rct\_mask is the same but co-registered
*   tp\_\* images are the tonemapped images, i.e. copies of the images with a better

    contrast
* rpostop\_ct: co-registered,
* glpostop\_ct: normalized

![](<../../.gitbook/assets/image (23).png>)
