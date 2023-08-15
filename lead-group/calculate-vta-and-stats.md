# Calculate VTA and Stats

To Calculate stats and VTA, click "Calculate stats & VTA" in the main GUI.&#x20;

<figure><img src="../.gitbook/assets/calculatestats.png" alt=""><figcaption></figcaption></figure>

This will calculate the VTAs and electrical fields for both hemispheres for each patient, in native and in MNI space. The generated files will be stored under "stimulations" folder of each patient. An example of the folder structure is displayed below:

<figure><img src="../.gitbook/assets/Screen Shot 2023-08-14 at 22.35.44.png" alt=""><figcaption></figcaption></figure>

## Explore Stats

After calculating VTA and stats, Lead Group provides statistical tests for group comparison. It is possible to see which electrode contacts reside within an anatomical atlas structure, to calculate the distance of contacts to an anatomical atlas structure, to generate correlation plots between a clinical variable and the intersection of contacts with a structure.

![](<../.gitbook/assets/Screen Shot 2023-08-15 at 11.28.52.png>)Figure 3: Explore Stats

### Calculate Distance Between VTA and an Anatomical Atlas Structure

1. Click "Explore Stats" under Calculate Stats & VTA section in the main GUI.
2. From the window that pops up(Fig.3), choose the subcortical region you're interested in. <mark style="background-color:yellow;">If the structure you're interested in is not on the list, you can change the subcortical atlas from the main GUI under "General Settings."</mark>
3. From the "Activated regions" menu, choose VTAs or E-fields.&#x20;
4. Click on "Generate Target Report". From the pop-up window, select the threshold you want to use in mm's.
5. Two windows will pop up, one showing the distances of electrode centers to the nearest voxel of the target and one showing electrode centers residing in the target structure based on the selected threshold. <mark style="background-color:red;">Active contacts</mark> will be highlighted in <mark style="background-color:red;">red.</mark>

<figure><img src="../.gitbook/assets/Screen Shot 2023-08-15 at 11.29.06.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Since the distance to the closest voxel of a target is rendered, **even if the electrode contact is in the middle of the target structure, the distance to the shell of the target will be listed**. Thus, a visual check of the contact positions is recommended!
{% endhint %}

### Correlate Variable and VTA Intersection

1. Click "Explore Stats" under Calculate Stats & VTA section in the main GUI.&#x20;
2. From the window that pops up(Fig.3), choose the variable and subcortical region of your interest. If the structure you're interested in is not on the list, you can change the subcortical atlas from the main GUI under "General Settings."&#x20;
3. From the "Activated regions" menu, choose VTAs or E-fields.
4. Click on "Correlate Variable and VTA Intersection". This will generate correlation plots(Fig. 4), showing the correlation between VTA and target intersection and the clinical variable of choice.

<figure><img src="../.gitbook/assets/Screen Shot 2023-08-15 at 11.31.06.png" alt=""><figcaption><p>Figure 4</p></figcaption></figure>

