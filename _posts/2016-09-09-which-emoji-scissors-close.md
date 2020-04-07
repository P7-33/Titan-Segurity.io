---
title: 'Which Emoji Scissors Close?'
date: 2020-01-03T04:06:00+01:00
draft: false
---

Which emoji scissors close
==========================

2020/01/02

Ah, scissors. They’re important enough that we have an emoji for them. On your device, it appears as ✂️. Unlike the real world tool it represents, the emoji’s job is to convey the idea, especially at small sizes. It doesn’t need to be able to swing or cut things. Nevertheless, let’s judge them on that irrelevant criterion.

Methodology
-----------

Conveniently, the emojis studied in this post depict the scissors from a viewpoint parallel to the axis of the hinge. This allows us to simulate swinging the blades with basic image rotations. I collected a dataset of emojis from different vendors from [Emojipedia](https://emojipedia.org/black-scissors/). In the following experiments, I swing the blades around the hinge until the handles collide with each other.

The evaluation is all subjective.

Left handed scissors
--------------------

It turns out that some vendors depict left handed scissors, where the top blade swings counterclockwise. I’ve put these in their own bracket.

### Messenger

![](https://wh0.github.io/assets/2020/scissors-messenger-open.png)

![](https://wh0.github.io/assets/2020/scissors-messenger-closed.png)

You get use out of about half of the blade. It’s not great.

### Samsung

![](https://wh0.github.io/assets/2020/scissors-samsung-open.png)

![](https://wh0.github.io/assets/2020/scissors-samsung-closed.png)

These scissors achieve about the same, with half of the blade being usable. But these ones look like they are better at poking than Messenger’s, so I gave them a slight lead.

### JoyPixels 🥇

![](https://wh0.github.io/assets/2020/scissors-joypixels-open.png)

![](https://wh0.github.io/assets/2020/scissors-joypixels-closed.png)

These are very good! It’s probably within the margin of experimental error that they don’t close all the way. JoyPixels receives the gold medal in left handed scissors.

Right handed scissors
---------------------

Now on to the main event, the most popular type of scissors.

### Microsoft

![](https://wh0.github.io/assets/2020/scissors-microsoft-open.png)

![](https://wh0.github.io/assets/2020/scissors-microsoft-closed.png)

Microsoft’s emoji have a heavy black outline. In my professional opinion, the outline is not part of the scissors depicted. And even with that concession, the handles collide very early. You couldn’t cut with these. I get frustrated just looking at the image of the closed position.

### Apple

![](https://wh0.github.io/assets/2020/scissors-apple-open.png)

![](https://wh0.github.io/assets/2020/scissors-apple-closed.png)

These scissors look very heavy duty. But you can’t cut very far at all.

### Google

![](https://wh0.github.io/assets/2020/scissors-google-open.png)

![](https://wh0.github.io/assets/2020/scissors-google-closed.png)

Actually it’s not very clear if these are right handed or left handed. But these close very little.

### Facebook

![](https://wh0.github.io/assets/2020/scissors-facebook-open.png)

![](https://wh0.github.io/assets/2020/scissors-facebook-closed.png)

The handles on these collide very close to the hinge, so they barely close at all. If you could file those parts down, you could close them a lot more:

![](https://wh0.github.io/assets/2020/scissors-facebook-closed2.png)

But you couldn’t, because 📁 is the only file you can get in emoji, so this altered version doesn’t count.

### WhatsApp 🥉

![](https://wh0.github.io/assets/2020/scissors-whatsapp-open.png)

![](https://wh0.github.io/assets/2020/scissors-whatsapp-closed.png)

These are pretty good. They almost fully close. WhatsApp gets third place.

### emojidex 🥈

![](https://wh0.github.io/assets/2020/scissors-emojidex-open.png)

![](https://wh0.github.io/assets/2020/scissors-emojidex-closed.png)

These close perfectly! emojidex gets second place though, because the shading doesn’t inspire confidence in the blade geometry.

### LG 🥇

![](https://wh0.github.io/assets/2020/scissors-lg-open.png)

![](https://wh0.github.io/assets/2020/scissors-lg-closed.png)

These also close perfectly. First place goes to LG!

Non-conducive depictions
------------------------

### Twitter

![](https://wh0.github.io/assets/2020/scissors-twitter-open.png)

![](https://wh0.github.io/assets/2020/scissors-twitter-closed.png)

These are left handed.

This depiction is highly simplified, so much so that it’s not clear how the handles would interact with each other. They appear to transition seamlessly from the blade, such that the two handles occupy different depths in the image. Supposing that the handle materials could “overlap” in the closed position, we would be able to swing these to the point where one handle pokes into the opening of the other handle. Even if we allow the handles to overlap, they don’t close all the way. They’d be uncomfortable too, with the place where you actually apply pressure being only half as thick as they should be.

### OpenMoji

![](https://wh0.github.io/assets/2020/scissors-openmoji-open.png)

These are right handed.

These scissors start out with the handles already overlapping. We could apply the same lenient overlapping-handles rule from the Twitter experiment, but these don’t even have the hinge drawn. I traced out the outline of the back blade to judge where would be a good place to put a hinge.

![](https://wh0.github.io/assets/2020/scissors-openmoji-hinge.png)

In order to have the hinge centered on the metal part on both sides, it would probably have to be about where the handle starts.

![](https://wh0.github.io/assets/2020/scissors-openmoji-closed.png)

With all guesswork and alterations to the experiment, these close pretty well.

My last post was about either **How to transport a convex object on a camel** or **Android Studio’s “Code contains easter egg” inspection**. Find out [which](https://wh0.github.io/2019/11/16/easter-egg-inspection.html).

Please do not write below this line.

  
  
from Hacker News https://ift.tt/37sj5SH