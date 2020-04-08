---
title: 'GigaSnap – Making a Prototype Device (2018)'
date: 2019-09-29T04:42:00+01:00
draft: false
---

![](https://miro.medium.com/max/1000/1*xjwwl8Bx6KRl8rntlQeL_g.jpeg "GigaSnap —A Prototyping Story - Keith Chester - Medium")  

GigaSnap —A Prototyping Story
=============================

Let’s talk about a prototype I built with my fellow developers ([Zachary Hartwick,](https://twitter.com/zachtweetsagain) [Kyle Jones](https://twitter.com/GiantToast1), and [Declan McKelvey-Hembree](https://github.com/dexo568)) about a year back. I think it’s an interesting look at how you can take simple technical solutions, and create something awesome out of it.

Let’s go back in time to the start of 2017. The B2C (business to consumer) team for [Fusion Marketing](https://thisisfusion.com/) (we created interactive digital experiences for people at events like concerts, sports stadiums — anywhere our client’s brand wanted to interact with consumers) found that we were being inundated with work, forcing us to come to the conclusion that we needed turn-key solutions we could white label in a day or two to reduce pressure on developers. We created quite a few products — including some obvious and popular ones, such as photo/gif-booths, interactive surveys, etc.

Version 1 used 6 cameras, version 2 a few weeks later switched to a single camera that ran along an internal track to the top, taking pictures the whole way.

We wanted to push the limit, however. Selfies were popular — everyone wanted to have a memento for the “I was there” social share, but how did you create something truly memorable? We tried a few years prior for one client, where we created a 20 foot metal palm tree with rising and tilting camera that would create a gif of you and the huge concert crowds or beach and ocean behind you. It worked well enough, but it was a time consuming one-off project. We wanted something cool that could be moved place to place and resold without having to figure out what other brands could use palm tree paraphernalia.

Eventually, we brainstormed the idea of the ultimate selfie — it shows you in perfect detail, but also captures the essence of you at the event — often a giant concert. The idea was to create a movie or gif, starting zoomed in as if done by a friend with a phone — and then smoothly zoom out, without a pause or hitch — until we’re a kilometer away or more — and you can see the scope of the awesome place you’re at. Imagine crowds all around you, or beautiful natural scenery.

So, Fusion took a risk and let us spend some developer time —with no guarantee of it selling — to create _GigaSnap_. And yes, we definitely debating what to name it before creating it, because you can’t create something before making a totally cool name.

Of course, the idea is simple — execution is everything. After some research, I found that, yes, there are super cameras that can take singular shots of such high resolution you can zoom in significantly. Their costs was higher than what most clients pay for complete deliverables — we’d be priced out immediately. I considered buying a telephoto lens and 3d printing a robotic controller for it — it’d rotate the lens to pre-configured positions to control a zoom in/out — but I realized there was a far simpler solution — multiple cameras.

GigaSnap being tested in Forest Park, St Louis. This is actually a **_ve_ry** steep hill — it’s a 1/3 mile distance as the crow flies from the camera to the lake.

The cameras would be equipped with different lenses for the scope of the shot —a standard 35mm for the shot of the whole area, and increasingly zoomed telephoto lenses. While the cameras would be shooting the same subject at different angles due to displacement, the difference was so minute because of overall distance away from the subject that it was negligible.

My boss with a camera lens that is borderline ridiculous

But how does one control multiple cameras? Turns out that software control of cameras are… finicky. Some camera manufacturers have APIs, but they limit who can access them. [_gphoto2_](http://gphoto.org/), which was used later in this project, could control a lot of cameras we tested, but with limited support. Not only did _gphoto2_ occasionally glitch out more-often-than-we’d-like when controlling the cameras to simple never fire off like instructed, the software had odd delays prior to the shutter of the camera firing off. Since we needed to execute each camera as close together as possible, this method wasn’t going to work well.

Our cameras featured “wireless” remotes for about $40 each, and had a proprietary port for “wired” remotes at $25 each. We picked up a wired remote and disassembled it to see if we could reverse engineer how it worked. I overestimated what I was paying for — inside were simply pieces of metal, which button presses would push down on, completing the circuit. Once the camera detected that the circuit in the remote was grounded in a certain order (with a time delay, interestingly enough, between “stages”) the camera would trigger the shutter. I bought a few more of the remotes simply so I could steal the proprietary cable connector. I wired in a few relays, connected a Raspberry Pi to control the relays with internet, used my library [serial-synapse](https://github.com/hlfshell/serial-synapse) to automate it, and then [wrap it in a socket server](https://github.com/hlfshell/serial-synapse-socket)…

I had a lot of pictures of my coworker’s unsuspecting stomach.

…and presto! We had a system that could technically trigger as many cameras as I pleased simultaneously. While the flashes pop out of tune, the pictures were as simultaneous as we could see — pictures of stop-watch apps showed the same hundredths of seconds. Perfect for our purposes.

Getting the photos off of the cameras posed another challenge. If we mounted the cameras as USB media devices, the cameras could not take photos. We tried mounting and then unmounting automatically, but sometimes cameras required a full power cycle to be detectable again. That’s not good. Enter _gphoto2_ again — however it accomplished it, its image pull functionality never failed us.

So we could download the image, but how did we associate what camera was what? Every time the Raspberry Pi booted, it would load each camera onto a different USB port. We used _gphoto2_ to modify a camera setting that took “comments” that it appended to each photo. We could query this setting whenever we scanned images, so we knew, even after reboot or complete redeployment elsewhere, which camera was which in terms of zoom.

_GigaSnap_ lived! The first prototype worked, even though this shot was a mere 200 hundred feet in range, it tested most of the core systems required for _GigaSnap_.

Once the photos were downloaded, they’d be batched and uploaded to our remote server, internet permitting. But before we go onto processing those images, let’s discuss that last bit — internet permitting. If you’ve ever worked in the event business, you’ll know that on-site internet — hell, even cell reception — is often so unreliable as to be nonexistent. WiFi slows to a crawl, and cell towers become overloaded as 40,000 people flood a usually quiet area. On top of that, _GigaSnap_ would require the camera to be set up far away from where the picture was being taken.

The general user flow for _GigaSnap_ was imagined to be a brand ambassador would tell the user what the shot would be like, where to stand, and would tell them when to pose, and finally, when the shot was done. Likewise, we needed to collect the user’s information — not only because brands love to gobble up any data it can, but we needed to know where to send the picture when it was done! To do all of this we not only needed the brand ambassador to be able to trigger the cameras from a great distance away — we needed to pass a unique identifier so we could later associated what photos went to which consumer!

Surface Pro’s running Electron apps, talking to Sparkfun’s USB XBee Explorer

With internet being unreliable, we had to explore other radio routes. Enter XBee! We picked up some [Xbee-Pro 900 XSC](https://www.sparkfun.com/products/11634)’s and [Sparkfun’s XBee Explorer](https://www.sparkfun.com/products/11812) to make a quick USB XBee interface. We created a quick chat app using Electron and tested its range — reliable to about a half mile in the center of downtown St Louis! We’re also only using the provided wire-antennae — we could improve the antennas to get even more range. These will work great for most of our shots.

Once the photos were taken, we needed to overlay them and create our movie file — so they’re uploaded remotely and then a job is queued on a Windows desktop somewhere at Fusion. This is the weird part.

We found that Adobe After Effects has a CLI — we can set certain variables that get used internally for AE in its own scripting language. We wrapped that into a custom node module and sure enough, we could soon pass in just enough information to adjust overlay positioning and which images to use. The idea was that AE would control the zoom-out effect of the video, but would “swap” the images out after a certain distance, for a seamless zoom out.

The tough part was the AE image manipulation. This bit was completely manual, and required constant supervision. For starters — little movements of the camera resulted in _large_ displacements of where the subject was in the camera, so any bumping of the camera tripod resulted in a complete re-calibration being required. Plus, while the different cameras would capture the same moment in time, they all exposed the image sensor for different lengths of time per their focal length. This resulted in highly varying levels of brightness, so we had to adjust for it. The problem was that as the daylight situation changed, so too did those adjustments. In fact, here’s what just a few hours of setup, testing, resulting in — our earlier brightness adjustments were no longer worked!

Take a look at one of our first battery and radio only tests: The script that worked well at the beginning of the shoot had some brightness issues towards the end.

I’ve since taken quite a few classes and have completed a couple of computer vision projects. Thinking about this now, I would probably figure out a way to align the camera images automatically each processing time — finding like edges and finding the maximum overlay. Once that’s accomplished, I could probably slowly fade brightness and images programmatically too — but when you’re prototyping, time is literally money, so you use what you know whenever you can. If I ever get back to it, I’ll try out those ideas.

Finally, we encountered other issues that aren’t technical at all. Even with example images — low in quantity because of the pain of setup time, it became immediately obvious that this was non-obvious. No one understood what we built. Our first ever nibble of interest asked us to set it up for a night shoot, looking down 30 stories to a pool on a balcony below. They didn’t realize that _GigaSnap_ operated on cameras, and thus needed significant amount of light to work. Even so, we tested the scenario locally — about a 14 story 2 camera setup, at night.

With prototyping done, we presented it to the sales people to try and sell to their clients. We pitched them on wide shots of consumer’s on the beach on a branded platform, the cameras stashed on some hotel balcony a half mile away. Perfect seflies on a raised platform in the middle of a crowd at a music festival. Glamour shots surrounded by party goers at a huge pool party.

In the end — clients always want innovative, fresh, unique ideas brought to them — but very few ever buy anything beyond what they know. _GigaSnap_ was never sold to anyone, and it was shelved. Maybe we’ll revive it one day when the right scenario presents itself. Maybe it’ll bring someone happiness one day. Maybe it’ll just be that cool prototype I built back in 2017.

  
  
from Hacker News https://ift.tt/2EMdmtV