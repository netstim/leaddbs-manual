# Useful command-line tools

We will list useful scripts / command-line calls that are shipped within Lead-DBS on this site. Please note that a lot of these scripts are buggy and may not be well maintained. Also, the documentation may be outdated. But they provide some insight about useful tools for expert users.

## 3D Visualization / Elvis viewer

### ea\_mnifigure

```text
ea_mnifigure(atlasname);
ea_mnifigure('DISTAL Minimal (Ewert 2017)');
```

This snippet will open the 3D viewer "Elvis" of Lead-DBS with an atlas. It is a normal MATLAB figure, so you can then plot additional content onto it.

### ea\_keepatlaslabels

```text
ea_keepatlaslabels('on'); ea_keepatlaslabels('off');
ea_keepatlaslabels('STN');
```

This call will hide all atlas structures from an open viewer that are not specified in the script.

### ea\_setplanes

```text
ea_setplanes(X,Y,Z);
ea_setplanes(0,-30,nan); % will not show the z-plane at all
```

This call will move or hide \(when supplying NaN\) the MRI planes to specific mm values.

### ea\_view

```text
v = ea_view();
ea_view(v);
```

Store the current 3D view \(v = ea\_view;\) as variable v or set the current 3D view to the view stored in v.

### Elvis scripting example scripts

```text
ea_mnifigure('DISTAL Minimal (Ewert 2017)'); % open up Elvis viewer
ea_keepatlaslabels('GPI'); % hide all structures except GPi
load([ea_space([],'atlases'),'DISTAL Minimal (Ewert 2017)',filesep,'atlas_index.mat']); % manually load definition of DISTAL atlas.
rSTN=atlases.fv{1,1}; % extract the right STN.
rSTN=reducepatch(rSTN,0.5); % reduce patch a bit.
patch('Faces',rSTN.faces,'Vertices',rSTN.vertices,'facecolor','none','edgecolor','w'); % visualize the right STN as wireframes.
lSTN=atlases.fv{1,2}; % do the same for the left STN.
lSTN=reducepatch(lSTN,0.5);
patch('Faces',lSTN.faces,'Vertices',lSTN.vertices,'facecolor','none','edgecolor','w');
ea_setplanes(0,-30,nan); % set planes to a nice view.

% now define a specific camera view:
v.az= 126.0430;
v.el= -34.9893;
v.camva= 0.4648;
v.camup= [0 0 1];
v.camproj= 'orthographic';
v.camtarget= [-1.2419 -23.0911 3.9242];
v.campos= [1.0973e+03 1.0671e+03 -1.0542e+03];
ea_view(v); % apply view.

```

![The code above should produce something like this screenshot \(showing the STN wireframes in the Elvis viewer\).](.gitbook/assets/bildschirmfoto-2019-02-17-um-13.58.55.png)

## Export / Data Visualization

### ea\_surfice

```text
ea_surfice(nifti);
ea_surfice('/path/to/your/nifti/file.nii');
ea_surfice('/path/to/your/nifti/file.nii',[threshs],[sides=2],[colorbar=false],smoothed);
```

Overlay a nifti file to the MNI space surfice templates and export results as png.



## Coordinates and image manipulation

### ea\_spherical\_roi

This function will make a spherical region of interest around a user identified mni coordinates. It takes file name, mni coordinates in \(mm\), radius \(in mm\), and path of space template file in which the sphere will be identified, as arguments  

```text
ea_spherical_roi('/path/to/your/nifti/file_name.nii',mni_coordinates,radius_in_mm,crop,'/path/to/your/nifti/template_image.nii');
ea_spherical_roi('/Computer/Desktop/spherical_rois/DBS_ET.nii',[-14,-18.5,-2],1,1,'/Computer/lead/templates/space/MNI_ICBM_2009b_NLIN_ASYM/t1.nii');
```



### ea\_vox2mm

Converts voxel-coordinates to mm-coordinates. Coordinates need to be row vector: N\*3

```text
ea_vox2mm(vox, transform);
ea_vox2mm([122,220,133],'/Computer/lead/templates/space/MNI_ICBM_2009b_NLIN_ASYM/t1.nii');

ans =

  -37.5000  -24.5000   -6.0000
```



### ea\_flip\_lr\_nonlinear

Flip files / coords nonlinearly from Left to Right hemisphere \(or vice versa\) based on asymmetric template

```text
ea_flip_lr_nonlinear(from,to,interp)
ea_flip_lr_nonlinear('/Computer/Desktop/spherical_rois/DBS_ET.nii','/Computer/spherical_rois/DBS_ET_flipped_to_right.nii',1);
```

