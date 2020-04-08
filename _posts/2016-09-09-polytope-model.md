---
title: 'Polytope Model'
date: 2019-12-02T03:19:00+01:00
draft: false
---

The **polyhedral model** (also called the **polytope method**) is a mathematical framework for programs that perform large numbers of operations -- too large to be explicitly enumerated -- thereby requiring a _compact_ representation. Nested loop programs are the typical, but not the only example, and the most common use of the model is for [loop nest optimization](https://en.wikipedia.org/wiki/Loop_nest_optimization "Loop nest optimization") in [program optimization](https://en.wikipedia.org/wiki/Program_optimization "Program optimization"). The polyhedral method treats each loop iteration within nested loops as [lattice points](https://en.wikipedia.org/wiki/Lattice_points "Lattice points") inside mathematical objects called [polyhedra](https://en.wikipedia.org/wiki/Polytope "Polytope"), performs [affine transformations](https://en.wikipedia.org/wiki/Affine_transformation "Affine transformation") or more general non-affine transformations such as [tiling](https://en.wikipedia.org/wiki/Loop_tiling "Loop tiling") on the polytopes, and then converts the transformed polytopes into equivalent, but optimized (depending on targeted optimization goal), loop nests through polyhedra scanning.

Simple example
--------------

Consider the following example written in [C](https://en.wikipedia.org/wiki/C_(programming_language) "C (programming language)"):

```
 const int n \= 100; int i, j, a\[n\]\[n\]; for (i \= 1; i < n; i++) { for (j \= 1; j < (i + 2) && j < n; j++) { a\[i\]\[j\] \= a\[i \- 1\]\[j\] + a\[i\]\[j \- 1\]; } } 
```

The essential problem with this code is that each iteration of the inner loop on `a[i][j]` requires that the previous iteration's result, `a[i][j - 1]`, be available already. Therefore, this code cannot be parallelized or [pipelined](https://en.wikipedia.org/wiki/Pipelining "Pipelining") as it is currently written.

An application of the polytope model, with the affine transformation (i′,j′)=(i+j,j){\\displaystyle (i',\\,j')=(i+j,\\,j)}![{\displaystyle (i',\,j')=(i+j,\,j)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f4b6a0c677875545644ce7d35d44846c9c3d9cdd) and the appropriate change in the boundaries, will transform the nested loops above into:

```
 a\[i \- j\]\[j\] \= a\[i \- j \- 1\]\[j\] + a\[i \- j\]\[j \- 1\]; 
```

In this case, no iteration of the inner loop depends on the previous iteration's results; the entire inner loop can be executed in parallel. (However, each iteration of the outer loop does depend on previous iterations.)

Detailed example
----------------

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/1/1e/Polytope_model_unskewed.svg/220px-Polytope_model_unskewed.svg.png)](https://en.wikipedia.org/wiki/File:Polytope_model_unskewed.svg)

The dependencies of

`src`

, before

[loop skewing](https://en.wikipedia.org/wiki/Loop_optimization#Common_loop_transformations "Loop optimization")

. The red dot corresponds to

`src[1][0]`

; the pink dot corresponds to

`src[2][2]`

.

The following [C](https://en.wikipedia.org/wiki/C_(programming_language) "C (programming language)") code implements a form of error-distribution [dithering](https://en.wikipedia.org/wiki/Dither "Dither") similar to [Floyd–Steinberg dithering](https://en.wikipedia.org/wiki/Floyd%E2%80%93Steinberg_dithering "Floyd–Steinberg dithering"), but modified for pedagogical reasons. The two-dimensional array `src` contains `h` rows of `w` pixels, each pixel having a [grayscale](https://en.wikipedia.org/wiki/Grayscale "Grayscale") value between 0 and 255 inclusive. After the routine has finished, the output array `dst` will contain only pixels with value 0 or value 255. During the computation, each pixel's dithering error is collected by adding it back into the `src` array. (Notice that `src` and `dst` are both read and written during the computation; `src` is not read-only, and `dst` is not write-only.)

Each iteration of the [inner loop](https://en.wikipedia.org/wiki/Inner_loop "Inner loop") modifies the values in `src[i][j]` based on the values of `src[i-1][j]`, `src[i][j-1]`, and `src[i+1][j-1]`. (The same dependencies apply to `dst[i][j]`. For the purposes of [loop skewing](https://en.wikipedia.org/wiki/Loop_optimization#Common_loop_transformations "Loop optimization"), we can think of `src[i][j]` and `dst[i][j]` as the same element.) We can illustrate the dependencies of `src[i][j]` graphically, as in the diagram on the right.

```
#define ERR(x, y) (dst\[x\]\[y\] - src\[x\]\[y\]) void dither(unsigned char\*\* src, unsigned char\*\* dst, int w, int h) { int i, j; for (j \= 0; j < h; ++j) { for (i \= 0; i < w; ++i) { int v \= src\[i\]\[j\]; if (i \> 0) v \-= ERR(i \- 1, j) / 2; if (j \> 0) { v \-= ERR(i, j \- 1) / 4; if (i < w \- 1) v \-= ERR(i + 1, j \- 1) / 4; } dst\[i\]\[j\] \= (v < 128) ? 0 : 255; src\[i\]\[j\] \= (v < 0) ? 0 : (v < 255) ? v : 255; } } } 
```

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a9/Polytope_model_skewed.svg/220px-Polytope_model_skewed.svg.png)](https://en.wikipedia.org/wiki/File:Polytope_model_skewed.svg)

The dependencies of

`src`

, after loop skewing. The array elements will be processed in the order

_gray, red, green, blue, yellow..._

Performing the affine transformation (p,t)=(i,2j+i){\\displaystyle (p,\\,t)=(i,\\,2j+i)}![(p,\, t) = (i,\, 2j+i)](https://wikimedia.org/api/rest_v1/media/math/render/svg/5aca8b12993b71d5f1bb6cd57dcaf41e7914fbd1) on the original dependency diagram gives us a new diagram, which is shown in the next image. We can then rewrite the code to loop on `p` and `t` instead of `i` and `j`, obtaining the following "skewed" routine.

```
 void dither\_skewed(unsigned char \*\*src, unsigned char \*\*dst, int w, int h) { int t, p; for (t \= 0; t < (w + (2 \* h)); ++t) { int pmin \= max(t % 2, t \- (2 \* h) + 2); int pmax \= min(t, w \- 1); for (p \= pmin; p <= pmax; p += 2) { int i \= p; int j \= (t \- p) / 2; int v \= src\[i\]\[j\]; if (i \> 0) v \-= ERR(i \- 1, j) / 2; if (j \> 0) v \-= ERR(i, j \- 1) / 4; if (j \> 0 && i < w \- 1) v \-= ERR(i + 1, j \- 1) / 4; dst\[i\]\[j\] \= (v < 128) ? 0 : 255; src\[i\]\[j\] \= (v < 0) ? 0 : (v < 255) ? v : 255; } } } 
```

See also
--------

External links and references
-----------------------------

<img src="https://en.wikipedia.org/wiki/Special:CentralAutoLogin/start?type=1x1" alt="" title="" />

  
  
from Hacker News https://ift.tt/2pPw39u