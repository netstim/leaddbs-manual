# Sweetspot Explorer

{% hint style="warning" %}
This page is currently under construction.
{% endhint %}

## Content

***

* Sweetspot Explorer allows user to identify local clusters that are associated with the clinical outcome following the DBS e.g. clinical (e.g. % UPDRS-III improvement following STN-DBS).&#x20;
* It has been developed to map anatomical hot- and cold-spots within DBS targeted region.&#x20;
* The Sweetspot Explorer explains the outcome based on the stimulation location, which can be determined in several ways: as coordinates of active electrodes, weighted by distance from the active electrode via a Gaussian function, as a binary VTA (thresholded here at 200V/m), or weighted by the strength of the electric field (thresholded here at 100V/m).

## How to

***

### 1. User Interface

<figure><img src="../.gitbook/assets/image (1).png" alt="" width="375"><figcaption><p>Image 1. Sweetspot Explorer user interface.</p></figcaption></figure>

Sweetspot Explorer builds upon Lead group and therefore, all the VTAs/E-fields have to be calculated (press the `Calculate stats & VTA` button in Lead group interface) in order to use it. Click on the `Visualize 3D` button inside Lead group and in the 3D viewer window, click on `Add sweetspot analysis` button.

<figure><img src="../.gitbook/assets/image.png" alt="" width="52"><figcaption></figcaption></figure>

A new window with Sweetspot Explorer user interface pops up, offering a selection of methods for the further analysis. The window can be divided into 3 subparts: Interactive Model Setup, Visualization & Thresholds, and Crossvalidation & Prediction (Figure 1).

### 2. Model Setup

<figure><img src="../.gitbook/assets/image (2).png" alt="" width="345"><figcaption><p>Image 2. Sweetspot Explorer Interactive Model Setup options window.</p></figcaption></figure>

* `Interactive Model Setup` (Image 1, arrow 1) allows you to define methods and parameters to generate the computational model. You can define the analysis level, subcohort selection, dependent variable selection, covariates, statistical tests, option to mirror VTAs/Efields (Image 2, arrows 1-8).
* `Analysis Level` - allows you simply select whether you want to continue working on your model using VTAs or E-Fields. VTAs are stored in binary format \[0 and 1], where all voxels within the VTA are stimulated and all the voxels outside are not stimulated. E-Fields are stored in a continuous fashion and contain information on the spatial distribution of the voltage. This selection will determine your options in the following section called “Inspire Analysis by …” (Figure 2, arrow 1)
* `VTA/E-Field Threshold [V/mm]` - determines what effect will be considered as “stimulating” (Figure 2, arrow 2).
* `Voxels covered` - Allows you to define the VTA/E-Field threshold required for voxels to be included in the model (Figure 2, arrow 3).
* `Variable of Interest (VOI)`, `Normalize & Zero-Center VOI` & `Clean VOI from the following covariates` - (Figure 2, arrows 4-6)

#### 2.1 Inspire Analysis by ...

These options allow you to select one of the methods from previously published literature, or also create your custom model. The descriptions were adapted from Dembek et al., 2022.

<details>

<summary>Butson 2011</summary>

Butson et al., (2011) mapped a sweetspot in patients suffering from Parkinson’s disease using a VTA-based model. The mean-effect image was generated and thresholded to select voxels with the average clinical improvement above 50%.

</details>

<details>

<summary>Cheung 2011</summary>

Cheung et al., (2011) mapped a sweetspot of patient suffering from dystonia by looking at patients with good DBS outcome and the voxels that were covered by VTAs most often in those cases. In their cohort, 75% of patients with the best outcome were used.

</details>

<details>

<summary>Eisenstein 2014</summary>

Eisenstein et al., (2014) used voxel-wise statistics to define voxels associated with a significant improvement of patients suffering from Parkinson's disease. The outcome was weighted for each voxel dependent on its distance from the active electrode contact. Each voxel was then assigned a resulting weighted outcome, and was then tested against zero. Results determined voxels leading to a significant improvement.

</details>

<details>

<summary>Reich 2019</summary>

Reich et al., (2019) used VTA based mean-image and identified voxels that had significantly higher outcome compared to the average of all VTA outcomes, which did not stimulate that particular voxel.

</details>

<details>

<summary>Dembek 2019</summary>

Dember et al., 2019 generated a mean-effect image combined with voxel-wise statistics to compare the outcomes in each voxel against average outcomes of the cohort as a whole.

</details>

<details>

<summary>Elias 2020</summary>

Elias et al., (2020) weighted each patient’s VTA by the corresponding % change from basline and calculated mean outcome metric. Then generated an N-map (frequency map) representing the number of VTAs that overlapped a given voxel and thresholded this map at 10%. Two-tailed voxel-wise Wilcoxon-signed rank tests were performed, generating a p-map denoting the confidence about association between stimulation at each voxel and the clinical improvement. P-map was then used as a mask over an average map (Elias et al., 2020).

</details>

#### 2.2 Statistical Test

<details>

<summary>Mean-Image</summary>

Mean-Image with VTAs is calculated by the summation of multiplication of the VTA and the outcome parameter. The resulting image corresponds to the sum of clinical outcomes that are caused by the VTAs stimulating those voxels. The voxels in this sum image are then divided by how often they were stimulated – showing the average outcome.

