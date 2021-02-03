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
* *Luminance* :  linear combination of the three intensities. 
```math 
Y = 0.299r + 0.587g + 0.114b
```
* *Grayscale*: compute *Luminance* -> replace RGB values.
* *compatibility*: rule of thumb - difference between the luminance of the foreground and background color > 128.

Example: [Luminance.java](https://introcs.cs.princeton.edu/java/31datatype/Luminance.java.html) - a static method library that we can use to convert to grayscale and test whether two colors are compatible. 

### Image Processing
In simple words -> filters that scan through all of the pixels in a source image and then perform some computation to determine the color of each pixel in a target image. 
* [*Grayscale*](https://introcs.cs.princeton.edu/java/31datatype/Grayscale.java.html).
* [*Scale*](https://introcs.cs.princeton.edu/java/31datatype/Scale.java.html), simple way which uses the average filter.

### Input and output streams
* [*Extracting data*](https://introcs.cs.princeton.edu/java/31datatype/Split.java.html) -> multiple output streams to split a CSV file into separate files, one for each comma-delimited field. 

### Creating Data Types
Basic elements with an illustrated graph.
* API - Application Programming interface: the contract with all clients.
* Instance variables: declarations appear as the first statements in the class.
* Constructors: creates an object and provides a reference to that object.
* Instance methods: perform operations on instance variables.
* Test client: call every constructor and instance method in the class.

<p align="center">
<img src = "/assets/image/data-type.png" alt="hi" max-width="60%"/>
<em>Example code using the data type - charge </em>
</p>

### Designing Data Types
<ul>
 <li>**Encapsulation**: separte clients from implmentations by hiding information to enable modular programming, faciitate debugging and clarify program code.
  <ul> 
   <li>*Private*: make the instance variable/method impossible for any client to directly access.</li>
   <li> *Limiting the potential for error*: ensure code operates as intended. </li>
   <li><a href="https://introcs.cs.princeton.edu/java/33design/Counter.java.html">Example code: Counter.java</a></li>
  </ul> 
</li>
  
</ul>

