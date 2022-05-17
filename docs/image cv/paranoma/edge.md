---
layout: default
title: edge detection
nav_order: 1
parent: fitting and alignment
grand_parent: Computer Vision
---
<!-- <head>
<meta charset="UTF-8">
  <title>Katex</title>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.css" integrity="sha384-zB1R0rpPzHqg7Kpt0Aljp8JPLqbXI3bhnPWROx27a9N0Ll6ZP/+DiW/UqRcLbRjq" crossorigin="anonymous">
  <script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.js" integrity="sha384-y23I5Q6l+B6vatafAwxRu/0oK/79VlbSz7Q9aiSZUvyWYIYsd+qj+o24G5ZU2zJz" crossorigin="anonymous"></script>
  <script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/contrib/auto-render.min.js" integrity="sha384-kWPLUVMOks5AQFrykwIup5lo0m3iMkkHrD0uJ4H5cjeGihAutqP0yW0J6dpFiVkI" crossorigin="anonymous" onload="renderMathInElement(document.body);"></script>
</head> -->

# Edge Detection

## Edge detection using gradients
An edge is a place of rapid change in the image intensity 
function.

### Partial derivatives of an image
for 2D function $f(x, y)$, the partial derivative w.r.t. $x$ is <br>

$$\frac{\partial f(x, y)}{\partial x}=\lim _{\varepsilon \rightarrow 0} \frac{f(x+\varepsilon, y)-f(x, y)}{\varepsilon}$$

For **discrete data**, we can approximate using finite differences: <br>

$$\frac{\partial f(x, y)}{\partial x}=\frac{f(x+1, y)-f(x, y)}{1}$$

### Gradient: local extrema
$\bigtriangledown f =  (\frac{\partial f}{\partial x}, \frac{\partial f}{\partial y})$, pronounced as **Del**

<img src='/assets/image/edge_files/gradient.jpg'>

### Gradient Operators
<img src='/assets/image/edge_files/operator.jpg'>
Kernel size affects localization and noise sensitive.

## Laplacian($\bigtriangledown^{2}$) as edge detector: zero-crossings
<!-- <img src='/assets/image/edge_files/laplacian.jpg'> -->

$$\bigtriangledown^{2} f = \frac{\partial^{2} f}{\partial x^{2}}+\frac{\partial^{2} f}{\partial y^{2}}$$

### Code Explanation
```python
import cv2
import numpy as np
from matplotlib import pyplot as plt
from skimage import io as io_url
from func.mysubplot import mysubplot
from func.canny import non_max_suppression, double_threshold, hysteresis,sobel_filter,canny_detector
```


```python
frame = io_url.imread('images/scotty.jpg', as_gray=True)
k = 7 # Kernel size

sobel_x = cv2.Sobel(frame,-1,1,0,ksize=k)
sobel_y = cv2.Sobel(frame,-1,0,1,ksize=k)
magnitude = np.sqrt(sobel_x**2 + sobel_y**2)
orientation = np.arctan2(sobel_y, sobel_x) * (180 / np.pi) % 180
laplacian = cv2.Laplacian(frame,-1,ksize=k)

data = 255*magnitude/magnitude.max()
data = data.astype(np.uint8)
ret,th = cv2.threshold(data,0,255,cv2.THRESH_BINARY+cv2.THRESH_OTSU)
```

Use [my subplot function](https://github.com/EeToSe/image-cv/blob/main/cmu_cv/func/mysubplot.py) to show all the results.

```python
fig = plt.subplots(nrows=2, ncols=3, figsize=(16, 8))
titles = ['Original','Sobel X','Sobel Y','Gradient Magnitude','Gradient Magnitude after otsu thresholding','Laplacian']
images = [frame, np.abs(sobel_x)/np.abs(sobel_x).max(), np.abs(sobel_y)/np.abs(sobel_y).max(), magnitude/magnitude.max(), th, laplacian]
mysubplot(images, titles, 2, 3)
```


![png](/assets/image/edge_files/edge_9_0.png)

### Threshold after gradient operations
The otsu thresholoding and other thresholding approaches could see this page 

### Derivative of Gaussian (DoG)
#### image corrupted by additive Gaussian noise
<img src='/assets/image/edge_files/DoG_noise.jpg'>

#### Smooth by gaussian filter
<img src='/assets/image/edge_files/DoG.png'>
Take derivatives of Gaussian filtered image = apply DoG to image directly

#### Gaussian vs DoG
Gaussian:
- remove “high-frequency” components;  “low-pass” filter
- Can the weights' values of a smoothing filter be negative? No
- The values sum to **One**: constant regions are not affected by the filter

DoG:
- Can the values of a derivative filter be negative?
- Can the weights' values of a smoothing filter be negative? Yes
- The values sum to **Zero**: no response in constant regions

## Canny Edge Detector
A step-by-step [link](https://towardsdatascience.com/canny-edge-detection-step-by-step-in-python-computer-vision-b49c3a2d8123),  [source code](https://github.com/EeToSe/image-cv/blob/main/cmu_cv/func/canny.py) implemented.
- Noise reduction using Gaussian filter
- Gradient calculation
- Non-maximum suppression: thin the edges
- Double threshold: weak, strong and uncertain positions
- Edge Tracking by Hysteresis: are uncertain connnected with strong positions?

```python
mag_thin = non_max_suppression(magnitude, angle)
t = 0.09
mag_th = double_threshold(mag_thin, t, 2*t)
res = canny_detector(frame, t, 2*t)

frame = 255*frame/frame.max()
edges = cv2.Canny(frame.astype('uint8'),60,120)

fig = plt.subplots(nrows=2, ncols=2, figsize=(8, 16))
titles = ['non maximum suppression','double thresholding', 'hysteresis', 'opecv canny']
images = [mag_thin, mag_th, res, edges]
mysubplot(images, titles, 2, 2)
```
<img src='/assets/image/edge_files/canny.png'>
    

