---
title: 'This App Lets You Run Linux Distros on Android Without Root'
date: 2019-12-07T20:40:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  
![](https://beebom.com/wp-content/uploads/2019/12/This-App-Lets-You-Run-Linux-Distros-on-Android-Without-Root.jpg)

Ever wanted to run Linux distros on Android? Well, this app will let you distro-hop right from your Android smartphone running Android Lollipop and above **without root**.  

Named Andronix, the app offers some of the popular Linux distributions including Ubuntu, Manjaro, Kali Linux, Debian, Parrot OS, Fedora, and Arch Linux. All you need is a smartphone with ARMv7, ARM64, or x64 device architecture.  

Notably, this is not yet another command-line tool for running commands supported by a specific distribution. You can install desktop environments on top of it for a user-friendly interface. The supported desktop environments are KDE, LXDE, LXQT, MATE, and XFCE.  

I tried installing Ubuntu 19 along with XFCE DE on a OnePlus 7T Pro and it worked flawlessly. To get started, make sure you have Termux ([free](https://play.google.com/store/apps/details?id=com.termux)) or any Terminal emulator app for Android installed on your smartphone. Choose your favorite Linux distribution from Andronix, copy its command and paste it on Termux.  

After Termux completes downloading the required files, start the Linux distribution with the command displayed in the console. In my case, it was **./start-ubuntu19.sh**. The command may vary based on the distribution you choose.  

Now, choose the desktop environment you prefer from Andronix and paste the command on Termux. After the installation process is complete, Termux will ask you to set a VNC password. Set the password and do not forget to note the port on which the VNC server has been invoked.  

You can use the commands **vncserver-start **and **vncserver-stop **to control the VNC. Enter the port number along with localhost address on the VNC Viewer app. You will now be prompted to enter the VNC password that you had set earlier. In case you’re feeling confused to choose a VNC, the developer of Andronix suggests using [VNC Viewer](https://play.google.com/store/apps/details?id=com.realvnc.viewer.android) by RealVNC.  

![](https://beebom.com/wp-content/uploads/2019/12/ubuntu-19-running-xfce.jpg)

This should be good news for Samsung users who are disappointed with the South Korean tech giant’s [decision to discontinue](https://beebom.com/samsung-linux-on-dex-project-dead/) the [Linux on Dex](https://beebom.com/install-linux-on-dex/) project. Now, even they can run Linux Distros on their Android devices. Check out the app from the link below and let us know if you found this helpful in the comments.  

_[Download](https://play.google.com/store/apps/details?id=studio.com.techriz.andronix) AndroNix | [Download](https://play.google.com/store/apps/details?id=com.termux) Termux | [Download](https://play.google.com/store/apps/details?id=com.realvnc.viewer.android) VNC Viewer_  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/run-linux-distros-android-without-root/)  
\[the\_ad id='1307'\]