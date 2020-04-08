---
title: 'Poor man''s PoE for Raspberry pi-3 under $2'
date: 2019-09-28T05:57:00+01:00
draft: false
---

![](https://1.bp.blogspot.com/-m1t3I2xKvm4/XYu9az889TI/AAAAAAAAUHo/DdwIbcESPU0YRoH0LSrU2UjIBYUlJ-S0ACLcBGAsYHQ/w1200-h630-p-k-no-nu/20190925_195022.jpg "Albert: Poor man's PoE for Raspberry pi-3 under ~$2")  

**Warning: This blog is about powering your raspberry pi-3 over ethernet cable(length upto 100Meters), It uses Passive PoE mechanism where T568b wire color ** **Blue/Blue-White is used  for     +(positive) terminal of DC supply** **Brown-White/Brown is used for -(negetive) terminal of DC supply** **If you dont know what is a passive PoE, then dont proceed!!!**

, instead buy a proper PoE Hat for Raspberry pi-3.

If you are a tinkerer/hw-enthusiest/diy-hobbyist(and you know what you are doing), here is what you need,

**1)PoE Injector cable(costs less than 80cents)** **2)DC-DC buck converter from aliexpress that costs less than 50cents(Look for Hesai brand).** **3)female-to-female jumper wire(cut into 4 pieces) and solder as shown in the picture** **4)Cover DC-DC converter in a heatshrink sleev, and connect to raspi-3 as shown.** **5)Feed 12v-DC and  Network-connection to the PoE Injector and connect CAT-5 cable(upto 100m) between Injector cable and Raspberry-Pi-3 as shown below**

  
  
from Hacker News https://ift.tt/2niWrdB