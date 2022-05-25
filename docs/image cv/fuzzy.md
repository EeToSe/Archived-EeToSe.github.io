---
layout: default
title: fuzzy logic
# nav_order: 2
parent: Computer Vision
---
# Fuzzy logic theory
This is a large section, we only discuss rule-based techniques in this blog. <br>
More should refer to this book: Fuzzy techniques in image processing.

---

## Fuzzy set
- A fuzzy set $A \subset Z$ is characterized by a membership function $\mu_{A}(z)$. <br> (e.g. Z is all men; A is yong men).
- A fuzzy set is an ordered pair: $A_{fuzzy} = \{(z, \mu_{A}(z)) \mid z \in Z, \mu_{A}(z) \in [0,1] \}$
- Membership function $\mu_{A}(z)$ quantifies the degree of $z$ in $A$.

## Fuzzy Rule Base and Inference Engine
Approximate an unknown I/O mapping by inference from a set of fuzzy rules (**IF-THEN**).

![](/assets/image/fuzzy/scheme.jpg)<br>
<em> General scheme of a fuzzy inference system</em>

**The fuzzy inference engine** combines the rules in the rule base according to approximate reasoning theory to produce 
a mapping from fuzzy sets in the input space to fuzzy sets in the output space.

$R_{k} \text{: IF (x is } A_{k}) \text{ THEN (y is } B_{k})$

## General Steps
1. **Fuzzify the inputs** <br> map membership value([0,1]) to each pixel by the membership function.
2. **Fuzzy logical operations** <br> combine the outputs of all *IF* operators to a single value using the appropriate logic.
3. **Apply an implication method** <br> clip each fuzzy output of according to the result of *step2*.
4. **Aggregation method to the clipped output fuzzy sets** <br> combine the output of each fuzzy rule.
5. **Defuzzify the final output fuzzy set** <br> e.g. center of gravity.
   
---
Applications as [homework](https://github.com/EeToSe/image-cv/blob/main/image_analysis/data/ass2/fuzzy%20methods%20experiment.pdf) and [solution](/assets/algorithm/ass2-solution.pdf)

## Contrast enhancement

<p align = "center">
<img src="/assets/image/fuzzy/member.png" alt="hi" class="inline" width="300"/>
<img src="/assets/image/fuzzy/einstein.png" alt="hi" class="inline" width="500"/> <br>
<em>Look at gray hair and crossed fingers</em>
</p>

$$ v_{0} = \frac{\mu_{dark}(z_{0})\times v_{d} + \mu_{gray}(z_{0})\times v_{g} + \mu_{bright}(z_{0})\times v_{b}}{\mu_{dark}(z_{0})+\mu_{gray}(z_{0})+\mu_{bright}(z_{0})}$$

## Boundary extraction
**Step 1**: Define input and output membership functions
![png](/assets/image/fuzzy/step1.png) 
**Step 2-4**: rule 1 and overall membership function
```python
mu1 = np.minimum(min(mu_zero_d2, mu_zero_d6), mu_white) # Step 2-3
mu = np.maximum.reduce([mu1, mu2, mu3, mu4, mu5]) # Step 4
```

![png](/assets/image/fuzzy/step234.png)

**Step5**:  centroid of gravity

$$
Z_{5}=\frac{\sum_{Z_{5}=0}^{255} Z_{5} \mu\left(Z_{5}\right)}{\sum_{Z_{5}=0}^{255} \mu\left(Z_{5}\right)}
$$

![png](/assets/image/fuzzy/boundary.png)

## Thresholding
### OTSU ([code](https://github.com/EeToSe/image-cv/blob/main/cmu_cv/func/otsu.py) implementation)
- Minimize the intra-class variance
- Or Maximize the inter-class variance 
 
$$ \sigma^{2}_{b}(t) = w_{0}(t)w_{1}(t)[\mu_{0}(t) - \mu_{1}(t) ]^{2} $$

- t - variant threshold, dividing the image intensity pixels into two classes - background and foreground;
- $w_{0,1}(t)$ - class probability;
- $\mu_{0,1}(t)$ - mean intensity of the class;

### Fuzzy method
- For each tested threshold, a point is assigned to the obj/bckgrnd with the membership 0.5~1.0
- The closer the pixel intensity to the mean of the region, the higher its membership to that region
- The optimal threshold → the entropy in the image is minimized

Average gray level for background $\mu_{0}$ and for object $\mu_{1}$

$$\mu_{0}=\sum_{g=0}^{t} g H(g) / \sum_{g=0}^{t} H(g)$$

$$\mu_{1}=\sum_{g=t+1}^{L-1} g H(g) / \sum_{g=t+1}^{L-1} H(g)$$

Membership function of the object/background region:

$$
\mu_{X}(x)=\left\{\begin{array}{l}
\frac{1}{1+\frac{\left|x-\mu_{0}\right|}{C}}, x<t \text{for background}\\
\frac{1}{1+\frac{\left|x-\mu_{1}\right|}{C}}, x \geq t \text{for object}
\end{array}\right.
$$

Entropy

$$S(\mu_{X})=-\mu_{X}(x) \ln \mu_{X}(x)-\left[1-\mu_{X}(x)\right] \ln \left(1-\mu_{X}(x)\right)$$

$$E(x) = \sum_{m,n}S(\mu_X(x_{mn}))$$

![png](/assets/image/fuzzy/threshold.png)