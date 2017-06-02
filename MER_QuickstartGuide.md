# QuickStart Guide for MER Localization in LEAD-DBS

### Enter Developer Mode
1. In the main lead dbs gui, go to 
    - `Preferences > Edit Preferences File...`
2. Under `%% environment` change 
    - `prefs.env.dev=0;` to `prefs.env.dev=1;`
3. You should now see a new button when opening a 3-D scene 
<img src="https://github.com/akapp/leaddbs-manual/blob/master/images/MER_toolbar.png" height="75%" width="75%" align="center" />

### Load MER Localizer
1. Clicking the MER icon in the 3D viewer toolbar will give you a reconstruction of the MER locations based on the lead localization.

<img src="https://github.com/akapp/leaddbs-manual/blob/master/images/MER_screenshot.png" height="50%" width="50%" align="center" />

2. And a new MER Control GUI will pop up.

<img src="https://github.com/akapp/leaddbs-manual/blob/master/images/MER_controlgui.png" height="50%" width="50%" align="center" />

3. Choose the implanted tract from the dropdown menu near `Right` or `Left`

4. Toggle the implanted tracks on and off `Central, Anterior, Posterior, Lateral, Medial`.

5. Change the location of the MER site by
  a) Entering the position in the edit box, 
  OR
  b) Using the arrow keys `Left/Right` or `Up/Down` to edit the position of the microelectrode location.
      - note: Choose a toggle button for the electrode of interest. Hold `Shift` to increase step size.
      
6. Mark a recording site using keyboard shortcuts
`spacebar = generic`
