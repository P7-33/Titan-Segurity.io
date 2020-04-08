---
title: 'Grandmaster level in StarCraft II using multi-agent reinforcement learning'
date: 2019-10-31T01:12:00+01:00
draft: false
---

![](https://lh3.googleusercontent.com/jVZ3VN7wwx2dSowqLmhqm0qAzAmcb-1t7ks3HiNnoHknihF5sl9VDEwuCNTSxfx8jFIi7mBQkvHUdnSKXSPgYLNpvCuE4YajJeMnrYA "AlphaStar Resources | DeepMind")  

### Replays of Nature paper version

* * *

### Replays of previous versions

From matches between AlphaStar and [Team Liquid’s](https://www.teamliquid.com/) Grzegorz [MaNa](https://liquipedia.net/starcraft2/MaNa) Komincz, and AlphaStar and [Team Liquid’s](https://www.teamliquid.com/) Dario [TLO](https://liquipedia.net/starcraft2/TLO) Wunsch:

#### Camera interface

##### **MaNa v AlphaStar (24 January 2019)**

[Exhibition game](https://kstatic.googleusercontent.com/files/f1e83ddef39df7f0af74675cc665ddb54984bd73f9e6caf56acd4065d104db9c35d4ce564f66b2496cbc23e820a535131759c44c0947f0f1e154be8391185154)

#### Raw interface

##### **TLO v AlphaStar (12 December 2018)**

[Game 1](https://kstatic.googleusercontent.com/files/a41defaef2b6ad55d2be225ee1efa1156ba7d429a7348f36ecfd74950f685c03baa0b743635a57173aa93d0adf9563f397f3db5fcbe7c1c42eb03c9a5007ccf9)

[Game 2](https://kstatic.googleusercontent.com/files/176e8943c7c5cd3bc44434f2f3e40b676ba3a731fc66e9aa7cc2becc537ddbb23d83433d85cae46f90e1abc61443492b3bb116fa749ca3bf39907a54d7379097)

[Game 3](https://kstatic.googleusercontent.com/files/5811c130edd5be43b0be3bd7dfb817a3f0dc9acee4b7f7dfa56cb3440d0aee8acefa3d08c5e6b57219cdd9f748cccf179ec9b3f2abbd8e372efd504d0e52948e)

[Game 4](https://kstatic.googleusercontent.com/files/a6eb29bd4c698980b22408859c697e2fd50a6c3f1365a38be318ba6dfa94500a865246843df72caba7ca5baf6f9f5eac6d81e3df6f43f969167be13f4867761c)

[Game 5](https://kstatic.googleusercontent.com/files/07ca46ac2150541126f04c04ff1d1518cd7387f5a8e5316c74d4cf0eafc9d4a0f996fb110829b171741a7c9b5a77427141bda60c3cba68a20eebf0c74bb9da36)

##### **MaNa v AlphaStar (19 December 2018)**

[Game 1](https://kstatic.googleusercontent.com/files/32c35730e8b9a7ad1d07a3d52a61674d5536adc336fa88fe633e7c23c738dfbe91c6fe4b0a8f7c2ee535c4dca8808c700986657eb72b6160c305e5b34c1f3b55)

[Game 2](https://kstatic.googleusercontent.com/files/0e1feddd0f3d667109be1e08b497bbad031f6f5c647b3811817f3c219f11ccfe9a3bed901e7a7fcea65ce92dae169ae2fa57776dde02edd32812cda38a7512a1)

[Game 3](https://kstatic.googleusercontent.com/files/9b16d575e6271d2770d6e00340108e3e5bd19425d8f7d58bbc4010e2e48cca9555ebe3969a93e20ca091be650e2bc6a738525aa7603f888dac6f7701b756f418)

[Game 4](https://kstatic.googleusercontent.com/files/ad38f0a9a758c354cdf752a6309637a0086f85c30dc05e1db546522960b8754fd8eac1173b9f184a065215e2fabd152f7f70270b9d47762ec9fce15dd0316cec)

[Game 5](https://kstatic.googleusercontent.com/files/221973091c1a6b5ee66aa67b0beb3528e9e36d77dc48dd3a4b6d4a9307e9e3ee80691ac472006639fb8ff6fcb0af691f4e41d661de3aa0157da5fa9c680bba46)

Please note that the raw interface agents weren’t using the camera directly. The 10 replays have therefore been post-processed to add heuristic camera movements, such that the target location of each agent action is visible on screen. This is to make the replays easier to follow from the agent's perspective.

#### To load the replays:

*   Create the StarCraft Maps directory:

*   Windows: C:\\Program Files (x86)\\StarCraft II\\Maps

*   Mac: /Applications/StarCraft II/Maps

*   Move it into the Maps directory.

*   Download the replays above, and open them as usual.

More information on AlphaStar and the matches played between MaNa and TLO can be found on the DeepMind **[blog](https://deepmind.com/../../../../../../../blog/article/alphastar-mastering-real-time-strategy-game-starcraft-ii).**

  
  
from Hacker News https://ift.tt/2N1FbE8