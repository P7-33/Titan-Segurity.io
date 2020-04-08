---
title: 'This App Brings Back Notification Tickers on Android'
date: 2019-11-30T16:55:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  
![](https://beebom.com/wp-content/uploads/2019/11/tinynotif-ft.-e1575107400817.jpg)

With Android Lollipop, Google brought heads-up notifications to Android and bid goodbye to notification tickers. Heads-up notifications are useful for quickly drawing attention to the notifications but it can be annoying when a notification suddenly covers up a portion of your screen while you’re watching a video or a movie. To solve this problem, a developer has come up with a new app named TinyNotif that brings back the good-old notification tickers on newer Android devices.  

To get started, you will have to allow the necessary permissions. You can set the permissions by tapping on the “Request Permissions” button. On tapping the button, TinyNotif will **request overlay and notification access permissions** for the app to trigger the notification ticker every time a new notification comes in your phone.  

![](https://beebom.com/wp-content/uploads/2019/11/tinynotif.jpg)

Once you’re done setting permissions, you will have to disable heads-up notifications to avoid duplicate notifications. You can achieve this by three methods – **[using ADB](https://beebom.com/how-to-install-adb-windows-mac/) command**, using **DND mode**, or **manually disabling notifications** for every app.  

I would recommend you to use the ADB method as it is a one-time process. Connect your phone to your PC and run the ADB command given below to disable heads-up notifications.  

```
adb shell settings put global heads\_up\_notifications\_enabled 0
```  

In case you wish to revert the changes and enable heads-up notifications later, simply run the same command by replacing the 0 at the end by 1. You can use the DND mode to temporarily achieve the same but it comes at the cost of muting your phone.  

The app also offers you the ability to **tweak the font size** and **scroll speed** of the notification ticker so that you can customize it as per your preference.  

Check out TinyNotif from the link below and let us know if you found this helpful in the comments.  

_[Download](https://gitlab.com/CraftedCart/tinynotif/-/tags) TinyNotif (Free)_  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/bring-back-notification-tickers-android/)  
\[the\_ad id='1307'\]