---
title: 'The Arduino IDE Finally Grows Up'
date: 2019-10-21T12:01:00+01:00
draft: false
---

While the Arduino has a very vocal fan club, there are always a few people less than thrilled with the ubiquitous ecosystem. While fans may just dismiss it as sour grapes, there are a few legitimate complaints you can fairly level at the stock setup. To address at least some of those concerns, Arduino is rolling out the [Arduino Pro IDE](https://blog.arduino.cc/2019/10/18/arduino-pro-ide-alpha-preview-with-advanced-features/) and while it doesn’t completely address every shortcoming, it is worth a look and may grow to quiet down some of the other criticisms, given time.

For the record, we think the most meaningful critiques fall into three categories: 1) the primitive development environment, 2) the convoluted build system, and 3) the lack of debugging. Of course, there are third party answers for all of these problems, but now the Pro IDE at least answers the first one. As far as we can tell, the IDE hides the build process just like the original IDE. Debugging, though, will have to wait for a later build.

We were happy to see a few things with the new IDE. There’s some autocompletion support, Git is integrated, and there’s still our old friend the serial monitor. The system still uses the [Arduino CLI](https://hackaday.com/2018/08/26/arduino-gets-command-line-interface-tools-that-let-you-skip-the-ide/), so that means there isn’t much danger of the development getting out of sync. The actual editor is Eclipse Theia. People typically either love Eclipse or hate it, however, it is at least a credible editor. However, Theia uses Electron which makes many people unhappy because Electron applications typically eat a lot of resources. We’ll have to see how taxing using the new Pro IDE is on typical systems with normal workloads.

On the future feature list is our number one pick: debugging. They are also promising support for new languages, third party plugins, and synchronization with the Web-based editor. All good features.

This is just an alpha preview release, but it is a great start. Our only question is will existing users really care? Most people already write code in another editor. Many use an external build system like [PlatformIO](https://hackaday.com/2017/04/07/platformio-and-visual-studio-take-over-the-world/). [Eclipse already has a plug in for Arduino](https://hackaday.com/2015/10/30/code-craft-using-eclipse-for-arduino-development/) that supports debugging with the right hardware. So while new users may appreciate the features, advanced users may be wondering why this is so late to the party.

  
  
from Hackaday https://ift.tt/2By3GC8  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)