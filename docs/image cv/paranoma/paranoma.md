---
layout: default
title: panorama
has_children: true
nav_order: 2
parent: Computer Vision
---

# Image stitching aka panorama

1. Feature detection - detect corners with Harris corner detector.
2. Feature description - SIFT.
3. Match descriptors and homography estimation - simultaneously using RANSAC.
4. Stitch together images with homography
   
{: .no_toc .text-delta }




