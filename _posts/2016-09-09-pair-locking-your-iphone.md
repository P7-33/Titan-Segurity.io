---
title: 'Pair Locking Your iPhone'
date: 2019-10-10T03:08:00+01:00
draft: false
---

Pair Locking your iPhone with Configurator 2
============================================

Oct 7th, 2019 | 11 minute read

In response to the recent [iphone bootrom bug](https://twitter.com/axi0mX/status/1177542201670168576) (and also because I was already in the market for a new phone), I recently purchased a new iPhone XR. This gave me a chance to re-run the steps required to **pair lock** the device, a process which prevents law enforcement from using forensics tools against your phone, and the result of which is this blog post.

It covers:

*   Why pair lock your device?
*   How does it work?
*   Supervising and pair locking your device

Why pair lock your device?
--------------------------

It’s an unfortunate state of affairs but people’s digital privacy is increasingly under attack by law enforcement agencies, especially at protests, airports, and border crossings. Articles like the following have become all too common:

and closer to my home in San Francisco we see tweets like [this one](https://twitter.com/DrJorts/status/1081937709243916288): ![](https://arkadiyt.com/images/iphone-pair-locking/tweet.png)

By pair locking your device you will prevent iPhone forensics tools from being able to connect to your device, image it, scan through your messages and camera roll, read your contacts and call history, etc - even if you’ve been compelled by law enforcement to unlock your device! They can still _manually_ look through your unlocked phone contents, but they can’t image the device for offline analysis, they can’t run automated content scanners, and they no longer get access to your various app authentication tokens.

I originally learned about this feature / unintended side effect from Jonathan Zdziarski’s excellent [blog post](https://www.zdziarski.com/blog/?p=2589) about it. Jonathan was a well-known iOS security researcher who now works on Apple’s security team. Unfortunately since joining Apple he stopped blogging about iOS security (and deleted his twitter), and the instructions in his original 2014 blog are now slightly dated. The purpose of this post is to provide updated instructions, though it is still heavily based on Jonathan’s post.

How does it work?
-----------------

Forensics tools pull data from iPhones using a concept called _pairing_, which Jonathan explained best:

> A pairing is a trusted relationship with another device, where a computer is granted privileged, trusted access on the iPhone. In order to have the level of control to backup the phone, download personal data, install applications, or perform other such tasks on an iOS device, the machine it’s connected to must be paired with the device. This is what iTunes and Xcode do to talk to the phone, but also what forensic imaging tools and a number of free hacking tools do as well.

By pair _locking_ your device, you instruct your iPhone to never create a new trusted relationship with any device that connects to it except the device which created the lock, which has the side effect of breaking all forensics tools. In the presence of pair locking, the only way to harvest data off your phone would be with a hardware vulnerability (like the bootrom one mentioned in the opening line of this blog post).

To enable pair locking we need to put the phone into a _supervised_ state, which enables a large number of restrictions you can place on the phone’s functionality and behavior. It was built for enterprises to enforce security controls on their employees’ phones but it’ll work just as well for us here.

Before proceeding with the process there are three caveats to keep in mind:

*   Putting your phone into a supervised state will fully wipe it. After wiping it you can log back into iCloud and all settings/apps/etc you have configured to sync will be there again. However you cannot take a device backup, supervise the device, and then restore the backup (as this would also restore the unsupervised state).
*   Anyone who gains access to your laptop can get the pairing record from it and have complete access to everything on your phone (after physically connecting to it).
*   If you lose access to your laptop or pairing record then you will also be locked out of connecting to your phone.

So, how do you actually do it?

Supervising and pair locking your device
----------------------------------------

1.  Download and install Apple’s [Configurator 2](https://apps.apple.com/us/app/apple-configurator-2/id1037126344) application.
    
2.  Plug your phone into your computer with a USB cable.
    
3.  In Configurator, click on your phone and then click on the `Prepare` button in the upper navigation. Click to expand image![](https://arkadiyt.com/images/iphone-pair-locking/1.png)
4.  In the dialog that opens:
    
    *   Ensure `Supervise devices` is checked
    *   Check `Allow devices to pair with other computers`
    *   Click `Next`
    
    Click to expand image![](https://arkadiyt.com/images/iphone-pair-locking/2.png)
    
    Pair locking can be done at 2 different levels: at the supervisor level or at the profile level (a profile is a collection of iPhone settings to enforce). Following Jonathan’s advice we opt for profile enforcement, which is why we checked `Allow devices to pair with other computers` here - we’re allowing it at the supervisor level and we’ll block it later at the profile level. The reasoning for this is that profiles can be added/removed without wiping the device, which is helpful if you ever need to switch to a new laptop.
    
5.  In the next dialog page, select `Do not enroll in MDM` and click `Next`: Click to expand image![](https://arkadiyt.com/images/iphone-pair-locking/3.png)
6.  You’ll be prompted to create a new organization. Click `Next`: Click to expand image![](https://arkadiyt.com/images/iphone-pair-locking/4.png)
7.  When prompted to sign into Device Enrollment Program, click `Skip`: Click to expand image![](https://arkadiyt.com/images/iphone-pair-locking/5.png)
8.  Fill out the name for your organization (everything else can be left blank) and click `Next`: Click to expand image![](https://arkadiyt.com/images/iphone-pair-locking/6.png)
    
    You can choose whatever organization name you want but keep in mind it will be displayed at the top of your iPhone settings: ![Preparing your device](https://arkadiyt.com/images/iphone-pair-locking/7.png "Preparing your device")
    
9.  On the following page, select `Generate a new supervision identity` and click `Next`: Click to expand image![](https://arkadiyt.com/images/iphone-pair-locking/8.png)
10.  On the next page leave the settings unchanged and click `Prepare`: Click to expand image![](https://arkadiyt.com/images/iphone-pair-locking/9.png)
    
    This will prompt you for your laptop password to update your certificate settings - once you enter your password and click `Update Settings` the process to wipe and supervise your phone will begin. If your device is already supervised you’ll get an error about needing to restore the device first (but this likely doesn’t affect you, since you’re reading this post!).
    
11.  After the process completes, you can create a new profile which will have your pair locking restriction:
    
    *   Click `File -> New Profile` and give your new profile a name
    *   Under the `Controls when the profile can be removed` section, select either `Never` or `With Authorization`
    
    Click to expand image![](https://arkadiyt.com/images/iphone-pair-locking/11.png)
    
    This setting controls when someone can remove the profile from within the phone itself. If it’s left as the default value of “Always” then anyone with access to your unlocked phone could remove the pair lock (which would defeat the entire purpose). You can either set it to `Never` to never allow removing the profile, or `With Authorization` and set a password to allow removing the profile with the given password (this might be useful to remove the pairing restriction if you do lose access to your laptop).
    
12.  Go to the `Restrictions` section in the left navigation and click `Configure` in the right pane: Click to expand image![](https://arkadiyt.com/images/iphone-pair-locking/12.png)
13.  In the restrictions pane you’ll see a large number of settings you can configure to disallow certain apps, set password/touchid/faceid restrictions, etc. Uncheck the box `Allow pairing with non-Configurator hosts`: Click to expand image![](https://arkadiyt.com/images/iphone-pair-locking/13.png)
    
    You can also go ahead and set any other restrictions that seem appealing to you.
    
14.  Exit the “New Profile” window. You’ll be prompted to save your new profile somewhere.
    
15.  In the main Configurator window, right click your phone and select `Add -> Profiles...`, and load your newly saved profile: Click to expand image![](https://arkadiyt.com/images/iphone-pair-locking/15.png)

You’ve now successfully pair locked your device! If you attempt to plug your phone into a different laptop you should see the following error: ![](https://arkadiyt.com/images/iphone-pair-locking/access_denied.png)

and forensics tools should similarly fail to connect to your device. If you later want to remove this restriction you can `Remove -> Profiles...` in Configurator, analogous to step 15.

Conclusion
----------

Pair locking is a useful feature to protect yourself against invasive device searches. If this topic concerns you then you should also check out the EFF’s detailed [Digital Privacy at the U.S. Border](https://www.eff.org/files/2018/01/11/digital-privacy-border-12-2017.pdf) guide, which covers both the technological aspects of digital privacy (like minimizing data when crossing borders) as well as the legal frameworks used for device searches (discussing what is and is not allowed).

While I feel safer having this protection on my phone, no amount of technology will solve what is ultimately a policy issue - we need modern privacy laws and regulations for that.

  
  
from Hacker News https://ift.tt/31Zl5zq