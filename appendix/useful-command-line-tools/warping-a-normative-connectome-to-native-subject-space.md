---
description: >-
  This example shows how to warp the fibertracts represented in a normative
  connectome to the space of the "anat_t1.nii" (anchor space) of a subject and
  to convert the result to a .trk file.
---

# Warping a normative connectome to native subject space

This example shows how to warp the fibertracts represented in a normative connectome to the space of the "anat\_t1.nii" (anchor space) of a subject and to convert the result to a .trk file.

The example is not a "typical use-case" but I wrote the code for a colleague and potentially, some bits and pieces could be helpful for others. It could also be helpful to do the reverse (warp subject specific fibers to template space), however, this functionality is supported within `lead connectome`anyways.

```
clear
lead path % set matlab path to include lead-dbs
prefs=ea_prefs;

 % load the connectome of choice
conn=load([prefs.lc.datadir,'dMRI',filesep,'HCP_MGH_32fold_groupconnectome (Horn 2017)',filesep,'data.mat']);

patientfolder='/set/path/to/your/patientfolder/'; % needs to be a patient that was normalized to MNI using Lead-DBS

% now map coordinates to patient space T1
fibercoords=conn.fibers(:,1:3);
fibercoords=ea_map_coords(fibercoords', [patientfolder,'anat_t1.nii'], [patientfolder,'y_ea_normparams.nii'],... % keep the y_ thing even if this file does not exist. This is for historic reasons so Lead-DBS will know to take go from MNI to patient (and not the other way around). It will use whichever normalization you used.
    [ea_space,'T1.nii']);

% coordinates are now in mm space of the anat_t1.nii file.
% could now further transform coordinates from T1 to e.g. B0 space as you
% usually do (e.g. by multiplying coordinates with the affine transform
% matrix or so if you need them in B0 space.

% if you want to have them in voxel space instead, add the following:
V=ea_open_vol([patientfolder,'anat_t1.nii']);
fibercoords=V.mat\[fibercoords;ones(1,size(fibercoords,2))];
fibercoords=fibercoords(1:3,:);

conn.fibers(:,1:3)=fibercoords';
save([patientfolder,'HCP_connectome_native.mat'],'-struct','conn');

% now convert to .trk - this is sometimes tricky, since the .trk format is
% not well defined (e.g. dsi studio and trackvis treat them quite
% differently).

fibs=conn.fibers;
ea_ftr2trk([patientfolder,'HCP_connectome_native.mat'],[patientfolder,'anat_t1.nii']);
```
