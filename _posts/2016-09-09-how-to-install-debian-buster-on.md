---
title: 'How to Install Debian Buster on Chromebook (Debian 10)'
date: 2020-02-04T07:46:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  

Linux on Chromebook which is also called Project Crostini was announced in 2018 and since then it has used Debian Stretch (Debian 9) as its base. We were hoping after [Debian Buster](https://www.debian.org/News/2019/20190706) (Debian 10) release in 2019, [Chrome OS](https://beebom.com/best-chrome-os-tips-tricks/) would move to the latest build since Debian 9 was released way back in 2017. The day has finally arrived in 2020 and now you can move to the latest Debian 10 on your Chromebook. The new update will bring Linux Kernel 4.19 LTS, support for ARM64 boards, Bash 5.0 and more. Other than that, you will see a good performance jump while using [Linux apps on your Chromebook](https://beebom.com/best-linux-apps-chromebook/). Now having said all of that, let’s go ahead and learn how to install Debian Buster on Chromebook.  

Install Debian Buster on Chromebook
-----------------------------------

  

If you are already [using Linux on your Chromebook](https://beebom.com/how-use-linux-chromebook/) either in Stable, Beta, or Dev channel then **you will have to disable Linux and turn it on again to get the latest Buster update**. I know this is not the best solution, but if you are someone who wants to jump from Debian 9 to 10 anyhow then this is the only way right now. Of course, in coming March, you will get the stable Chrome 81 update which will have Buster by default, but again this guide is not for those who _can_ wait. So if you are willing to set up Linux all over again then let’s go ahead and taste the latest Debian 10 on [Chromebook](https://beebom.com/what-is-a-chromebook/) right now.  

1\. If you are on Stable or Beta channel then you will have to **switch to the Dev channel**. The Buster update is only available on Chrome OS version 81.0.4037.0 Dev channel. To change the update channel, open Settings -> About Chrome OS -> Additional Details -> Change Channel -> Choose Developer-unstable. Now go back to the “About Chrome OS” page and check for updates.  

![Install Debian Buster on Chromebook](https://beebom.com/wp-content/uploads/2020/02/Install-Debian-Buster-on-Chromebook-1.jpg)

2\. Now that you are on the Dev channel, open `chrome://flags` and **enable these three [Chrome flags](https://beebom.com/google-chrome-flags/)**: ‘New Crostini containers use Buster’, ‘Allow resizing Crostini disks’ and ‘Allow picking your Crostini username’. After making the changes, restart your Chromebook.  

![Install Debian Buster on Chromebook 4](https://beebom.com/wp-content/uploads/2020/02/Install-Debian-Buster-on-Chromebook-4.jpg)

3\. Next, open Settings and move to the “Linux (Beta)” menu. Here, **click on the “Remove” button and disable Linux**. Finally, restart your Chromebook. Keep in mind, this will uninstall all your Linux apps and erase files from the Linux directory. So before removing Linux, make sure to move all the Linux files to Google Drive or Download directory.  

_**Note:** If you were not using Linux earlier then you can simply skip this step._  

![remove linux](https://beebom.com/wp-content/uploads/2020/02/Install-Debian-Buster-on-Chromebook-5.jpg)

  
  

  

4\. After the restart, open Settings again and go to the “Linux (Beta)” menu, Now, **click on the “Turn on” button** and let it download all the required files. This time, the Linux setup will install the Buster build on your Chromebook.  

![turn on linux](https://beebom.com/wp-content/uploads/2020/02/Install-Debian-Buster-on-Chromebook-6.jpg)

5\. During the process, **it** **will ask for Linux disk size**. You can choose anything above 1.8GB depending on your available internal storage. As for my Chromebook, I have chosen 12GB for storing Linux apps and files. Also, unlike earlier, now you can also **choose your Linux username**. So, go ahead and pick your favorite one.  

![Install Debian Buster on Chromebook 3](https://beebom.com/wp-content/uploads/2020/02/Install-Debian-Buster-on-Chromebook-3.jpg)

6\. After the installation, now you will be able to use Debian Buster on your Chromebook. **You can check the version by opening the Terminal and executing the below command**. If it shows “Buster” and “10” then you have successfully moved to Debian 10 on your Chromebook. While you won’t see any visual changes, you will definitely find better performance while using Linux on Chromebook.  

```
cat /etc/os-release
```  

![Install Debian Buster on Chromebook](https://beebom.com/wp-content/uploads/2020/02/Install-Debian-Buster-on-Chromebook-.jpeg)

Enjoy Debian 10 on Your Chromebook Right Now
--------------------------------------------

  

So that is how you can install Debian 10 on your Chromebook. For a very long time, we were waiting for this update and finally, it’s here. Sure, the update process is not that straightforward, but it’s expected as we are dealing with Dev builds. If you are a developer or student who uses Linux for programming then I would highly recommend installing this update. But if you are a general user then stay away from Buster at this point as it’s likely to bring more bugs. Anyway, that is all from us. If you found the article helpful, do let us know in the comment section below.  

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/how-install-debian-buster-chromebook/)  
\[the\_ad id='1307'\]