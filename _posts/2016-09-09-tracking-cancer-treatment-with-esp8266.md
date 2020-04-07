---
title: 'Tracking Cancer Treatment with an ESP8266-Based Radiation Sensor'
date: 2020-01-26T07:08:00+01:00
draft: false
---

Those of us who have not been in that position can only imagine the anguish of learning that your teenager has cancer. This happened to \[Rob\], whose child was diagnosed with papillary thyroid cancer. It’s a condition that can be treated with surgery followed by a course of radioactive iodine to kill any remaining cancer cells. During iodine treatment, the patient is radioactive enough that other people must maintain a distance of 3m from them, and as a learning exercise for both father and teen he created and refined the design of [a portable wireless radioactivity monitor](https://github.com/finderoffail/radiation_sensor).

There are a variety of sensors for radiation monitoring including the well-known Geiger–Müller tube, but he settled on a PIN photodiode based sensor supplied by [radiation-watch.org](http://www.radiation-watch.org/). This sensor is not at its most sensitive at the energy levels emitted by the iodine isotope used in the treatment, but the relatively high intensity of the radiation meant that enough would register for a useful reading to be taken. The sensor board he was mated to an ESP8266 module. \[Rob\] went through three iterations of the balance of the hardware before settling on a lithium-ion battery and a plastic case.

On the software side, the ESP connects to an MQTT server, from which a CSV file of data is derived. On a computer, the CSV data is collected and plotted to a graph. The data take during treatment clearly shows the reduction in radiation following the isotope’s half-life. The graph isn’t perfect though, there is a gap due to the second prototype’s batteries running flat

From his epilogue it appears that his son has recovered, and we wish them further good health. The details have been published in the hope that other young people facing the same trial might benefit from building their own radiation monitor.

  
  
from Hackaday https://ift.tt/2O1SWTn  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)