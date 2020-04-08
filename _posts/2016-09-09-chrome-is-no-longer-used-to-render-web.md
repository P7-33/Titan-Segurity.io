---
title: 'Chrome is No Longer Used to Render Web Pages in Android 10'
date: 2019-09-28T06:19:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  
![](https://beebom.com/wp-content/uploads/2019/09/android-10.jpg)

Android relies on WebView for rendering web pages inside apps – the pages you see inside a lot of apps that require user inputs. Login screens are a typical example of this implementation and it is highly likely that you would have come across one if you’ve been using an Android smartphone. Ever since Android 5 Lollipop, WebView became a separate component and from Android 7 Nougat, Chrome started handling it which will be changing again on [Android 10](https://beebom.com/tag/android-10/).  

A curious Android 10 user raised an issue on the Android bug tracker regarding the disappearance of Chrome in the WebView picker, usually found inside Developer Options. Following this issue, a Google engineer stated that Android 10 has got a new implementation that they call **“Trichrome”**.  

_“Chrome is no longer used as a WebView implementation in Q+. We’ve moved to a new model for sharing common code between Chrome and WebView (called “Trichrome”) which gives the same benefits of reduced download and install size while having fewer weird special cases and bugs.”, _wrote the Google engineer.  

This essentially means that Chrome will not double up as a webview implementation anymore. However, the new WebView will be based on the Chromium project but will show no attachment to the Chrome browser app.  

Also, the Chromium project page states that there will be multiple release tracks for WebViews as well just like how it is for Chrome browser. _“For Android Q+, WebView and Chrome are again separately installed APKs. However, Google began building a separate package of WebView for each of the four Chrome channels: Stable, Beta, Dev, and Canary.”_  

_“Like with Monochrome, users can find each of these four channels of WebView on the Play Store and install them simultaneously on a single device. Also like Monochrome, users can use the “WebView implementation” menu to choose which installed WebView the system should use.”, _reads the [Chromium project page](https://chromium.googlesource.com/chromium/src/+/HEAD/android_webview/docs/channels.md).  

So, what are your thoughts on this new WebView implementation? Let us know in the comments.  

  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/web-page-rendering-android-10-no-chrome/)  
\[the\_ad id='1307'\]