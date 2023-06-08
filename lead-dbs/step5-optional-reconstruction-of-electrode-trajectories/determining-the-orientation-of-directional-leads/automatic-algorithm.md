# Automatic Algorithm

LEAD-DBS includes an algorithm based on work by the Cologne group which can automatically detect lead orientation. The algorithm has been validated for Boston Scientific Cartesia directional leads and postoperative CT imaging (Sitz et al. 2017 and Hellerbach et al. 2018). It is based on the CT artifacts generated by the stereotactic marker and the directional electrodes. In theory this algorithm could also work for the St. Jude / Abbot directional leads but results have not been validated for these leads yet and could be confounded by the very small size of their stereotactic marker.

## Running the Algorithm

The algorithm is called from inside the manual reconstruction GUI ("Localize DBS electrodes" in the main LEAD DBS GUI) by clicking the auto-rotation button:

![](../../../.gitbook/assets/DiDOeMenu.png)\
Lead positions should have been verified and corrected prior to running the algorithm, since the algorithm finds the ct artifacts according to the coordinates stored in the `ea_reconstruction.mat` file.

## Interpretation of Results

The algorithm performs two steps to find the exact lead orientation. It first analyzes the artifact generated by the stereotactic marker to define a first, preliminary rotation or roll angle. In a second step the algorithm tries to get a more accurate estimate, by analyzing the hypodense, 6-streak artifacts generated by the two levels of directional electrodes. For this it analyzes an angular range from - 30 ° to + 30° with respect to the preliminary roll angle determined during the first step.

A case with a very good result is shown here:

![](../../../.gitbook/assets/DiDOeResult.png)

As one can see in the upper left corner, the algorithm has chosen the anterior hyperdensity of the stereotactic marker artifact as its prelimenary orientation, with a roll angle of about 3,7 ° (filled green circle). It then compared the artifacts of the directional electrodes (center left, bottom left) against expected artifacts generated for roll angles of 3,7 ° +/- 30 °. For directional level 1 the roll angle with the optimal result was circa -0.3 ° and for directional level 2 +0.7 °. One can see that the expected artifacts (red circles) closely match the hypodense streaks in the real artifact (center left, bottom left) as well as the corresponding dips in the intensity profiles (center center, bottom center). In this case the user would be well-advised to accept reconstructions for both directional levels by checking both `Accept` checkboxes and then clicking `Accept & Save` to automatically store the changes in rotation and end the algorithm. The user will be led back to the manual reconstruction GUI were the lead will now be properly oriented. Please note that the rotation angle displayed in the GUI is different from the roll angle determined by the algorithm since both use different coordinate systems. Upon clicking `Accept & Save` this difference is also shown in the Matlab command line as e.g. : `Corrected roll angle roll = 0.18291 deg, has been converted to orientation angle = 0.030403 for compatibility with ea_mancorupdatescene.`