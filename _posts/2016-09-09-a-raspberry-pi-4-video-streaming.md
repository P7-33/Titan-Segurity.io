---
title: 'A Raspberry Pi 4 Video Streaming Backpack'
date: 2019-09-28T06:04:00+01:00
draft: false
---

Were you aware that there’s a market for backpack-housed live streaming video systems, and that they can cost as much as $1600? Apparently these things are popular with social media moguls who want to stream themselves living their fabulous lives to people sitting at home watching on YouTube or Twitch. But believing that even slack jawed yokels like us should have access to the same technology, \[Speedify Labs\] has been working on [less expensive DIY alternative based on the Raspberry Pi 4](https://hackaday.io/project/167778-diy-irl-streaming-backpack-using-raspberry-pi).

Now you’ll note we didn’t use the term “cheap” to describe this build. As detailed here, it’s still going to cost you around $600. You could always swap out the Sony AS-300 camera and Elgato Cam Link capture device with cheaper versions, but the goal of this project was to deliver high quality HD video that’s comparable to what the professional rigs are capable of, so those kinds of concessions were avoided.

Whatever video source your audience and budget are comfortable with, it eventually gets fed into the Raspberry Pi 4 which uses an `ffmpeg` one-liner to encode the video and ultimately push it out as 720p at 24 FPS, which \[Speedify Labs\] says seems to be about as good as the Pi can do. The operator is able to start and stop the stream at will using a Circuit Playground Express and a Python script.

Of course, the trick to all of this is getting the video stream uploaded over potentially flaky mobile networks. But as you might have guessed, that’s where \[Speedify Labs\] gets to flex their eponymous product: a VPN with software channel bonding that allows you to combine multiple Internet connections for higher bandwidth and reliability. With their software, the Pi is able to stream the video through two mobile phones connected to it over USB. As demonstrated in the video below, the setup was able to maintain the stream even as they walked in and out of buildings.

Our very own \[Lewin Day\] wrote about his experiments with [streaming video over 4G on the Raspberry Pi](https://hackaday.com/2017/09/12/video-streaming-like-your-raspberry-pi-depended-on-it/) which might be of interest to anyone looking to take their show on the road. Though if you want to get serious it would be worth taking a look at the [impressive mobile streaming rig that \[Jenny List\] saw](https://hackaday.com/2019/08/18/an-all-in-one-conference-video-streaming-box/) at the BornHack 2019 hacker camp in Denmark.

  
  
from Hackaday https://ift.tt/2mwAp73  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)