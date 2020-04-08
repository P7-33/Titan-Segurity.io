---
title: 'Calculating signed distance fields #Math #Modeling'
date: 2019-10-24T14:29:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/10/Untitled-84.png)

From the [Almost Looks Like Work blog](https://jasmcole.com/2019/10/03/signed-distance-fields/), signed distance fields (SDFs) is a fancy name for something very simple. An SDF is just a function which takes a position as an input, and outputs the distance from that position to the nearest part of a shape.

> The question is, how are the individual SDFs combined to make a new, global SDF representing the joined object (the boolean union)?
> 
> Thinking about it for a second, we should first calculate the SDF for each circle individually – ![S_1(\mathbf{x})](https://s0.wp.com/latex.php?latex=S_1%28%5Cmathbf%7Bx%7D%29&bg=ffffff&fg=333333&s=0 "S_1(\mathbf{x})") and ![S_2(\mathbf{x})](https://s0.wp.com/latex.php?latex=S_2%28%5Cmathbf%7Bx%7D%29&bg=ffffff&fg=333333&s=0 "S_2(\mathbf{x})"). We should then return whichever circle edge is the closest, i.e.
> 
> ![\displaystyle{S_{\text{union}}(\mathbf{x}) = \text{min}(S_1( \mathbf{x} ), S_2( \mathbf{x} ))}](https://s0.wp.com/latex.php?latex=%5Cdisplaystyle%7BS_%7B%5Ctext%7Bunion%7D%7D%28%5Cmathbf%7Bx%7D%29+%3D+%5Ctext%7Bmin%7D%28S_1%28+%5Cmathbf%7Bx%7D+%29%2C+S_2%28+%5Cmathbf%7Bx%7D+%29%29%7D&bg=ffffff&fg=333333&s=0 "\displaystyle{S_{\text{union}}(\mathbf{x}) = \text{min}(S_1( \mathbf{x} ), S_2( \mathbf{x} ))}")
> 
> This is cool, and there is a great list of SDFs for different primitive shapes listed [here](http://www.iquilezles.org/www/articles/distfunctions/distfunctions.htm), but how do we actually draw the result of an SDF?

Check out the enjoyable rabbit hole [here](https://jasmcole.com/2019/10/03/signed-distance-fields/).