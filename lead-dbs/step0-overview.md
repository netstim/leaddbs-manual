# Overview

The app Lead-DBS is the main application of the Lead suite. It allows the reconstruction of electrodes for one patient or a batch of patients, if multiple folders are selected. To start, run `lead dbs`from the Matlab command prompt. The window below will pop up.

We explain steps 1 through 7 in more detail below, assuming a patient implanted bilaterally in the subthalamic nucleus. In brief:

<figure><img src="../.gitbook/assets/overview (2).png" alt=""><figcaption><p>Lead DBS Main Window</p></figcaption></figure>

1. The user selects the patient folder and electrode type.
2. Patient images can be converted from DICOM to NIfTI and renamed interactively to fit the Lead-DBS naming convention.
3. The patient images are co-registered and if selected, normalized into MNI template space and corrected for brain shift. The user can check the results and manually refine the atlas fit.
4. (optional) The surface is reconstructed.
5. (optional) The electrode trajectories are pre-reconstructed. The user can choose between different methods, depending on the postoperative imaging modality. For instance, for postoperative CT, PaCER is an effective method. Afterwards, the user localizes the electrodes to refine the position and --- if applicable --- the orientation of the electrodes.
6. (optional) The user can run connectivity analysis with Lead Connectome.
7. The reconstructed electrodes can be visualized in 2D or 3D in template or patient space. The user can select from a comprehensive list of atlases.

<mark style="background-color:blue;">The button</mark> <mark style="background-color:blue;"></mark><mark style="background-color:blue;">`Run`</mark> <mark style="background-color:blue;"></mark><mark style="background-color:blue;">in the bottom right runs</mark> <mark style="background-color:blue;"></mark><mark style="background-color:blue;">**all**</mark> <mark style="background-color:blue;"></mark><mark style="background-color:blue;">processes that are checked within the main window.</mark> To run only one specific process, please make sure that only the desired checkbox is selected. Checkboxes marked with a **bold** text-face address steps that actually perform an analysis themselves, other checkboxes (standard text-face) are used as options within certain processes.

Hovering over the checkboxes with the mouse will show an explanation of each element of the Main Window.
