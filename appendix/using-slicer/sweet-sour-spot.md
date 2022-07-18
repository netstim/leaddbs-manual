# Sweet-sour spot

## Introduction

Some analysis produce an image containing a sweet and sour spot in MNI space. In this example we want to visualize this image with Slicer, together with a reference atlas.

## Go-to approach

The steps to realize this are the following (this is just one way to do it):

1. Load template image (for example t1 MNI image).
2. Load image containing the sweet-sour spot.
3. Set the template as background and sweet-sour as foreground in the viewers.
4. Change the sweet-sour colormap.

With this we come up with something like the following (see included text annotations for some notes on using Slicer):

![](../../.gitbook/assets/Sweet-sour\_01.png)

## Problem

The issue with this approach is that when visualizing images that range from negative to positive values we still see the voxels with value zero, and close to zero. This is usually not the intended purpose when visualizing a sweet-sour image. When thresholding with the GUI in the Volumes module, it is not possible to mask out inner ranges.&#x20;

* Alternative 1: Create an image for the positive values and another one for the negative ones. The problem here is that it is not possible to visualize 3 Volumes (positive, negative and template) at the same time in Slicer.
* Alternative 2: Use the Segment editor to threshold the image and create segmentations of the sweet and sour spots. The problem here is that the segments are seen with one color and not with a gradient indicating the intensity ranges.

## Solution

Here, we will use Slicer's scripting capabilities to customize the range of the image that we see. Select **View -> Python Interactor** to see the python command window. See [Slicer's scripting repository](https://slicer.readthedocs.io/en/latest/developer\_guide/script\_repository.html) to see the interactor capabilities.

#### Imports

```
import slicer 
import numpy as np
```

#### Get image node and array

Set the name of the volume in your scene. Here, it is `'sweet-sour'`.

```
sweet_sour_node = slicer.util.getNode('sweet-sour')
sweet_sour_array = slicer.util.array(sweet_sour_node.GetID())
sweet_sour_array_backup = sweet_sour_array.copy()
```

#### Inner thresholds

The values specified within `[negative_threshold, positive_threshold]` will be masked out.&#x20;

```
negative_threshold = -0.1
positive_threshold = 0.1
```

#### Apply

```
sweet_sour_array[(sweet_sour_array>negative_threshold) & (sweet_sour_array<positive_threshold)] = np.nan
sweet_sour_node.Modified()
```

This will apply the threshold, but we still need to update the display node. This will also set the min/max range to the min/max values of the image.

```
sweet_sour_node.GetDisplayNode().SetApplyThreshold(1)
sweet_sour_node.GetDisplayNode().SetAutoThreshold(slicer.qMRMLVolumeThresholdWidget.Auto)
sweet_sour_node.GetDisplayNode().SetThreshold(np.nanmin(sweet_sour_array),np.nanmax(sweet_sour_array))
```

Now we reached the following:

![](../../.gitbook/assets/Sweet-sour\_02.png)

#### Custom colormap

The following specifies a custom colormap, based on three colors (min, center, max):

```
colorNode = slicer.mrmlScene.AddNewNodeByClass("vtkMRMLProceduralColorNode","MyColormap")
colorNode.SetHideFromEditors(False)
colorMap = colorNode.GetColorTransferFunction()
colorMap.RemoveAllPoints()
colorMap.AddRGBPoint(0.0, 60/255.0, 161/255.0, 244/255.0)
colorMap.AddRGBPoint(0.5, 1.0, 1.0, 1.0)
colorMap.AddRGBPoint(1.0, 237/255.0, 124/255.0, 92/255.0)
sweet_sour_node.GetDisplayNode().SetAndObserveColorNodeID(colorNode.GetID())
```

#### Restore

Use the following to go back to original (and start over if wanted).

```
sweet_sour_array[:] = sweet_sour_array_backup
sweet_sour_node.Modified()
```

## Conclusion

This tutorial shows a way to visualize a sweet-sour image in Slicer while masking out an inner range of the intensity values. Further things can be automatized by scripting in Slicer, like loading the images and saving screenshots (see the [script repository](https://slicer.readthedocs.io/en/latest/developer\_guide/script\_repository.html) for more examples).

Here are all the commands for easier copy-pasting:

```
# Imports
import slicer
import numpy as np

# Get image node and array
sweet_sour_node = slicer.util.getNode('sweet-sour')
sweet_sour_array = slicer.util.array(sweet_sour_node.GetID())
sweet_sour_array_backup = sweet_sour_array.copy()

# Inner thresholds
negative_threshold = -0.1
positive_threshold = 0.1

# Apply
sweet_sour_array[(sweet_sour_array>negative_threshold) & (sweet_sour_array<positive_threshold)] = np.nan
sweet_sour_node.Modified()

sweet_sour_node.GetDisplayNode().SetApplyThreshold(1)
sweet_sour_node.GetDisplayNode().SetAutoThreshold(slicer.qMRMLVolumeThresholdWidget.Auto)
sweet_sour_node.GetDisplayNode().SetThreshold(np.nanmin(sweet_sour_array),np.nanmax(sweet_sour_array))

# Custom colormap
colorNode = slicer.mrmlScene.AddNewNodeByClass("vtkMRMLProceduralColorNode","MyColormap")
colorNode.SetHideFromEditors(False)
colorMap = colorNode.GetColorTransferFunction()
colorMap.RemoveAllPoints()
colorMap.AddRGBPoint(0.0, 60/255.0, 161/255.0, 244/255.0)
colorMap.AddRGBPoint(0.5, 1.0, 1.0, 1.0)
colorMap.AddRGBPoint(1.0, 237/255.0, 124/255.0, 92/255.0)
sweet_sour_node.GetDisplayNode().SetAndObserveColorNodeID(colorNode.GetID())

# Restore
sweet_sour_array[:] = sweet_sour_array_backup
sweet_sour_node.Modified()

```
