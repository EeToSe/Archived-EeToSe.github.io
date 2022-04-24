---
layout: default
title: "feature detector"
nav_order: 4
parent: Computer Vision
---
<head>
<meta charset="UTF-8">
  <title>Katex</title>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.css" integrity="sha384-zB1R0rpPzHqg7Kpt0Aljp8JPLqbXI3bhnPWROx27a9N0Ll6ZP/+DiW/UqRcLbRjq" crossorigin="anonymous">
  <script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.js" integrity="sha384-y23I5Q6l+B6vatafAwxRu/0oK/79VlbSz7Q9aiSZUvyWYIYsd+qj+o24G5ZU2zJz" crossorigin="anonymous"></script>
  <script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/contrib/auto-render.min.js" integrity="sha384-kWPLUVMOks5AQFrykwIup5lo0m3iMkkHrD0uJ4H5cjeGihAutqP0yW0J6dpFiVkI" crossorigin="anonymous" onload="renderMathInElement(document.body);"></script>
</head>

# Corner Detection
<p align='center'>
<img src='/assets/image/corner/motivation.png'>
</p>
**Motivation**:  Shifting a window W in any direction should give a large change in intensity.

## Correlation
$$\textbf{f - image, h - kernel} \\$$

$$g=f \otimes h  \quad \textcolor{blue}{\text{cross correlation}}$$<br>

$$g(i, j)=\sum_{k} \sum_{l} f(i+k, j+l) h(k, l)$$<br>

$$g=f \otimes f \quad \textcolor{blue}{\text{auto correlation}}$$<br>

$$g(i, j)=\sum_{k} \sum_{l} f(i+k, j+l) f(k, l)$$<br>

$$g_{N}(i,j) = \frac{\sum_{k} \sum_{l} f(i+k, j+l) h(k, l)} 
{\sqrt{\sum_{k} \sum_{l} f^{2}(i+k, j+l)} {\sqrt{\sum_{k} \sum_{l} h^{2}(k, l)}}} 
\textcolor{blue}{\quad \text{Normalized cross correlation}}$$<br>

$$g_{N}(i,j)$$ is used in **template matching**.

## Summed square difference(SSD)

$$SSD(i,j)=\sum_{k} \sum_{l}(f(i+k, j+l)-h(k, l))^{2} $$ 

$$ SSD(i,j)=\sum_{k} \sum_{l}\left(\cancel{f(i+k, j+l)^{2}}-2 f(i+k, j+l) h(k, l)
        +\cancel{h(k, l)^{2}}\right) \\ 
        = \sum_{k} \sum_{l}(-2 f(i+k, j+l) h(k, l))$$

### Relation between cross correlation and SSD
$$ \mathop{SSD(i,j)}\limits_{minimize} = \sum_{k} \sum_{l}{-2 h(i+k, j+l) f(k, l)} \\
    \text{is \textbf{equal} to} \\
    \mathop{\text{cross correlation(i,j)}} \limits_{maximize} = \sum_{k} \sum_{l} 2 h(i+k, j+l) f(k, l)$$


## Self-difference 
How well does image match shifted version of itself?

Change in appearance of window $$w$$ for the shift $$(u, v)$$:

$$E(u, v)=w(x,y)\sum_{(x, y) \in W}[I(x+u, y+v)-I(x, y)]^{2}$$

First-order Taylor approximation for small shifts $$(u, v)$$ :

$$I(x+u, y+v) \approx \textcolor{red}{I(x, y)+I_{x} u+I_{y} v}$$

Let's plug this into $$E(u, v)$$:

$$E(u, v)\approx w(x,y)\sum_{(x, y) \in W}\left[I(x, y)+I_{x} u+I_{y} v-I(x, y)\right]^{2} \\
=w(x,y)\sum_{(x, y) \in W}\left[I_{x} u+I_{y} v\right]^{2}= w(x,y)\sum_{(x, y) \in W} I_{x}^{2} u^{2}+2 I_{x} I_{y} u v+I_{y}^{2} v^{2}$$

### Second moment matrix

$$E(u, v) \approx w(x,y)(u^{2} \sum_{x, y} \textcolor{red}{I_{x}^{2}}+2 u v \sum_{x, y} \textcolor{red}{I_{x} I_{y}}+v^{2} \sum_{x, y} \textcolor{red}{I_{y}^{2}}) \\
=\left(\begin{array}{ll}u & v\end{array}\right)\left[\textcolor{red}{\begin{array}{cc}w(x,y)\sum_{x, y} I_{x}^{2} & w(x,y)\sum_{x, y} I_{x} I_{y} \\ w(x,y)\sum_{x, y} I_{x} I_{y} & w(x,y)\sum_{x, y} I_{y}^{2}\end{array}}\right]\left(\begin{array}{l}u \\ v\end{array}\right)$$

$$M = \left[\textcolor{red}{\begin{array}{cc}w(x,y)\sum_{x, y} I_{x}^{2} & w(x,y)\sum_{x, y} I_{x} I_{y} \\ w(x,y)\sum_{x, y} I_{x} I_{y} & w(x,y)\sum_{x, y} I_{y}^{2}\end{array}}\right]$$

This matrix is weighted sum of nearby gradient information (could use Gaussian weighting). 

In general, $$M$$ needed to diagonalize:

$$
M=R^{-1}\left[\begin{array}{cc}
\lambda_{1} & 0 \\
0 & \lambda_{2}
\end{array}\right] R
$$

$$\lambda_{1}$$ and $$\lambda_{2}$$ are eigenvalues
- $$\lambda_{1}$$ and $$\lambda_{2}$$ both small: no gradient
- $$\lambda_{1} \gg \lambda_{2}$$ : gradient in one direction
- $$\lambda_{1}$$ and $$\lambda_{2}$$ similarly large: multiple gradient directions, corner
  
### Estimating the smallest eigenvalue
$$\operatorname{det}(M)=\lambda_{1} * \lambda_{2} \\
\operatorname{trace}(\mathrm{M})=\lambda_{1}+\lambda_{2}\\
\operatorname{det}(M)-a \operatorname{trace}(M)=\lambda_{1} \lambda_{2}-\alpha\left(\lambda_{1}+\lambda_{2}\right)^{2}$$ 
If these estimates are large, $$\lambda_{2}$$ is large.

## Harris Corner Detection
1. Compute partial derivatives $$I_{x}$$ and $$I_{y}$$ at each pixel
2. Compute second moment matrix in a Gaussian window around each pixel
3. Compute corner response function $$R=\operatorname{det}(M)-\alpha \operatorname{trace}(M)^{2}$$
4. Threshold $$R$$
5. Find local maxima of response function (NMS)


