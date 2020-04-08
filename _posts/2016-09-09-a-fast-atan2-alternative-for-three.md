---
title: 'A fast atan2() alternative for three-phase angle
measurement #Math #Programming'
date: 2019-10-23T16:44:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-80.png)

[Shane Colton blogs](http://scolton.blogspot.com/2019/09/fast-atan2-alternative-for-three-phase.html) about an alternative, faster algorithm to compute an arctangent in phase measurements.

> Normally, to get the phase angle of a set of (assumed balanced) three-phase signals, I’d do a [Clarke Transform](https://en.wikipedia.org/wiki/Alpha%E2%80%93beta_transformation) followed by a [atan2](https://en.wikipedia.org/wiki/Atan2)(β,α). This could be atan2f(), for single-precision floating-point in C, or some other [approximation](http://www-labs.iro.umontreal.ca/~mignotte/IFT2425/Documents/EfficientApproximationArctgFunction.pdf) that trades off accuracy for speed. The crudest (and fastest) of these is a first-order approximation atan(x) ≈ (π/4)·x which has maximum error of ±4.073º over the range {-1 ≤ x ≤ 1}.
> 
> It’s possible to extend this method to three inputs, a set of three-phase signals assumed to be balanced. Instead of quadrants, the input domain is split based on the six possible sorted orders of the three-phase signals. Within each sextant, the middle input (the one crossing zero) is divided by the difference of the other two to form a normalized input, analogous to selecting x = β/α or x = α/β in the atan2() implementation.
> 
> For this three-phase approximation the maximum error is ±1.117º, significantly lower than the four-quadrant approximation. If starting from three-phase signals anyway, this method may also be faster, or at least nearly the same speed.

See the details in the [post here](http://scolton.blogspot.com/2019/09/fast-atan2-alternative-for-three-phase.html).