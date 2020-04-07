---
title: 'Random Numbers From Outer Space'
date: 2020-01-21T01:44:00+01:00
draft: false
---

Need a random number? Sure, you could just roll a die, but if you do, you might invite laughter from nearby quantum enthusiasts. If it’s truly, unpredictably random numbers you need, look no farther than the background radiation constantly bombarding us from the safety of its celestial hideout.

[![](https://hackaday.com/wp-content/uploads/2020/01/visit-the-anode.png?w=400)](https://hackaday.com/wp-content/uploads/2020/01/visit-the-anode.png)In a rare but much appreciated break from the Nixie tube norm of clock making, \[Alpha-Phoenix\] [has designed a muon-powered random number generator](https://www.youtube.com/watch?v=gwIGnATzBTg) around that warm, vintage glow. Muons are subatomic particles that are like electrons, but much heavier, and are created when pions enter the atmosphere and undergo radioactive decay. The Geiger-Müller tube, mainstay of Geiger counters the world over, detects these incoming muons and uses them to generate the number.

Inside the box, a 555 in astable mode drives a decade counter, which outputs the numbers 0-9 sequentially on the Nixie via beefy transistors. While the G-M tube waits for muons, the numbers just cycle through repeatedly, looking pretty. When a muon hits the tube, a second 555 tells the decade counter to stop immediately. Bingo, you have your random number! The only trouble we can see with this method is that if you need a number right away, you might have to go get a banana and wave it near the G-M tube.

Whether this all makes sense or not, you should check out \[Alpha-Phoenix\]’s project video, which is as entertaining as it is informative. He’s planning a follow-up video focused on the randomness of the G-M tube, so look out for that.

Looking for a cheaper way to catch your random numbers? [You can do it with a fish tank, some air pumps, and a sprinkle of OpenCV](https://hackaday.com/2019/12/09/generating-random-numbers-with-a-fish-tank/).

Via [r/electronics](https://www.reddit.com/r/electronics/comments/eluq11/i_just_finished_up_an_alldiscrete_quantumrandom/)

  
  
from Hackaday https://ift.tt/2RBxfdW  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)