# WarpDrive

WarpDrive is a feature used to manually correct for misalignments after image normalization. It used currently under development but can already be accessed enabling the developer mode in Lead-DBS.\
\
For using WarpDrive, we suggest to use the develop branch from git and follow the next steps:

1. Install [Slicer](https://download.slicer.org/). (Being familiarized with Slicer will help then to navigate the views. There is documentation on this from their [user manual](https://slicer.readthedocs.io/en/latest/user\_guide/user\_interface.html)).
2. Launch Slicer and install the **MarkupsToModel** and **SlicerRT** extensions from the [Extensions Manager](https://slicer.readthedocs.io/en/latest/user\_guide/extensions\_manager.html)).
3. Enable developer mode in Lead-DBS:
   1. Launch Lead-DBS and go to Preferences -> Edit Preferences File...
   2. Set the variable `prefs.env.dev=1` (\~ line 210).

You're ready to go! Check the **Refine Atlas Fit** checkbox to run WarpDrive in Slicer. If you never opened Slicer from Lead-DBS before you will be prompted to enter it's file location.\
\
WarpDrive is still under development and we are working on a better way to install and launch it.
