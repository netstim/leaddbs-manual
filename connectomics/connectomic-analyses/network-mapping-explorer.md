# Network Mapping Explorer

{% hint style="warning" %}
This page is currently under construction.
{% endhint %}

## Context

***

* Network Mapping Explorer can be used to associate observed effects with distributed functional or structural brain networks. This effect could be e.g. clinical (e.g. %-UPDRS-III improvement following STN-DBS) or behavioral (e.g. change in risk-taking behavior or movement speed in a motor task).
* The connectivity profiles (fingerprints) are calculated seeding from active DBS contacts, volume of tissue activated, or estimated electric field. Connectivity estimates can be calculated for each voxel in the brain (sometimes referred to as a voxel-wise parcellation) or to a specific set of larger brain regions.
* Derivation of these estimates involves projections to the cortical surface and calculation of cortico-subcortical connectivity strength by means of voxel-wise correlation.

## How to

***

### 1. User Interface

<figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption><p><em>Image 1. Network Mapping Explorer user interface.</em></p></figcaption></figure>

Network Mapping Explorer builds upon [**Lead group**](../../lead-group/group-analyses-with-lead-dbs.md). For this step, all the VTAs/E-fields have to be calculated (press the `Calculate stats & VTA` button in Lead group interface). Click on the `Visualize 3D button` inside Lead group and in the 3D viewer window, click on `Add DBS network mapping analysis` button.

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption><p>Network Mapping Explorer icon.</p></figcaption></figure>

A new window with Network Mapping Explorer user interface pops up. Connectivity fingerprints have to be calculated in the first step. Select the Connectome of your choice from the drop-down selection and press `Calculate` (Image 1). Once it is done, you will be able to continue with your analysis.

{% hint style="info" %}
Time it takes to calculate connectivity fingerprints depends on your sample size, normative connectome, or your computer. This step, therefore, may take a few minutes, but also days.
{% endhint %}

{% hint style="info" %}
In this analysis stream, you have to once calculate connectivity fingerprints for any combination of normative connectomes and statistical metric. Once this is done, you can explore the results more or less "live.
{% endhint %}

The resulting connectivity fingerprints can be seen as estimates of how the DBS electrodes are connected to other areas of the brain. However, the noninvasive methods used to derive them have strong limitations and a multitude of inherent problems and therefore, results should be interpreted with caution.

### 2. Model Setup

<figure><img src="../../.gitbook/assets/image (3) (1).png" alt="" width="375"><figcaption><p>Image 2. Network Mapping Explorer Interactive Model Setup options window.</p></figcaption></figure>

