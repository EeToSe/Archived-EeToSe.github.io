---
layout: default
title: foundamental
nav_order: 1
parent: Algorithms
---

## Java programming environment

## Functions

## OOP
Data type example: **string** and **colour** .
### About Colour  
* *Luminance* :  linear combination of the three intensities  $'Y = 0.299r + 0.587g + 0.114b'$
* *Grayscale*: compute *Luminance* -> replace RGB values 
* *compatibility*: rule of thumb - difference between the luminance of the foreground and background color > 128

Example: [Luminance.java](https://introcs.cs.princeton.edu/java/31datatype/Luminance.java.html) - a static method library that we can use to convert to grayscale and test whether two colors are compatible. 

### Image Processing
In simple words -> filters that scan through all of the pixels in a source image and then perform some computation to determine the color of each pixel in a target image. 
* [*Grayscale*](https://introcs.cs.princeton.edu/java/31datatype/Grayscale.java.html) 
* [*Scale*](https://introcs.cs.princeton.edu/java/31datatype/Scale.java.html), simple way which uses the average filter

### Input and output streams
* [*Extracting data*](https://introcs.cs.princeton.edu/java/31datatype/Split.java.html) -> multiple output streams to split a CSV file into separate files, one for each comma-delimited field. 
