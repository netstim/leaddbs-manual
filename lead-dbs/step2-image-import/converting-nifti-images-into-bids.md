# Converting NIfTI-images into BIDS

| <h4 id="_toc95749082">Context</h4>                                                                                                                                                                                                                                                                                                                                                                                                |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <ol><li>In the following steps, Lead DBS converts the legacy NIfTI-images into Brain Imaging Data Structure (BIDS) images.</li><li>BIDS is a data structure for neuroimaging and behavioural data used in the imaging domain.</li><li>This step is necessary to re-assure that the lead-DBS will be able to work with data. Moreover, using BIDS is an easy way to store and re-use the data between various toolboxes.</li></ol> |

| <h4 id="_toc95749083">Info panel</h4>                                                                                                                                                                                                                                                                                                                                                            |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <ol><li><strong>Make sure that one folder stores all of your patient data, that data are in NIfTI format, and the file names do not contain any spaces or special character</strong>s.</li><li>The folder should contain <strong>pre-operative anat files and post-operative postop files</strong>.</li><li>CT files cannot be used as pre-operative data, MRI files are used instead.</li></ol> |

Screenshot 1. Patient file - NIfTI

<figure><img src="../../.gitbook/assets/patientfolder.png" alt=""><figcaption></figcaption></figure>

To start the importing process, simply select "Import NIfTI to BIDS dataset" and click "RUN". It is possible to import multiple patient files by holding shift and selecting multiple patients.

<figure><img src="../../.gitbook/assets/import.png" alt="" width="563"><figcaption></figcaption></figure>

A window will pop up where you need to s**pecify the session (preop or postop), type (anat, functional, dwi), modality and acquisition (sag, cor, axial, iso)**

<figure><img src="../../.gitbook/assets/import-modality123.png" alt=""><figcaption></figcaption></figure>

Here is another example with postoperative CT scans.

<figure><img src="../../.gitbook/assets/postopct.png" alt=""><figcaption></figcaption></figure>

#### Output

* After Lead migrated all NIfTI files into BIDS format, you can find them in the selected output folder/dataset directory. In our case, the folder’s name was “Directory”
* The folder contains three main sub-folders: “derivatives”, “raw data” and "source data". Each of these files contains data about our patients. The raw images that we have just converted will be stored under the **"rawdata/sub-\[PATIENTNAME]”** folder. The Lead will use these data for further analysis.
* “Dataset\_description” file contains information about your dataset.

<figure><img src="../../.gitbook/assets/folder2.png" alt=""><figcaption></figcaption></figure>



