---
description: Troubleshooting VTA Generation
---

# VTA Calculation Troubleshoot

Dear traveler in the realms of VTAs and electric fields & Lead-DBS user! If you reached this page, we likely pointed you to it on Slack and it means you have been frustratingly trying to calculate VTAs or E-Fields with the FieldTrip/SimBio method inside Lead-DBS.

In general, you have two options:

1. Go for the new and shiny tool, OSS-DBS v2. This is the future anyways, the model is better and it just works. We would recommend to try that. Soon, OSS-DBS will become the default and part of the official release, but unfortunately, we are not there yet.&#x20;
   1. To use it anyways:&#x20;
      1. Install Lead-DBS via github (see [Installation](../../installation.md#installation-via-github))[ ](../../installation.md)
      2. Check out the branch ‘ossdbsV2’ (you can google how to check out branches on git if new to git, it’s all very well documented with tons of tutorials online).&#x20;
      3. Open Lead-DBS and Choose the Preferences Menu -> Edit Preferences File… In the file that opens, find the line that says prefs.env.dev=0; and switch to prefs.env.dev=1;&#x20;
      4. Have fun with OSS-DBS (choose the model instead of the fieldtrip one).&#x20;
2. Try to debug the old (FieldTrip/SimBio) tool:&#x20;
   1. Calculating the stimulation volume is dependent on creating a suitable tetrahedral volumetric mesh describing the structure of the conducting & insulating parts of the electrode surrounded by anatomical structures (grey and white matter). Lead-DBS uses multiple tools to do this, including the SimBio - FieldTrip pipeline (Vorwerk et al, 2018) as well as Iso2Mesh (Qianqian Fang, 2009) and, most importantly, TetGen (Hang Si. 2015) .
   2. Given the variations of electrode placements relative to anatomical structures, it can happen that during mesh building, triangles of the two components intersect. This will lead to downstream problems for calculating the voltage distribution and electric field. If this happens, Lead-DBS will throw out an error.
   3. This is a general problem of finite element method (FEM)-related mesh building and not unique to Lead-DBS. In other words, this is often not easy to automate for all cases of electrode placements and all atlases. For that reason, commercial software, such as SureTune or GuideXT uses heuristic shortcuts to calculate VTAs more robustly. In Lead-DBS, a similar shortcut that will work robustly has been implemented in form of the FastField method (Baniasadi et al, 2020).
   4. We have tried to make the process as robust as possible. However, despite many strategies and attempts, calculating VTAs with the SimBio method can still fail in some cases.
   5. If none of this helps, see below.
3. The following troubleshooting steps could be tried to debug the Fieldtrip/Simbio model:
   1. First make sure that no other matlab code is on your path except the base folder of lead dbs and the base folder of spm. Retry and see if it works. If it does, great.&#x20;
   2. Make sure you have the toolboxes (statistics, image processing and signal processing) installed which lead-dbs generally needs.&#x20;
   3. Make sure the fortran libraries are installed (see `Troubleshooting / Specific Help` module of the manual).
   4. Change the VTA settings to use no atlas or the DISTAL nano atlas under `7. Visualization` model (see below).

![](<../../.gitbook/assets/Screen Shot 2022-07-19 at 10.12.20 AM.png>) ![](<../../.gitbook/assets/Screen Shot 2022-07-19 at 10.13.41 AM.png>)

1. Even more help:
   1. Delete the `headmodel.mat` files (e.g `headmodel1.mat`) under `headmodel`directory, and re-run VTA reconstruction.
   2. Retry calculating the VTAs several times, even if it failed the first time (there are some non-deterministic components in the pipeline).
   3. If all fails, slightly reposition the electrodes (by sub-millimeters that still make the reconstruction accurate) using the `5.Reconstruction of electrode trajectories (optional)` module.
   4. If none of that solves the issue: Set a breakpoint on line 135 in the file ea\_genvat\_horn.m Click the calculate button again to calculate a VTA. The code will stop at that line. Select the line (\[mesh.tet,mesh.pnt,activeidx,wmboundary,centroids,tissuetype]=ea\_mesh\_electrode(fv,elfv,ntissuetype,electrode,options,S,side,electrode.numel,Ymod,elspec);) and right click -> Evaluate Selection in Command Window. This will likely crash and show an error report. Send us that error report (on Slack) if it is not obvious to solve the issue for yourself.

**References:**

\[1] Vorwerk, J., Oostenveld, R., Piastra, M.C. _et al._ The FieldTrip-SimBio pipeline for EEG forward solutions. _BioMed Eng OnLine_ **17,** 37 (2018). https://doi.org/10.1186/s12938-018-0463-y

\[2] Qianqian Fang and David Boas, "Tetrahedral mesh generation from volumetric binary and gray-scale images," Proceedings of IEEE International Symposium on Biomedical Imaging 2009, pp. 1142-1145, 2009

\[3] Hang Si. 2015. "[_TetGen, a Delaunay-Based Quality Tetrahedral Mesh Generator_](https://doi.acm.org/10.1145/2629697)". ACM Trans. on Mathematical Software. **41** (2), Article 11 (February 2015), 36 pages. DOI=10.1145/2629697 https://doi.acm.org/10.1145/2629697

\[4] Baniasadi M, Proverbio D, Gonçalves J, Hertel F, Husch A. FastField: An open-source toolbox for efficient approximation of deep brain stimulation electric fields. Neuroimage. 2020 Dec;223:117330. doi: 10.1016/j.neuroimage.2020.117330. Epub 2020 Sep 2. PMID: 32890746.
