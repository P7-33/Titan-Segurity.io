---
title: 'Show HN: uPlot.js – An exceptionally fast, tiny time series chart'
date: 2019-10-10T05:03:00+01:00
draft: false
---

![](https://avatars2.githubusercontent.com/u/43234?s=400&v=4 "GitHub - leeoniya/uPlot: An exceptionally fast, tiny time series chart")  

In order to stay lean, fast and focused the following features will not be added:

```
<link rel\="stylesheet" href\="src/uPlot.css"\> <script src\="dist/uPlot.iife.min.js"\>script> <script\>  const data \= \[  \[1566453600, 1566457260, 1566460860, 1566464460\], // Unix timestamps  \[0.54, 0.15, 3.27, 7.51 \], // CPU  \[12.85, 13.21, 13.65, 14.01 \], // RAM  \[0.52, 1.25, 0.75, 3.62 \], // TCP Out  \];   const opts \= {  width: 800,  height: 400,  cursor: true,  series: {  x: {  data: data\[0\],  },  y: \[  {  label: "CPU",  data: data\[1\],  scale: "%",  value: v \=> v.toFixed(1) + "%",  color: "red",  width: 2,  dash: \[10, 5\],  },  {  label: "RAM",  data: data\[2\],  scale: "%",  value: v \=> v.toFixed(1) + "%",  color: "blue",  },  {  label: "TCP Out",  data: data\[3\],  scale: "mb",  value: v \=> v.toFixed(2) + "MB",  color: "green",  }  \],  },  axes: {  y: \[  {  scale: '%',  values: (vals, space) \=> vals.map(v \=> +v.toFixed(1) + "%"),  },  {  side: 3,  scale: 'mb',  values: (vals, space) \=> vals.map(v \=> +v.toFixed(2) + "MB"),  grid: null,  },  \],  },  };   let uplot \= new uPlot(opts);   document.body.appendChild(uplot.root); script>
```

  
  
from Hacker News https://ift.tt/2VtMuqB