---
title: 'Compiler Explorer, Explored'
date: 2019-10-01T03:05:00+01:00
draft: false
---

It wasn’t long ago that we introduced you to a web site, the Godbolt compiler explorer, that allows the visitor to compile code using a slew of compilers and compare their output. We suspect some number of readers said, “Wow! I can use that!”, while perhaps everyone else said, “Huh?” Well if you were in the second group, you ought to watch \[What’s a Creel’s\] video below where he [walks through using the website](https://www.youtube.com/watch?v=ysaBmhMEyUg&feature=share). He looks at four different algorithms using four different compilers and it is a good example of how you might use the tool to make decisions about how you write software.

If you missed our original post about the tool, you can still [catch up](https://hackaday.com/2019/09/13/peek-into-the-compilers-code-lots-of-compilers/). Even if you don’t care much about the compiler explorer, this is an opportunity to gaze over an experienced programmer’s shoulder as he looks at some C code and generated assembly code.

The results might surprise you. In the first example, CLANG did some great optimization but other compilers created a lot of code by comparison. One of the compilers, the Microsoft compiler, had an incorrect option specified, so it didn’t so well, but would probably do better with the right options. You could always try it yourself if you are interested.

We’d love to see something like this done for [FPGAs](https://hackaday.com/2015/07/21/learn-fpgas-in-your-browser/). If you can run Docker, you might also be interestedin [PenguinTrace](https://hackaday.com/2019/05/09/examine-source-code-to-assembly-mapping-with-penguintrace/).

  
  
from Hackaday https://ift.tt/2oIZU5P  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)