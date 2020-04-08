---
title: 'Triangular Grids (2014)'
date: 2019-10-12T05:43:00+01:00
draft: false
---

> “Triangles have fou… three sides!” —bootnecklad

I received an interview question back when I was doing consulting in which I had to write a program with a GUI where I could change the color of triangles in an isometric grid, also known as a **triangular lattice**, by clicking on them. Instead of using linear transformations or barycentric coordinates for this task, I tried to do something a little bit more interesting. I’d like to informally discuss some of the mathematics behind my solution.

[![Notes on the triangle problem.](http://web.archive.org/web/20140711171632im_/http://i.imgur.com/gtWV1iY.jpg "Some notes on the triangle problem.")](http://web.archive.org/web/20140711171632/http://i.imgur.com/gtWV1iY.jpg)

A page of some ideas on the triangle problem.

The crucial thing we need to be able to do is to be able to identify what triangle we are clicking inside of. This means we need a way to locate them. Perhaps if we can locate the vertices of the triangles with some sort of coordinate, we can go from there.

I used a concept called Eisenstein coordinates. An Eisenstein coordinate is a concept derived from an **Eisenstein integer**, which are the members of the commutative ring formed by the field extension $\\mathbb{Q}(\\omega)$ where \\\[\\omega = \\frac{-1+\\mathrm{i}\\sqrt{3}}{2}.\\\] What does this have to do with triangular lattices though? If we have integers $r$ and $t$, then $r+t\\omega$ is a triangular lattice point. In other words, the set of Cartesian coordinates \\\[\\{(\\operatorname{Re} c, \\operatorname{Im} c) \\mid c = r+t\\omega; r,t\\in\\mathbb{Z}\\}\\\] forms the triangular lattice. These numbers $r+t\\omega$ are very similar looking to complex numbers $a+b\\mathrm{i}$. In fact, they are about the same, except complex numbers form the familiar square lattice—the Cartesian coordinates.

Why though? Well suppose we have a unit equilateral triangle. Then its height is $\\tfrac{1}{2}\\sqrt{3}$. If our origin is at the center of a regular unit hexagon (oriented in such a way that the $x$-axis coincides with two of the hexagon’s vertices), then upper left vertex of that hexagon is $(-\\tfrac{1}{2}, \\tfrac{1}{2}\\sqrt{3})$. As a complex number, this is \\\[-\\frac{1}{2}+\\frac{1}{2}\\sqrt{3}\\mathrm{i},\\\] which is equal to $\\omega$. Since we have two vectors now: a vector to move right one unit, $1$, and a vector to move 60 degrees northwest, $\\omega$. The span of these vectors, \\\[\\operatorname{span}(1,\\omega)=\\{r+t\\omega\\},\\\] identify all vertices of the triangular lattice.

![A picture of a triangular lattice.](http://web.archive.org/web/20140711171632im_/http://i.imgur.com/CIoROCI.png "Triangular Lattice")

A triangular lattice with two vectors: the horizontal vector $1$ and diagonal vector $\\omega$.

We define an **Eisenstein coordinate** as a coordinate pair $(r, t)\\in\\mathbb{R}^2$ whose Cartesian coordinate is derived from above. It would be useful to explicitly have a way to transform between Cartesian and Eisenstein coordinates.

\\begin{align\*}  
(x,y) &= \\left( r – \\frac{1}{2}t, \\frac{\\sqrt{3}}{2}t \\right)\\\\  
(r,t) &= \\left( x+\\frac{1}{\\sqrt{3}}y, \\frac{2}{\\sqrt{3}}y \\right)  
\\end{align\*}

Eisenstein coordinates allow us to conveniently describe lattice points as integers. This is useful because it allows us to store the state of the grid in a rectangular array. But Eisenstein coordinates only describe the vertices of the grid, and not triangles themselves.

We can look at a triangular grid as alternating upward and downward pointing triangles. We can identify a triangle by precisely the vertex that is pointing up or down, but because of this ambiguity, we need to have a third value saying whether we are looking at the upward- or downward-pointing triangle. For example, the vertex $(0,0)$ could either represent the triangle whose other vertices are $\\omega$ and $1+\\omega$, or $-\\omega$ and $-\\omega-1$. (Note that $-\\omega$ is diametric reflection on the hexagon, and _not_ about the $x$-axis!)

This value, called the **orientation**, is just a binary value. In a language like C, the orientation might be represented as an integer 0 or 1, or a boolean in C++, or an entirely different data type in Haskell. I used the integers $1$ for the downward-pointing triangle and $-1$ for the upward-pointing triangle because that made conversion between coordinates nicer, as in the last paragraph.

As such, our triangles are identified by an Eisenstein coordinate equipped with an orientation: $(r, t, o)$. We will call this a **triangle coordinate**. It is important to note that triangle coordinates are _unique_ and _complete_: every coordinate maps to exactly one triangle, and there are no skipped triangles.

The interview question boils down to the following:

> Given a Cartesian coordinate $(x,y)$, find the corresponding triangular coordinate $(r, t, o)$.

We do this by finding the closest Eisenstein coordinate. If we convert a Cartesian coordinate to an Eisenstein coordinate, and we take the floor and ceiling of each component, we will get two opposing vertices of a rhombus created by gluing together the right and left edges of two triangles. (We will get the points along the glued edge.) From there, we can actually determine which triangle our point is in.

```
          upper vertex (from ceiling)          |          v          o -- o        /  \\  /       o -- o  <-- lower vertex (from floor) 
```

If we have a Cartesian point in this rhombus, we need to determine which triangle we are in. This is equivalent to determining if we are above or below the seam. We know the Eisenstein coordinate of the upper vertex, say $(r\_0, t\_0)$, we convert it into a Cartesian coordinate via the previous transformation equations, giving $(x\_0, y\_0)$. An equilateral triangle has angles $\\pi/6$ radians, which corresponds to a slope of $\\pm\\sqrt{3}$. Our seams are of negative slope, so the equation of the seam is \\\[f(x) = y\_0 - \\sqrt{3}(x - x\_0).\\\] In order to check if our point $(x’, y’)$ is above or below, we simply check if $f(x’) > y’$, in which case the point is below the line, otherwise it is above. (The case in which they’re equal is just said to be above.)

Once we have decided which vertex it is, we construct the vertex, and we do whatever operation we’d like. Operations such as drawing the triangle, changing its color, and so on, are easy when we have the triangle coordinate. Most importantly, we can refer to triangles by storing in an array.

Naively, we can just use an array of size $M\\times N\\times 2$ to store information about triangles in the lattice, where $M$ and $N$ are as big as we’d like (up to a restriction on $M$, see below). This is the approach I took because it’s simplest and the board is small. However, depending on the data we are storing, we can do some optimizations. For example, if we want to store some data about the color of a triangle at a point, we could use the upper half of the word for upward orientation, and the lower half for downward orientation.

However, there is a fundamental problem with storing these coordinates in a rectangular array: for a rectangular screen, there tends to be a lot of wasted elements of the array. This is a result of the fact that Eisenstein coordinates are not orthogonal. In order to identify a triangle, say, on the $y$-axis, we must overshoot to the right, then “backtrack” with $\\omega$. For a triangle on the $y$-axis at $y=n$, we have to use the Eisenstein coordinate $(n/2, n)$. If we are to support roughly a grid of $P\\times Q$ triangles, then $M>P+Q/2$ in order to be able to identify the triangle most northeast in the grid.

Using the above, iterating through triangles, drawing a mesh, etc. turns out to be easy. I specifically stored an array of integers, which contains the numbers 0 through 3, where 0 means “off”, and 1–3 represent the colors red, green, and blue. The final result, for me, is depicted in the next figure.

![](http://web.archive.org/web/20140711171632im_/http://i.imgur.com/NEwkZDW.png "Interactive triangle coloring.")

Screenshot of the produced GUI with the triangles in a multicolor Sierpinski-esque pattern.

Unfortunately, I did **not** get the job. :)

_Disclosure: I notified the company that I would be writing this article, they agreed as long as I neither named them nor posted the code to my solution._

  
  
from Hacker News https://ift.tt/OP73dM