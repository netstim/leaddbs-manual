---
description: Electrophysiology setup to use the Lead-OR platform
---

# Electrophysiology setup

## Requirements

1. **OpenEphys:** The [OpenEphys GUI](https://open-ephys.org/gui) (v >= 0.6.4) should be installed.
2. **Custom Plug-Ins:** The following plug-ins should be installed to use the platform: [OpenEphysIGTLink](https://github.com/netstim/OpenEphysIGTLink), [OpenEphysLeadOR](https://github.com/netstim/OpenEphysLeadOR) and [OpenEphysRMS](https://github.com/netstim/OpenEphysRMS).
3. **Data source:** the [OpenEphysNeuroOmega](https://github.com/netstim/OpenEphysNeuroOmega) plug-in (which requires the NeuroOmega SDK; Windows only) provides an interface to use the NeuroOmega device in real-time. To test the platform, example recordings can be downloaded from [here](https://github.com/netstim/SlicerNetstim/releases/download/SampleData/SampleRecordings.zip), and streamed to OpenEphys via the built-in File Readed plug-in.

## Custom plug-ins installation

The links above describe the different ways to install the plug-ins. Here, only the one via GitHub CLI is described. Install [GitHub CLI](https://cli.github.com/) and run the following commands to install the plug-ins:

#### Windows

```
copy /y "C:\Program Files (x86)\AlphaOmega\Neuro Omega System SDK\CPP_SDK\win64\NeuroOmega_x64.dll" "C:\ProgramData\Open Ephys\shared-api8"
gh release download --clobber --dir "C:\ProgramData\Open Ephys\plugins-api8" --pattern *.dll --repo netstim/OpenEphysNeuroOmega
gh release download --clobber --dir "C:\ProgramData\Open Ephys\configs-api8" --pattern *.xml --repo netstim/OpenEphysNeuroOmega
gh release download --clobber --dir "C:\ProgramData\Open Ephys\plugins-api8" --pattern *.dll --repo netstim/OpenEphysRMS
gh release download --clobber --dir "C:\ProgramData\Open Ephys\shared-api8" --pattern *.dll --repo netstim/OpenEphysIGTLink
gh release download --clobber --dir "C:\ProgramData\Open Ephys\plugins-api8" --pattern *.dll --repo netstim/OpenEphysLeadOR
```

## Building a processing pipeline

OpenEphys has a modular framework to create custom processing pipelines. Here, the default processing pipeline for Lead-OR is described. Although this example is done with example recordings, the File Reader plug-in can be replaced by the OpenEphysNeuroOmega plug-in for a novel real-time scenario.

1. Open OpenEphys GUI
2. Drag-and-drop the following plug-ins in order from the left Processors list to the Signal Chain and follow the instructions:
   1. File Reader
      * Click on _F_ to navigate and select the downloaded [example recordings](https://github.com/netstim/SlicerNetstim/releases/download/SampleData/SampleRecordings.zip).
   2. Bandpass Filter
      * Click on _Channels_ and select all.&#x20;
      * Default 300 to 6000 bandpass should be ok.
   3. LFP Viewer
   4. Root Mean Square
      * Click on _Channels_ and select all.&#x20;
      * Set _window\_ms_ to 3000.
   5. Lead-OR
      * Click on _Channels_ and select all.&#x20;
      * Check _feature_ and set _feature\_name_ to RMS
      * See next page for the following instructions.

See following screenshot for reference:

<figure><img src="../.gitbook/assets/Screenshot 2023-03-20 at 14.30.14.png" alt=""><figcaption><p>OpenEphys signal chain.</p></figcaption></figure>
