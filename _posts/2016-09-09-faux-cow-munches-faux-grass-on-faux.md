---
title: 'Faux Cow Munches Faux Grass On A Faux Roomba'
date: 2019-10-25T06:07:00+01:00
draft: false
---

Out in the countryside, having a cow or to wouldn’t be a big deal. You can have a cattle shed full of them, and no one will bat an eyelid. But what if you’re living in the big city and have no need of pet dogs or cats, but a pet cow. It wouldn’t be easy getting it to ride in the elevator, and you’d have a high chance of being very, very unpopular in the neighbourhood. \[Dane & Nicole\], aka \[8 Bits and a Byte\] were undaunted though, and built the [Moomba – the Cow Roomba](https://www.hackster.io/8bitsandabyte/mooomba-the-cow-roomba-be3a52) to keep them company in their small city apartment.

The main platform is built from a few pieces of lumber and since it needs to look like a Roomba, cut in a circular shape. Locomotion comes from two DC geared motors, and a third swivel free wheel, all attached directly to the wooden frame. The motors get their 12V juice from eight “AA” batteries. The free range bovine also needs some smarts to allow it to roam at will. For this, it uses a Raspberry Pi powered by a power bank. The Pi drives a 2-channel relay board which controls the voltage applied to the two motors. Unfortunately, this prevents the Moomba from backing out if it gets stuck at a dead end. For anyone else trying to build this it should be easy enough to fix with an electronic speed controller or even by adding a second 2-channel relay board which can reverse the voltage applied to the motors. The Moomba needs to “Moo” when it feels like, so the Raspberry Pi streams a prerecorded mp3 audio clip to a pair of USB speakers.

If you see the video after the break, you’ll notice that making the Moomba sentient is a simple matter of doing “ctrl+C” and “ctrl+V” and you’re good to go. The python code is straight forward, doing one of four actions – move forward, turn left, turn right or play audio. The code picks a random number from 0 to 3, and then performs the action associated with that number. Finally, as an added bonus, the Moomba gets a lush carpet of artificial green grass and it’s free to roam the range.

At first sight, many may quip “where’s the hack” ? But simple, easy to execute projects like these are ideal for getting younglings started down the path to hacking, with adult supervision. The final result may appear frivolous, but it’ll excite young minds as they learn from watching.

  
  
from Hackaday https://ift.tt/2Phypf1  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)