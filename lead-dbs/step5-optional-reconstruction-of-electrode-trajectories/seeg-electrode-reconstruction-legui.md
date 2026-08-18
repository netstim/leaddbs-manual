---
description: SEEG electrode reconstruction and labelling using LeGUI.
---

# SEEG electrode reconstruction (LeGUI)

Lead-DBS supports SEEG electrode reconstruction, labelling, and visualization through integration of the LeGUI software by Davis et al. The paper describing the legacy version of LeGUI can be found here.&#x20;

The LeGUI pipeline consists of 3 main steps:&#x20;

1. Automatic contact detection ('AutoElec') and manual corrections&#x20;
2. Electrode contact labelling ('Assign Electrodes') through a semi-automatic algorithm&#x20;
3. (Optional) Electrode re-alignment ('Align lead').

To start LeGUI, select `'LeGUI (Davis 2021)'` in the pre-reconstruction method drop-down menu.&#x20;

### LeGUI main window

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-17 at 10.21.55 PM.png" alt=""><figcaption></figcaption></figure>

The LeGUI main window consists of a left panel showing the preoperative MRI and postoperative CT (2D view), a right panel showing the cortical surface reconstruction (3D view), and a toolbar at the top.&#x20;

To adjust the view in the left panel:&#x20;

* Move the slider at the bottom to adjust the CT-MRI overlay (i.e., show the CT or MRI) **(1)**.&#x20;
* Under the `Image Display` toolbar **(2)**, use the View dropdown menu to select the axial, coronal, or saggital view.&#x20;
* The `CLim` values control the color contrast in the CT and MRI.&#x20;
* The `Inline` option allows to rotate the MRI and CT images so that the selected lead is effectively brought into the viewing plane, meaning that all contacts along the entire lead are displayed together on one 2D slice. This requires assigning electrodes first.&#x20;
* The `Label` option will show the assigned contact labels. This requires assigning electrodes first.&#x20;

The view in the right panel is controlled by the button range above **(3)**.&#x20;

* Select the `Rotate 3D` button to activate 3D rotation of the surface model.&#x20;
* Set the `Brain Vis` option below this panel **(4)** to lower opacity values (e.g. 0.1) to visualize electrode contacts within the brain.&#x20;

Contacts can be selected in two ways:&#x20;

* Use left click to select a contact in the 2D or 3D view.&#x20;
* Select the `Polygon selection` tool above the 3D panel to select a group of contacts by circling them with the mouse in the 3D panel.&#x20;
* Selected contacts are displayed in red.&#x20;

### Electrode contact detection&#x20;

#### How to&#x20;

1. Click the `Auto Elec` button in the `Electrode Creation and Display` toolbar to launch automatic contact detection. This step typically runs in less than 20s. The contact count will reflect how many electrode contacts have been detected. Detected contacts are shown as blue dots.
2. Carefully review the results by looking at the different views as needed. Some electrodes may be easier to review in the axial plane, while others may be easier to review in the coronal plane.&#x20;
3. To remove one or several false positive contact(s), select them with a left click or with by circling them with the polygon selection tool. Selected contacts are shown in red. Then, press the delete key.
4. To add a missing contact, right click its position on the CT (2D view). LeGUI enforces a minimal distance between contacts; if you are not able to add a contact for this reason, select the `Manual Draw` option in the `Electrode Creation and Display` panel to override this constraint.&#x20;
5. Once all electrode contacts are properly marked, you may proceed to electrode assignment.&#x20;

### Electrode assignment&#x20;

This step allows to name all electrodes contacts following the implantation scheme, using a semi-automatic approach.&#x20;

#### How to&#x20;

1. Once both automatic and manual electrode detection are complete, click the `Assign Electrodes` button at the top of the window.
2. Display options in the electrode assignment GUI are similar to those of the main GUI.
3. Click the `Auto Name` button at the top of the window. The following window opens, showing the electrodes that were detected.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-17 at 10.36.14 PM.png" alt=""><figcaption></figcaption></figure>

1. It is possible that some contacts may be incorrectly grouped into electrodes; you will be able to fix this in the next step.&#x20;
2. Select the correct electrode model and name each of the electrodes based on your implantation scheme. To identify which electrode each row corresponds to, click rows to highlight the corresponding contacts in the 3D view.&#x20;
3. Once you are done, click `Apply Changes` and close the window. Note that you will be able to come back to it if you made a mistake, but changes only get transfetted to the main electrode assigment GUI when you click `Apply Changes`.&#x20;
4. You can now check and correct electrodes assignments in the main assignment GUI. First, set the table control mode to `Check`.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-17 at 10.41.11 PM.png" alt=""><figcaption></figcaption></figure>

1. You can now check whether contacts were correctly labelled. Click a contact in the 3-D view to highlight its label, or click a label in the table to highlight its corresponding contact. By default, contacts are numbered from deepest to closest to the cortical surface. You may select the deepest contact in the table and use the top arrow to quickly verify the contact numbering for a given electrode.&#x20;
2. If some assignments are incorrect, first, switch to the `Edit` table control mode to correct the table. Right click on a column header to delete a column/electrode. Contacts that are no longer assigned will be highlighted in blue. You can also add additional contacts to an electrode by manually entering additional labels, or rename any contacts in the table.&#x20;
3. Once the table is correct, switch to the `Assign` table control mode to re-assign blue contacts. Select the contacts using a left click or the polygon selection tool, then select the corresponding labels in the table, and click the `Assign` button below the table.&#x20;
4. When all assignments are correct, close the electrode assignment window, which will save your work.&#x20;

### Electrode alignment &#x20;

The `Align Lead` option, accessible from the LeGUI main window, allows to align contacts along a modeled electrode trajectory, taking into account the geometry of the same electrode model (i.e., electrode spacing, which is shown as 5 mm in the example below). This step is optional and may be only applied to electrodes that look poorly aligned. This may occur as the LeGUI automatic contact detection algorithm does not use information on electrode trajectory, but instead detects each contact individually. Use the polygon selection tool to select the electrode contacts to be realigned, and click Align Lead. A warning message will appear if the stored electrode spacing does not correspond to the empirical electrode spacing.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-17 at 10.55.28 PM.png" alt=""><figcaption></figcaption></figure>

You are now done with electrode reconstruction and labeling! Do not forget to click the `Save` button before you exit LeGUI!

