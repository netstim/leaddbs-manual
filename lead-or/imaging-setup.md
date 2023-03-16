---
description: Imaging setup to use the Lead-OR platform
---

# Imaging setup

## Requirements

### 3D Slicer

3D Slicer (v >= 5.2.2) together with the SlicerNetstim, SlicerOpenIGTLink and SlicerIGT extensions should be installed.

### ORScene

In order to create an _ORScene_ (set of data ready to plug into the real-time platform) it is necessary to have a Lead-DBS subject processed with the **co-registration** and **normalization** steps.

Next, the surgical planning files should be placed under a `leador` subfolder within the subject folder. The following image shows an example subject with Brainlab planning:

<figure><img src="../.gitbook/assets/Screenshot 2023-03-16 at 18.02.11.png" alt=""><figcaption></figcaption></figure>

#### Create ORScene

Next, to create the ORScene, load the subject to Lead-DBS and select `Tools > Lead-OR > Create ORScene`, as the following image shows. Note that the selected atlas will be put into the scene as well.

<figure><img src="../.gitbook/assets/Screenshot 2023-03-16 at 17.30.22.png" alt=""><figcaption></figcaption></figure>

The subject `leador` directory now should look as follows:

<figure><img src="../.gitbook/assets/Screenshot 2023-03-16 at 18.01.51.png" alt=""><figcaption></figcaption></figure>

#### Loading the ORScene in Slicer

Simply drag-and-drop the ORScene.mrb file into Slicer to see the subject images, together with the planned trajectories and atlas structures.
