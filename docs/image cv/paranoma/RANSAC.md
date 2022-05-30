---
layout: default
title: "RANSAC"
nav_order: 5
parent: fitting and alignment
grand_parent: Computer Vision
---
# RANSAC
{: no_toc}
Dealing with outliers
{: .fs-6 .fw-300 }

## Example: fitting lines
![png](/assets/image/panorama/RANSAC.png)

## Estimating homography using RANSAC
1. Randomly choose $s$ samples. Typically $s$ is the minimum samples to fit a model.
2. Fit the model to the randomly chosen samples, i.e. compute H.
3. Count inliers that fit the model within a measure of error $\varepsilon$.
4. Repeat Steps $N$ times.
5. Choose the model that has the largest number inliers and recompute H using all inliers.

Where $s=4$ pairs of feature points and $\varepsilon$ is acceptable alignment error in pixels for homography.

## How to choose parameters