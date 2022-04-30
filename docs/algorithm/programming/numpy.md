---
layout: default
title: numpy
nav_order: 1
# has_children: true
parent: programming
grand_parent: Algorithms
---

# Array programming with Numpy
- [Advanced NumPy: Master stride tricks with 25 illustrated exercises](https://towardsdatascience.com/advanced-numpy-master-stride-tricks-with-25-illustrated-exercises-923a9393ab20) <br>
   1) what is strides? <br> The number of bytes to jump to reach the next pixel in each dimension.
     
    ```python
    arr = np.asarray(range(1,26), np.int8).reshape(5,5)
    arr.strides

    (5, 1)
    ```
    2) dasd