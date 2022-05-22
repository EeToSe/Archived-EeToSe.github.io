---
layout: default
title: Essence
nav_order: 1
# has_children: true
parent: Linear algebra
grand_parent: Math
---

# Essence of Linear algebra
{: .no_toc .text-large }
<div style = "background-color:black">
<span style="color:#F8F9F9">"There is hardly any theory which is more elementary than linear algebra, in spite of the fact that generations of professors and textbook writers have obscured its simplicity by <del>preposterous calculations with matrices</del>". </span> <br>
<span style="color:#F7DC6F"> - Jean Dieudonné</span>
</div>

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}
---

## Vector
### Coordinate systems
<div style = "background-color:black">
<span style="color:#F8F9F9">"The introduction of numbers as coordinates is an act of violence." </span> <br>
<span style="color:#F7DC6F"> - Hermann Weyl</span>
</div>

The coordinates of a vector: **instructions** for how to get from the tail of that vector at the origin, to its tip.
- $1^{st}$ number: how far to walk along the x-axis (right is + left is -);
- $2^{nd}$ number: how far to walk along the y-axis (up is + down is -).

3D with third axis - perpendicular to both x and y axis. 
<p align="center">
<img src="/assets/image/linAlg/essence/vector_instructions.svg" width =400/>
<img src="/assets/image/linAlg/essence/3D_vector.png" width =400/>
</p>

###  Vector Operations
*Addition* as a walk from the origin.
<p align="center">
<img src="/assets/image/linAlg/essence/walk_path.svg" width =400/>
<img src="/assets/image/linAlg/essence/vector_addition_numerical.svg" width =400/>
</p>
*Scaling*: stretching, squishing, and reversing direction.
<p align="center">
<img src="/assets/image/linAlg/essence/multiply_third.svg" width =400/>
<img src="/assets/image/linAlg/essence/multiply_negative.svg" width =400/>
</p>

---
## Linear combinations, span, and basis vectors
<div style = "background-color:black">
<span style="color:#F8F9F9">"Mathematics requires a small dose, not of genius, but of an imaginative freedom which, in a larger dose, would be insanity." </span> <br>
<span style="color:#F7DC6F"> - Angus K. Rodgers</span>
</div>

### Basis vectors 
Each coordinate as a *scalar*:  how each one stretches or squishes vectors;<br>
*Basis vectors* are what those scalars actually scale;<br>
The vector that these coordinates describe is <u>the sum of two scaled vectors  $\color{blue}{\text{Linear Combinations}}$</u>.
<p align="center">
<img src="/assets/image/linAlg/essence/unit_bases.svg" width =400/>
<img src="/assets/image/linAlg/essence/basis_vectors.svg" width =400/>
</p>

### Span
<p align="center">
<img src="/assets/image/linAlg/essence/span_def.svg" width = 700/>
</p>

### Span in 3D
**Linearly Dependent**: $\quad \overrightarrow{\mathbf{u}}=a \overrightarrow{\mathbf{v}}+b \overrightarrow{\mathbf{w}} \quad$ for some $a$ and $b$ or $\overrightarrow{\mathbf{u}}$ is in the **span** of $\overrightarrow{\mathbf{v}}$ and $\overrightarrow{\mathbf{w}}$

Review: The of $\color{blue}{basis}$ of a vector space is a set of linearly independent vectors that span the full space.

---
## Linear transformations and matrices
<div style = "background-color:black">
<span style="color:#F8F9F9">“Unfortunately, no one can be told what the Matrix is. You have to see it for yourself.”</span> <br>
<span style="color:#F7DC6F"> - Morpheus</span>
</div>

'Transformation' suggests **movement**!

### What makes a transformation "linear"?
A transformation LL is linear if it satisfies the following two properties.

$$L(\overrightarrow{v}+\overrightarrow{w}) = L(\overrightarrow{v}) + L(\overrightarrow{w})$$

$$L(s\overrightarrow{v}) = sL(\overrightarrow{v})$$

<p align="center">
<img src="/assets/image/linAlg/essence/basis_example.svg" width =400/>
<img src="/assets/image/linAlg/essence/basis_example2.svg" width =400/>
</p>

### Matrices
Look at coordinates of where $\hat{i}$ and $\hat{j}$ land.

$$
\left.\left[\begin{array}{l}
x \\
y
\end{array}\right] \rightarrow x\left[\begin{array}{c}
1 \\
-2
\end{array}\right]+y\left[\begin{array}{l}
3 \\
0
\end{array}\right]=\left[\begin{array}{c}
1 x+3 y \\
-2 x+0 y
\end{array}\right] \quad \begin{array}{cc}
1 & 3 \\
-2 & 0
\end{array}\right]
$$

A 2x2 matrix actually describes a linear transformation and columns of matrix are **transformed versions of your basis vectors**.

