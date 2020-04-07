---
title: 'Using Machine Learning to “Nowcast” Precipitation in High Resolution'
date: 2020-01-16T06:22:00+01:00
draft: false
---

![](https://1.bp.blogspot.com/-JEPbuWisBas/Xhyq_qjRgbI/AAAAAAAAFL0/VauDukDx-lo0n6WHdx0LmaB_MDu-4fpQQCLcBGAsYHQ/w1200-h630-p-k-no-nu/WeatherPatterns.gif " Google AI Blog: Using Machine Learning to “Nowcast” Precipitation in High Resolution ")  

  
  
from Hacker News https://ift.tt/2tcGiJW

**Top (left to right):** The first three panels show radar images from 60 minutes, 30 minutes, and 0 minutes before now, the point at which a prediction is desired. The right-most panel shows the radar image 60 minutes after now, i.e., the ground truth for a nowcasting prediction. **Bottom Left:** For comparison, a vector field induced from applying an optical flow (OF) algorithm for modeling advection to the data from the first three panels above. Optical flow is a computer vision method that was developed in the 1940s, and is frequently used to predict short term weather evolution. **Bottom Right:** An example prediction made by OF. Notice that it tracks the motion of the precipitation in the bottom left corner well, but fails to account for the decaying strength of the storm.