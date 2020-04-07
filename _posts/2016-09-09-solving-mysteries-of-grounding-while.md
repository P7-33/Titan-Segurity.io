---
title: 'Solving The Mysteries Of Grounding While Improving A Power Supply'
date: 2020-02-05T01:32:00+01:00
draft: false
---

Grounding problems and unwanted noise in electrical systems can often lead to insanity. It can seem like there’s no method to the madness when an electrical “gremlin” caused by one of these things pops its head out. When looking more closely, however, these issues have a way of becoming more obvious. [In a recent video](https://www.youtube.com/watch?v=VkdtESI6C74), \[Fesz Electronics\] shows us how to investigate some of these problems by looking at a small desktop power supply, modelling it in LTSpice, and reducing the noise on the power supply’s output.

While everything in this setup is properly grounded, including the power supply and oscilloscope, the way the grounding systems interact can contribute to the high amount of noise. This was discovered by isolating the power supply from earth ground using electrical tape (not recommended as a long-term solution) and seeing that the noise was reduced. However, the ripple increased substantially, so a more permanent fix was needed. For that, the power supply was modelled in LTSpice. This is where a key discovery was made: since all the parts of the power supply aren’t ideal, noise can be introduced from the actual real-life electrical behavior of some of the parts. In this case, it was non-ideal capacitance in the transformer.

According to the model, this power supply could be improved by adding a larger capacitor across the output leads, and also by increasing their inductance. A large capacitor was soldered in the power supply and an iron ferrule was added, which decreased the noise level from 100 mV to around 20. Still not perfect, but a much needed improvement to the simple power supply. If, on the other hand, you want to make sure you eliminate that transformer’s capacitance completely, you can always [go with a transformerless power supply](https://hackaday.com/2017/04/04/the-shocking-truth-about-transformerless-power-supplies/). That carries other risks, though.

  
  
from Hackaday https://ift.tt/2ubuTLc  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)