$$\left[\begin{array}{ll}
a & b \\
c & d
\end{array}\right] \cdot\left[\begin{array}{l}
x \\
y
\end{array}\right]=x\left[\begin{array}{l}
a \\
c
\end{array}\right]+y\left[\begin{array}{l}
b \\
d
\end{array}\right]=\left[\begin{array}{l}
a x+b y \\
c x+d y
\end{array}\right]$$

---
## Matrix multiplication as composition

$$\underbrace{\left[\begin{array}{ll}1 & 1 \\ 0 & 1\end{array}\right]}_{\text {Shear }}(\underbrace{\left[\begin{array}{lc}0 & -1 \\ 1 & 0\end{array}\right]}_{\text {Rotation }}\left[\begin{array}{l}x \\ y\end{array}\right])=\underbrace{\left[\begin{array}{cc}1 & -1 \\ 1 & 0\end{array}\right]}_{\text {Composition }}\left[\begin{array}{l}x \\ y\end{array}\right]$$

<p align="center">
<img src="/assets/image/linAlg/essence/rotation.png" width =400/>
<img src="/assets/image/linAlg/essence/shear.png" width =400/>
</p>

### General form of matrix multiplication

$$
\begin{aligned}
&{\left[\begin{array}{ll}
a & b \\
c & d
\end{array}\right]\left[\begin{array}{l}
e \\
g
\end{array}\right]=e\left[\begin{array}{l}
a \\
c
\end{array}\right]+g\left[\begin{array}{l}
b \\
d
\end{array}\right]=\left[\begin{array}{l}
a e+b g \\
c e+d g
\end{array}\right]} \\
&{\left[\begin{array}{ll}
a & b \\
c & d
\end{array}\right]\left[\begin{array}{l}
f \\
h
\end{array}\right]=f\left[\begin{array}{l}
a \\
c
\end{array}\right]+h\left[\begin{array}{l}
b \\
d
\end{array}\right]=\left[\begin{array}{l}
a f+b h \\
c f+d h
\end{array}\right]}
\end{aligned}
$$

---
## Determinant
<div style = "background-color:black">
<span style="color:#F8F9F9">"The purpose of computation is insight, not numbers." </span> <br>
<span style="color:#F7DC6F"> - Richard Hamming</span>
</div>

The **factor** by which a linear transformation changes areas, is called the “determinant” of that transformation.
The determinant of a 2D transformation is 0 ->  transformation associated with a matrix squishes everything into a smaller dimension.
<p align="center">
<img src="/assets/image/linAlg/essence/determinant.svg" width =400/>
<img src="/assets/image/linAlg/essence/determinant_0.svg" width =400/>
</p>

### Negative determinant

<p align="center">
<img src="/assets/image/linAlg/essence/j_left_of_i.svg" width =400/>
<img src="/assets/image/linAlg/essence/j_right_of_i.svg" width =400/>
</p>

### computation

<p align="center">
<img src="/assets/image/linAlg/essence/determinant_diagram.svg" width =600/>
</p>

Applying two matrices sequentially leads to a new linear transformation

$$det(M_{1}M_{2}) = det(M_{1})det(M_{2})$$

<!-- $det(\left[\begin{array}{ll}a & b \\ c & d\end{array}\right]) = ad - bc$ -->

## Under the light of linear transformations
### Linear Systems of Equations

$\color{blue}{Essence}$: solving $A\overrightarrow{x}= \overrightarrow{v}$ means we’re looking for a vector $\overrightarrow{x}$ which, after applying that transformation A, lands on $\overrightarrow{v}$.

<p align="center">
<img src="/assets/image/linAlg/essence/transformation_ax=v.svg" width =600/>
<img src="/assets/image/linAlg/essence/linear_equation.png" width =600/>
</p>

The way we think about solutions to this equation depends on whether the transformation associated with A squishes all of space into a lower dimension ($\color{orange}{det(A)=0}$), like a line or a point, or if it leaves everything spanning the full two dimensions where it started ($\color{orange}{det(A)\neq0}$).

### Inverse($det(A)\neq0$)
- As long as the transformation for A doesn’t squish all of space into a lower dimension, meaning its determinant is not zero, there will be an inverse transformation $A^{-1}$ 
   
$$det(A)\neq0 \rightarrow A^{-1} \quad exists$$

- Since applying one transformation after another is captured algebraically with matrix multiplication, the core property of this reverse transform $A^{-1}$  is that $A^{-1} \times A$ equals the matrix that corresponds to doing nothing - "identity" transformation $I$.

$$A^{-1}A = \left[\begin{matrix}
 1 & 0\\
 0 & 1     
\end{matrix}\right]$$

-  Geometrically is that you’re playing the transformation in reverse and following $\overrightarrow{v}$ to end up $\overrightarrow{x}$
  
