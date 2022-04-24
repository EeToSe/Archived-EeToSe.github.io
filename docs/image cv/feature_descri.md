---
layout: default
title: "feature descriptor"
nav_order: 5
parent: Computer Vision
---
<head>
<meta charset="UTF-8">
  <title>Katex</title>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.css" integrity="sha384-zB1R0rpPzHqg7Kpt0Aljp8JPLqbXI3bhnPWROx27a9N0Ll6ZP/+DiW/UqRcLbRjq" crossorigin="anonymous">
  <script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.js" integrity="sha384-y23I5Q6l+B6vatafAwxRu/0oK/79VlbSz7Q9aiSZUvyWYIYsd+qj+o24G5ZU2zJz" crossorigin="anonymous"></script>
  <script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/contrib/auto-render.min.js" integrity="sha384-kWPLUVMOks5AQFrykwIup5lo0m3iMkkHrD0uJ4H5cjeGihAutqP0yW0J6dpFiVkI" crossorigin="anonymous" onload="renderMathInElement(document.body);"></script>
</head>

# feature descriptors
After the [feature detection](https://eetose.github.io/docs/image%20cv/corner/), we need to 

- match image patches to each other
  - what is a patch?
  - How to look for a patch?
  - pixels?
- figure out transform between images
  - how can we transform images?
  - how do we solve for this transformation in given matches?
  
## 2D planar transformations
![png](/assets/image/feature%20descriptor/transformation.jpg)

### Scaling

$$
\mathbf{x}^{\prime}=\mathbf{S} \mathbf{x} \quad \mathbf{x}^{\prime}=\left[\begin{array}{ll}
s & 0 \\
0 & s
\end{array}\right] \mathbf{x}
$$

### Translation

$$
\mathbf{x}^{\prime}=[\mathbf{I} \quad \mathbf{t}] \overline{\mathbf{x}} \\
\mathbf{x}^{\prime}=\left[\begin{array}{ccc}
1 & 0 & t_ \mathbf{x} \\
0 & 1 & t_ \mathbf{y}
\end{array}\right]\left[\begin{array}{l}
\mathbf{x} \\
\mathbf{y} \\
1
\end{array}\right] \\
\text{where } \overline{\mathbf{x}} = [\text{x y 1}]^{t} \text{ :augment vector; } \mathbf{t} \text{: translation matrix.} 
$$

### Euclidean: rotation + translation

$$
\mathbf{x}^{\prime}=\left[\begin{array}{ll}
\mathbf{R} & \mathrm{t}
\end{array}\right] \overline{\mathbf{x}} \\
\text{where } \mathbf{R}=\left[\begin{array}{cc}
\cos \theta & -\sin \theta \\
\sin \theta & \cos \theta
\end{array}\right] \text{ - rotation matrix}
$$

### Similarity: scale, rotate, translate
 
 $$
 \mathrm{x}^{\prime}=\left[\begin{array}{ll}s \mathbf{R} & \mathbf{t}\end{array}\right] \overline{\mathbf{x}}=\left[\begin{array}{ccc}a & -b & t_{x} \\ b & a & t_{y}\end{array}\right] \overline{\mathbf{x}}
 $$

### Affine: scale, rotate, translate, shear

$$
\mathbf{x}^{\prime}=\left[\begin{array}{lll}
a_{00} & a_{01} & a_{02} \\
a_{10} & a_{11} & a_{12}
\end{array}\right]\left[\begin{array}{l}
x \\
y \\
1
\end{array}\right]
$$

## Matching patches: **descriptors**!
Why do we need feature descriptors? What is wrong with distance metric： 

$$\sum_{x,y} [I(x+u, y+v)-I(x, y)]^{2}$$

Just use the pixel values of the patch!
![png](/assets/image/feature%20descriptor/image%20patch.jpg)
Fine iff geometry and appearance is unchanged.



<!--  we must determine which features come from corresponding locations in different images.
Corner detector does not the degree of overlap between two patches. it just look for good corners. -->
