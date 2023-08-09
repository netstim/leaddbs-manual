# Fiber Filtering Explorer

{% hint style="warning" %}
This page is currently under construction.
{% endhint %}

## Context

***

* Fiber Filtering Explorer serves to identify tracts associated with observed changes in clinical outcomes. Currently, the tool derives tracts from a structural connectome or using a pathway model.&#x20;
* The tool incorporates two streamlines and OSS-DBS.&#x20;
* The first one uses a combination of binary stimulation volumes and two-sample t-tests. Essentially, the investigated cohort is divided into one group inducing action potentials to streamline and one group having no effect at all.&#x20;
* The second strategy uses E-fields and correlation coefficients. The weight assigned to a streamline is a correlation coefficient of E-field vector magnitude and clinical improvement.&#x20;
* The third, OSS-DBS strategy applies two-sample t-tests, calculating binary tract activation using OSS-DBS. Then, the streamlines are weighted by the clinical outcome of patients touching and not touching the streamline.

{% hint style="info" %}
Fiber Filtering Explorer helps us understand which specific fiber tracts are associated with maximal clinical improvement.
{% endhint %}

## How to

***

### 1. User Interface

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption><p>Image 1. Fiber Filtering Explorer user interface.</p></figcaption></figure>

Fiber Filtering Explorer builds upon [**Lead group**](broken-reference). For this step, all the VTAs/E-fields have to be calculated (press the `Calculate stats & VTA` button in Lead group interface). Click on the `Visualize 3D` button inside Lead group and in the 3D viewer window, click on `Add fiber filtering analysis` button.

<figure><img src="../../.gitbook/assets/image (11).png" alt="" width="56"><figcaption></figcaption></figure>

A new window with Fiber Filtering Explorer user interface pops up. the connectome of your choice from the drop-down selection and press Calculate (Image 1). Once it is done, you will be able to continue with your analysis.

{% hint style="info" %}
In this analysis stream, you have to once calculate tract metrics for any combination of normative connectomes and statistical metrics. Once this is done, you can explore the results more or less "live."
{% endhint %}

{% hint style="info" %}
The time it takes to calculate connected fiber tracts depends on your sample size, normative connectome, or your computer.
{% endhint %}

### 2. Model Setup

<figure><img src="../../.gitbook/assets/image (12).png" alt="" width="356"><figcaption><p>Image 2. Fiber Filtering Explorer Interactive Model Setup options window.</p></figcaption></figure>

Model Setup (Image 1, arrow 1) allows you to define methods and parameters to generate the computational model. You can determine subcohort selection, dependent variable selection, covariates, statistical tests, an option to mirror VTAs/Efields (Image 2, arrows 1-9).

#### 2.1 Model Setup Options

<details>

<summary>Two_Sample T-Test / VTAs (Baldermann 2019) / PAM (OSS DBS)</summary>



</details>

<details>

<summary>One-Samplte Tests / VTAs / PAM (OSS-DBS)</summary>



</details>

<details>

<summary>Correlations / E-Fields (Irmen 2020)</summary>



</details>

<details>

<summary>Proportion Test (Chi-Square) / VTAs (binary vars)</summary>



</details>

<details>

<summary>Binomial Tests / VTAs (binary vars)</summary>



</details>

<details>

<summary>Reverse T-Test / E-Fields (binary vars)</summary>



</details>

<details>

<summary>Plain Connections</summary>



</details>



`Tracts connected if peak E-Field Magnitude they traverse is > … V/mm` ...

`Tracts connected to > … % of E-Fields` <mark style="color:blue;">…</mark>

`Variable of interest` (VOI) is the dependent variable, such as clinical score (Image 2, arrow 2). This variable can also be cleaned from covariates (Image 2, arrow 8).

Subcohorts can be created by selecting patients in the bottom window this selection can be saved by clicking on Subcohorts (Image 2, arrow 5) and selecting one of the options: `Create Subcohort from Selection` or `Create Subcohort from Inverse Selection`.

If `Mirror VTAs/Efields` box is selected (Image 2, arrow 9), VTAs/Efields from one hemisphere will also be used for the second hemisphere (mirroring the effect).

`VTAs show (Figure 2, arrow 6)` ...

`Connected Fibers Show (Figure 2, arrow 7)` ...

### 3. Visualisation & Thresholding

<figure><img src="../../.gitbook/assets/image (13).png" alt="" width="375"><figcaption><p>Image 3. Fiber Filtering Explorer Visualization &#x26; Thresholds window.</p></figcaption></figure>

The tool allows you to visualize the fibers, as it is essential to check whether they make sense anatomically. You can include only significant fibers in your analysis, by ticking `Consider Significant Fibers only`(Figure 3, arrow 1) and als othe correction strategy (Fiure 3, arrow 2). You can also select different types of thresholding for the fibers, set to `Show Negative Fibers` or `Show Positive Fibers` and also set `Fixed Amount` of positive and negative fibers (Figure 3, arrow 4).

The model you selected can also be exported: `Export as Atlas` or `Export Model` (Figure 3, arrow 6).

After you select all the settings, press `Refresh View` or alternatively, tick the `Auto-Refresh` box that will refresh the view automatically (Figure 3, arrow 7).

### 4. Crossvalidation & Prediction

<figure><img src="../../.gitbook/assets/image (14).png" alt="" width="375"><figcaption><p>Image 4. Fiber Filtering Explorer Crossvalidation &#x26; Prediction window.</p></figcaption></figure>

The final step across frameworks is Crossvalidation & Prediction (Image 1, red arrow 3). This step is crucial to establish the validity of generated models within and generalizability across cohorts. Current validation strategies include permutation (Leave-Nothing-Out) based approaches, as well as Leave-One-Patient-Out, Leave-One-Cohort-Out, and k-fold (randomized) cross-validations (Image 4, arrow 1). In addition, it is possible to customize this process and generate predictions for individual patients, as well as predefined subcohorts, cohorts, and sets (Image 4, arrow 2).

`Model Normalization` allows you to select a z-score method or von Albada 2007 method (Figure 4, arrow 3).&#x20;

Base Prediction on (Figure 4, arrow 4):&#x20;

<details>

<summary>Mean of Scores</summary>



</details>

<details>

<summary>Sum of Scores</summary>



</details>

<details>

<summary>Peak of Scores/Peak 5% of Scores</summary>



</details>

<details>

<summary>Histogram/Z-scored Histogram</summary>



</details>

At last, data can be fit to scores and post-hoc corrected for groups (Figure 4, arrow 5).

### 5. Multitract Analysis



## Output

***

## Publications:

***

## References:

> Information on this page was taken from the book "Connectomic Deep Brain Stimulation" by Horn, 2022 and the following research publication:
>
> * Neudorfer C, Butenko K, Oxenford S, Rajamani N, Achtzehn J, Goede L, Hollunder B, Ríos AS, Hart L, Tasserie J, Fernando KB, Nguyen TAK, Al-Fatly B, Vissani M, Fox M, Richardson RM, van Rienen U, Kühn AA, Husch AD, Opri E, Dembek T, Li N, Horn A. Lead-DBS v3.0: Mapping deep brain stimulation effects to local anatomy and global networks. Neuroimage. 2023 Mar;268:119862. doi: 10.1016/j.neuroimage.2023.119862. Epub 2023 Jan 5. PMID: 36610682; PMCID: PMC10144063.

***
