---
layout: default
title: threshold
nav_order: 2
parent: Computer Vision
---
<head>
<meta charset="UTF-8">
  <title>Katex</title>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.css" integrity="sha384-zB1R0rpPzHqg7Kpt0Aljp8JPLqbXI3bhnPWROx27a9N0Ll6ZP/+DiW/UqRcLbRjq" crossorigin="anonymous">
  <script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.js" integrity="sha384-y23I5Q6l+B6vatafAwxRu/0oK/79VlbSz7Q9aiSZUvyWYIYsd+qj+o24G5ZU2zJz" crossorigin="anonymous"></script>
  <script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/contrib/auto-render.min.js" integrity="sha384-kWPLUVMOks5AQFrykwIup5lo0m3iMkkHrD0uJ4H5cjeGihAutqP0yW0J6dpFiVkI" crossorigin="anonymous" onload="renderMathInElement(document.body);"></script>
</head>


# Threshold methods

## OTSU ([code](https://github.com/EeToSe/image-cv/blob/main/cmu_cv/func/otsu.py) implementation)
- Minimize the intra-class variance
- Or Maximize the inter-class variance 
 
$$ \sigma^{2}_{b}(t) = w_{0}(t)w_{1}(t)[\mu_{0}(t) - \mu_{1}(t) ]^{2} $$

- t - variant threshold, dividing the image intensity pixels into two classes - background and foreground;
- $$w_{0,1}(t)$$ - class probability;
- $$\mu_{0,1}(t)$$ - mean intensity of the class;
