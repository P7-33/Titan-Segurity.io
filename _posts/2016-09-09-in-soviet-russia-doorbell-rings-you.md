---
title: 'In Soviet Russia, Doorbell Rings You'
date: 2020-01-14T07:18:00+01:00
draft: false
---

We can imagine that the origin of the doorbell is truly ancient. if you lived in a cave, you probably had a stick and a rock nearby for people to get your attention without invading your cave. In 1817 a Scot named William Murdoch had a bell in the house that visitors rang via a compressed air system, but the electric doorbell had to wait until 1831. Since then, little has changed with the basic idea. \[Erientes\] — who lives in the Netherlands, not Russia — wanted a smarter doorbell. In particular, he’s read about older people being victimized by people who ring the doorbell for entry. So \[Erientes\] used a Raspberry Pi to make [a doorbell that supports facial recognition](https://www.instructables.com/id/Doorbell-With-Face-Recognition/).

The exercise is really more of an operations challenge than a technical one thanks to a high-quality Python library for [face recognition](https://github.com/ageitgey/face_recognition) powered by DLib. However, we did like the user interface aimed at non-technical users. The metaphor is a traffic light in which a red light means do not allow entry. The lights are buttons, so you can use them to whitelist or blacklist a particular person.

We could see this being coupled with a keypad to make a two-factor access control system. To unlock the door, you have to present your face and enter a code number. While it is true that the facial recognition system isn’t perfect, the chances that someone would learn your code and be able to duplicate your face well enough to fool the algorithm seems pretty slim.

If you want to play with the facial recognition online, you [won’t need to install any software](https://beta.deepnote.com/project/a72491db-ee65-4a47-9843-575e1afc71bd). That’s a great use of [Jupyter](https://hackaday.com/2019/02/22/drops-of-jupyter-notebooks-how-to-keep-notes-in-the-information-age/). As for fooling facial recognition, maybe [this project needs a bit more work](https://hackaday.com/2019/10/31/be-anyone-or-anything-with-facial-projection-mask/).

  
  
from Hackaday https://ift.tt/2QRCTcP  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)