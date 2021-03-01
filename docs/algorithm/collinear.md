---
layout: default
title: collinear
parent: assignment
grand_parent: Algorithms
nav_order: 3
---
<img align="right" src="/assets/image/collinear.png" alt = "hi" width="400">

# Collinear Points

## Algorithm

* Brute Force
* faster, sorting-based solution
  * For each point p -> origin, every other point q, determine slope q -> p
  * Sort the points based on slope q -> p
  * Check if any 3 or more adjacent points have the same slopes

## Learned Lessons

1. **slopeTo()** method: int/int will round round down, solution ((double) int)/int.
2. 当使用ArrayList to append 找到的 line segments, 要注意variable scope, 否则declare的ArrayList会留在memory中, 导致第二次call segments()时结果改变了.
3. create a defensive copy of the object referenced by the parameter  variable ‘points’ and store that copy in the instance variable ‘points’.
4. **Comparable** and **Comparator**
5. To filter the **subsequence**, simply check if this point is at the bottom/ top in the found collinear points.
6.  Returns a reference to the mutable object stored in the instance variable 'collinearPoints', which exposes the internal representation of the class 'BruteCollinearPoints'
