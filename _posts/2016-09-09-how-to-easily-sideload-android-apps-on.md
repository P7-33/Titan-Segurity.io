---
title: 'How to Easily Sideload Android Apps on Chromebook (2020)'
date: 2020-01-03T06:36:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  

With the [release of Chrome OS 80](https://chromereleases.googleblog.com/2019/12/dev-channel-update-for-chrome-os_19.html), [Google](https://beebom.com/google-page/) has finally brought the ability to install Android apps on Chromebook without Developer Mode. This is truly great and path-breaking for both developers as well as the [Chrome OS enthusiast](https://beebom.com/best-chrome-os-tips-tricks/) community. You can finally install Android APKs that are not available on the Play Store, and for that, you don’t have to sacrifice your security. However, keep in mind, you will at least have to move from Stable to the Dev channel of updates. So without any delay, let’s go ahead and learn how to sideload Android APKs on Chrome OS.  

Sideload Android Apps on Chromebook Without Developer Mode
----------------------------------------------------------

  

Before we begin, make sure to **switch the Chrome OS from Stable to the Dev channel**. Just open Settings and move to About Chrome OS -> Additional Details -> Change Channel to Dev. Now, come back and check for updates on the “About Chrome OS” page. Thereafter, it will download and install the update automatically. Do not worry, moving to Dev Channel does not reset your Chromebook. After the update, your Chromebook should be on Chrome OS 80.0.3987.18 (Platform version: 12739.12.0).  

Keep in mind, **Dev Channel is not the same as [Developer Mode](https://beebom.com/how-turn-chromebook-developer-mode/)**. The former just brings the future (can be buggy) updates while the latter is an OS environment where security restrictions are relaxed for testing purposes. Anyway, having done that, let’s move to the steps and learn how to install Android apps on Chromebook without Developer Mode.  

1\. Open Settings and **turn on Linux (Beta)** from the left menu. If you don’t know how to do it, follow our guide from [here](https://beebom.com/how-use-linux-chromebook/).  

![8 How to Install Android Apps on Chromebook Without Developer Mode](https://beebom.com/wp-content/uploads/2020/01/8-How-to-Install-Android-Apps-on-Chromebook-Without-Developer-Mode-1.jpg)

2\. After setting up Linux, open Settings again and navigate to Linux -> Develop Android Apps -> **Enable the toggle for ADB Debugging**. Now, restart your Chromebook and an ADB prompt will come up after the reboot. Click on “Allow” and you are done.  

_**Note:** In case, ADB toggle is not turning on then you will have to reset your Chromebook. A similar thing happened with our machine as well and powerwashing the Chromebook resolved the issue._  

![](https://beebom.com/wp-content/uploads/2020/01/5-How-to-Install-Android-Apps-on-Chromebook-Without-Developer-Mode.jpg)

3\. Now, open Terminal from the app drawer and execute the below command to **install the [ADB platform tools](https://beebom.com/cool-things-adb-lets-you-do-android-device/)**. Further, press “Y” to allow the installation.

  
  

  
```
sudo apt-get install android-tools-adb
```  

![4 How to Install Android Apps on Chromebook Without Developer Mode](https://beebom.com/wp-content/uploads/2020/01/4-How-to-Install-Android-Apps-on-Chromebook-Without-Developer-Mode.jpg)

4\. After the installation, run the below command to **[connect the Android system](https://beebom.com/how-use-adb-wirelessly-android-device/) with Linux on Chrome OS**. Remember, your Chromebook should be connected to a WiFi network for this to work.  

```
adb connect 100.115.92.2:5555
```  

![](https://beebom.com/wp-content/uploads/2020/01/3-How-to-Install-Android-Apps-on-Chromebook-Without-Developer-Mode.jpg)

**If the Terminal shows “Permission Denied” or “Command Not Found”** error then run the below command and then try again with the _adb connect_ command mentioned above.  

```
adb start-server
```  

5\. A window will instantly open up to “Allow USB Debugging”. **Enable the checkbox for “Always allow”** and then click on the “Ok” button. By now, you have successfully set up the foundation.  

![7 How to Install Android Apps on Chromebook Without Developer Mode](https://beebom.com/wp-content/uploads/2020/01/7-How-to-Install-Android-Apps-on-Chromebook-Without-Developer-Mode.jpg)

*     
    
    ### Install Android App on Chrome OS
    
      
    
  

6\. Now, go ahead and **download the Android APK that is not available on the Play Store and move it to Linux files**. For example, I have downloaded the [Firefox](https://beebom.com/cool-firefox-hidden-settings/) APK to install on my Chromebook without Developer Mode.  

_**Note:** Rename the downloaded APK to something easier, just so you can easily type it on the Terminal._  

![2 How to Install Android Apps on Chromebook Without Developer Mode](https://beebom.com/wp-content/uploads/2020/01/2-How-to-Install-Android-Apps-on-Chromebook-Without-Developer-Mode.jpg)

  
  

  

7\. Open the [Terminal](https://beebom.com/essential-linux-commands/) and **type the below command to sideload the Android app** on Chrome OS. For your case, you will have to change the app name in place of _firefox_.  

```
adb install firefox.apk
```  

![](https://beebom.com/wp-content/uploads/2020/01/1-How-to-Install-Android-Apps-on-Chromebook-Without-Developer-Mode.jpg)

8\. Now, open the app drawer and you will find the Android app that you just installed. Keep in mind, **the Android app is using its [ART](https://beebom.com/dalvik-vs-art-runtime-android/) (Android Run Time) framework** and not running in a Linux container. So, the performance is great and similar to other apps downloaded from the Play Store. Enjoy!  

![6 How to Install Android Apps on Chromebook Without Developer Mode](https://beebom.com/wp-content/uploads/2020/01/6-How-to-Install-Android-Apps-on-Chromebook-Without-Developer-Mode.jpg)

Install Any Android App on Your Chromebook
------------------------------------------

  

So that was our guide on how to sideload Android apps on [Chromebook](https://beebom.com/what-is-a-chromebook/) without Developer mode. While the solution is not that straightforward, it’s much better than moving to Developer mode which is a security nightmare for general users. Also, once you set up the ADB, you just have to download the APK and you can install it via the _adb install_ command. That’s it. So that was all from our side. If you want to learn more hacks about Chromebooks and Chrome OS then stay tuned with us as we bring some interesting guide for you in the coming days. As for now, we have covered the [best Chrome OS apps](https://beebom.com/best-chrome-os-apps-install-chromebook/) in a detailed article so check that out.  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/how-sideload-android-apps-chromebook/)  
\[the\_ad id='1307'\]