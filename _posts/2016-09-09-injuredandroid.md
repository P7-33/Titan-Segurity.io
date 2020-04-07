---
title: 'InjuredAndroid'
date: 2020-02-15T01:31:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-DL57X-4Jm4w/XjovuwaAzpI/AAAAAAAARoE/oBVzC6A-Y30TwgQve0V__DLfh6uj7WnlgCNcBGAsYHQ/s640/android-hd-wallpapers_2580602.jpg)](https://1.bp.blogspot.com/-DL57X-4Jm4w/XjovuwaAzpI/AAAAAAAARoE/oBVzC6A-Y30TwgQve0V__DLfh6uj7WnlgCNcBGAsYHQ/s1600/android-hd-wallpapers_2580602.jpg)

**InjuredAndroid - A Vulnerable Android Application That Shows Simple Examples Of Vulnerabilities In A CTF Style**

  
A [vulnerable](https://www.kitploit.com/search/label/Vulnerable "vulnerable") Android application with ctf examples based on bug bounty findings, [exploitation](https://www.kitploit.com/search/label/Exploitation "exploitation") concepts, and pure creativity.  
  
**Setup for a physical device**  

1.  Download injuredandroid.apk from Github
2.  Enable USB debugging on your Android test phone.
3.  Connect your phone and your pc with a usb cable.
4.  Install via adb. `adb install injuredandroid.apk`. Note: You need to use the absolute path to the .apk file or be in the same directory.

  
**Setup for an Android Emulator using Android Studio**  

1.  Download the apk file.
2.  Start the emulator from [Android Studio](https://www.kitploit.com/search/label/Android%20Studio "Android Studio") (I recommend downloading an emulator with Google APIs so root adb can be enabled).
3.  Drag and drop the .apk file on the emulator and injuredandroid.apk will install.

  
**Tips and CTF Overview**  
Decompiling the Android app is highly recommended.  

*    XSSTEST is just for fun and to raise awareness on how WebViews can be made vulnerable to XSS.
*    The login flags just need the flag submitted.
*    The flags without a submit that demonstrate concepts will automatically register in the "Flags Overview" Activity.
*    The last two flags don't register because there currently isn't a remote verification method (I plan to change this in a future update). This was done to prevent using previous flag methods to skip the exploitation techniques.
*    There is one flag with a Pentesterlab 1 month gift key. The key is stored in a self destructing note after It's read, do not close the browser tab before copying the url.
*    The exclamatory buttons on the bottom right will give users up to three tips for each flag.

Good luck and have fun! :D  
  
  

**[Download InjuredAndroid](http://whareotiv.com/oKm "Download InjuredAndroid")**

  

**Regards**

**Kang Asu**