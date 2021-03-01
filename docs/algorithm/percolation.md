---
layout: default
title: percolation
parent: assignment
grand_parent: Algorithms
nav_order: 1
---
<img align="right" src="/assets/image/percolation.png" alt = "hi" width="250">

# Percolation
## Union-Find
**Problem Statement**. Given a set of N objects.
* Union: connect two objects
* Find query: is there a path connecting the two objects?

**Algorithms comparison**
<ol>
<li>
<strong>Quick-find</strong>.
<ul>
<li><span style="color:blue">Data structure</span>.
Integer array id[] of length N.</li>
<li><span style="color:blue">Find</span>. Check if p and q have the same id.</li>
<li><span style="color:blue">Union</span>. Change all entries whose id equals id[p] to id[q]. </li>
</ul>
</li>

<li>
<strong>Quick-union</strong>.
<ul>
<li><span style="color:blue">Data structure</span>. </li>
<li><span style="color:blue">Find</span>. </li>
<li><span style="color:blue">Union</span>.</li>
</ul>
</li>

<li>
<strong>Improvements </strong>
<ul>
<li> Weighting  </li>
<li> Path compression  </li>
</ul>
</li>

</ol>
---

## Application
**Percolation**
* N*N grid of intensities
* Each site is open with probability p
* System percolates iff top and bottom are connected by open sites.

### FAQs
* The test cases provided **do not** correspond to specification - array index one start from 0 while another start from 1.
* Backwash problem caused by virtual top and bottom sites.
* Memory efficiency - see details in grader report
* Object Percolation shall be declared as local variable instead of instance variable
