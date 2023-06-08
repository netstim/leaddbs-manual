# Converting DICOM files into BIDS

### **Converting DICOM files into BIDS** <a href="#_toc96000785" id="_toc96000785"></a>

| <h4 id="_toc96000786">Context</h4>                                                                                                                                                                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <ol><li>Original patient imaging data are usually stored in the DICOM format. In the following steps, we will convert DICOM files into BIDS. The process is essentially similar to converting NIfTI to BIDS. However, DICOM files are first converted to NIfTI and then to BIDS.</li></ol> |

| <h4 id="_toc96000787">Info panel</h4>                                                                                                                                                                                                                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <ol><li>Make sure that one folder stores all of your patient data, and the file names do not contain any spaces or special characters.</li><li>Your patient’s folder should contain all the images in DICOM format (pre-operative structural T1-weighted and T2-weighted MRI and post-operative CT or MRI) (Screenshot 23).</li></ol> |

Screenshot 23. Patient file - DICOM

![](<../../.gitbook/assets/image (1).png>)

#### How to: <a href="#_toc96000788" id="_toc96000788"></a>

1. Select the patient that you want to convert from the main Lead DBS GUI.&#x20;
   1. From the **Import** section, select **"Import DICOM to BIDS dataset."**&#x20;
   2. Select the DICOM conversion tool you'd like to use.
   3. Click **RUN**.&#x20;
2. Lead will convert DICOM into NIfTI files, and a new window will appear. This is a new step we have not seen when converting NIfTI to BIDS (Screenshot 25)
   1. What you need to do here is to fill out the table using the drop-down menu and choose from the options (Screenshot 25B).
   2. In the **Session** column, choose whether the data are post-operative or pre-operative.
   3. The **Type** column is anat for both pre-and post-operative data.
   4. The **Modality** column is T1w and T2w for pre-operative data, and for post-operative data, you use CT (in this case) or MRI.
   5. The **Acquisition** section is filled automatically.

Screenshot 24. Import Section of the Main Lead DBS GUI

![](<../../.gitbook/assets/Screen Shot 2023-06-08 at 13.15.18.png>)

Screenshot 25. Lead-DBS to BIDS conversion

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

| <h4 id="_toc96000789">Output</h4>                                                                                                                                                                                                                                                                                       |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <ol><li>This time, three folders appeared in the output directory. (Screenshot 26)</li><li>Source data contain the original DICOM files.</li><li>Raw data contain raw NIfTI files with pre-operative and post-operative data.</li><li>Derivatives folder – contains the main output from the processing tool.</li></ol> |

Screenshot 26. Lead-DBS to BIDS conversion

![](<../../.gitbook/assets/image (2).png>)

### &#x20;<a href="#_toc96000790" id="_toc96000790"></a>
