---
layout: default
title: fuzzy logic
# nav_order: 2
parent: Computer Vision
---
<head>
<meta charset="UTF-8">
  <title>Katex</title>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.css" integrity="sha384-zB1R0rpPzHqg7Kpt0Aljp8JPLqbXI3bhnPWROx27a9N0Ll6ZP/+DiW/UqRcLbRjq" crossorigin="anonymous">
  <script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.js" integrity="sha384-y23I5Q6l+B6vatafAwxRu/0oK/79VlbSz7Q9aiSZUvyWYIYsd+qj+o24G5ZU2zJz" crossorigin="anonymous"></script>
  <script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/contrib/auto-render.min.js" integrity="sha384-kWPLUVMOks5AQFrykwIup5lo0m3iMkkHrD0uJ4H5cjeGihAutqP0yW0J6dpFiVkI" crossorigin="anonymous" onload="renderMathInElement(document.body);"></script>
</head>


# Fuzzy logic theory
This is a large section, we only discuss rule-based techniques in this blog. <br>
More should refer to this book: Fuzzy techniques in image processing.

---

## Fuzzy set
- A fuzzy set $$A \subset Z$$ is characterized by a membership function $$\mu_{A}(z)$$. <br> (e.g. Z is all men; A is yong men).
- A fuzzy set is an ordered pair: $$A_{fuzzy} = \{(z, \mu_{A}(z)) \mid z \in Z, \mu_{A}(z) \in [0,1] \}$$
- Membership function $$\mu_{A}(z)$$ quantifies the degree of $$z$$ in $$A$$.

## Fuzzy Rule Base and Inference Engine
Approximate an unknown I/O mapping by inference from a set of fuzzy rules (**IF-THEN**).

![png](/assets/image/fuzzy/scheme.jpg)<br>
<em> General scheme of a fuzzy inference system</em>

**The fuzzy inference engine** combines the rules in the rule base according to approximate reasoning theory to produce 
a mapping from fuzzy sets in the input space to fuzzy sets in the output space.

$$R_{k} \text{: IF (x is } A_{k}) \text{ THEN (y is } B_{k})$$

## General Steps
1. **Fuzzify the inputs** <br> map membership value([0,1]) to each pixel by the membership function.
2. **Fuzzy logical operations** <br> combine the outputs of all *IF* operators to a single value using the appropriate logic.
3. **Apply an implication method** <br> clip each fuzzy output of according to the result of *step2*.
4. **Aggregation method to the clipped output fuzzy sets** <br> combine the output of each fuzzy rule.
5. **Defuzzify the final output fuzzy set** <br> e.g. center of gravity.
   
---
## Contrast enhancement


## Thresholding
### OTSU ([code](https://github.com/EeToSe/image-cv/blob/main/cmu_cv/func/otsu.py) implementation)
- Minimize the intra-class variance
- Or Maximize the inter-class variance 
 
$$ \sigma^{2}_{b}(t) = w_{0}(t)w_{1}(t)[\mu_{0}(t) - \mu_{1}(t) ]^{2} $$

- t - variant threshold, dividing the image intensity pixels into two classes - background and foreground;
- $$w_{0,1}(t)$$ - class probability;
- $$\mu_{0,1}(t)$$ - mean intensity of the class;

### Fuzzy method