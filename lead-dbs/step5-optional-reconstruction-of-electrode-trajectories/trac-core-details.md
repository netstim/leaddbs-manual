# TRAC/CORE Details

To reconstruct as precise as possible, Lead-DBS uses different MR-acquisitions (if available) to pinpoint the artifacts caused by the electrodes. Several options are available to help with this process.

#### Entry point for electrodes

The parameter `Entry point for electrodes` presents these options:

* STN, GPi or Vim
* Cg25
* Manual

An **automatic** reconstruction will be performed if any of the first two options are chosen. The option `STN, GPi, or ViM` targets electrodes that have been implanted in patients with movement disorders. The option `Cg25` targets those in patients with depression.

The option `Manual` will require you to pinpoint the entry points of the artifacts within the image slices. This option should in theory work with all DBS electrodes (wherever they might be implanted). Please select the right electrode when prompted the first time and the left one when prompted the second time. The red square shows the area, Lead-DBS would scan in the `STN, GPi or ViM` mode and helps you to identify the right hemisphere in each step.

#### Axis

The parameter `Axis` determines the images and possible small preprocessing steps that Lead-DBS uses to locate the electrode. The following options should be preferred:

* Use transversal image only
* Use transversal but smoothed
* Use average of coronal and transversal, smoothed

#### Mask window size

The default option is an _automatic_ window size (enter “auto” into the field). This has often given good results in the reconstruction.

However, numeric values can be entered to fix the size of the mask. Best results were obtained with values between 5 to 15 or 20. A smaller mask avoids nearby structures that could interfere in the reconstruction step. If the image shows large artifacts, e.g. due to local edema, a larger mask should be chosen (e.g. enter `15` instead of `auto`). If the image is noisy, a smaller mask (e.g. `5` or `7`) might be of better use.
