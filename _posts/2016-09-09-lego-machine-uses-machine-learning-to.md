---
title: 'Lego Machine Uses Machine Learning To Sort Itself Out'
date: 2019-12-17T04:57:00+01:00
draft: false
---

In our opinion, the primary evidence of a properly lived childhood is an enormous box of every conceivable Lego piece, from simple bricks to girders and gears, all with a small town’s worth of minifigs swimming through it. It takes years of birthdays and Christmases to accumulate a Lego collection best measured by the pound, but like anything worth doing, it’s worth overdoing.

But what to do with such a collection? Digging through it to find Just the Right Piece![™](https://s.w.org/images/core/emoji/12.0.0-1/72x72/2122.png) can be frustrating, and bringing order to the chaos with manual sorting is just so impractical. How about putting some of those bricks to work with a [machine-vision Lego sorter built from Lego](https://towardsdatascience.com/a-high-speed-computer-vision-pipeline-for-the-universal-lego-sorting-machine-253f5a690ef4)?

\[Daniel West\]’s approach is hardly new – we’ve even featured [brick-built Lego sorters](https://hackaday.com/2011/04/08/nxt-machine-sorts-lego-blocks-automatically/) before – but we’re impressed by its architecture. First, the mechanical system is amazing. It uses a series of conveyors to transport bricks from a hopper, winnowing the stream down as it goes. The final step is a vibratory feeder that places one piece on a conveyor at a time. Those pass under a camera attached to a Raspberry Pi, where OpenCV does background subtraction from the video stream, applies bounding boxes to the parts, and runs the images through a convolutional neural network (CNN) that’s been trained on a database of every Lego part. Servo-controlled gates then direct the parts into one of 18 bins. See it in action in the video below.

We must admit that we’re not sure what the sorting criteria are, as some bins seem nearly as chaotic as the input mix. Still, we appreciate the fine engineering, and award extra style points for all the Lego goodness.

\[via [The Verge](https://www.theverge.com/2019/12/11/21011792/lego-ai-universal-sorting-machine)\]

Thanks to \[my wife\] for the tip.

  
  
from Hackaday https://ift.tt/35tKMde  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)