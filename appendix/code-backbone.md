# Code Backbone

```
lead.m
```

`lead.m` is the main function that calls the apps `lead_dbs.m`, `lead_connectome.m`, `lead_mapper.m`, `lead_group.m`. Thus, by calling `lead dbs`the function calls lead\_dbs.m

```
ea_run.m
```

…is the high-level "submit" function for any job submitted by lead DBS, lead connectome, lead mapper, lead anatomy etc (anything except `lead group` and `lead groupconnectome`). The function is also called when exporting code instead of actually running code and when using a "submit" function to submit code from the cluster. So basically, anything related to single-patient/subject analyses will pass through `ea_run`.

```
ea_autocoord.m
```

…is the main backbone of the pipeline that is then sometimes completed by `ea_write.m`. All functions that process data on a single level (i.e. do not stem from `lead group` or `lead groupconnectome`) branch off from `ea_autocoord`. As a side note, the name stems from the very early days in which lead dbs was still called "eAuto" for electrode autolocalization. The same is true for the prefix (`ea_*`) that we use in almost all functions.

```
ea_write.m
```

…is the final "writeout" function that exports 2D results or opens data in the 3D viewer `ea_elvis.m`.

```
ea_elvis.m
```

…is the 3D viewer of Lead-DBS. You can e.g. call it directly by running `ea_mnifigure.m`.

```
ea_handles2options.m
```

This is the function that converts handles (Matlab GUIDE handles to GUI elements) to the ubiquitous `options` struct that Lead-DBS uses to run jobs.

For example the struct may contain `options.dicomimp.do == 1;` to let `ea_autocoord` know to run the DICOM import module.

## Other important main functions in Lead-DBS

Most of the following branch off from `ea_autocoord` or `ea_elvis` – thus if you study these two a bit, you'll get a good feeling about the overall pipeline.

```
ea_dicom_import
```

…is the DICOM import module of the main GUI.

```
ea_imageclassifier
```

…opens the image classifier to rename Niftis that have been converted from DICOMs.

```
ea_lcm
```

…is the main subroutine to run everything related to `lead connectome mapper`.

```
ea_checkcoregallmri
```

…is the function to coregister preop MRIs of a specific patient.

```
ea_coregmr
```

…is the function used to coregister postop MRIs to preop MRIs of a specific patient.

```
ea_coregctmri_*
```

…all functions in this pattern will generate a CT to MRI coregistration entry in the main GUIs and will be called to perform the coregistration. They need to reside in the main lead-DBS code directory to be captured by the GUIs. If you want to create a new method to register CT to MRI, just duplicate one that is close and go from there. However, there are various things to consider, so maybe speak with us before/while you do.

```
ea_normalize_*
```

…similar with normalization methods: all files that match the above pattern found in the main code directory will create an entry for a normalization method in the GUIs. If you want to add such a method, duplicate on that is close and go from there. However, there are various things to consider, so maybe speak with us before/while you do.

```
ea_subcorticalrefine
```

…is the main function to run brainshift correction.

```
ea_checkcoreg
```

…is the function used when calling "Check Results" from the main GUIs.

```
ea_checkstructures
```

…is the function to open the "Refine atlas fit" function (which shows agreement between normalized patient images and specific atlas nuclei). This function can also be used to refine normalizations.

```
ea_runtraccore
```

…runs the main TRAC/CORE prereconstruction algorithm to detect leads.

```
ea_runpacer
```

…runs the PaCER prereconstruction algorithm to detect leads.

```
ea_runmanual
```

…runs the "Manual" preregistration module using SPM orthviews.

```
ea_runmanualslicer
```

…runs the "Manual" preregistration module using 3DSlicer.

```
ea_manualreconstruction
```

…main function of the manual reconstruction ("Localize DBS electrodes") view.

```
ea_orient_main
```

…main function of the DiODe rotation detection algorithm (Dembek et al) called from `ea_manualreconstruction`.

```
ea_writeplanes
```

Main 2D visualization output function ("Write out 2D") – while `ea_elvis` is the main 3D output function (see above).

## Preferences and Options

```
ea_prefs
```

Main function to get the prefs struct that is usually present as options.prefs. Prefs are defined by the function `.ea_prefs.m` in the user's home directory that is derived from `ea_prefs_default.m` in the lead-DBS code directory. You can open the user's prefs directory by hitting command/strg+P from a main GUI. If you need to add a prefs entry, make sure to add it to both `ea_prefs_default` and if needed to your own user prefs. `ea_prefs.m` will always combine entries from the two (if they are present in the user file, it will prefer these over the default prefs).

```
ea_prefs.mat
```

…along with the file `ea_prefs_default.mat` are analogous to the prefs text files (entry above) but more machine readable. That's why their content is stored in prefs.machine when calling `ea_prefs.m` (or in `options.prefs.machine` when in the main code somewhere).

```
options=ea_getptopts(directory,options)
```

…function to complete the `options` struct for patient-specific entries. For many things, you need only this limited `options` struct together with `options.prefs=ea_prefs;`

## Other functions that are often used and helpful to know

```
ea_assignpretra  || [options,presentfiles]=ea_assignpretra(options);
```

…is a function to assign the preoperative images of a patient folder (e.g. used for normalization).

```
ea_save_reconstruction(coords_mm,trajectory,markers,elmodel,0,options);
```

…is the function to properly save electrode localizations

```
[coords_mm,trajectory,markers,elmodel,manually_corrected,coords_acpc]=ea_load_reconstruction(varargin)
```

…is the function to properly load electrode localizations

```
ea_view
```

…can be used to save and store a 3D camera view.

```
ea_chirp
```

…plays the "done" sound if the user has activated it in her/his prefs.

```
ea_busyaction
```

…function to show/hide a spinning wheel on the current GUI to show the user something is running.

```
ea_dispercent
```

…used to show progress of a for-loop in the console output.e

```
ea_dispt
```

…function that will display a text string in the console but also protocol time (when calling the function on multiple occasions throughout laborious work.
