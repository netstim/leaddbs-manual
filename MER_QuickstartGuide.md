# QuickStart Guide for MER Localization in LEAD-DBS

### Enter Developer Mode
1. In the main lead dbs gui, go to 
    - `Preferences > Edit Preferences File...`
2. Under `%% environment` change 
    - `prefs.env.dev=0;` to `prefs.env.dev=1;`
3. You should now see a new button when opening a 3-D scene 
<img src="https://github.com/akapp/leaddbs-manual/blob/master/images/MER_toolbar.png" height="75%" width="75%" align="center" />

### Load MER Localizer
Clicking the MER icon in the 3D viewer toolbar will give you a reconstruction of the MER locations based on the lead localization, and a new MER Control GUI.

<img src="https://github.com/akapp/leaddbs-manual/blob/master/images/MER_screenshot.png" height="50%" width="50%" align="center" />


#
<img src="https://github.com/akapp/leaddbs-manual/blob/master/images/MER_controlgui.png" height="58%" width="58%" align="right" />
1. Choose the implanted tract from the dropdown menu near `Right` or `Left`

2. Toggle the implanted tracks on and off `Central, Anterior, Posterior, Lateral, Medial`.

3. Change the location of the MER site by
  a) Entering the position in the edit box, 
  OR
  b) Using the arrow keys `Left/Right` or `Up/Down` to edit the position of the microelectrode location.
      - note: Choose a toggle button for the electrode of interest. 
      - Hold `Shift` to increase step size. Hold `option` to decrease step size.
      
4. Mark a recording site using keyboard shortcuts
- Reserved keys:
    - `spacebar = "generic"`
    - `m = "MER"`
    - `l = "LFP"`
    - `t = "Top"`
    - `b = "Bottom"`

5. Use the `export markers` <img src="https://github.com/leaddbs/leaddbs/blob/master/icons/export.png" height="18" width="18" /> button in the MER Control GUI to save markers as a `.mat` file. 
