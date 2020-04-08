---
title: 'Floating Point C vs. C++'
date: 2019-11-12T02:03:00+01:00
draft: false
---

This post did not turn out as I expected. It started out to be a post about the quirks of floating point arithmetic, and it turned into a post about C vs C++.

It all started with an example by Jean-Michael Muller that I found in John Gustafson’s book [End of Error](https://amzn.to/36ZHaB1). The task is to evaluate the following function at 15, 16, 17, and 9999.

![\begin{align*} e(x) &= \frac{\exp(x) - 1}{x} \\ q(x) &= \left| x - \sqrt{x^2 + 1}\right| - \frac{1}{x + \sqrt{x^2 + 1}} \\ h(x) &= e(q(x)^2) \\ \end{align*}](https://www.johndcook.com/jmmuller.svg)

Here _e_(0) is defined by continuity to be 1.

This example was fiendishly designed to point out what could go wrong with floating point arithmetic, even with high precision.

If you directly implement the functions above in C, you will get 0 as the output, whether you use single, double, or even quadruple precision as the following code shows. However, the correct answer in each case is 1. (At least I got 0 every time. I would not be surprised if different compilers gave different results. More on that shortly.)

```
  
 #include #include #include #define T \_\_float128  
   
 T e(T x) {  
 return x == 0. ? 1. : (exp(x) - 1.)/x;  
 }  
   
 T q(T x) {  
 return fabs(x - sqrt(x\*x + 1.)) - 1./(x + sqrt(x\*x + 1.));  
 }  
   
 T h(T x) {  
 return e( q(x)\*q(x) );  
 }  
   
 int main() {  
   
 int x\[\] = {15, 16, 17, 9999};  
 int i;  
 for (i = 0; i < 4; i++) {  
 printf("%f\\n", h((T) x\[i\]));   
 }  
 } 
```

Here `T` is defined to `__float128` for quadruple precision. You can define `T` to be `float` or `double` for single or double precision respectively.

Here’s a C++ program that uses templates instead of the C preprocessor.

```
  
 #include #include #include using namespace std;  
   
 // Example by Jean-Michel Muller  
 // Popularized by William Kahan  
   
 template e(T x) {  
 return x == 0. ? 1. : (exp(x) - 1.)/x;  
 }  
   
 template q(T x) {  
 return fabs(x - sqrt(x\*x + 1.)) - 1./(x + sqrt(x\*x + 1.));  
 }  
   
 template h(T x) {  
 return e( q(x)\*q(x) );  
 }  
   
 int main() {  
   
 int x\[\] = {15, 16, 17, 9999};  
   
 for (int i = 0; i < 4; i++) {  
 cout << h( float(x\[i\]) ) << endl;  
 cout << h( double(x\[i\]) ) << endl;  
 cout << h(\_\_float128(x\[i\]) ) << endl;  
 }  
 } 
```

This code is essentially the same, and yet it returns 1 in each case! I’m compiling both with `gcc` 4.9.2. For the C++ program I’m giving it the argument `-lstdc++` to tell it the file is C++.

A little algebra shows that the function _q_(_x_) would return 0 in exact arithmetic, but not in floating point arithmetic. It returns an extremely small but non-zero number, and the numerator of `(exp(x) - 1.)/x` evaluates to 0.

If `q(x)` returned exactly zero, `h(x)` would correctly return 1. Interestingly, if `q(x)` were a little _less_ accurate, returning a little larger value when it should return 0, _h_ would be _more_ accurate, returning a value close to 1.

I tried replacing `exp(x) - 1` with `expm1(x)`. This did not help the C code, and it broke the C++ code. That is, both programs returned all zeros. (More on `expm1` [here](https://www.johndcook.com/blog/2010/06/07/math-library-functions-that-seem-unnecessary/).)

Incidentally, `bc -l` gives the right result, no matter how small you set `scale`.

```
  
 define ee(x) { if (x == 0) return 1 else return (e(x) - 1)/x }  
 define abs(x) { if (x > 0) return x else return -x }  
 define q(x) { return abs(x - sqrt(x^2 + 1)) - 1/(x + sqrt(x^2 + 1)) }  
 define h(x) { return ee( q(x)^2 ) }  
 
```

Related posts
-------------

  
  
from Hacker News https://ift.tt/2CBoNUV