---
title: 'How to Enable Microphone and GPU Acceleration in Linux on Chromebook'
date: 2020-01-06T11:09:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  

While [Linux support](https://beebom.com/how-use-linux-chromebook/) was announced two years back on Chromebooks, there were some basic features that were missing during the launch. However, Google seems to be catching up now as it’s spearheading to make [Chrome OS a viable platform](https://beebom.com/best-chrome-os-tips-tricks/) for everyone. For instance, now you can enable microphone and GPU acceleration in Linux on [Chromebooks](https://beebom.com/what-is-a-chromebook/). Both of these features were a long-standing demand from creative and power users and finally, Google has delivered the promise. So without further delay, let’s go ahead and learn how to enable Microphone support and hardware acceleration in Linux on Chrome OS.  

Enable Microphone Support in Linux on Chromebook
------------------------------------------------

  

You can enable the microphone in Linux on Chromebooks right now and for that, you don’t need to change your update channel or [move to the Developer Mode](https://beebom.com/how-turn-chromebook-developer-mode/). The feature is **available in the stable channel of Chrome OS 79**, but it’s disabled by default. So let’s go ahead and enable the microphone in Linux on Chrome OS.  

1\. Open Chrome browser and **press Ctrl + Alt + T shortcut** to open the Crosh Shell. If you don’t know, [Crosh Shell](https://beebom.com/chrome-os-commands-run-crosh/) is the native command line for Chrome OS.  

2\. Once here, **execute the below commands one by one**. Keep in mind, it will close all the [Linux apps](https://beebom.com/best-linux-apps-chromebook/) running in the background so save and close them before executing these commands.  

```
vmc stop termina  
vmc start termina --enable-audio-capture
```  

![Enable Microphone Support in Linux on Chromebooks](https://beebom.com/wp-content/uploads/2020/01/Enable-Microphone-Support-and-GPU-Acceleration-in-Linux-on-Chromebooks-2.jpg)

3\. Now, **open the Linux Terminal to fully restart the services** and then open any [audio-recording application](https://beebom.com/best-screen-recording-apps-android/). Here, I have used Audacity and it recorded my voice clearly which confirms microphone support in Linux on Chromebooks.  

_**Note:** You will have to change the recording device to `sysdefault: Line:0` in Audacity._  

![Enable Microphone Support in Linux on Chromebooks](https://beebom.com/wp-content/uploads/2020/01/Enable-Microphone-Support-and-GPU-Acceleration-in-Linux-on-Chromebooks-4.jpg)

You can also **use your earphones and other audio devices** through the USB plug. The best part about this feature is that now along with Linux apps, you can also take benefit of the microphone on [Windows apps running in Chrome OS](https://beebom.com/how-use-windows-10-apps-chromebook-using-wine/) as well.

  
  

  

Enable GPU Acceleration in Linux on Chromebooks
-----------------------------------------------

  

Before we begin, let me clarify that GPU acceleration has been added **in select Chromebooks only having “Fizz” and “nami” baseboard** as of now. So, if you own one of these [latest Chromebooks](https://beebom.com/best-chromebooks-you-can-buy/) then you can enable GPU acceleration on your Chromebook right now.  

*   Google Pixelbook (eve)
  
*   Pixelbook 2
  
*   HP X360 Chromebook 14
  
*   Acer Chromebook Spin 13
  
*   Dell Inspiron 14
  
*   Dell Latitude 5300
  
*   Acer Chromebook 714 / 715
  
*   Lenovo Yoga Chromebook C630
  
*   Acer Chromebook 13
  
*   Samsung Pro V2
  

1\. Open the Chrome browser and move to the [Chrome Flags](https://beebom.com/google-chrome-flags/) page.  

```
chrome://flags
```  

2\. After that, **search for “Crostini GPU Support”** and enable it from the drop-down menu. You can also directly open the dedicated flag from the below address. Now, click on the “Restart” button at the bottom.  

```
chrome://flags/#crostini-gpu-support
```  

![](https://beebom.com/wp-content/uploads/2020/01/Enable-Microphone-Support-and-GPU-Acceleration-in-Linux-on-Chromebooks-3.jpg)

3\. To confirm if GPU acceleration has been enabled or not, open the [Linux Terminal](https://beebom.com/essential-linux-commands/) and run the below command. **If it mentions “Device: virgl” and “Accelerated: Yes”** then you are done. You can now play [desktop-level games](https://beebom.com/best-chromebook-games/) and use graphics-intensive Linux apps on your Chromebook effortlessly. Enjoy!  

```
glxinfo -B
```  

![Enable GPU Acceleration in Linux on Chromebooks](https://beebom.com/wp-content/uploads/2020/01/Enable-GPU-Acceleration-in-Linux-on-Chromebooks.jpeg)

Make Your Chromebook a Powerful Machine
---------------------------------------

  

So that was our short guide on how to enable microphone support and GPU Acceleration in Linux on Chromebooks. These were two of the most highly-sought features from the creative and gaming community and Google has finally walked the talk. With the recent addition of [Android app sideloading on Chromebook](https://beebom.com/how-sideload-android-apps-chromebook/), Google has made amply clear that it’s taking the platform seriously. Now, all we need is USB support in Linux on Chromebooks. As and when that happens, we will definitely let you know. Anyway, that is all from us. So what do you think of these two new additions on Chrome OS? Let us know in the comment section below.  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/enable-microphone-gpu-acceleration-linux-chromebook/)  
\[the\_ad id='1307'\]