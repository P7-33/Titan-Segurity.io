---
title: 'How to Add 90 Hz Refresh Quick Toggle in OnePlus 7/7T Pro'
date: 2019-11-02T13:56:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  

One of the biggest improvements that OnePlus introduced with its 2019 smartphones is the high refresh rate screens which provide users with a fluid experience. The [OnePlus 7 pro](https://beebom.com/oneplus-7-pro-launched-price-rs-49999/), [OnePlus 7T](https://beebom.com/oneplus-7t-launched-price-specs-features/), and [OnePlus 7T Pro](https://beebom.com/oneplus-7t-pro-launched-price-specs-features/) come with a 90 Hz display which makes the experience smoother when you are playing games, scrolling through content on apps, or just traversing the UI. The benefits of 90 Hz display is something that cannot be explained but only experienced in person. And believe me when I say that a high refresh rate screen is exceptional. That said, the feature comes with a big penalty in terms of battery life. OnePlus does allow you to keep the screen in 60 Hz mode to save battery life but that is buried deep in the Settings app. So, to make life easier for you, we are going to show you how to enable a 90 Hz refresh rate quick toggle in OnePlus 7/7T Pro.  

Enable Display Refresh Rate Quick Toggle
----------------------------------------

  

While I have talked about battery life consequences of using the 90 Hz refresh rate, some users might not be bothered with it as they can charge their phones multiple times a day. Considering the ultra-fast charging speeds of OnePlus devices, no one can blame you if you want to use the phone always in the 90 Hz mode. Well, since the quick toggle will allow you to easily switch between 60 Hz and 90 Hz refresh rate, you can use it to quickly switch to 90 Hz mode whenever you want. With that said, here are the steps to enable the 90 Hz refresh rate quick toggle.  

### Adding the 90 Hz Toggle to Quick Settings Page

  

1\. First, we will install the app that we require to enable this quick toggle. So, **click on the link to visit the GitHub page and** [download the app](https://github.com/ti0ma/oneplus-screen-shortcut/blob/master/README.md). If you are installing an outside APK for the first time on your phone, it might ask permission. Allow it to install the app on your phone.  

![1. Enable Display Refresh Rate Quick Toggle](https://beebom.com/wp-content/uploads/2019/11/1.-Enable-Display-Refresh-Rate-Quick-Toggle.jpg)

2\. Once you install the app, it will add the 90 Hz refresh rate toggle to your Quick Settings panel. To find it, **drop down the Quick Settings panel and then tap on the edit button**. Now, hold and drag the 90 Hz quick toggle to show it in your Quick Settings panel.  

![2. Enable 90 Hz Display Refresh Rate Quick Toggle](https://beebom.com/wp-content/uploads/2019/11/2.-Enable-90-Hz-Display-Refresh-Rate-Quick-Toggle.jpg)

Once done, tap on the back button to save the changes. If you tap on the 90 Hz quick setting toggle, you will find that nothing is happening. **That’s because we have to first grant it permission using ADB**. If you don’t know anything about ADB then head over to our quick [ADB install guide for Windows and Mac](https://beebom.com/how-to-install-adb-windows-mac/) and first install the tool on your device. Once installed, follow the steps to enable the 90 Hz toggle.  

### Enabling the 90 Hz Refresh Rate Quick Toggle Using ADB

  

1\. First, we will have to enable “USB Debugging” on our OnePlus 7/7T Pro. To do that, launch Settings and then open “About Phone”. Here, **tap on “Build Number” 6-7 times till you see a “Developer Options Enabled”** message.  

![3. Enabling Developer Mode on OnePlus 7T Pro](https://beebom.com/wp-content/uploads/2019/11/3.-Enabling-Developer-Mode-on-OnePlus-7T-Pro.jpg)

  
  

  

2\. Now search for “USB Debugging” and tap on the first result. Enable it by turning on the toggle. If you can’t find it in search go to **Settings -> System -> Developer options -> USB debugging** and enable it.  

![4. Enabling USB Debuggin on OnePlus 7 Pro](https://beebom.com/wp-content/uploads/2019/11/4.-Enabling-USB-Debuggin-on-OnePlus-7-Pro.jpg)

3\. Now, connect the OnePlus device to your laptop. Launch Windows CMD Prompt/macOS Terminal and run the following command. If you have installed ADB correctly **it will show your device under the “List of device attached” section** just as shown in the picture below.  

```
adb devices
```  

Once your device is listed, **run the below command to grant the necessary permissions** for the quick toggle to work.  

```
adb shell pm grant me.molonosov.oprefreshrate android.permission.WRITE_SECURE_SETTINGS
```  

![Granting Permissions](https://beebom.com/wp-content/uploads/2019/11/Granting-Permissions-1024x530.jpg)

4\. That’s it. Your quick toggle is working now. You can verify it by tapping on the toggle. **It will turn blue whenever you use the 90 Hz display refresh rate.** Tap on it again to go back to the 60 Hz refresh rate if you want to.  

![90 Hz Quick Toggle Working](https://beebom.com/wp-content/uploads/2019/11/90-Hz-Quick-Toggle-Working.jpg)

**SEE ALSO: [How to Enable Fingerprint Lock on WhatsApp on Android](https://beebom.com/how-enable-fingerprint-lock-whatsapp-android/)**  

Easily Switch Between 60 Hz and 90 Hz Refresh Rate
--------------------------------------------------

  

I love this little tweak as it allows me to easily switch between 60 Hz and 90 Hz refresh rates. I no longer have to dig through the settings app to change my preferences. This way I can enjoy the fluid animation of 90 Hz display and switch to the 60 Hz refresh rate whenever I need to save some battery life. Do let us know your thoughts on this simple tweak and ask away any questions that you have by writing in the comments section below.  

  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/how-add-90-hz-refresh-rate-quick-toggle-oneplus-7-7t-pro/)  
\[the\_ad id='1307'\]