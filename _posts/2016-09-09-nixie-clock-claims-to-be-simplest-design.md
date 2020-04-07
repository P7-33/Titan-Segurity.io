---
title: 'Nixie Clock Claims to be Simplest Design'
date: 2020-02-15T07:10:00+01:00
draft: false
---

\[Engineer2you\] built a [nixie tube clock](https://www.youtube.com/watch?v=Xid7gH96P8I&feature=emb_logo) and claims it is the simplest design. We felt like that was a challenge. In this design, the tubes are set up as a matrix with optoisolators on each row and column. With 60 segments, the matrix allows you to control it all with 16 bits. There are six columns, each corresponding to a digit. That means each row has 10 lines.

[The Arduino code](https://drive.google.com/file/d/1WTzW9V61LM76PSIuZmJGfKkUc8ferXjo/view) reads the clock and produces the output to the tubes fast enough that your eye perceives each digit as being always on, even though it isn’t.

It may be semantics, but part of what makes the design simple isn’t that it is simple on its own, but that it does use a small number of dense modules. For example, the clock is a DS3231, and there is a DC step up board to generate 390V for the tubes. So instead of minimizing part count, this design really minimizes how many parts you have to connect by employing modules, including the Arduino. That’s still something, though.

It looks as though the nixie tubes used are of Soviet origin. They need no more than 170V to ignite and at least 120V to stay lit. Not a problem with a simple DC to DC converter since the current is very low — on the order of 2.5 mA or so.

We suppose one day the stock of nixie tubes will be gone. But there are still [people making them](https://hackaday.com/2019/12/12/custom-nixies-perform-when-cranked-up-to-100000-hertz/). Or you can do a modern version with [light pipes](https://hackaday.com/2019/04/09/the-display-for-when-you-want-nixies-without-all-the-hassle/).

  
  
from Hackaday https://ift.tt/2USj0Ve  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)