---
layout: default
title: fundamental
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
 <li> <strong>Encapsulation</strong>: separte clients from implmentations by hiding information to enable modular programming, faciitate debugging and clarify program code.
  <ul>
   <li> <em>Private</em>: make the instance variable/method impossible for any client to directly access.</li>
   <li> <em>Limiting the potential for error</em>: ensure code operates as intended. </li>
   <li><a href="https://introcs.cs.princeton.edu/java/33design/Counter.java.html">Example code: Counter.java</a></li>
  </ul>
</li>
<li> <strong>Immutability</strong>: An object from a data type is immutable if its data-type value cannot change once created.  
  <ul>
    <li><em>Final</em>: promised to assign it a value only once which helps enforce immutability</li>
  <li><em>Reference types</em>: the final access modifier <mark>does not guarantee immutability for instance variables of mutable types</mark>. In such cases, you must make a defensive copy. </li>
    </ul>
 </li>
 <li> <strong>Interface inheritance</strong>: declare a relationship between otherwise unrelated classes by specifying a common set of methods that each implementing class must include.
 <ul>
  <li> <em>Defining</em>: the body of the interface contains a list of <mark>abstract</mark> methods -
   which is declared but does not include any implementation code with only the method signature.
  </li>
  <li> <em>Implementing</em>: include an implements clause in the class declaration with the name of the interface & implement each of the abstract methods
  </li>
  <li><em>Using</em>: a reference type -> you can declare the type of a variable to be the name of an interface. <mark> Any object you assign to that variable must be an instance of a class that implements the interface.</mark>
  </li>
  </ul>
</li>
   <li> <strong>Implementation inheritance (subclassing) </strong>: another inheritance mechanism TODO
   </li>
 <li> <strong>Design by contract</strong>: enable you to verify assumptions
  <ul>
   <li> <em> Exceptions</em>: taken as throwing an exception to signal an error
    </li>
   <li> <em>Assertions</em>: a boolean expression affirming is true at some point during the execution of a prgram
    By default, they are disabled which are used for debugging only.
   </li>
   </ul>
 </li>

</ul>
