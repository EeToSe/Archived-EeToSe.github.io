---
layout: default
title: "stitching"
nav_order: 6
parent: fitting and alignment
grand_parent: Computer Vision
---

## Keypoint Detector

### The DoG Pyramid
```python
np.stack 
np.split 
np.concatenate
```
###  Edge Suppression
 the principal curvature ratio in a local neighborhood of a point

## elimination of visible seams
For overlapping pixels, it is common to blend the values of both images. You can
simply average the values but that will leave a seam at the edges of the overlapping
images. Alternatively, you can obtain a blending value for each image that fades one
image into the other