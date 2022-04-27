---
layout: default
title: "RANSAC"
nav_order: 4
parent: panorama
grand_parent: Computer Vision
---
<head>
<meta charset="UTF-8">
  <title>Katex</title>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.css" integrity="sha384-zB1R0rpPzHqg7Kpt0Aljp8JPLqbXI3bhnPWROx27a9N0Ll6ZP/+DiW/UqRcLbRjq" crossorigin="anonymous">
  <script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.js" integrity="sha384-y23I5Q6l+B6vatafAwxRu/0oK/79VlbSz7Q9aiSZUvyWYIYsd+qj+o24G5ZU2zJz" crossorigin="anonymous"></script>
  <script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/contrib/auto-render.min.js" integrity="sha384-kWPLUVMOks5AQFrykwIup5lo0m3iMkkHrD0uJ4H5cjeGihAutqP0yW0J6dpFiVkI" crossorigin="anonymous" onload="renderMathInElement(document.body);"></script>
</head>

# RANSAC
{: no_toc}
Dealing with outliers
{: .fs-6 .fw-300 }

## Example: fitting lines
![png](/assets/image/panorama/RANSAC.png)

## Estimating homography using RANSAC
1. Randomly choose $$s$$ samples. Typically $$s$$ is the minimum samples to fit a model.
2. Fit the model to the randomly chosen samples, i.e. compute H.
3. Count inliers that fit the model within a measure of error $$\varepsilon$$.
4. Repeat Steps $$N$$ times.
5. Choose the model that has the largest number inliers and recompute H using all inliers.

For homography:<br>
$$s=4$$ points. $$\quad \varepsilon$$ is acceptable alignment error in pixels.

## How to choose parameters