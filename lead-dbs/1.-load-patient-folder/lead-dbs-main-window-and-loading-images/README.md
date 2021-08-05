# Main Window and Loading Images

The main window of Lead-DBS is divided into 6 sections:

* Data import
* Selection of patient directory and imaging technique
* Normalization
* Reconstruction
* Manual correction
* Visualization

The button `Run` in the bottom right runs **all** processes that are checked within the main window.

To run only one specific process, please make sure that only the desired checkbox is selected. Checkboxes marked with a **bold** text-face address steps that actually perform an analysis themselves, other checkboxes \(standard text-face\) are used as options within certain processes.

Hovering over the checkboxes with the mouse will show an explanation of each element of the Main Window.

![](../../../.gitbook/assets/lead_maingui_2.png)

## 1. Selecting the file directory

By clicking on `Choose Patient Directory` on the top, you can browse and select the location of the image folder.

For _Lead-DBS_ to analyze the images, it needs at least the following views:

* for MR images, a post-operative image \(at least a transversal view\)
* for CT images, a post-operative acquisition plus a pre-operative MR image.

You may also have more views available, in which case the process of electrode localization is made easier, robust, and precise.

**IMPORTANT:**  
Images may be in DICOM or NIfTI format. If in DICOM, _Lead-DBS_ will need to convert them into NIfTI \(.nii\) format using the DICOM import function. You can start by simply choosing a folder containing DICOM images in Lead-DBS and run the **Import DICOM and/or assign NIfTI images** function.

Finally, to process data, images must be in the `*.nii` file format and must have a _**specific naming format**_. For details on how to format the file names, please refer to **Section 2.1**.

## 2. Selecting the imaging technique

After the image directory has been chosen, you must select the imaging technology in the dropdown menu on the top right of the window. `MR` imaging is the default setting. If images are named correctly, _Lead-DBS_ will automatically set this selection for you.

