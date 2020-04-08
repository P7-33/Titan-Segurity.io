---
title: 'Kali Linux 2019.4 Release'
date: 2019-11-26T18:41:00+01:00
draft: false
---

Time to grab yourself a drink, this will take a while!

![kali-preview-boot](https://www.kali.org/wp-content/uploads/2019/11/kali-preview-boot.gif)

We are incredibly excited to announce our fourth and final release of 2019, Kali Linux 2019.4, which is available immediately for [download](https://www.kali.org/downloads/).

2019.4 includes some exciting new updates:

*   A new default desktop environment, Xfce
*   New GTK3 theme (for Gnome and Xfce)
*   Introduction of “Kali Undercover” mode
*   Kali Documentation has a new home and is now Git powered
*   Public Packaging – getting your tools into Kali
*   Kali NetHunter KeX – Full Kali desktop on Android
*   BTRFS during setup
*   Added PowerShell
*   The [kernel is upgraded to version 5.3.9](https://pkg.kali.org/pkg/linux)
*   … Plus the normal bugs fixes and updates.

### [](#new-desktop-environment-and-gtk3-theme)New Desktop Environment and GTK3 Theme

There are a ton of updates to go over for this release, but the most in your face item that everyone is going to notice first are the changes to the desktop environment and theme. So let’s cover that first.

An update to the desktop environment has been a long time coming. We have been talking about how to address this, what we wanted to do, experimenting on different approaches, and so on for months now. As a summary we had a few issues we wanted to address head-on:

*   Performance issues – Gnome is a fully-featured desktop environment with a ton of awesome things it can do. But all these features comes with overhead, often overhead that is not useful for a distribution like Kali. We wanted to speed things up, and have a desktop environment that does only what it’s needed for, and nothing else. Gnome has been overkill for most Kali users, as many just want a window manager that allows you to run multiple terminal windows at once, and a web browser.
*   Fractured user experience – We support a range of hardware, from the very high end to the very low. Because of this, traditionally our lower-end ARM builds have had a completely different UI than our standard. That’s not optimal, and we wanted to unify this experience so it did not matter if you were running on a bare metal install on a high end laptop or using a Raspberry Pi, the UI should be the same.
*   Modern look – We have been using the same UI for quite a while now, and our old theme maintainer had moved on due to lack of time. So we wanted to go with something fresh, new, and modern.

To help us address these items, we tracked down [Daniel Ruiz de Alegría](https://drasite.com/) and started the development of a new theme running on Xfce. Why Xfce? After reviewing the above issues, we felt that Xfce addressed them best while still being accessible to the majority of users.

The solution we’ve committed to is lightweight and can run on all levels of Kali installs. It is functional in that it handles the various needs of the average user with no changes. It is approachable where it uses standard UI concepts we are all familiar with to ensure there is no learning curve. And it looks great with modern UI elements that make efficient use of screen space.

We are really excited about this UI update, and we think you are going to love it. However, as UI can be a bit like religion, if you don’t want to leave Gnome don’t worry. We still have a Gnome build for you, with a few changes already in place. As time goes by, we will be making changes to all of the desktop environments we release installs to get them “close” to a similar user experience no matter what DE you run. There will be limits to this, as we don’t have the resources to heavily invest in tweaking all these different environments. So if there is something you would like to see, feel free to submit a [feature request](https://bugs.kali.org/)!

We have also released a FAQ about the new theme that you can find on our [docs page](https://www.kali.org/docs/general-use/xfce-faq/). This includes some common items like how to switch to the theme on your existing install, how to change off of it if you don’t like it, and so on.

### [](#kali-undercover)Kali Undercover

With the change to the environment, we thought we would take a side step and do something fun. Thanks to Robert, who leads our penetration testing team, for suggesting a Kali theme that looks like Windows to the casual view, we have created the Kali Undercover theme.

![kali-undercover](https://www.kali.org/wp-content/uploads/2019/11/kali-undercover-1.gif)

Say you are working in a public place, hacking away, and you might not want the distinctive Kali dragon for everyone to see and wonder what it is you are doing. So, we made a little script that will change your Kali theme to look like a default Windows installation. That way, you can work a bit more incognito. After you are done and in a more private place, run the script again and you switch back to your Kali theme. Like magic!

### [](#kali-docs-is-now-on-markdown-and-new-home-docs)Kali-Docs is now on Markdown and new home (/docs/)

This may not be as flashy as the new theme, but the changes to the docs we have done is just as significant.

One of our go-forward goals with Kali is to move more of the development into the public and make it as easy as possible for anyone _(that means you!)_ to get involved and contribute to Kali. That’s what our move to GitLab [earlier in the year](https://www.kali.org/news/kali-linux-roadmap-2019-2020/) was all about. Another part of this is changing how we deal with docs.

We have since moved all of our documentation into Markdown in a [public Git repository](https://gitlab.com/kalilinux/documentation/kali-docs). From here on out anyone, not just Kali staff, can contribute to better documentation through merge requests. We will still approve any content changes, but once merged, changes will be automatically available on the docs section of our website.

We encourage everyone to get involved! If you see something wrong in the existing docs, change it! If you have an idea for new docs, write it! These sorts of contributions make Kali better for everyone.

This is just the first step. With this change in place, coming soon watch for a kali-docs package in Kali that gives you full offline access to the documentation on every install of Kali. Perfect for those situations where you are working in a closed-off environment with no Internet access.

### [](#public-packaging)Public Packaging

One of the more significant new documents we have done is [documenting how you can make a new package](https://www.kali.org/docs/development/public-packaging/) that will get included in Kali.

One of the most common bug reports is requests for us to add new tools or update existing ones. Oftentimes, by the tool developers themselves as they recognize that having their tool in the Kali repo is the easiest distribution channel for security assessment tools there is. The volume of this has always been difficult to keep up with, and we have to make some hard decisions on where to commit our limited resources.

Now with this work-flow in place and documented, you don’t have to wait on us. Go ahead and package up your tool and submit it off to us for approval. This is an awesome way to get involved with improving Kali.

### [](#btrfs-during-setup)BTRFS during setup

Another significant new addition to the documentation is the [use of BTRFS as your root file system](https://www.kali.org/docs/base-images/kali-linux-btrfs-install/). This is an amazing approach documented by Re4son, that when done gives you the ability to do file system rollbacks after upgrades.

When you are in a VM and about to try something new, you will often take a snapshot in case things go wrong you can easily go back to a known-good state. However, when you run Kali bare metal that’s not so easy. So you end up being extra careful, or if things go wrong have a lot of manual clean up to do. With BTRFS, you have this same snapshot capability on a bare metal install!

As this is new, it’s not integrated into our installer yet. Once we get some feedback on how it’s working for everyone, the next step is to streamline this and make it an easier option in our installer. So if you try it out, be sure to let us know how it works for you!

### [](#powershell)PowerShell

On to other features, in case you missed it PowerShell is now in Kali (We have a [blog post](https://www.kali.org/tutorials/installing-powershell-on-kali-linux/) about it). This has been really great to bring the ability to execute PowerShell scripts directly on Kali.

![apt install powershell](https://www.kali.org/wp-content/uploads/2019/11/power-shell-1-1.png "apt install powershell")

![Type: ](https://www.kali.org/wp-content/uploads/2019/11/kali-pwsh-powershell-1.png "Type: ")

### [](#nethunter-kex-full-kali-desktop-on-android-phones)NetHunter Kex – Full Kali Desktop on Android phones

Another feature we are super excited about is the introduction of NetHunter Kex. In a nutshell, this allows you to attach your Android device to an HDMI output along with Bluetooth keyboard and mouse and get a full, no compromise, Kali desktop. Yes. From your phone.

![KeX new Theme](https://www.kali.org/wp-content/uploads/2019/11/kali-kex-theme.gif)

We had a live [Penetration Testing with Kali](https://www.offensive-security.com/pwk-oscp/) course we were teaching, and NetHunter Kex was just in a beta stage. So we wanted to really push the limits. So, in the live course, what we did was attach a USB-C hub to our OnePlus7. This gave us HDMI and Ethernet access. We attached the HDMI to the projector and used a bluetooth keyboard/mouse. With this, we were able to do an entire PWK module from the phone.

This is a feature you have to see to believe. Until you experience it, you won’t fully understand what this provides. With a strong enough phone, this is very similar to using a nice full-featured portable ARM desktop that happens to fit in your pocket. The possible ways you can leverage this in assessments is huge.

To get a full breakdown on how to use NetHunter Kex, check out our [docs at](https://www.kali.org/docs/nethunter/nethunter-kex-manager/).

[](#arm)ARM
-----------

**2019.4 is the last release that will support 8GB sdcards on ARM. Starting in 2020.1, a 16GB sdcard will be the minimum we support. You will always be able to create your own image that supports smaller cards if you desire.**

*   RaspberryPi kernel was updated to 4.19.81, and the firmware package was updated to include the eeprom updates for the RaspberryPi 4.

During the release testing, a limited number of devices were not showing the Kali menu properly. This was not critical enough to delay the release, so instead as a work-around you can run the following command to display the menu correctly:

apt update && apt dist-upgrade

Once this completes, log out, so you’re back at the login manager. Then switch to a console via CTRL+ALT+F11 (on the Chromebooks this is the key pointing left next to the ESC key).

Login and then run:

rm -rf .cache/ .config/ .local/ && sync && reboot

After reboot, the menu will have the correct entries. We’re still looking into why it occurs on only some of the images.

[](#download-kali-linux-20194)Download Kali Linux 2019.4
--------------------------------------------------------

So what are you waiting for? Start the [download](https://www.kali.org/downloads/) now!

Also, just to mention we do also produce [weekly builds](https://cdimage.kali.org/kali-images/kali-weekly) that you can use as well. If it’s been some time since our last release and you want the latest packages you don’t have to go off our latest release and update. You can just use the weekly image instead, and have fewer updates to do. Just know these are automated builds that we don’t QA like we do our standard release images.

If you already have an existing Kali installation, remember you can always do a quick update:

root@kali:~# cat deb https://ift.tt/16Fqw4e kali-rolling main non-free contrib  
EOF  
root@kali:~#  
root@kali:~# apt update && apt -y full-upgrade  
root@kali:~#  
root@kali:~# \[ -f /var/run/reboot-required \] && reboot -f

If you want to switch to our new Xfce:

root@kali:~# apt -y install kali-desktop-xfce

You should now be on Kali Linux 2019.4. We can do a quick check by doing:

root@kali:~# grep VERSION /etc/os-release  
VERSION="2019.4"  
VERSION\_ID="2019.4"  
VERSION\_CODENAME="kali-rolling"  
root@kali:~#  
root@kali:~# uname -v  
#1 SMP Debian 5.3.9-3kali1 (2019-11-20)  
root@kali:~#  
root@kali:~# uname -r  
5.3.0-kali2-amd64  
root@kali:~#

NOTE: The output of “uname -r” may be different depending on [architecture](https://pkg.kali.org/pkg/linux-latest).

As always, should you come across any bugs in Kali, please submit a report on our [bug tracker](https://bugs.kali.org/main_page.php). We’ll never be able to fix what we don’t know about.

  
  
from Kali Linux https://ift.tt/35ykean