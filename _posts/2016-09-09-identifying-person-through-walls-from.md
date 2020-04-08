---
title: 'Identifying a person through walls from video footage, using only WiFi'
date: 2019-10-03T01:46:00+01:00
draft: false
---

![Researchers’ new method enables identifying a person through walls from candidate video footage, using only WiFi](https://scx1.b-cdn.net/csz/news/800/2019/researchersn.jpg)

(left) A pair of WiFi transceivers are inserted outside. The transmitter sends a wireless signal whose received power (or magnitude) is measured by the receiver. Then, given the video footage on the right — and by using only such received power measurements — XModal-ID can determine if the person behind the wall of the left figure is the same person in the video footage. Credit: B. Korany et al.

Researchers in the lab of UC Santa Barbara professor Yasamin Mostofi have enabled, for the first time, determining whether the person behind a wall is the same individual who appears in given video footage, using only a pair of WiFi transceivers outside.

This novel video-WiFi cross-modal gait-based person identification system, which they refer to as XModal-ID (pronounced Cross-Modal-ID), could have a variety of applications, from surveillance and security to smart homes. For instance, consider a scenario in which law enforcement has a [video footage](https://techxplore.com/tags/video+footage/) of a robbery. They suspect that the robber is hiding inside a house. Can a pair of WiFi transceivers outside the house determine if the person inside the house is the same as the one in the robbery video? Questions such as this have motivated this new technology.

"Our proposed approach makes it possible to determine if the person behind the wall is the same as the one in video footage, using only a pair of off-the-shelf WiFi transceivers outside," said Mostofi. "This approach utilizes only received power measurements of a WiFi link. It does not need any prior WiFi or video training data of the person to be identified. It also does not need any knowledge of the operation area."

The proposed methodology and experimental results [will appear](http://www.ece.ucsb.edu/~ymostofi/papers/MobiCom19_KoranyKaranamCaiMostofi.pdf) at the 25th International Conference on Mobile Computing and Networking (MobiCom) on October 22.

VIDEO

In the team's experiments, one WiFi transmitter and one WiFi receiver are behind walls, outside a room where a person is walking. The transmitter sends a [wireless signal](https://techxplore.com/tags/wireless+signal/) whose received power is measured by the receiver. Then, given video footage of a person from another area—and by using only such received wireless power measurements—the receiver can determine whether the person behind the wall is the same person seen in the video footage.

This innovation builds on previous work in the Mostofi Lab, which has pioneered sensing with everyday radio frequency signals such as WiFi since 2009.

"However, identifying a person through walls, from candidate video footage, is a considerably challenging problem," said Mostofi. Her lab's success in this endeavor is due to the new proposed methodology they developed.

"The way each one of us moves is unique. But how do we properly capture and compare the gait information content of the video and WiFi signals to establish if they belong to the same person?"

The researchers have proposed a new way that, for the first time, can translate the video gait content to the wireless domain.

"Our approach is multi-disciplinary, drawing from areas of both wireless communications and vision," said Chitra Karanam, one of three Ph.D. students on the project. Given some video footage, the team first utilized a human mesh recovery algorithm to extract the 3-D mesh describing the outer surface of the human body as a function of time. They then used Born electromagnetic wave approximation to simulate the RF signal that would have been generated if this person was walking in a WiFi area.

Next they employed their time-frequency processing approach to extract key gait features from both the real WiFi signal (that was measured behind the wall) and the video-based simulated signal. The two signals are then compared to determine if the person in the WiFi area is the same person in the video.

The researchers' processing pipeline involves a series of mathematical functions, including Short-time Fourier transform and Hermite functions, in order to get the spectrogram of the received signal. "A spectrogram carries the frequency-time content of the signal, which implicitly carries the gait information of the person," explained Belal Korany, another Ph.D. student involved in the effort.

Several important gait features are then extracted from both spectrograms and properly compared to declare if the person in the video is behind the wall.

"We have tested this technology extensively on our campus," said Herbert Cai, the third Ph.D. student on the project. The lab has tested their new technology on 1,488 WiFi-[video](https://techxplore.com/tags/video/) pairs, drawn from a pool of eight people, and in three different behind-wall areas, and achieved an overall accuracy of 84% in correctly identifying the person behind the wall.

* * *

* * *

**More information:**

More information about the project can be found at 

[www.ece.ucsb.edu/~ymostofi/Ide … ficationThroughWalls](https://www.ece.ucsb.edu/~ymostofi/IdentificationThroughWalls)

**Citation**: Researchers' new method enables identifying a person through walls from candidate video footage, using only WiFi (2019, October 1) retrieved 2 October 2019 from https://ift.tt/2o2DfRU

This document is subject to copyright. Apart from any fair dealing for the purpose of private study or research, no part may be reproduced without the written permission. The content is provided for information purposes only.

  
  
from Hacker News https://ift.tt/2o2DfRU