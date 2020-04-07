---
title: 'How to Install ADB on Windows and Mac'
date: 2020-02-15T14:11:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  

Android Debugging Bridge (ADB), as the name suggests, is a command line utility that offers developers to debug various parts of their applications. However, it is not restricted to just the developers. If you want to access certain features of the Android platform that are not otherwise accessible, you, too, can use the ADB commands by installing ADB on your computer – Windows or Mac. Once you install it, there are numerous [cool things](https://beebom.com/cool-things-adb-lets-you-do-android-device/) that you can do with your Android device. Plus, there are various apps that require ADB permissions to work. So, if you have been confused about how to install and use ADB on Windows or Mac, we have you covered. _**H****ere is how to install ADB on Windows or Mac:**_  

_**Note:** The Android device used for this method was a Moto G3 running Android 7.1.2; the Windows PC was running Windows 10 Pro; and the MacBook Pro was running macOS High Sierra public beta 8._  

Setup Your Android Device for ADB
---------------------------------

  

Even if you install ADB on your Windows PC or Mac, it is of no use unless you setup your Android device first to work with ADB. So in case you are not sure how to do that, follow the steps below to find out.  

*   **Open Settings** on your Android device, and **go to “About Phone”** (“System” in Android Oreo). Here, **tap on “Build number” 7 times** consecutively.
  

![Enable Developer Options](https://beebom.com/wp-content/uploads/2017/09/Enable-Developer-Options-1.jpg)

*   This will enable “Developer options” in the settings. **Head over to this setting**, and **enable “USB debugging”**.
  

![Enable USB Debugging](https://beebom.com/wp-content/uploads/2017/09/Enable-USB-Debugging.jpg)

Now your Android device will enter debug mode whenever it is connected to a computer using a USB. The next step is to set up ADB on your computer.  

Install ADB on Windows
----------------------

  

Here are the steps to install ADB on Windows:  

*   Firstly, **download** either [Minimal ADB and Fastboot](https://forum.xda-developers.com/showthread.php?t=2317790) or the official Google binaries using this [direct link](https://dl.google.com/android/repository/platform-tools-latest-windows.zip). Once downloaded, extract the contents of this file on your Windows PC using a file archiver utility like [WinRAR](https://www.win-rar.com/download.html?&L=0).
  

![Extracted ADB Files](https://beebom.com/wp-content/uploads/2017/09/Extracted-ADB-Files.jpg)

*   Now head over to the extracted folder, and **right-click anywhere while holding the Shift key**. From the context menu that pops up, **select “Open PowerShell window here” / “Open command window here”**.
  

![PowerShell in Context Menu](https://beebom.com/wp-content/uploads/2017/09/PowerShell-in-Context-Menu.jpg)

  
  

  

*   After this,** connect your Android device to your computer**, and **change the USB mode to “Transfer files”**.
  

![Change USB Mode](https://beebom.com/wp-content/uploads/2017/09/Change-USB-Mode.png)

*   In the command window, **execute the following code**, and, if prompted, allow USB debugging on your Android device. If everything goes fine, you should see your device’s serial number in the command window.  
    ```
    adb devices
    ```  
    
  

![CMD - ADB Devices](https://beebom.com/wp-content/uploads/2017/09/CMD-ADB-Devices.jpg)

Congratulations! ADB is now successfully installed on your Windows PC.  

Install ADB on Mac
------------------

  

If you own a Mac, the steps to install ADB are very similar to that on Windows and can be followed as mentioned below:  

*   **Download the official Google binaries** using this [direct link](https://dl.google.com/android/repository/platform-tools-latest-darwin.zip). Now, **extract this file** on your Mac using a file archiver like [The Unarchiver](https://theunarchiver.com/).
  
*   After this, **open Terminal**, and **browse to the extracted folder**.
  

![Browse to the Extracted Folder](https://beebom.com/wp-content/uploads/2017/09/Browse-to-the-Extracted-Folder.jpg)

*   Now **connect your Android device to your Mac**, and, on your Android device, **change the USB mode to “Transfer files”**.
  

![Change USB Mode](https://beebom.com/wp-content/uploads/2017/09/Change-USB-Mode.png)

*   You can now **execute the following command**. Grant the permission on your Android device, if asked. On successful execution, you should be able to see the serial number of your device.  
    ```
    adb devices
    ```  
    
  

![Terminal - ADB Devices](https://beebom.com/wp-content/uploads/2017/09/Terminal-ADB-Devices.jpg)

This signifies that ADB is successfully installed on your Mac. Now let’s take a look at how to use ADB.  

How to Use ADB on Windows and macOS
-----------------------------------

  

After you have successfully installed ADB on your Windows PC or Mac, using it is just a matter of **executing various ADB commands** in the Command Prompt / Terminal. Just make sure that you have connected your Android device to your computer while USB debugging is enabled. After this, you can try different commands and experience Android a whole lot differently. To help you get started, given below are **few of the most commonly used ADB commands**.  

  
  
  
  
  
  
  
  
  

Command

Description

adb devices

To view the list of Android devices communicating with your computer

adb push

To move a file onto your Android device programmatically

adb pull

To move a file from your Android device programmatically

apk install

To install apps programatically using APK files

adb reboot

To reboot your Android device

adb reboot recovery

To reboot your Android device in recovery mode

adb reboot bootloader

To reboot your Android devie to bootloader

adb shell

To start a remote shell with your Android device

**SEE ALSO: [How to Use ADB Wirelessly on Your Android Device](https://beebom.com/how-use-adb-wirelessly-android-device/)**  

Install ADB on Windows and Mac With Ease
----------------------------------------

  

ADB is a very useful utility for all Android programmers. Even if you are not one yourself, you now know how to set up ADB on your PC or Mac and use it with your Android device. And if you’re new to this, I’ve already listed some of the common ADB commands above. This allows you to experience Android like you’ve never before. Talking about ADB commands, which ones are your favorites? I would love to hear from you in the comments section below.  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/how-to-install-adb-windows-mac/)  
\[the\_ad id='1307'\]