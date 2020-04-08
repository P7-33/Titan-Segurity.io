---
title: 'Simple Seismic Sensor Makes Earthquake Detection Personal'
date: 2019-10-29T06:09:00+01:00
draft: false
---

When an earthquake strikes, it’s usually hard to miss. At least that’s the case with the big ones; the dozens or hundreds of little quakes that go largely unnoticed every day are interesting too, and make sense to track. That’s usually left to the professionals, with racks of sensitive equipment and a far-flung network of seismic sensors. That doesn’t mean you can’t keep track of doings below your feet yourself, with something like [this DIY seismograph](http://avtanski.net/projects/seismic_sensor/).

Technically, what \[Alex\] built is better called a “seismic detector” since it’s not calibrated in any way. It’s just a simple sensor for detecting ground vibrations, whether they be due to passing trucks or The Big One. \[Alex\] lives in California, wedged between the Hayward, Calaveras, and San Andreas faults in San Jose, so there is plenty of opportunity for testing his device. The business end is a simple pendulum sensor, with a heavy metal bob hanging from a long wire inside a length of plastic pipe. Positioned close to the bob is a copper plate; the bob and the plate form an air-dielectric variable capacitor that controls the frequency of a simple 555 oscillator. The frequency is measured by a PIC microcontroller and sent to a Raspberry Pi, which displays the data on a graph. You can check in on real-time seismic activity in San Jose using the link above, or check out historical quakes, like [the 7.1 magnitude Ridgecrest quake in July](https://hackaday.com/2019/07/22/watch-earthquake-roll-across-a-continent-in-seismograph-visualization-video/). \[Alex\]’s sensor is sensitive enough to pick up recent quakes in Peru, Fiji, and Nevada, and he even has some examples of visualizing the Earth’s core using data from the sensor. How cool is that?

We’ve seen other seismic detectors before, like [this piezo-based device](https://hackaday.com/2011/12/11/detecting-seismic-waves-with-a-piezo-element/), or even [one made from toilet parts](https://hackaday.com/2019/01/22/build-a-seismometer-out-of-plumbing-parts/). We like the simplicity of the capacitive sensor \[Alex\] used, though.

  
  
from Hackaday https://ift.tt/2WjHV2M  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)