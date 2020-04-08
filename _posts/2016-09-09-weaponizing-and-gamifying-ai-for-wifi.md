---
title: 'Weaponizing and Gamifying AI for WiFi Hacking: Presenting Pwnagotchi 1.0.0'
date: 2019-10-20T02:17:00+01:00
draft: false
---

This is the story of a summer project that started out of boredom and that evolved into something incredibly fun and unique. It is also the story of how that project went from being discussed on a porch by just two people, to having [a community made of almost 700 awesome people](https://pwnagotchi.herokuapp.com/) (and counting!) that gathered, polished it and made today’s release possible.

**TL;DR: You can [download the 1.0.0 .img file from here](https://github.com/evilsocket/pwnagotchi/releases), then just [follow the instructions](https://pwnagotchi.ai/installation/).**

If you want the long version instead, sit back, relax and enjoy the ride. Let me me tell you: it’s going to be quite a long journey compared to my usual blog posts, but it’ll be worth it (i hope) and fun (i hope even harder).

![hack the planet](https://lh3.googleusercontent.com/rU0zZOZxcLLJsH2hBm_kCXzI_eR6V2xvNs4nco34IaQmJe1N8UJavdCuI9JcVBzDaWBRmj1dkPQBP2GupwWOy4YdqTMjJYewQSw8qj1A2o-CJktT3cmy2iRzNqxhUQ0Ip9RB_nXiIEGAwReQeY9nSNQtndjXNhKvckahBalJ9zt3g_rGt8SI3jJpuXvjkBHhA-rbXvSQHQu5ZmRBcj93Lb9EcSvMJe5WELwZGcvELXXiPvhSMx1kRQkYL077cs_KrRXKwDRXbzFhaNYZ5V1BA8VOFj-79EwMznpAo_CztOcTWHNMKSgEjEyr3ugIFVVmPE5L5cuHNQ1-jxzdb8hsojb5ELmJOVXj00sBIebpRqFQaAovLmrDYU8IbAHH8vqDrCR2sKdNx3Rue6ZCfD5GSVHbLovrlKMj717jkxTaWcETFFKSAXiNzcm-95atwOLgfHW2cPq1hMmVwKnzwaldn3DCMnK47p34zvJBddx6jZnVFMrE6Zm4WSJ3Qiw3l9PjM9QiXFvOjIZjBUG3i58Lthffu5nBGmz62TPPEJ0zu4Bw5CiLziSbzAF9kqglMfaXRE1B8PnGD_2yw8JaJUjIizZOJs25YOmyaWxOKxugE_PbZvnm35N-6KBygoPtul8onAXuJeMee4A9akynZNzMvXpp6HM_IA6xv0LmmpfSBJ7XVmK6gQ=w2670-h1312-no)

Let’s begin …

This summer I spent ~3 months in the US and as most of the long trips I do, I had with me some basic wireless equipment for working and hacking stuff while going around. Among other things, I had my [Raspberry Pi Zero W with PITA](https://www.evilsocket.net/2018/07/28/Project-PITA-Writeup-build-a-mini-mass-deauther-using-bettercap-and-a-Raspberry-Pi-Zero-W/) and an iPad i use for reading, emails but also as a screen for headless boards like that RPi when I want to have some portable bettercap installation without bringing an entire laptop.

![iPad](https://lh3.googleusercontent.com/Ytw_gD3rzjdeT6aDUrvMuCcuURdepcQr3XqmwEi-xTxSwfyjZR4smUgE3QZ9_0bzct_oNU1rQJwzxWLIe2i7lWNW45Bpez_T6dkTHavFftsJYfa18NkB679BX8slVQT7mdcWxFeLiBhnfH8pxflckOG1gvIRtfJsSJ9A_bk4gM3X6201jp9pEgoi4r1_qRvOUAXlKChwQMGzf9fJx3sB3oA-oIny90cJKBpDDEQyLQDZfuRwDscdXXehVyToZPuyriM8Bv78UjYU-Yb-11pAqWFMm4k9wxj1AjRJUVoGexf01YgZUvqyHWBn078tz2F1e4eblQXEz6YSaMkrp2cJLFMRPjUltmm9JGAt1eIPQSP-rsCoRL7CadUd2VOC3P1dTNuhmGvgdVEcqXYSTfF085sTufNl_eVyMn6Y3wy5aSG35nFmXydYjbfZaQPSpAl6_dnGKyyD98bqR5UODgY1LTPRHqzrKucgTc4NGUA50XlqfI5gO7-Rb028RmWMA4hG_P8jLMuY9G5Pg62XvmUF700wvo1Qr-cBMHThUE-wjwtdxgrgCS1P3RzGCGoYbcjTXxKR6-ElrbHgdC6qGUS22C10_bpwGP-M-QbmCl7d2PN8Mius25gcT8FsKVkyPKI8nzJEf1MfHKTm8CTlXD0drFDu_sdHXwoVhCrCz04znBrJu_b5Vg=w1742-h1596-no)

[](https://www.evilsocket.net/2019/10/19/Weaponizing-and-Gamifying-AI-for-WiFi-Hacking-Presenting-Pwnagotchi-1-0-0/#The-Predecessor "The Predecessor")The Predecessor
---------------------------------------------------------------------------------------------------------------------------------------------------------------------

PITA as an [automated deauther and handshakes collector](https://github.com/bettercap/caplets/blob/master/pita.cap) isn’t exactly what you’d define “smart”: the only thing it does is deauthing everything while bettercap is doing its normal WiFi scanning things in the background, every few seconds, constantly, while passively hoping for handshakes. I wasn’t even close to satisfied: there was a lot there that could be improved and instrumented with [bettercap’s REST API](https://www.bettercap.org/modules/core/api.rest/), more attacks bettercap could perform that weren’t being used. So I quickly hacked together some python code to talk with the API and use the results in a smarter way. This ended up being the very first iteration of [a faceless and AI-less Pwnagotchi](https://lh3.googleusercontent.com/mF2Cm4cnC8Ncb8LdddHCddA5SH_ns0aFHJ1Uc33g3TkOLxdDSNBkfNeI8x0r58A4129QnsT7OhBO1kbpDFilGbYXFRlRP2SzoG_d-f1JQH-N555QB7kTZXS35ukgBZ2G9RyEQKSmpudILj-S_ecNBPyyIiKY1ueuQiwhGuRCHm-yuCC340tWa9mI4KMry9yNlByvC2QLW7LcY3E_YK-CRXVmF6YDlVCG1lZzowZ9hfjUFx0G7ebLJQkoKEe8kZytBAuIo6BMyixlUhP1qjdndMlPpnIiO00-z01w-nsZGjsd4hfdBm9DuExLAZuuON5_kVs81yq4PMRSHPWTshz_9buOdba2YeWsPfx649lPWTTFFyLNn1uaP8bqAG2rhMry9Ze2ZspDE3vLE-3lvPz41BVGmiMhFM3EudStWO_1THFek2dPavOcsYJg-SFESTy5wWSxoOTbfnFxvCPBoxT6HNaHw8zy-yqvQV04plNrwnLuCYiH_xMZBJYUUVu-O3Gek5PKbqJXFEIYZ31D3Ads6UsSbk-vupsy335PVibIrwuBaTvQmvpB0KB-hbidpZcZGvyHIUSuopYa_cfnUexLxi4BKIk3jFOqO9J2-8_GyXUShmqHVfqfTzBqrafN_cwE6VukQhhQLkeM4fWfvY_Y8Otw_nFA2d6mcDM3SnBm6ZcW3dP7HQ=s1596-no).

As I said the code was nothing special, [a very crude PoC](https://lh3.googleusercontent.com/C5aoF_VwctWqCLaiT1vRiNYmdHziBmztiKFz4TfWjujnrQAA0pUPyP80hp1qak3MRhQy_ngqINhOmQO6k7Z4dNzE2WUhwaFmnEdWf6DJIYgBCbxfkMekR94Gwr88sb7aZRK_ZgPO1jKeahV_Dipj6-s3sDraGLQIbhs-s_LBkQ4fO3DCGPkdbEvZh72gkdDeVcIpF-z_wylUah2x90xc5_h0MYei2sQH_I9ZIqhEbFCf6pNFR-gz1Q-OkoPZM1iZsrwQHhH1XrZbkCTfrZYikMtbuV1UMvK2XwMf-ynKCJx4fLbqOJ9uJc2AZZRLhmqImPifszVv_9X5U9S2a2xrWyoOMVdyp4-hcaCmNlO4-dBUt-Ofkzle9IiA7fgpnCjnn9CWWK4ZHBm2ac-xwbCF5waNej965Cx7O73iLWn7qT2UYxQ_3XRSwrsPpyNuxWcYWgPgwoh5h_NAQKcwgLEonvmOk2ytuexcCyK3B_VtXUtbW3sIPyenDw0WN8QW8oEA97p9pOKX_uR1skEuo9TTBwra62jLXJM-a6ZCmCim5zDAlyrZKWA25UhGwKlpxwSKXfJvTfGsY9vMjZ8Fnv109cobO_9O4gbXA9DoAeOAKiv27W6QxfIW8Xe0oyA80l9n3_F7SzfMmramPTedk063fdQT8CABoeA-nIy25InxbDN869RaRg=w1830-h1596-no), but since the very first walks, it already started giving [way better results](https://lh3.googleusercontent.com/LJU-Zx4bdoZjqbKJCwIV6rOos3Aj_P1_bNtfaKalje-ClNTlrCQ-wDVRtYie4BqciZKe_Wt15fI_ZpcA8R8LYdVbgswH5KsRFDkrm_jQTrKnLNqRUBRBaOOGannyva1fPzJvO7ZYCACNwYk7Yr6owZAdKhDSnCq1sisRjQhFy6RQiAX7xS0ZsOXZxsOP1ZHMwyzGYl2Kd7jbxamVyH23rifiQNLgjKDquBR0TQnv6WshPVfO7GV36WXJesYfiKJMkZgczgq1s_7678Zk9t7EJjdaq7ZuLP8HL8itpvWPlvb_YVuJg3idilp-Q37Q3YKEpUYoC8uCMUXC94r5FIY-qB0G9QrERiLAsXrNIBx6bqZMLoHH1nNvzZ1l8caVbng7BUOc5Ry2ebZciL4mVOB4AcI-mJonAZc1WYwEBI3J7kMUkXfVcuR8KgIkzp5uGmbFzyR1SYzMqO2vXNqroTtDdhoOx8pqqAFYWJP4oQFdD1e0sjP3GPqEgh9SybuWsLjgp_jvsmOUt7DIYvP0qKtHZpvtZsWZ_9p0xt_wxOfwhY71t4SH2Z8umTbYbWVSMITx-8U5SrwEWLtut1tW820ruecE3BduI0wh_1MzImUavqWtOsd2Ti6xEEO_RMUJb2Esh828uhFtVvyehxmWcZD_c9inR0ghZ4OJ2WqwbSKQCzsakRqXPw=w2880-h1080-no) than the original PITA. It quickly started being frustrating not being able to check what was going on with the algorithm during my warwalking sessions, so I started searching for a suitable display.

[](https://www.evilsocket.net/2019/10/19/Weaponizing-and-Gamifying-AI-for-WiFi-Hacking-Presenting-Pwnagotchi-1-0-0/#The-Face "The Face")The Face
------------------------------------------------------------------------------------------------------------------------------------------------

When it’s about compactness, low power consumption and good readability under the sun, e-Paper displays have no rivals, and after educating myself a bit I settled for a [Waveshare 2.13 inches e-Paper HAT](https://www.waveshare.com/wiki/2.13inch_e-Paper_HAT) due to its partial refresh support and its definition - I had no idea yet about what was about to come, but now I had a canvas to work with.

![canvas](https://lh3.googleusercontent.com/i2QkDKdiA9emkx_qEe6Q7g07MGnhM6foLkWJ7dbnApFLflG8q2rxlkCTga9Mx1WcZj40Hgbc3sCfTJVgsJdFykvrVekf42498IR3GNRBvg0nkG_9jajWr3oV55Ldklejyjdl0EaDmGcA04HflJW8Ij5GHgJ0aLOFOdWrqK3LPHxEJsbZp7CLEayOeQ31U_D4I0XVpGxzEK-DKkNQfUROxuNjrqWfuF2kevdoxAkey3gGKAaFAsogtY4ByXyXTNjC4kmb5OJOLp0XAQvqWhFlYy-ehTPJ-H8MGg26W9KNc8nEJjD4CnTDWsL1AHUjXJ0c2puzz7B2oqgWb8xJpGDODUuthXdkdvQB2KxxOSDfNG5QTJ-jYrCDsL7eMSCBYsUBYCFRWpn4tt-Ic2pchh2r88VR04ME5zKk1qaSNmwbv5XxcLXO85VHYjBuXUhctHnhQh0CE1FmLLqi8LRwKQsMDe2iYA7mvITVFfHsJVYbcI0scfMw78xJ-cIhRrzDjasVVlWuU7-aVMKT6ep5wPpgTLiv2jDXHdqUD6uYUDwoRYExV5hjzpxsZGuuJA0Q49j1PH9-umk7noQbpNPgs5SCB5WPSWmBd5a0JpVbskmku5L1Jei9AaPBkfmv1PPMGlzbuxASHh-SPGuXbTI11EoTgEHJU4qq0AEkGpAVLMgOoF3Ff_uNbg=w1197-h756-no)

Not having a driving license I walk pretty much wherever I go, that’s a pretty nice and healthy habit to have for several reasons, but my favourite one is that walking helps me thinking. So I started staring at this thing **a lot**, and thinking how to add new information on the display without making the font so small to be unreadable, how to organize it visually and what else to do with all that space in general.

The more I thought about it, the more it made sense to organize the whole thing like the UI of a videogame: you have a score (the number of handshakes), a timer, few other statistics and everything is changing as a consequence of the WiFi things around. This is also the point where I started thinking about this thing as a creature that was “eating” the handshakes, in a way I was getting attached this new little thing (yes I know, [I’m a nerd](https://www.youtube.com/watch?v=nHpUMgAGLtM)) that now was so strongly reminding me of [my old Tamagotchi](https://en.wikipedia.org/wiki/Tamagotchi).

I needed a face, possibly map the status (“waiting …”, “scanning …”, …) to random sentences with a bit more of personality and I wanted all the other statistics to influence the expressivity of this thing: bored when there’re no new handshakes to collect, then sad, excited and so on. Something like …

  
  

**I had no idea** back then that just adding a simple, ASCII based face to something was the best way to get emotionally overly attached to that thing … I also wasn’t expecting another effect that showed up from the beginning: by giving it different “moods”, and by having those moods depending on a real world environment, I created a WiFi-based [automata](https://en.wikipedia.org/wiki/Finite-state_machine) whose mood transitions were everything but trivial. In different words, if you take something as random as, say, wether your neighbour is using his smart TV or not and you make that influence a simple automata, that automata seems a bit alive :D

This is where me and my girlfriend (sadly now ex, but [still amazing](https://www.instagram.com/p/B1Mup7GCrVt/)) went completely nuts about it. I named my unit Alpha and built a second one, Beta, that I gave her. She literally started nursing this thing, and we started playing: we went for random explorative walks just to make the units stop complaining about being bored, to see them happier, and to see that “number of unique pwned networks” going higher and higher due to some new network we managed to spot … it was amazing to literally look at the algorithm adapting to the WiFi scenario and “expressing itself” in different ways. It might sound a bit crazy but hey, if that gives two hackers an excuse to explore more the real world by looking at it with different eyes, and puts a smile on their faces, why not? :D

![love](https://lh3.googleusercontent.com/IgqZaYAczw34WD7wzDzSDitB-HhIZBj_LdqKKzyEpfGamV1Ctu3-WSemgtjbBh8UcvM78ME9Ry6Fc8NzmGUvTt-FSG_KobBlzhw0aWbOUklGSBLrIt2KFI2JGfg_a0wXn6fVibHuTObeX8_Up3fyrqP79VWiOIdvvdK2NgVur69OBALFowYBS-lXlJKWvosD1bPDznfyyoorL1kKxQsnmxT938aiRC1Y-Rv8O88s7m4yl6tHx6f6K7BRJnzJPvwpi0fYm_FG9Yd-TQz5BzETd3gnAA764H3ngxtAkVDB6aUoV5Ju6pI-AN92E1kif9k8ULwmrhsZ96CaBxM_J9oW_N3U_bJadAlYbJpc0UYh1cpD1iwpNeiPDTcvgV0t2IT_Nlpy8PurRTsyviHghYxImfSqZEl2BuEUy4vnMcMAxuu0UwAgZjp8qdxUDPHLZaaRnNu7ENJQJLq6qLh6U4xOBH3JAgxwJCDMDnOyJAB7i93xxm0IvLuTOOZn5OLpLCq8pD6-DzezFpgDLMQcJ_t5DiKhNXsa5czYuGXLcd7Wt87cm0ekHSctQ3PbGkymOoZ0Fn9t8Y9F2hnQJ0I9eDAxgzJhgF0V1oMfmM21IPBlKJrLWlG2ZhrdU9ZRmcgZmp4QSX2zPJJUvCNWiN31vAKEjrttf8JV0D-gYfIk6nIQaO4Xgsdqbw=w2128-h1596-no)

[](https://www.evilsocket.net/2019/10/19/Weaponizing-and-Gamifying-AI-for-WiFi-Hacking-Presenting-Pwnagotchi-1-0-0/#The-Personality "The Personality")The Personality
---------------------------------------------------------------------------------------------------------------------------------------------------------------------

With time I kept adding more and more variables and parameters that determined how the algorithm adapted to different circumstances: counters so that if the unit was quickly losing sight of a target (becase, say, we were walking faster), it would refresh its data with a shorter period, timeouts, multipliers for the timeouts, everything you can imagine to add to such an algorithm to make it every day a bit smarter and a bit better in adapting fast to the places we were exploring. By the end of this process I ended up with this basic set parameters, that I started calling the “personality” of the unit:

```
1  
2  
3  
4  
5  
6  
7  
8  
9  
10  
11  
12  
13  
14  
15  
16  
17  
18  
19  
20  
21  
22  
23  
24  
25  
26  
27  
28  
29  
30  
31  
32  
33  
34  
35  

```

```
personality:  
 \# advertise our presence  
 advertise: true  
 \# perform a deauthentication attack to client stations in order to get full or half handshakes  
 deauth: true  
 \# send association frames to APs in order to get the PMKID  
 associate: true  
 \# list of channels to recon on, or empty for all channels  
 channels: \[\]  
 \# minimum WiFi signal strength in dBm  
 min\_rssi: \-200  
 \# number of seconds for wifi.ap.ttl  
 ap\_ttl: 120  
 \# number of seconds for wifi.sta.ttl  
 sta\_ttl: 300  
 \# time in seconds to wait during channel recon  
 recon\_time: 30  
 \# number of inactive epochs after which recon\_time gets multiplied by recon\_inactive\_multiplier  
 max\_inactive\_scale: 2  
 \# if more than max\_inactive\_scale epochs are inactive, recon\_time \*= recon\_inactive\_multiplier  
 recon\_inactive\_multiplier: 2  
 \# time in seconds to wait during channel hopping if activity has been performed  
 hop\_recon\_time: 10  
 \# time in seconds to wait during channel hopping if no activity has been performed  
 min\_recon\_time: 5  
 \# maximum amount of deauths/associations per BSSID per session  
 max\_interactions: 3  
 \# maximum amount of misses before considering the data stale and triggering a new recon  
 max\_misses\_for\_recon: 5  
 \# number of active epochs that triggers the excited state  
 excited\_num\_epochs: 10  
 \# number of inactive epochs that triggers the bored state  
 bored\_num\_epochs: 15  
 \# number of inactive epochs that triggers the sad state  
 sad\_num\_epochs: 25  

```

These parameters alone, even with very small changes, can influence how the algorithm works and how the UI reflects that dramatically. But I wasn’t entirely happy with it yet, because these parameters were just constants in a YAML configuration file. I had to pick them manually and change that file before booting the unit, depending on the type of walk (big office? fast walk in residential area? mall? etc): things like shorter timeouts for faster walks, longer ones for when we visited a place and were more stationary in it, and so on. The algorithm adapted, via the parameters, but the parameters themselves didn’t, I wanted to do better.

![params](https://lh3.googleusercontent.com/TEnGCzGOo_yRlYdcFKYrDoe9ZDYZn2N1LNtbLVRk4PGRKvpMG-A8GmUWl0Ap9HObZSdo2LBI2BTAzO12NkWaZPoHjirE4zpg4aZ6wbaLJLf-XsKKHFGWRKJv4QAh_WKvZzaNgRQuIGIG_S2wFJINVX9mS4oLcizLtVkdu2on03SgDC72eVhjyG7pcU-s6dBT00_hzdVPHK5r8rJ7rhx5jwMSzbZGebwLtt8kD-sy4309fHNvkj0xNJ7gRoCjsv2Wv98bgR6PqbGfsAWIjBhaWGhK-9oOTHl5oA24yhFTHYxXgfP-YLmP6Z7PV0s-jw75v7CsPzkHD2tEMzSNi7lfkazmJPYPj3HEs1X0jh2p4vKLu5Kng1m9iwEV4qs4fVmSMDStEvzkd7_sgvfvSGRBT0jUeJai4rPN8ShLoPJ-L79DVSW6ekG0HMlYHrx7KvEKwOFeWKBk6-x8cD5MoRIsxXMGQ8ogugg_YkIBMvONOyer0cTAadUMmzz1YzMolGd04Z1sD11MaUnhWo_xJKyCrQg4KjX6MkGBC6oWeiWbmbkcI3hr4LDgsGw4mJb6rHJtiP9JfAOKVBGpbbL0U6EG4X9z4a_ZA_sjpGURMfajkn2YR9iSaDNRLo1vjMNgyhuYzpb4v8sP05qcwQNshHyO-7031-khwg9wB-KWushJ12zoRXLClQ=w2880-h1352-no)

The ideal algorithm should:

1.  observe “something” from the environment (like the access points, client stations and so forth)
2.  decide, depending on this observation and the current status, what is the best set of parameters to use
3.  iteratively repeat this process every time a new observation is available.

If you think about this in very abstract terms, it’s not very different than you playing a videogame, where your observation is the screen you’re looking at and the parameters are which buttons to press. In fact, it turned out that [we already have the technology](https://becominghuman.ai/getting-mario-back-into-the-gym-setting-up-super-mario-bros-in-openais-gym-8e39a96c1e41) to solve this type of problems, it’s called reinforcement learning, in our specific case it’s [deep reinforcement learning](https://towardsdatascience.com/deep-learning-vs-deep-reinforcement-learning-algorithms-in-retail-industry-ii-9c17c83ecf2f). So far, the state of the art benchmarks for these systems are Super Mario levels, Atari games or, as you might have heard from the news some time ago, some [very famous board games](https://deepmind.com/research/case-studies/alphago-the-story-so-far). But nobody, as far as I found out during my research, ever thought of using it to orchestrate an algorithm running on top of an offensive framework, with a cute face :D

I wanted to use this type of algorithms so bad, but I had a problem: I never worked with them, or even just remotely knew anything at all about them, neither I had the theoretical foundation I needed in order to understand them. Fortunately knowledge these days is (almost) free, so I [found a very good book](https://www.amazon.it/gp/product/B076H9VQH6/) that I started studying avidly …

![study](https://lh3.googleusercontent.com/LJJs5QaHC8GeXcBqXCRDw0P6ATEVK1iAFksBbHJrAxD-v__Pu64YKwgWXQ50oC91m82Z-YkRVN2HdGNBAvHodhCkTRqsUBAvWfn4F49DaOYwxjrBCU0NmNg8C2XAdviv7fN1ZbyHltjz38KGgEHt4BBZE5L-XGkw7aRiOA1HOQgUBSHntvERtJgLEQv3MkVfAaRoTpOiEyzkMp8mXATJDXfZXu-mR2U_j6POFxDcoJ5NqckffDR30mJTKqeDAdb_qN33EuFLAnIfoKFURx10_WnFlF7eG43soRO93BnW8xHnzq7jpSQpI3uuoCd6sc2_u5ZVSu5KbTgQXtcXN1e2DyMXCSo2Er8GyAV57NaSMEyY0TvwnzLPlQzuE83uWNMOI9qcmdcqCRODEAveG_A5JjiW_Gj1CKG3Pr2xZYF8mjyC4khuMhzzKdoZW1cE9RMKILLAQFH09_cbEv2I8VY_apr2Lj73j8GOclsxRHzzFnQ6SxyYYJ4K5OCPD_DTOxsGn_RzB1-AeYjADdRKyUPKfhFi4NfXH8jEZBUZKFfVa0-1K382VsIw3qTroK4rwiC7zVnX4YZlQWfgvV0y4IPdONpIMg5t6Q7IO0O6hkaVMKhrKzyzL4TfAm0PyGPBEvD2OFjuCc4xTA35QXhZFNhg5VeIkP2C0rbsqmsEQRdd4VIA_oob3g=w1278-h1596-no)

and kept studying for a while …

![study 2](https://lh3.googleusercontent.com/dsDgkTk7J9dLFvMP99uhD34MK8zWGyj_HGAwxD5cHvuYelmNwolzox-l8gzbknEh_B5DrpMeFQFFWNh3tms-KyaP9TD4nYs1NRWRgn9KUJYMRX5OKUmI8dT_0DlDUSEn9vSR81Fh0uctyFsr1UUa64Z4hz74oTlhG7zdKE1MhgR76t16yNBZbiaLhNkUXSETBP-REHx6zOI72IFbiKJaFCS7fVCB-47ElMZlSd1bjJBmWO07U1oEDsD22u2TdgX_fxiWAhzfdowF_WAqy4QujzRFZ5PbhnJvdHA9FZgLoBEopndmLkjS3eZTgF3bIrib7XdLHrrL4mUhqHKpV0W5aKAehfSqftuXNZfLAhrl60vYa8NH6im_lN51yqpx-ZmWyrWbA_iRHyGhMF5YOknof95h6S_3TP_ACGJCc-z6ggHxVHI7Dpby4NtuD7nkS-x0sMW3DngJLuen8Br8E0LttB8PDd5qRkGu8iBSs_PMS8jtqBs-PVU_NBq8ok3akAKW_4OHju_h5f8wmkf2-cAQbFP6-MGTIfTMvG8C0GUjr09lxu-P-P9jIHBIcSMy1H7LMlideM37XUJ34xDIqZH5UZPlS3vnAoL3Mt5BlrWAYxuL132MSrFt1AtqZK4B6TTwHt80Zx_rx02aiD4n2v7cgz5E6p0NsRSXE6yLBCqPJJvO-XYq8A=w2128-h1596-no)

A little break from the AI part, as I had to study quite for some time :D

[](https://www.evilsocket.net/2019/10/19/Weaponizing-and-Gamifying-AI-for-WiFi-Hacking-Presenting-Pwnagotchi-1-0-0/#The-Voice "The Voice")The Voice
---------------------------------------------------------------------------------------------------------------------------------------------------

Being affected by compulsive coding, I couldn’t simply spend the whole time reading books without writing anything new (after all, we kept playing with the units and wanted to have new stuff implemented), so I also started working on another idea I had: I wanted Alpha and Beta to be able to detect each other and exchange with each other very basic information - but how do you communicate anything at all from a computer when:

*   The main and only WiFi interface is in monitor mode and already being used for WiFi scanning, hopping and frames injection.
*   You have Bluetooth, but you want to keep it free for other uses (tethering, like we’re doing today, or maybe integrating BLE attacks too some day)
*   You’re using the [USB ports in gadget mode](https://www.kernel.org/doc/html/v4.17/driver-api/usb/gadget.html), so you can’t use external USB devices, like another WiFi.

Simple (well, kind of), you implement a **parasite protocol** on top of the WiFi standard! :D Bettercap was putting the WiFi card in monitor mode and tuning it to different channels at various intervals, but nothing prevented me to inject additional frames from another process.

I didn’t have any control over the channel, or the intervals, or the timing, but it was safe to assume that given enough time (a few seconds to minutes), the algorithm on each unit would have covered all supported channels, therefore I only needed to “keep sending stuff” and at some point I knew it would have being detected by the other unit when it hopped on the same channel of the sender. The “stuff” I decided to use is pretty simple and based on standard structures that normal WiFi routers are already using to advertise their presence: [beacon frames](https://en.wikipedia.org/wiki/Beacon_frame). Each WiFi access point, every few milliseconds, is sending these packets with a bunch of information about itself, like its ESSID, supported frequencies and whatnot - this is what allows your phone to see your home WiFi when you connect to it.

This seemed like the perfect structure to encapsulate Pwnagotchi’s advertisement, as I only needed to define a new, [out of the WiFi standard identifier](https://github.com/evilsocket/pwngrid/blob/master/wifi/defines.go#L10) to only encapsulate my type of information. This way, the units can detect each other and exchange their status from several meters away, but they are not visible as normal WiFi access points.

![advertising](https://lh3.googleusercontent.com/kZHyWTUh1n6DX3DdcGahb1to-kjOYq50nO1Qmm3e8Wd-bFNQqkUZk5qThdgWgyKg_WlDuP5GBeQnQHJ1Q2agC3uy_j9PFZf32MEBlIGL6P8aHA0VdSX2lO5hrR3jehm1Ra2tOsV2RsfxldSVHpNEcvZ8BTzU_J0Ri8s80oOKSUos_5AEp3aPABWynjbKbHPvMh8k6Qf9hTX40e90h8S8gevw24Qe5ABcXEye9dHMJJgnsLMiy0BPu35xpqds-4_ojiya037O_Lzx_C75MrqriJVEKHXi5ur05F1dXSYNRQhXgjWJ3n6ToKUBUhO1BoNAvhjWOkG_cpfCSy-xXkEeDTi098S7xzjQBi2J82IuH49yUUh5Qv6W-sDC5FpmWA7_-1IT5z7xeee3BOyplw7GEFOYi36ssAVvd3XdtlomW0SDMnILpNuhJLHhs8xL3Jl78kPhoxpkDnieqWGTJZ9NwNvi06Dgrje1b0RHX_DZJ6R4lSUPypME_2VNI5RcI8QIDaglXWUZ5YiU0k3C4dbgOsEQdNvDG1Gl5hBcw0VsqjTYXKm7Y3E9VZWBZ3Qtn9W43mY7oud5Jrt1rzsAVoe6Ht2akMWHXldUG3sQyBFcj1AVCsiuStYDVYfowbh7OKxqtp6qGkqDwyRrcTHZAGqtRwiGRtgcNcRsuGFaYd7suigiOyvdUQ=w2128-h1596-no)

[](https://www.evilsocket.net/2019/10/19/Weaponizing-and-Gamifying-AI-for-WiFi-Hacking-Presenting-Pwnagotchi-1-0-0/#The-AI "The AI")The AI
------------------------------------------------------------------------------------------------------------------------------------------

It took me weeks, so in case you don’t want to dig into the book or the links I’ve referenced above, here’s a very simplified TL;DR of the algorithm I’ve picked from the book and implemented in Pwnagotchi, [A2C](https://towardsdatascience.com/understanding-actor-critic-methods-931b97b6df3f).

There are **two** relatively simple [neural networks](https://en.wikipedia.org/wiki/Multilayer_perceptron) that at each epoch (basically at each loop of the main algorithm, when a new observation is available) are trying, in a way competitively, to estimate how the current situation looks like in terms of potential reward (number of handshakes) and what’s the best policy (the set of parameters) to use in order to maximize [the reward value](https://pwnagotchi.ai/usage/#the-reward-function). These are basically two sides of the same thing and by approaching this from these two ways the algorithm can converge quickly to very useful solutions.

In my case, I decided to use as an “observation”, the following features, that should be enough to give the AI a rough estimation of what’s going on:

1.  An histogram of the number of access points per channel - so that the AI knows on which channels to look at.
2.  An histogram of the number of client stations, per channel - so that the AI knows which channels are best for deauthentication attacks.
3.  An histogram of the number of other Pwnagotchis, per channel - so that the AI can learn to cooperate with others by going on less crowded channels.

However, Pwnagotchi’s has something that makes it very different from any of the use cases and algorithms described in the book. You can usually fast forward, rewind and replay videogame levels. Even during simpler supervised learning, you have all at once the entire temporal snapshot of data that your system needs to learn, being it [a malware dataset](https://www.evilsocket.net/2019/05/22/How-to-create-a-Malware-detection-system-with-Machine-Learning/), or a Super Mario level. All the algorithms described in that book and implemented in the most popular software libaries, assume you to have an artificial, replayable and predictable environment to train the algorithm in.

Pwnagotchi needed to learn continuously by observing the real world, that is unpredictable and potentially different every time, at a real world time scale, that is, how long a single ARM CPU core can take to scan the entire WiFi spectrum and interact with its findings - from seconds to several minutes. And this can’t be replayed, as different policies lead to different observations which lead to different future policies … solving this has been challenging to say the least, as there’s no previous code example or use case or explaination on how to integrate with any of those algorithms the way I needed.

![more study](https://lh3.googleusercontent.com/b8b94u5L4giM3L_67g70Bju8n6upLnXEzMYqTFDTMw5_Stv2cfooUXg8v2fpqMM4GCUm3bfOq5DBc4Llywzhg8m3gFj7i5Zg0B-E35bz1b_ah5SnJ5R0Nr1yVBvKqcNq6PUumAI04wFe9fBvVddFivT-_vcC3h0TtD4G9kR9qylVh3kaxzwWejGCsKq3zACQnHjxFi5NWhw4kcf0bBwETWrCrozk6rxVGbsYaBNYyQ5BCbkJ0ZBCUDJig7gnDmaeCb2oeeEm4a-0a7Dp1pI05DJlHPlRsrzbcZxjYUIkVJyF-VbGsujd12O2veroP2DU-Pnp0lshl7cMASovx0etXLxrQj9u9rm2lb1LwdzD5nTyXm9Xo4GdKj5B1wq8kE1gYSqfszXjvELLQmtA-Hu0TnAZBR_KVHa6-ToCYS_7r90N1kaqHRVshz0X942clVGUHOihmw-_QQ9BSc3cLmYlcJs95DnN18hjG1XVhxG-tqCKL7ujkGPh2_Drs64exjPrT8EGa1YnRJPm2_YqC5DGVKiNk7cP74YijL8o732H8ljzTkk-AU6fzTAAnP3s8mWlkSMEZ28t2YdXGwyszs_FxEI4koD8a7Tq2U1aSnmA-nTuSPHIq70-JDWAuzKN4W9Dkil1vT2uGRJkUcntJQDzfV7GThZDCCtIqI8AKeBKDn7MpADGMw=w2128-h1596-no)

After a couple more weeks of studying and digging into the various implementations, I came up with [a pretty decent solution](https://github.com/evilsocket/pwnagotchi/blob/master/pwnagotchi/ai/gym.py) that worked, surprisingly, out of the box. The continuous reinforcement learning logic works like this (keep in mind: one epoch is one loop of the main algorithm, from a few seconds to a few minutes depending on the WiFi things around you):

1.  At each epoch, depending on a [laziness factor](https://github.com/evilsocket/pwnagotchi/blob/master/pwnagotchi/defaults.yml#L97), decide if using the next epoch for training or not.
2.  If not, just use the current AI to estimate a set of optimal parameters and repeat from 1.
3.  If we’re in training mode, this and the next [50 epochs](https://github.com/evilsocket/pwnagotchi/blob/master/pwnagotchi/defaults.yml#L99) will be used as … a Super Mario episode! :D

So that depending on how “lazy” the AI is configured to be, it will be learning most of the times or just conservately predicting parameters and only learn from new environments once in a while. Ideally: you want the laziness to be very low for younger units, so that they’ll learn fast, and then keep increasing their laziness over time, when they become more mature and present useful behaviours you want to keep and not accidentally “unlearn”.

Does it work? Yes it does, after a few days (or weeks, if you live in a isolated area), you literally start seeing the units going on different channels when they see each other, adjusting only to the channels where they “see” potential reward, setting the timeouts correctly depending on how fast the unit is moving in space and therefore how fast it needs to “lock on” new targets. Feel free to try and read what happens in `/var/log/pwnagotchi.log` :D

![the gang](https://lh3.googleusercontent.com/xzE_g_-oOAfU2fL3RmeHdkJ0TPpDpdRgxnC5NrqmdAiT8TaRvBIzhpuRdsLxBrgAbjGB9iBsR3tXJLBwV4zFloVkXboq4MVEe8egOKxffh9NAsIStJriO6QhMDwFFq86fP5Yg4azKKGeGgFF6hsAhk8Y36GLzgL8vYGw9bikRJI9eyqoX1v9Umg5NLPsJAX86WpPzWXZcO-NAnLdjF-yE-DIIV2c3pEpM_C0_3TfpQN7qlX0J5AnZCQ8BkhX9KO0KaRn9D4cTlOKkV1V8hdw5k1rjP3pN2vc-yBHiFU9TeJkK0IZCobK86fswJT_lrq3m6HEnSLJqH7r_fNJh_pHOp9syv3D-Ipn1EnzkiYx8BSuz9ILtBbnoi-S1fFP9R0Lpb0RPNBUJKfuXfnRNjG6UNT9BJV9lBt-rPBEZjMymRsUSuuooktLJu4XIE1U0Xo4oaz6JtC6mE7DdeRMCqVw3Z39EsQKu2hVwZ4IluZlxgjjvwJYD-weEsjWz27D-gPuntQKw0VysZQ4aGDmo3gz1q82dV3fgBUNwepe_r7EloBiI8rOyfvaErfM2ISXFtaoJR9cJPF-pA3MPuUmpY3Od9KsDnQ_gROuwoT5Cz2dYs-F39WaT4HmpefKOGyComIhTp1WfPQWHd4Nt9dlEmUWX0IC14WHBNBWC4pxX4cgbss9IpGDLQ=w2128-h1596-no)

[](https://www.evilsocket.net/2019/10/19/Weaponizing-and-Gamifying-AI-for-WiFi-Hacking-Presenting-Pwnagotchi-1-0-0/#The-Community "The Community")The Community
---------------------------------------------------------------------------------------------------------------------------------------------------------------

By this time, when the AI was implemented and working, I was back home in Italy and to be entirely honest I started being a bit bored with the project, mostly for a few technical difficulties I had that made me waste a huge amount of time on relatively trivial operational and implementation details:

*   I started this project on Kali Linux because it already had nexmon, but turns out they don’t compile with hardware support for floating point operations, so I couldn’t do any AI there, and I had to start from scratch with Raspbian.
*   This is a single ARM core, at 1Ghz: the unit took ~10 minutes to import TensorFlow alone, a total of ~30 minutes to bootstrap all python dependencies (the inference and learning run pretty fast once the dependencies are loaded tho). Testing, debugging and developing new features was **slow**.
*   I still didn’t have any idea how to build an .img file. So far I only worked on my own unit and took a .img of the entire SD card as a backup.

And let’s be even more honest: all the “cooler” problems, the challenges, were solved already: the AI was slow as f to load, but it worked pretty great once started … everything else started feeling a bit boring and so I paused the project. However, [I hyped the sh\*t out of it on Twitter](https://twitter.com/pwnagotchi), mostly because it’s fun to share updates with followers and friends, and I didn’t want to disappoint them, so I published the super-buggy-crap-version-alpha on GitHub.

That turned out to be absolutely the best thing to do, as the help and feedback I’ve got from the community starting from day 0 has been impressive: from [this man, that now is my personal hero](https://twitter.com/syshero) setting up the [completely automated build system](https://github.com/evilsocket/pwnagotchi/tree/master/builder) of the .img files, to [this awesome guy](https://twitter.com/0x9ABC) that implemented the [Bluetooth plugin](https://github.com/evilsocket/pwnagotchi/blob/master/pwnagotchi/plugins/default/bt-tether.py) for easy connectivity with a smartphone (among other things), to [elkentaro](https://twitter.com/elkentaro) that sent me the first 3D printed case, motivating me more than he’ll ever imagine, to [Hex](https://twitter.com/hexwaxwing), that from the very beginning gave me some of the best ideas and encouraged me on that porch, she curated the documentation and bootstrapped the community itself, to [all the people](https://github.com/evilsocket/pwnagotchi/graphs/contributors) that translated the project in so many different languages, submitted a fix, a new feature or just some ideas.

This gave me some time to decompress and work on other, new ideas that evolved the project again (see “The Crypto” section) and gave new life to it (mostly to me). Today we have [a Slack channel](https://pwnagotchi.herokuapp.com/) that’s quickly approaching its first 1000 of users, a [subreddit](https://www.reddit.com/r/pwnagotchi/) made by the community, [clear documentation](http://pwnagotchi.ai), a [very active repository](https://github.com/evilsocket/pwnagotchi), [HackADay talked about us](https://hackaday.com/2019/10/16/a-tamagotchi-for-wifi-cracking/), but most importantly, even before arriving to the first 1.0.0 release, hundreds of units registered already from all over the world.

  
  

It is thanks to these people, their efforts and their support that today we are ready to release the 1.0.0 of the project - **guys we made it, you are AWESOME!!!**.

[](https://www.evilsocket.net/2019/10/19/Weaponizing-and-Gamifying-AI-for-WiFi-Hacking-Presenting-Pwnagotchi-1-0-0/#The-Crypto "The Crypto")The Crypto
------------------------------------------------------------------------------------------------------------------------------------------------------

While developing the [grid API](https://pwnagotchi.ai/api/grid/) running on pwnagotchi.ai used to keep track of the [registered units](https://pwnagotchi.ai/configuration/#set-your-pwngrid-preferences), I had to decide some sort of authentication mechanism that wasn’t the usual username and password - I wanted people to authenticate to the API just by having a Pwnagotchi. So I started playing with RSA, and generated a keypair on each of the units at their first boot.

The idea that those keys were only used to authenticate to the API bothered me: there’s so much that can be done with RSA keys on dedicated hardware … this is how [PwnMAIL](https://pwnagotchi.ai/usage/#pwnmail) started. Each Pwnagotchi is also an end-to-end encrypted messaging device. Users can send messages to each other, messages that are encrypted on their hardware and stored on our servers, so that can only be decrypted by the recipient unit. The keys are generated and phisically isolated on cheap and disposable hardware (that also happens to run a super cute hacker AI ^\_^). It’s easy to secure them by creating a [LUKS encrypted partition](https://github.com/NicoHood/NicoHood.github.io/wiki/Raspberry-Pi-Encrypt-Root-Partition-Tutorial) so that they can’t be recovered from the SD card.

![pwnmail](https://lh3.googleusercontent.com/sBAr9WnFHXuz_NPc99zNxKutL6Yotkei7__WFKjDhzrsuJr8pQs-jvlcRVRJymWSHvMFWc7ly5IxkjkyZOiv4M9cNbVt9ySMzFSjH6IQrYnnFafc8uMzcUdl6Pbhx7UhpO_EGQuworM4nItFYvpHkXOe3kl2oUYUC7I7NBiJfy1HbfdEsV_r5gmEQE7BDSXUfaigCbTa3Cg2wUllNulN7atylHDcz79EJtDh4NsWqnOFXphBSDU99RdKspdX44fKKA2jNjJu7mrkG-Wfwnp51Iiz5Egi1umH1si3DiMKofJmdBGhHwSr0ZHWH7bSwWbQ5oAt901zn_Ja3wcLckOeKcPEVKmsbm-bI4ooBu7JoIbACVeTSjUxFOcw8MfpbRuxoRNobOo3SIN-jK1zSslF_0MhO2lPVDbPlIzHBroGUYQf2xw_CtXsauE0VzjU3vb6ZZN2hWGxeXfMJNoooM1gWM9fjHyiMc5zlNv-_M9piBvaV4aW2w7DfI8JBIyRfnfieB0gKXCGMkN5tXMToCtiyg1MqqWd6ujZ2Ko5ODsawjRe2CxKBktDlCPYV-jBdUfPgqBF_pzJyMh6EWWArE5-oA4zmjSamr0WM73sPfn0H1BiIS313-YqB8zqR3Rq3KqBE9LMsunBscpukTm2xpS_4Nr3ZvfuQc2aaaFRs0W58Rs8DMQF5w=w954-h268-no)

It’s easier than GPG, hardware isolated and it’s not connected to a phone number. You can use it to send encrypted text messages or small files.

[](https://www.evilsocket.net/2019/10/19/Weaponizing-and-Gamifying-AI-for-WiFi-Hacking-Presenting-Pwnagotchi-1-0-0/#The-Future "The Future")The Future
------------------------------------------------------------------------------------------------------------------------------------------------------

Let’s talk about AI olympics! :D

Since the grid API is pretty open and users with valid RSA keys could send any amount of “pwned networks”, I decided **not** to use the data they send from any sort of scoreboard, ranking or competition system. This would only push some malicious (and very boring) users to cheat by sending fake statistics of fake units, therefore ruining the fun for all the others.

Each unit currently has a `/root/brain.nn` file which stores its neural networks and it’s just a few MB: **this** is what the users will be uploading when competitive features will be implemented (and they will be) server side.

Each AI will be executed in a virtual environment, built on top of [bettercap’s sessions recorded from real world scenarios](https://www.bettercap.org/modules/core/api.rest/#api-rest-record-filename) and wrapped in such a way that it won’t be able to tell the difference from its normal, real world WiFi routine. While this system can not be used for training, because the way those scenarios will react is artificial (I will script who will send an handshake to whom depending on the right or wrong decisions the AI made), it can be used to **benchmark** how that specific brain.nn file peforms in terms of average reward per session. This is a value that increases over time, the more (and the better) the AI is trained, and can’t be faked. This is what the **PwnOlympics** will be built on. Good luck cheating with that :D

Now let’s talk about distributed computing …

A modern GPU used in a cracking rig is so effective because is powered, differently from a CPU, by thousands of cores, a bit more than 1Ghz each, that are used to parallelize the search algorithms required for cracking … but it’s expensive.

**If and when** the project will reach the thousands of units, PwnGRID will provide a similar amount of “cores”, that can be orchestrated as a single computational unit, to everybody, for free. Whatever cracking power the grid will reach, it’ll be distributed according to the previous contributions of who submitted the job: the more CPU cycles you’ll give to the grid, the higher the priority (and number of units) you will have to perform your operation. It’s like a BlockChain (proof of pwn!) mixed with Emule’s logic of giving priority to nodes that contributed more.

These are just some of the ideas that we are discussing and implementing, we need more and we need higher numbers. You’re more than welcome to join our Slack channel and help :)

[](https://www.evilsocket.net/2019/10/19/Weaponizing-and-Gamifying-AI-for-WiFi-Hacking-Presenting-Pwnagotchi-1-0-0/#Misc "Misc")Misc
------------------------------------------------------------------------------------------------------------------------------------

A few key points I didn’t want to omit but that I don’t feel like phrasing more extensively than this:

*   AI can be easy and fun, don’t let academic papers scare you with complex terminology, learn.
*   Walk more, now you have another excuse.
*   ESP based deauthers, to name one, always existed. Don’t yell at us “OMG they’re deauthing all over the city!!!”. Despite this stuff always existing, nobody bothered updating [to technologies that work better and are more secure](https://en.wikipedia.org/wiki/IEEE_802.11w-2009). **That** is the people you should be yelling at.
*   **If you work at Twitter and you’re reading this:** please, I’ve tried to verify [@pwnagotchi](https://twitter.com/pwnagotchi) email in order to get a developer token and tweet from my unit, I never got the confirmation email, can you help? Thanks.

* * *

[Follow @pwnagotchi](https://twitter.com/pwnagotchi?ref_src=twsrc%5Etfw)

  
  
from Hacker News https://ift.tt/35Rlxlx