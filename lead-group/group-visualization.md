---
description: Adapted from the Walkthrough Tutorial by Svenja Treu.
---

# Group Visualization

The original tutorial can be found [here.](https://ars.els-cdn.com/content/image/1-s2.0-S1053811920305048-mmc1.pdf)

### 1) 2D Visualization of Electrodes as Point Clouds colored by Group

![](<../.gitbook/assets/image (19).png>)Example Image of 2D visualization by group. Adapted from S. Treu et al., 2020.

<figure><img src="../.gitbook/assets/2dsettingsmaingui (1).png" alt=""><figcaption><p>Figure 1a</p></figcaption></figure>

1.1. In the main Lead Group GUI, select all the patients you want to visualize.

1.2. In the visualization options, select “show active contacts” (additionally “show passive contacts”, if preferred)

1.3. Under 2D options – Settings, you can adjust the backdrop from the dropdown menu. (Figure 1b) Try 7T Ex vivo 100um Brain Atlas (Edlow et al., 2019). Save and close.

![Figure 1b](../.gitbook/assets/2dsettings.png)

1.4. Press Visualize 2D. The results will also be saved under leadgroup/groupanalysisname/export/2D folder.

![](../.gitbook/assets/2dfolder.png)

***

### 2) 3D visualization

2.1. Select all the patients you want to visualize.

2.2. Click "Settings" under "3D Options". Here you can find options for electrode rendering. It is possible to visualize point clouds and solid or transparent electrodes. An example of each is given [at the end of this section](group-visualization.md#3d-visualization-examples). Click "Save".

<figure><img src="../.gitbook/assets/3delectrodesettings.png" alt=""><figcaption></figcaption></figure>

2.3. Click "Visualize 3D." 3 new windows will pop up: Electrode scene, atlas settings and anatomy slices. From anatomy slices window, you can select the backdrop of your choice and adjust slice position. From atlas settings, you can choose which atlas structures to display. From the electrode scene window you can adjust the camera angle, lighting of the scene and colors of individual atlas structures.

#### 3D Visualization Examples

![](<../.gitbook/assets/Screen Shot 2023-08-14 at 12.09.39.png>)**Point clouds.** Groups are represented by different colors. GPe is shown blue, STN and GPi are displayed in gray.

![](<../.gitbook/assets/Screen Shot 2023-08-14 at 12.25.23.png>)**Transparent electrodes with "Highlight Active Contacts" option.**

![](<../.gitbook/assets/Screen Shot 2023-08-14 at 12.29.02.png>)**Solid electrodes.**

***

### 3) Clinical Regressors

#### 3.1. Point clouds, colored by regressor&#x20;

![](<../.gitbook/assets/image (20).png>)3.1. Active contacts colored by regressor intensity.

* From 3D Settings, select point clouds and check the box “color by regressor”. This box can only be checked if Point-Clouds are selected.
* ![](<../.gitbook/assets/Screen Shot 2023-08-14 at 16.22.42.png>)
* Preferences for the colormaps can be edited by clicking "Colormap" in 3D Settings.

![](<../.gitbook/assets/Screen Shot 2023-08-14 at 16.23.11.png>)

#### 3.2. Map regressor as interpolated point mesh&#x20;

![](<../.gitbook/assets/image (21).png>)

Fig. 3.2. The regressor mapped to an equidistant point grid after solving a scattered interpolant based on the original values and active coordinates.

* Under 3D Visualization Settings check the box “Map regressor to Coords”
* Uncheck the box “Show Active Contacts”&#x20;
* In 3D options, select “Visualize regressor as: Interpolated point mesh”&#x20;

<figure><img src="../.gitbook/assets/mapregressortocoords.png" alt=""><figcaption></figcaption></figure>

#### 3.3. Map regressor as isosurface

![](<../.gitbook/assets/image (22).png>)

Fig. 3.3. The equidistant grid in the previous step can be thresholded and visualized as a 3D surface.

* From 3D settings, select “Visualize regressor as: isosurface”
* In the group folder you can then find the resulting surfaces as nifti files, named after the regressor and one for each hemisphere.&#x20;

## References

* Treu, Svenja, Bryan Strange, Simon Oxenford, Wolf-Julian Neumann, Andrea Kühn, Ningfei Li, and Andreas Horn. “Deep Brain Stimulation: Imaging on a Group Level.” NeuroImage 219 (October 1, 2020): 117018. https://doi.org/10.1016/j.neuroimage.2020.117018.
