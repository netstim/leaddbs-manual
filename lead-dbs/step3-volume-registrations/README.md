# 3. Volume Registrations

![](<../../.gitbook/assets/lead-dbs-registration.png>)

First, Lead-DBS coregisters preoperative and postoperative images. MR images are coregistered to MR images by default with SPM. Postoperative CT images are coregistered to preoperative MR images by default with ANTs.

Second, you can choose to normalize the volumes to the MNI nonlinear 2009b space with ANTs. The ANTs settings are optimized for the subcortex, see [Ewert et al. (2019)](https://doi.org/10.1016/j.neuroimage.2018.09.061). If you have a multi-core computer, you can increase the number of threads to reduce computation time. To do this, click on `Settings`. Find more information about [MNI spaces here](https://www.lead-dbs.org/about-the-mni-spaces/). More information about templates and other normalization methods, see [this page](normalization-of-images.md).

Third, brainshift correction is recommended to improve the lead localization. Due to the lead implantation, brain shift is highly likely, i.e., the brain moves with respect to the skull. More information about the correction on[ this page](subcortical-refine-post-to-pre-transforms.md).

Finally, you can approve, recalculate or reject the registration and normalization results visually by ticking **Check Results. Refine Atlas Fit** allows for fine manual adjustments to better match, for instance, an atlas fit of the subthalamic nucleus with the patient-specific nucleus. See [this page](refine-atlas-fit-with-warpdrive.md) for more information on WarpDrive.

The following subpages provide more technical detail.
