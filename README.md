# Introduction

Lead-DBS is an open-source, MATLAB-based toolbox to **localize** and **visualize** electrodes in patients treated with deep brain stimulation. Importantly, the toolbox is intended for research and not for clinical use. First, this user guide focuses on Lead-DBS and single patient analysis with co-registration, normalization and reconstruction. Second, the user guide covers group analyses with Lead-Group.

This user guide is intended to cover most use cases. It pairs well with the primer for [postoperative CT data](https://www.lead-dbs.org/?page\_id=220) or [postoperative MR data](https://www.lead-dbs.org/?page\_id=225). It also goes well with the [basic walkthrough video](https://www.lead-dbs.org/helpsupport/knowledge-base/walkthrough-videos/) and a [more recent walkthrough video](https://youtu.be/xobhQDgtVfs) (Lead-DBS v2.5 new tools). For troubleshooting or other questions, the Lead-DBS community offers great support on the [Slack user channel](https://www.lead-dbs.org/helpsupport/slack-user-channel/).

**Quick history:** Lead-DBS was initially developed at the [Movement Disorders Unit of Andrea Kühn](https://neurologie.charite.de/forschung/arbeitsgruppen/bewegungsstoerungen_andrea_kuehn), Department of Neurology, Charité – University Medicine (CCM), Berlin, Germany. Since 2019, the [Network Stimulation Laboratory of Andreas Horn ](https://www.netstim.org)has been coordinating the development.

**Other useful links:** [Lead-DBS website](https://github.com/netstim/leaddbs), [Lead-DBS on GitHub](https://github.com/netstim/leaddbs), [Lead-DBS on Twitter](https://twitter.com/leaddbs),

## Key Features

* Linear and nonlinear registration of MRI and CT images
* Reconstruction of the electrode trajectories
* Manual correction of the electrode localization
* Visualization of results in 2D slice views
* Visualization of a 3D model showing DBS electrodes and their target areas
* Calculation of the Volume of Activated Tissue (VAT) and visualization of the structural connectivity from the VAT to other brain areas
* Group analysis

## Dependencies

Lead-DBS is a collection of tools for the purpose of DBS electrode reconstructions and related processing. The core job of our development team is to find and integrate the best neuroimaging tools available within the open-source community and develop our own code where no good code can be found. Thus, Lead-DBS heavily depends on other tools that should be referenced properly if used for research projects. Please find a list of tools used by Lead-DBS [here](https://www.lead-dbs.org/?page\_id=1126).
