---
layout: default
title: Code with line numbers
parent: Algorithms
grand_parent: Assignment
---

# Case Study: Percolation
## Union-Find
**Problem Statement**. Given a set of N objects.
* Union: connect two objects
* Find query: is there a path connecting the two objects?

**Algorithms comparison**
<ol>
<li>
<strong>Quick-find</strong>.
<ul>
<li>Data structure.
{.text-blue-000}
Integer array id[] of length N.</li>
<li>Find. Check if p and q have the same id.</li>
<li>Union. Change all entries whose id equals id[p] to id[q]. </li>
</ul>
</li>

<li>
*Quick-union*.
<>
</li>
</ol>
