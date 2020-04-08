---
title: 'The Basil Speaks to Me – soil moisture
readings #Sensors #Automation @electr_bob'
date: 2019-11-07T18:28:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/11/Untitled-23.png)

[ElectroBob posts](http://www.electrobob.com/the-basil-speaks-to-me-part-2/) about using a 555 based moisture sensor monitoring basil plants with automatic watering when things become a bit dry.

> The watering algorithm is very simple: I wait until the moisture level drops under a low threshold. Then I go into water mode: as long as the sensor reads below the high threshold, I water it for a few seconds. Once it hits the high threshold, it stops watering.
> 
> This means that the watering happens bit by bit, with the pump running for 2 seconds every 5 minutes while the moisture is brought from the low threshold to the high threshold. Then the plant it left to mind its business until the moisture drops below the low threshold again. The goal of this approach is to not waste water by running the pump too long and to allow the water to diffuse in the soil so I don’t read less humidity than there is water in the soil.

The resulting soil moisture over the last 7 weeks looks like this:

![](http://www.electrobob.com/wp-content/uploads/2019/11/basil_humidity_graph-600x122.jpg)

> The algorithm seems to work at maintaining the moisture between 80% and 50%. Yes, there are some weird values read out by the sensor on the right side, where moisture appears over 100. I am checking those. Another thing to see on the graph is that the last 7 days on the right the time resolution is higher, while the left part is down sampled. Due to that, it is possible that the 80% peak is lost.

[See the entire post here](http://www.electrobob.com/the-basil-speaks-to-me-part-2/).

See [Adafruit Learning System tutorials on monitoring plant moisture here](https://learn.adafruit.com/search?q=moisture).