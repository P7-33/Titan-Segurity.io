---
title: 'The Smart Home Gains An Extra Dimension'
date: 2019-12-30T04:26:00+01:00
draft: false
---

With an ever-growing range of smart-home products available, all with their own hubs, protocols, and APIs, we see a lot of DIY projects (and commercial offerings too) which aim to provide a “single universal interface” to different devices and services. Usually, these projects allow you to control your home using a list of devices, or sometimes a 2D floor plan. \[Wassim\]’s project aims to take the first steps in providing a 3D interface, by creating an [interactive smart-home controller in the browser](https://hackaday.io/project/169046-smart-home-3d-webapp).![](https://hackaday.com/wp-content/uploads/2019/12/3d_smarthome_demo.gif?w=400)

Note: this isn’t just a rendered image of a 3D scene which is static; this is an interactive 3D model which can be orbited and inspected, showing information on lights, heaters, and windows. The project is well documented, and the code can be found on [GitHub](https://github.com/HomeSmartMesh/smart_home_3d_webapp). The tech works by taking 3D models and animations made in Blender, exporting them using the .glTF format, then visualising them in the browser using three.js. This can then talk to Hue bulbs, power meters, or whatever other devices are required. The technical notes on this project may well be useful for others wanting to use the Blender to three.js/browser workflow, and include a number of interesting demos of isolated small key concepts for the project.

We notice that all the meshes created in Blender are very low-poly; is it possible to easily add subdivision surface modifiers or is it the vertex count deliberately kept low for performance reasons?

This isn’t our first unique home automation interface, we’ve previously written about [shAIdes, a pair of AI-enabled glasses that allow you to control your devices just by looking at them.](https://hackaday.com/2019/08/15/home-automation-at-a-glance-using-ai-glasses/) And if you want to roll your own home automation setup, we have plenty of resources. The Hack My House series contains valuable information on [using Raspberry Pis in this context](https://hackaday.com/2018/09/26/hack-my-house-raspberry-pi-as-infrastructure/), we’ve got information on [picking the right sensors](https://hackaday.com/2019/04/16/picking-the-right-sensors-for-home-automation/), and even [enlisting old routers for the cause](https://hackaday.com/2016/10/26/converting-a-tp-link-router-to-mission-control-for-cheap-433mhz-home-automation/).

  
  
from Hackaday https://ift.tt/2Qv5IKz  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)