$$ A^{-1}A \overrightarrow{x} = A^{-1}\overrightarrow{v} $$

$$ \overrightarrow{x} =  A^{-1}\overrightarrow{v} $$

###  Irreversibility($det(A)=0$)
$\color{red}{\text{No inverse}}$: You cannot unsquish a line to turn it into a plane. At least, that’s not something a function can do.
<p align="center">
<img src="/assets/image/linAlg/essence/multiple_vectors.svg" width =600/>
</p>

### Column Space
But still possible that a solution exists when there is $\color{red}{\text{No inverse}}$: have the vector $\overrightarrow{v}$ live somewhere on that line.
<p align="center">
<img src="/assets/image/linAlg/essence/no_solution_exists.svg" width =600/>
</p>

The word $\color{blue}{\text{rank}}$ means dimensions # in the output of a transformation or <u>  dimensions # in the column space</u>.

<p align="center">
<img src="/assets/image/linAlg/essence/rank_1.svg" width = 400/>
<img src="/assets/image/linAlg/essence/rank_2.svg" width = 400/>
</p>

$\color{blue}{\text{column space}}$ is the $\color{blue}{\text{span}}$ of the columns of your matrix.
- the columns of your matrix tell you where the basis vectors land
- span of those transformed basis vectors gives you all possible outputs

### Null space

- If a 3D transformation squishes space onto a plane, there is a line full of vectors that land on the origin.
- If a 3D transformation squishes all of space onto a line, there is a whole plane full of vectors that land on the origin.
  
<p align="center">
<img src="/assets/image/linAlg/essence/null_line_3D.svg" width = 400/>
<img src="/assets/image/linAlg/essence/null_plane.svg" width = 400/>
</p>

Null space gives you all possible solutions to the equation $A\overrightarrow{x} = \mathbf{0}$.

## Dot product and duality
### Projection
<p align="center">
<img src="/assets/image/linAlg/essence/dot_product_positive.png" width = 420/>
<img src="/assets/image/linAlg/essence/dot_product_negative.png" width = 380/>
</p>

### Symmetry($\overrightarrow{v}  \cdot \overrightarrow{u} = \overrightarrow{u}  \cdot \overrightarrow{v} $)
<p align="center">
<img src="/assets/image/linAlg/essence/symmetry.png" width = 320/>
<img src="/assets/image/linAlg/essence/symmetry_broken.png" width = 480/>
</p>

### Transform from 2D to 1D
Connection between linear transformations that take vectors to numbers and vectors themselves.
<p align="center">
<img src="/assets/image/linAlg/essence/12_matrix_eg.png" width = 600/>
</p>

### Unit vector with $\hat{i}$ and $\hat{j}$ 
$\text{linear transformation from 2D to number line}  \Leftrightarrow \text{projection length aka } \color{blue}{\text{dot product}} $

<p align="center">
<img src="/assets/image/linAlg/essence/connection_eg.png" width = 400/>
<img src="/assets/image/linAlg/essence/projection.png" width = 400/>
</p>
Matrix-vector multiplication $\Leftrightarrow$ Dot product

$$ \left[\begin{array}{ll}u_{x} & u_{y}\end{array}\right]\left[\begin{array}{l}x \\ y\end{array}\right]=u_{x} \cdot x+u_{y} \cdot y$$

$$
\left[\begin{array}{l}
u_{x} \\
u_{y}
\end{array}\right] \cdot\left[\begin{array}{l}
x \\
y
\end{array}\right]=u_{x} \cdot x+u_{y} \cdot y
$$

Summary: <u>applying a 2d-to-1d linear transformation is associated with some vector in 2d space</u>.
<p align="center">
<img src="/assets/image/linAlg/essence/dot_product_summary.png" width = 600/>
</p>

$\color{blue}{Duality}$: "dual" the linear transformation which the vector encodes & "dual" of a linear transformation from space to 1-d is a certain vector in that space.

<p align="center">
<img src="/assets/image/linAlg/essence/dual_1.png" width = 420/>
<img src="/assets/image/linAlg/essence/dual_2.png" width = 380/>
</p>

## Cross products
2-D version of the cross product $\overrightarrow{v}\times\overrightarrow{w}$
<p align="center">
<img src="/assets/image/linAlg/essence/cross_product.png" width = 600/>
</p>
3-D version of the cross product $\overrightarrow{v}\times\overrightarrow{w} = \overrightarrow{p}$
<p align="center">
<img src="/assets/image/linAlg/essence/cross_product_3d.png" width = 600/>
</p>

### Under the light of linear transformation
Consider the function below, $1\times3$ matrix take 3d vector to the number line.
<p align="center">
<img src="/assets/image/linAlg/essence/cross_product_func.png" width = 460/>
<img src="/assets/image/linAlg/essence/cross_product_func2.png" width = 340/>
</p>

