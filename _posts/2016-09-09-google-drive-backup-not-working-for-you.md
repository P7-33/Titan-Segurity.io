---
title: 'Google Drive Backup Not Working For You? Here is the Fix'
date: 2019-11-30T06:39:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  

As an Android user, one of the features I feel envious about is the [seamless iOS backup system](https://beebom.com/how-backup-iphone-using-itunes-or-icloud/). No matter which iPhone you switch to, all your backups — from system settings to passwords are imported without a hitch. So to bring a similar backup system on Android, Google has been revising its backup mechanism to bring seamless transition through [Google Drive](https://beebom.com/google-drive-tips-and-tricks/). However, there have been many frailties — sometimes it picks up your data and settings, but does not import it and sometimes it straight-up stops backing up your data. Recently, many have reported that their Google Drive backup is not working and has been perennially showing “Waiting to Backup” error. So to solve this problem, in this article, we bring you a step by step guide with detailed instructions. That being said, let’s get started without any delay.  

Fix Google Drive Backup Not Working
-----------------------------------

  

![Fix Google Drive Backup Not Working 3](https://beebom.com/wp-content/uploads/2019/11/Fix-Google-Drive-Backup-Not-Working-3.jpg)

Here, we are going to fix the Google Drive backup issue using a few ADB commands. For that, we are following Dexer125’s guide from [XDA Forums](https://forum.xda-developers.com/mi-8/how-to/guide-google-backup-waiting-to-backup-t3895101). In case you are wondering about root– no, **you don’t need [root](https://beebom.com/how-install-use-magisk-android/) privilege** to fix this issue. The steps are quite straightforward but it does require a PC to execute the commands. Now having said that, let’s go through the steps.  

*     
    
    ### Fix “Waiting to Backup” Error in Google Drive
    
      
    
  

Before we begin, make sure you have enabled “[USB Debugging](https://beebom.com/cool-things-adb-lets-you-do-android-device/)” from Developer Options. If you have not done this before, follow these steps. Open Settings and go to “About Phone”. Here, tap on the “Build Number” continuously for seven times to activate Developer Options. Now, go back and you will have the menu enabled. Open it and scroll down and **enable “USB debugging”**. There you have it.  

Secondly, **make sure [ADB is properly set up](https://beebom.com/how-to-install-adb-windows-mac/)** on your computer. Again, if you are new to this, follow our tutorial by clicking on the link. Now that you have set up the basics, let’s begin.  

![Fix "Waiting to Backup" Error in Google Drive](https://beebom.com/wp-content/uploads/2019/11/4-3.jpg)

1\. Connect your device to the computer and **open the platform-tools or ADB folder**. Here, type `cmd` in the Explorer’s address bar and hit enter.  

![Fix Google Drive Backup Not Working](https://beebom.com/wp-content/uploads/2019/11/Fix-Google-Drive-Backup-Not-Working.jpg)

2\. A [Command Prompt](https://beebom.com/command-prompt-tricks-to-know/) window will open up. Now, type `adb devices` to check if the computer has detected your Android device. A **prompt will appear on your smartphone** asking for permission. Allow it and then Command Prompt will show a serial number of your device.

  
  

  

![2](https://beebom.com/wp-content/uploads/2019/11/2-7.jpg)

3\. Now that we have established the connection, let’s get to the main thing. **Type the below commands one by one** and hit enter. If you don’t get any error during the process, you are done. After that, restart your smartphone.  

```
adb shell  
bmgr run  
bmgr backupnow --all
```  

![Fix Waiting to Backup Error in Google Drive 2](https://beebom.com/wp-content/uploads/2019/11/Fix-Waiting-to-Backup-Error-in-Google-Drive-2.jpg)

4\. Now, Google Drive **backup should start working again** and the greyed out backup button should go live.  

![3](https://beebom.com/wp-content/uploads/2019/11/3-6.jpg)

5\. However, **in case, you encounter any kind of error,** execute the below commands one by one and then restart your device. This will manually force Google Drive to start the backup process. Make sure you are in the adb shell mode.  

```
bmgr backupnow appdata  
bmgr backupnow --all
```  

![Fix Waiting to Backup Error in Google Drive](https://beebom.com/wp-content/uploads/2019/11/Fix-Waiting-to-Backup-Error-in-Google-Drive.jpg)

Is Your Google Drive Backup Working Again?
------------------------------------------

  

So that was our guide on how to fix the Google Drive backup issue that has been plaguing Android devices for a long time. While Google is trying hard to unify Android backup system, these kinds of basic issues don’t bode well for the Android ecosystem. Anyway, if the article helped you fix the problem, do comment down below and let us know. In case, you are still facing some problems, let us know the exact error that you getting. We will definitely take a look into it.  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/google-drive-backup-not-working-for-you-fix/)  
\[the\_ad id='1307'\]