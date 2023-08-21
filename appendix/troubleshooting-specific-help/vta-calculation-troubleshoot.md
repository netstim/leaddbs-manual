---
description: Troubleshooting VTA Generation
---

# VTA Calculation Troubleshoot

1. Calculating the stimulation volume is dependent on creating a suitable tetrahedral volumetric mesh describing the structure of the conducting & insulating parts of the electrode surrounded by anatomical structures (grey and white matter). Lead-DBS uses multiple tools to do this, including the SimBio - FieldTrip pipeline (Vorwerk et al, 2018) as well as Iso2Mesh (Qianqian Fang, 2009) and, most importantly, TetGen (Hang Si. 2015) .
2. Given the variations of electrode placements relative to anatomical structures, it can happen that during mesh building, triangles of the two components intersect. This will lead to downstream problems for calculating the voltage distribution and electric field. If this happens, Lead-DBS will throw out an error.
3. This is a general problem of finite element method (FEM)-related mesh building and not unique to Lead-DBS. In other words, this is often not easy to automate for all cases of electrode placements and all atlases. For that reason, commercial software, such as SureTune or GuideXT uses heuristic shortcuts to calculate VTAs more robustly. In Lead-DBS, a similar shortcut that will work robustly has been implemented in form of the FastField method (Baniasadi et al, 2020).
4. We have tried to make the process as robust as possible. However, despite many strategies and attempts, calculating VTAs with the SimBio method can still fail in some cases.
5. We are also currently having some issues with VTA calculation errors on MAC M1-chip computers.&#x20;

The following troubleshooting steps could be tried in case of such failures:

* Make sure the fortran libraries are installed (see `Troubleshooting / Specific Help` module of the manual).
* Change the VTA settings to use no atlas or the DISTAL nano atlas under `7. Visualization` model (see below).

![](<../../.gitbook/assets/Screen Shot 2022-07-19 at 10.12.20 AM.png>)![](<../../.gitbook/assets/Screen Shot 2022-07-19 at 10.13.41 AM.png>)

* Delete the `headmodel.mat` files (e.g `headmodel1.mat`) under `headmodel`directory, and re-run VTA reconstruction.
* Retry calculating the VTAs several times, even if it failed the first time (there are some non-deterministic components in the pipeline).
* If all fails, slightly reposition the electrodes (by sub-millimeters that still make the reconstruction accurate) using the `5.Reconstruction of electrode trajectories (optional)` module.

**References:**

\[1] Vorwerk, J., Oostenveld, R., Piastra, M.C. _et al._ The FieldTrip-SimBio pipeline for EEG forward solutions. _BioMed Eng OnLine_ **17,** 37 (2018). https://doi.org/10.1186/s12938-018-0463-y

\[2] Qianqian Fang and David Boas, "Tetrahedral mesh generation from volumetric binary and gray-scale images," Proceedings of IEEE International Symposium on Biomedical Imaging 2009, pp. 1142-1145, 2009&#x20;

\[3] Hang Si. 2015. "[_TetGen, a Delaunay-Based Quality Tetrahedral Mesh Generator_](https://doi.acm.org/10.1145/2629697)". ACM Trans. on Mathematical Software. **41** (2), Article 11 (February 2015), 36 pages. DOI=10.1145/2629697 https://doi.acm.org/10.1145/2629697

\[4] Baniasadi M, Proverbio D, Gonçalves J, Hertel F, Husch A. FastField: An open-source toolbox for efficient approximation of deep brain stimulation electric fields. Neuroimage. 2020 Dec;223:117330. doi: 10.1016/j.neuroimage.2020.117330. Epub 2020 Sep 2. PMID: 32890746.