* `Model Setup` (Image 1, arrow 1) allows you to define methods and parameters to generate the computational model. You can define subcohort selection, dependent variable selection, covariates, statistical tests, option to mirror VTAs/Efields (Image 2, arrows 1-8).
* Model options can be selected in the drop-down menu (Image 2, arrow 1). For more information consult the following section [**2.1 Model Setup Options**](network-mapping-explorer.md#2.1-model-setup-options-image-2-arrow-1) below.
* `Variable of interest (VOI)` is the dependent variable, such as clinical score (Image 2, arrow 2). This variable can also be cleaned from covariates (Image 2, arrow 3).
* `Subcohorts` can be created by selecting patients in the bottom window (Image 2, arrow 6), this selection can be saved by clicking on `Subcohorts` (Image 2, arrow 4) and selecting one of the options: `Create Subcohort from Selection` or `Create Subcohort from Inverse Selection.`
* If `Mirror VTAs/Efields` box is selected (Image 2, arrow 5), VTAs/Efields from one hemisphere will also be used for the second hemisphere (mirroring the effect).
* The connectivity fingerprints can also be `smoothed` to avoid the “patchy” image (Image 2, arrow 7), as well as `normalized` so the peak voxel values are comparable across patients (Image 2, arrow 8).

#### 2.1 Model Setup Options:

* One of the following model options can be selected:

<details>

<summary>Correlations (Horn 2017)</summary>

Correlation maps model constitutes a model of optimal connectivity. For each patient, each voxel has a correlation value represented as a single scalar. Each patient also has a dependent variable assigned, such as clinical improvement. Averaging correlation values for this specific voxel and the dependent variable across patients results in a correlation map (Image below).

<img src="../../.gitbook/assets/image (6) (1).png" alt="" data-size="original">

_Image 2.1 Calculating correlation maps, adapted from Horn, 2022._

</details>

<details>

<summary>Weighted Average (Horn 2017)</summary>

In Weighted Average maps, the correlation value assigned to a specific voxel for each patient is multiplied by patient’s improvement. The results are summarised resulting in one map. In clinical settings, voxels associated with higher improvement would have higher resulting value.

<img src="../../.gitbook/assets/image (7).png" alt="" data-size="original">

_Image 2.2 Calculating weighted average maps, adapted from Horn, 2022._

</details>

<details>

<summary>Combined Map (Horn 2017)</summary>

The Combined Map combines Correlation and Weighted average results. The respective values for each voxel are first multiplied, and then, only positive or negative voxels in both maps are kept in the weighted average map. The rest is turned to "NaN' values.



</details>

<details>

<summary>Thresholded N-map (Boes 2015)</summary>

Using this method, a summary of voxels negatively correlated with VTA/E-Fields below a certain threshold are subtracted from the summary of voxels that are positively correlated with the VTA/E-Fields above certain threshold. This way, voxels out of interest are eliminated from the analysis.

</details>

<details>

<summary>One Sample T-Test</summary>

One sample t-test is used to generalize our results to the population, hence whether the brain areas correlated with the VTA/E-Fields would be observed in population. For these purposes, one-sample t-test is run for the correlation values associated with each voxel across the sample.

</details>

<details>

<summary>Two Sample T-Test</summary>

Two sample t-test is used to compare results between two groups. Lead-DBS allows you to select two cohorts to compare to, for example patients with high versus patients with low improvement. For these purposes, Lead-DBS runs independent-samples t-test.

</details>

### 3. Visualisation & Thresholding

<figure><img src="../../.gitbook/assets/image (4) (1).png" alt="" width="563"><figcaption><p>Image 3. Network Mapping Explorer Visualization &#x26; Thresholds window.</p></figcaption></figure>

* Generated model can be visualized and further adjusted during `Visualization & Thresholding` (Image 1, red arrow 2). Specifically, this step allows thresholding of the generated maps based on a predefined alpha-level and correction for multiple comparison (Image 3, arrows 1&2).
* You can select to `show voxels` positively or negatively correlated with your selected dependent variable (Image 3, arrow 3), as well as their respective color (Image 3, arrow 5). The surface to visualize on and further smoothing of the resulting model can also be selected (Image 3, arrow 4).
* For more advanced post-hoc analysis, the option to export the generated maps in the form of NIfTI files is also available, by ticking the box `Export as NIfTI` (Image 3, arrow 6).
* After you select all the settings, press `Refresh View` or alternatively, tick the `Auto-Refresh` box that will refresh the view automatically.

### 4. Crossvalidation & Prediction

<figure><img src="../../.gitbook/assets/image (5) (1).png" alt="" width="329"><figcaption><p>Image 4. Network Mapping Explorer Crossvalidation &#x26; Prediction window.</p></figcaption></figure>

* The final step across frameworks is `Crossvalidation & Prediction` (Image 1, red arrow 3). This step is crucial in establishing the validity of generated models within and generalizability across cohorts. Current validation strategies include permutation (Leave-Nothing-Out) based approaches, as well as Leave-One-Patient-Out, Leave-One-Cohort-Out, and k-fold (randomized) cross-validations (Image 4, arrow 1). In addition, it is possible to customize this process and generate predictions for individual patients, as well as predefined subcohorts, cohorts, and sets (Image 4, arrow 2).
* Drop down window allows you to select the type of spatial correlation on which to select similarity between training and test datasets (Spearman, Pearson, Bend) (Image 2, arrow 3). Mask can be applied, by selecting one of the predefined masks (Gray Matter, Brain, Cortex & Cerebellum, Cortex, Cerebellum, Custom Image, Custom Equation, Gray Matter) (Image 4, arrow 4). Applying the mask during cross-validation means that only voxels located within that brain structure will be considered for crossvalidations. For example, using Cerebellum as a mask will keep voxel correlation values associated with cerebellum unchanged, but other voxels, such as voxels in cortex, or striatum will be set to NaN. If Custom Image is selected, UI accepts data in a .nii format and in the same space dimensions as the connectivity fingerprints.
* Individual fingerprints can also be exports by ticking the box `Export Models as NIfTI` (Image 4, arrow 5).
* After pressing `Run`, cross-validations will run automatically and return a graph with the clinical improvement on the x-axis and the network score on the y-axis.&#x20;

## Output

***

* Connectivity fingerprints.&#x20;
* Model results.&#x20;
* Cross-validation correlation results.

## Publications:

***

> 1.  Hollunder, B. _et al._ (2022) ‘Toward personalized medicine in connectomic deep brain stimulation’, _Progress in Neurobiology_, 210, p. 102211. Available at: https://doi.org/10.1016/j.pneurobio.2021.102211.
>
>
> 2.  Horn, A. _et al._ (2022) ‘Optimal deep brain stimulation sites and networks for cervical vs. generalized dystonia’, _Proceedings of the National Academy of Sciences_, 119(14), p. e2114985119. Available at: https://doi.org/10.1073/pnas.2114985119.
>
>
> 3.  Neudorfer, C. _et al._ (2023) ‘Lead-DBS v3.0: Mapping deep brain stimulation effects to local anatomy and global networks’, _NeuroImage_, 268, p. 119862. Available at: https://doi.org/10.1016/j.neuroimage.2023.119862.
>
>
> 4.  Ríos, A.S. _et al._ (2022) ‘Optimal deep brain stimulation sites and networks for stimulation of the fornix in Alzheimer’s disease’, _Nature Communications_, 13, p. 7707. Available at: https://doi.org/10.1038/s41467-022-34510-3.
>
>
> 5. Sobesky, L. _et al._ (2021) ‘Subthalamic and pallidal deep brain stimulation: are we modulating the same network?’, _Brain_, 145(1), pp. 251–262. Available at: https://doi.org/10.1093/brain/awab258.

## References:

***

> Information on this page was taken from the book"Connectomic Deep Brain Stimulation" by Horn, 2022 and the following research publication:
>
> 1. &#x20;Neudorfer C, Butenko K, Oxenford S, Rajamani N, Achtzehn J, Goede L, Hollunder B, Ríos AS, Hart L, Tasserie J, Fernando KB, Nguyen TAK, Al-Fatly B, Vissani M, Fox M, Richardson RM, van Rienen U, Kühn AA, Husch AD, Opri E, Dembek T, Li N, Horn A. Lead-DBS v3.0: Mapping deep brain stimulation effects to local anatomy and global networks. Neuroimage. 2023 Mar;268:119862. doi: 10.1016/j.neuroimage.2023.119862. Epub 2023 Jan 5. PMID: 36610682; PMCID: PMC10144063.
