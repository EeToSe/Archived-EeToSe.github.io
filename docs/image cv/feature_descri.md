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

### <a name="translation"></a> Translation

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

### Similarity: scale + rotate + translate
 
 $$
 \mathrm{x}^{\prime}=\left[\begin{array}{ll}s \mathbf{R} & \mathbf{t}\end{array}\right] \overline{\mathbf{x}}=\left[\begin{array}{ccc}a & -b & t_{x} \\ b & a & t_{y}\end{array}\right] \overline{\mathbf{x}}
 $$

## Homogeneous Coordinates (齐次坐标)
Or projective coordinate, homogeneous is damn confusing terminology. <br>
Excellent videos: [Projective geometry](https://www.youtube.com/watch?v=NYK0GBQVngs) provided by [NJ Wildberger](https://web.maths.unsw.edu.au/~norman/), **UNSW** Prof！
### Why we bring in this?
Concepts first introduced in [translation](#translation) where $$\overline{\mathbf{x}} = (x, y, 1)$$ is the augmented vector. <br>

![png](/assets/image/feature%20descriptor/pinhole.png) <br> 
Consequences of such projection could see the below picture.<br>
![png](/assets/image/feature%20descriptor/consequence.png)
1. Farther away objects are smaller $$\frac{Y+h}{Z} - \frac{Y}{Z} = \frac{h}{Z}$$
2. Parallel lines converge at a point.
3. Parallel planes converge! *消失的地平线*

### Cartesian -> Homogeneous
We can only understand the 2D projection in the 3D homogeneous coordinate.
<p align = "center">
<img src="/assets/image/feature%20descriptor/homo.png" alt="hi" class="inline"/><br>
<em>Cartesian plane overlaid in the homogeneous coordinate</em>
</p>

The $$\textcolor{orange}{homogenous}$$(scale invariant) representation of a 2D point $$ \mathbf{x} = (x,y)$$ is a line L from origin through $$\widetilde{\mathbf{x}} = (\widetilde{x}, \widetilde{y}, \widetilde{z})$$. The third coordinate $$\widetilde{z}$$ is fictitious(虚构) such that:

$$\mathbf{\widetilde{x}} \equiv\left[\begin{array}{c}
\widetilde{x} \\
\widetilde{y} \\
\widetilde{z}
\end{array}\right] \equiv  \left [\begin{array}{c}
\frac{\tilde{x}}{\tilde{z}} \\
\frac{\tilde{y}}{\tilde{z}} \\
1
\end{array}\right] \Rightarrow {\mathbf{x}} = \left[\begin{array}{l}
\frac{\tilde{x}}{\tilde{z}} \\
\frac{\tilde{y}}{\tilde{z}}
\end{array}\right] = 
\left[\begin{array}{l} x\\ y \end{array}\right]
$$
(In case $$\tilde{z}=0$$ "point at infinity")<br>
$$\textcolor{red}{Insights}$$: Transform $$\mathbf{homogenous}$$ (scale invariant) 3D coordinates to ordinary cartesian 2D. <br>
The $$\textcolor{orange}{homogenous}$$ representation of a 2D line:

$$
\mathbf{\widetilde{x} \cdot \mathbf{\widetilde{l}} = ax+by+c=0} 
$$

Where $$\mathbf{\widetilde{l}=(a,b,c)}$$ could be normalized as $$\mathbf{\widetilde{l}=(\mathbf{n}, d)}$$
<p align = "center">
<img src="/assets/image/feature%20descriptor/line.jpg" alt="hi" class="inline"/><br>
<em>2D line equation</em>
</p>

### Review of transformations in homogeneous coordinates
$$
\begin{aligned}
&{\left[\begin{array}{c}
\tilde{x} \\
\tilde{y} \\
\tilde{z}
\end{array}\right]=\left[\begin{array}{ccc}
s & 0 & 0 \\
0 & s & 0 \\
0 & 0 & 1
\end{array}\right]\left[\begin{array}{c}
x \\
y \\
1
\end{array}\right] \quad\left[\begin{array}{c}
\tilde{x} \\
\tilde{y} \\
\tilde{z}
\end{array}\right]=\left[\begin{array}{ccc}
1 & 0 & t_{x} \\
0 & 1 & t_{y} \\
0 & 0 & 1
\end{array}\right]\left[\begin{array}{c}
x \\
y \\
1
\end{array}\right]} \\
&\quad\quad\quad\quad\quad\quad\text {Scaling \quad\quad\quad\quad\quad\quad\quad\quad\quad\quad Translation} \\
&{\left[\begin{array}{c}
\tilde{x} \\
\tilde{y} \\
\tilde{z}
\end{array}\right]=\left[\begin{array}{ccc}
\cos \theta & -\sin \theta & 0 \\
\sin \theta & \cos \theta & 0 \\
0 & 0 & 1
\end{array}\right]\left[\begin{array}{c}
x \\
y \\
1
\end{array}\right] \quad\left[\begin{array}{c}
\tilde{x}_{2} \\
\tilde{y}_{2} \\
\tilde{z}_{2}
\end{array}\right]=\left[\begin{array}{ccc}
a & -b & t_{x} \\
b & a & t{y} \\
0 & 0 & 1
\end{array}\right]\left[\begin{array}{c}
x_{1} \\
y_{1} \\
1
\end{array}\right]} \\
&\quad\quad\quad\quad\quad\quad\quad\quad\text {Rotation \qquad\qquad\qquad\qquad\qquad\qquad\qquad Similarity} 
\end{aligned}
$$
### Affine: combinations of above are still affine

$$
\mathbf{x}^{\prime}=\left[\begin{array}{ccc}
a_{11} & a_{12} & a_{13} \\
a_{21} & a_{22} & a_{23} \\
0 & 0 & 1
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
