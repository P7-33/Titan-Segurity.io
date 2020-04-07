---
title: 'How to Run GUI-based Linux Programs on Windows 10'
date: 2020-02-03T06:35:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  

At the end of 2016, Microsoft in an unexpected move announced its [partnership with the Linux Foundation](https://www.theverge.com/2016/11/16/13651940/microsoft-linux-foundation-membership). The new-age collaboration was to bring a part of Linux on Windows 10 to make it a developer-friendly platform. Fast forward to 2020 and it seems the partnership has largely paid off as the project has gone through some great improvements and beyond the [Linux Terminal commands](https://beebom.com/essential-linux-commands/). Now, you can run GUI-based Linux programs on Windows 10 without many workarounds. We tried a few [popular Linux apps](https://beebom.com/best-linux-apps/) and they worked flawlessly on our Windows laptop. So, if you want to learn how to install and use Linux applications on Windows 10 in a graphical user interface, follow our guide step by step.  

Install Linux Programs on Windows 10 with WSL
---------------------------------------------

  

Here, we are going to show you how to install Linux programs on Windows 10 using the WSL (Windows Subsystem for Linux) feature. If you are out of the loop, **WSL is an actual Linux kernel that is shipped with Windows 10.** It’s not a compatibility layer or a [virtual machine on Windows 10](https://beebom.com/how-create-virtual-machine-windows-10/) so the performance remains top-notch. Now having said all of that, let’s move to the steps without any delay.  

1\. First and foremost, [enable the Linux Bash Shell on Windows 10](https://beebom.com/how-enable-linux-bash-shell-windows-10-wsl-2/) in case you have not done yet.  

_**Note:** Do not upgrade to WSL 2 as it has some bugs that block GUI-based Linux programs on Windows 10._  

![1. Install Linux Programs on Windows 10 with WSL](https://beebom.com/wp-content/uploads/2020/02/1.-Install-Linux-Programs-on-Windows-10-with-WSL.jpg)

2\. Now that you have set up WSL 1, let’s [install the VcXsrv application](https://sourceforge.net/projects/vcxsrv/) on your PC. It’s a Windows Desktop Server application that enables Linux programs to run in a graphical user interface. During the installation, **keep everything default and complete the setup**. Finally, VcXsrv will start running in the background and will sit in the system tray.  

![Install Linux Programs on Windows 10 with WSL](https://beebom.com/wp-content/uploads/2020/02/1-install-linux-programs-on-windows-10.jpg)

3\. Next, you might be prompted with a [Windows Firewall](https://beebom.com/best-free-firewall-software-windows/) dialog. Enable the checkbox for private networks too and **click on the “Allow Access” button**.  

![install linux programs](https://beebom.com/wp-content/uploads/2020/02/install-linux-programs.jpg)

  
  

  

4\. Now, let’s install Linux programs on our PC. You can choose whichever program you want right from Vim to Gedit and install them **in traditional Linux fashion using the _apt-get install_ command**. For your perusal, a GitHub user has created [a list of Linux programs that run quite well on Windows 10](https://github.com/ethanhs/WSL-Programs/blob/master/README.md) so check that out for more information. Here, for instance, I am installing Gedit through the Linux Terminal.  

```
sudo apt-get install gedit
```  

![2](https://beebom.com/wp-content/uploads/2020/02/2.jpg)

5\. After the app is installed, run the below command to **connect the VcXsrv Windows Server with Linux**.  

```
export DISPLAY=:0  

```  

![2 install linux programs on windows 10](https://beebom.com/wp-content/uploads/2020/02/2-install-linux-programs-on-windows-10.jpg)

6\. Having done that, now run the Linux program the same way you do on [Linux distros](https://beebom.com/linux-distros-you-should-know-about/). **Type the app name and hit enter**. The Linux program will instantly open up in a GUI interface on Windows 10. That’s awesome, right?  

```
gedit
```  

![](https://beebom.com/wp-content/uploads/2020/02/3-install-linux-programs-on-windows-10.jpg)

7\. If you want to run multiple Linux programs at once then [open the Linux Bash Shell in Windows Terminal](https://beebom.com/windows-terminal-update-ui-profiles/). Here, you can use Linux Bash Shell in multiple tabs and execute commands simultaneously. All you have to do is **execute the _export DISPLAY=:0_ command in each tab** and then run the Linux program as you usually do. Here, I am running VLC (Linux-based) and Gedit side by side on Windows 10.  

![4 install linux programs on windows 10](https://beebom.com/wp-content/uploads/2020/02/4-install-linux-programs-on-windows-10.jpg)

Linux Program not Opening in GUI on Windows 10? Here’s the Fix
--------------------------------------------------------------

  

1\. As I said above, the issue is because of the latest WSL 2 build. If you are already on the latest update, **you need to downgrade to WSL 1 manually**. Execute the below command in Windows PowerShell to find the WSL version.

  
  

  
```
wsl -l -v
```  

![](https://beebom.com/wp-content/uploads/2020/02/5-install-linux-programs-on-windows-10.jpg)

2\. If it shows “version 2” then **run the below command to move back to WSL 1** which is much more stable and bug-free. It will take around 20-30 minutes for the process to complete. After that, go through the above guide and Linux apps will start opening in GUI without any issue.  

```
wsl --set-version Ubuntu 1
```  

![change wsl 2 to wsl 1](https://beebom.com/wp-content/uploads/2020/02/Annotation-2020-02-01-172826-e1580558438934.jpg)

Run Any Linux Program on Windows 10 Through WSL
-----------------------------------------------

  

So that is how you can install and use Linux programs on Windows 10 using the awesome WSL feature. As it’s evident, the Linux applications run perfectly fine and without any glitches. However, if you want to run media apps then you may face some problems due to sound and mic issues. Other than that, the Windows Subsystem for Linux is a legit way, at least, for developers to enjoy the best of both worlds. Anyway, that is all from us. If you want to learn more such [tips and tricks about Windows 10](https://beebom.com/beginner-tips-for-windows-10/) then stay tuned with us. And if you are facing any issue then do comment down below and let us know.  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/how-run-gui-based-linux-programs-windows-10/)  
\[the\_ad id='1307'\]