Then this matrix multiplication can be written as dot product.
<p align="center">
<img src="/assets/image/linAlg/essence/cross_product_func3.png" width = 600/>
</p>

We ask what vector $\overrightarrow{p}$ has the above property <br>
**Equation right** is determinant - the volume of parallepiped
<p align="center">
<img src="/assets/image/linAlg/essence/cross_product_func5.png" width = 600/>
</p>
Therefore we know the orientation and length of $\overrightarrow{p}$
<p align="center">
<img src="/assets/image/linAlg/essence/cross_product_func6.png" width = 600/>
</p>

## Cramer's rule
### Special case: orthonormal matrix
$T$ is "Orthonormal" $\Rightarrow$ $T(\overrightarrow{v}) \cdot T(\overrightarrow{w})= \overrightarrow{v} \cdot \overrightarrow{w}$ for all $\overrightarrow{v}$ and $\overrightarrow{w}$.<br>
If $\overrightarrow{v} = [1 \quad 0]^{T}$ and $\overrightarrow{w} = [x \quad y]^{T}$, 
then as the example below we have:
<p align="center">
<img src="/assets/image/linAlg/essence/cramer_rule.png" width = 600/>
</p>

### geometric understanding for the input vector coordinates
Use the determinant in 2d(area) and 3d(volume) to represent the coordinates.
<p align="center">
<img src="/assets/image/linAlg/essence/cramer_rule2.png" width = 350/>
<img src="/assets/image/linAlg/essence/cramer_rule3.png" width = 460/>
</p>

### Transformation scales the area
The key is to interpret the coordinates as the determinant of the matrix formed by the input vector and corresponding basis vector.
关键在于将坐标想象成由输入向量与基向量所形成矩阵的determinant.
<p align="center">
<img src="/assets/image/linAlg/essence/cramer_rule4.png" width = 600/>
</p>

3D case: think of z is the volume constructed with $\hat{i}$ and $\hat{j}$ and input vector. <br>
Similar to 2D case: $\color{orange}{\text{Volume}} = det(A)z$
<p align="center">
<img src="/assets/image/linAlg/essence/cramer_rule5.png" width = 600/>
</p>

## Change of basis
Some implications behind the vector:
<p align="center">
<img src="/assets/image/linAlg/essence/basis_1.png" width = 530/>
<img src="/assets/image/linAlg/essence/basis_2.png" width = 290/>
</p>

How we could interpret from one coordinate system to another.
<p align="center">
<img src="/assets/image/linAlg/essence/basis_3.png" width = 400/>
<img src="/assets/image/linAlg/essence/basis_7.png" width = 400/>
</p>
From Jeniffer system to ours, matrix-vector multiplication

$$
\left[\begin{array}{cc}
2 & -1 \\
1 & 1
\end{array}\right]\left[\begin{array}{c}
-1 \\
2
\end{array}\right]=-1\left[\begin{array}{c}
2 \\
1
\end{array}\right]+2\left[\begin{array}{c}
-1 \\
1
\end{array}\right]=\left[\begin{array}{c}
-4 \\
1
\end{array}\right]
$$


<p align="center">
<img src="/assets/image/linAlg/essence/basis_5.png" width = 400/>
<img src="/assets/image/linAlg/essence/basis_6.png" width = 400/>
</p>

$$\underbrace{\left[\begin{array}{cc}2 & -1 \\ 1 & 1\end{array}\right]^{-1}}_{\text {inverse}} =  \underbrace{\left[\begin{array}{cc} \frac{1}{3} & \frac{1}{3} \\ -\frac{1}{3} & \frac{2}{3}\end{array}\right]}_{\text {inverse change of basis matrix}} \left[\begin{array}{cc} -4 \\ 1 \end{array}\right] = \underbrace{\left[\begin{array}{cc} -1\\ 2\end{array}\right]}_{\text {same vector in her language}} $$

### How to translate a vector
Vectors aren't the only thing with coordinates(which coordinate system it is in?) <br>
**Transformed vector** in her language
<p align="center">
<img src="/assets/image/linAlg/essence/basis_8.png" width = 600/>
</p>

$\color{blue}{\text{Example}}$: 90 degree of rotation from $[1 \quad 2]^{T}$to $[-1 \quad 1]^{T}$ in her coordinate system.
<p align="center">
<img src="/assets/image/linAlg/essence/basis_9.png" width = 500/>
<img src="/assets/image/linAlg/essence/basis_10.png" width = 300/>
</p>

$A_{-1} \textcolor{blue}{M} A$ suggests a mathematical sort of empathy
- a transformation of some kind, as you see it; 
- the outer two matrices represent the shift in perspective;    
- the full matrix product represents that same transformation but as some else sees it.