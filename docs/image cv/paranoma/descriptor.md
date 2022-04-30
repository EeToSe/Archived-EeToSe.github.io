---
layout: default
title: "feature descriptor"
nav_order: 3
parent: fitting and alignment
grand_parent: Computer Vision
---

## Matching patches: **descriptors**!
Why do we need feature descriptors? What is wrong with distance metric： 

$$\sum_{x,y} [I(x+u, y+v)-I(x, y)]^{2}$$

Just use the pixel values of the patch!
![png](/assets/image/panorama/image%20patch.jpg)
Fine iff geometry and appearance is unchanged.


<!--  we must determine which features come from corresponding locations in different images.
Corner detector does not the degree of overlap between two patches. it just look for good corners. -->