</details>

<details>

<summary>N-Image</summary>

N-Image represents the number of times it was covered by VTAs from the dataset. It is simply generated by adding up all the VTAs. It does not include information on the stimulation outcomes and only informs on the location where patients were stimulated.

</details>

<details>

<summary>T-Test</summary>



</details>

<details>

<summary>Wilcoxon-Test</summary>



</details>

<details>

<summary>Proportion Test (Binary Var)</summary>



</details>

<details>

<summary>Binomial Test (Binary Var)</summary>



</details>

* Subcohorts can be created by selecting patients in the bottom window this selection can be saved by clicking on `Subcohorts` (Image 2, arrow 10) and selecting one of the options: `Create Subcohort from Selection` or `Create Subcohort from Inverse Selection`.&#x20;
* If `Mirror Data` box is selected (Image 2, arrow 11), VTAs/Efields from one hemisphere will also be used for the second hemisphere (mirroring the effect).

### 3. Visualisation & Thresholding

<figure><img src="../.gitbook/assets/image (3).png" alt="" width="375"><figcaption><p>Image 3. Sweetspot Explorer Visualization &#x26; Thresholds window.</p></figcaption></figure>

* The generated sweet and sour spots can be visualized and further adjusted during `Visualization & Thresholding` (Image 1, red arrow 2). Specifically, this step allows thresholding of the generated maps based on a predefined alpha-level and correction for multiple comparison (Image 3, arrows 1&2).
* You can select to visualize voxels positively or negatively correlated with your selected dependent variable (Image 3, arrow 3), as well as change their color (Image 3, arrow 4).
* For more advanced post-hoc analysis, the option to export the generated maps in the form of NIfTI files is also available, by clicking on `Export as NIfTI` (Image 3, arrow 5). These NIfTI images can then be visualized and processed in Slicer, for further information [sweet-sour-spot.md](../appendix/using-slicer/sweet-sour-spot.md "mention").
* After you select all the settings, press `Refresh View` or alternatively, tick the `Auto-Refresh` box that will refresh the view automatically (Image 3, arrow7).

### 4. Crossvalidation & Prediction

<figure><img src="../.gitbook/assets/image (5).png" alt="" width="375"><figcaption><p>Image 4. Network Mapping Explorer Crossvalidation &#x26; Prediction window.</p></figcaption></figure>

* The final step across frameworks is `Crossvalidation & Prediction` (Image 1, red arrow 3). This step is crucial establishes the validity of generated models within and generalizability across cohorts. Current validation strategies include permutation (Leave-Nothing-Out) based approaches, as well as Leave-One-Patient-Out, Leave-One-Cohort-Out, and k-fold (randomized) cross-validations (Image 4, arrow 1). In addition, it is possible to customize this process and generate predictions for individual patients, as well as predefined subcohorts, cohorts, and sets (Image 4, arrow 2).
* Drop down window will allow you to select strategy based on which predictions will be made of. The current selection offers using mean of scores, sum of scores, peak of scores, and peak 5% of scores (Image 4, arrow 3).
* The results can also be post-hoc corrected for group, if that option is selected (Image 4, arrow 4).

## Output

***

* Sweetspots corresponding to improvement.
* Model results.
* Cross-validation correlation plot.

## Publications:

***



## References:

***

> Information on this page was taken from the book"Connectomic Deep Brain Stimulation" by Horn, 2022 and the following research publications:&#x20;
>
> 1. Neudorfer C, Butenko K, Oxenford S, Rajamani N, Achtzehn J, Goede L, Hollunder B, Ríos AS, Hart L, Tasserie J, Fernando KB, Nguyen TAK, Al-Fatly B, Vissani M, Fox M, Richardson RM, van Rienen U, Kühn AA, Husch AD, Opri E, Dembek T, Li N, Horn A. Lead-DBS v3.0: Mapping deep brain stimulation effects to local anatomy and global networks. Neuroimage. 2023 Mar;268:119862. doi: 10.1016/j.neuroimage.2023.119862. Epub 2023 Jan 5. PMID: 36610682; PMCID: PMC10144063.
> 2. Elias, G.J.B., Boutet, A., Joel, S.E., Germann, J., Gwun, D., Neudorfer, C., Gramer, R.M., Algarni, M., Paramanandam, V., Prasad, S., Beyn, M.E., Horn, A., Madhavan, R., Ranjan, M., Lozano, C.S., Kühn, A.A., Ashe, J., Kucharczyk, W., Munhoz, R.P., Giacobbe, P., Kennedy, S.H., Woodside, D.B., Kalia, S.K., Fasano, A., Hodaie, M. and Lozano, A.M. (2021), Probabilistic Mapping of Deep Brain Stimulation: Insights from 15 Years of Therapy. Ann Neurol, 89: 426-443. https://doi.org/10.1002/ana.25975
> 3. Dembek TA, Baldermann JC, Petry-Schmelzer JN, Jergas H, Treuer H, Visser-Vandewalle V, Dafsari HS, Barbe MT. Sweetspot Mapping in Deep Brain Stimulation: Strengths and Limitations of Current Approaches. Neuromodulation. 2022 Aug;25(6):877-887. doi: 10.1111/ner.13356. Epub 2022 Feb 10. PMID: 33476474.
