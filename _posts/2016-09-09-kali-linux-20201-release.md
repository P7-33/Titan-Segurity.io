---
title: 'Kali Linux 2020.1 Release'
date: 2020-01-28T16:55:00+01:00
draft: false
---

We are here to kick off our first release of the decade, with Kali Linux 2020.1! Available for immediate [download](https://www.kali.org/downloads/).

The following is a brief feature summary for this release:

*   [Non-Root by default](https://www.kali.org/news/kali-default-non-root-user/)
*   Kali single installer image
*   [Kali NetHunter Rootless](https://www.kali.org/docs/nethunter/nethunter-rootless/)
*   Improvements to theme & kali-undercover
*   New tools

Non-Root
--------

Throughout the history of Kali (and its predecessors BackTrack, WHAX, and Whoppix), the default credentials have been `root/toor`. This is no more. We are no longer using the superuser account, root, as default in Kali 2020.1. The default user account is now a [standard, unprivileged, user](https://www.kali.org/docs/policy/kali-linux-user-policy/).

For more of the reasons behind this switch, please see our [previous blog post](https://www.kali.org/news/kali-default-non-root-user/). As you can imagine, this is a very large change, with years of history behind it. As a result, if you notice any issues with this, please do let us know on the [bug tracker](https://bugs.kali.org/).

`root/toor` is dead. Long live `kali/kali`.

![kali-kali-login](https://www.kali.org/wp-content/uploads/2020/01/kali-kali-login.png)

#### Kali as your Main OS

So with this, should you use Kali as your daily driver, as the primary OS? It’s up to you.  
There wasn’t anything really stopping you before, we just don’t encourage it. We still don’t. But its a helping hand for the people who are familiar with Kali enough.

Why do we not recommend it?  
Because we are unable to test for that usage pattern and we don’t want the influx of bug reports that would come with it.  
If you are brave enough to try it, you may wish to switch the [branch from “rolling” to “kali-last-snapshot”](https://www.kali.org/docs/introduction/kali-branches/) to try and be more stable.

Kali Single Installer Image
---------------------------

We took a good hard look at the usage of Kali, what images are actually downloaded, how they are put to use, and so on. With this information in hand, we decided to completely restructure and simplify the images we release. Going forward, we will have an installer image, a live image, and a network installer image.

These changes should allow for easier selection of the right image for you to download, while increasing flexibility on installation and further reducing download sizes.

**Our Installer Image**

*   This is what we recommend for most users that want to install Kali on their system
*   Doesn’t require a network connection (aka offline install) for the default package selection
*   Able to select desktop environment to install (Previously there was a separate image for each DE: XFCE, GNOME, KDE, etc.)
*   Able to select tools to install at install time
*   Can’t be used to boot a live system. This is just an installer image.
*   Filename:
    *   `kali-linux-2020.1-installer-.iso`

We are no longer offering separate images for every desktop environment (DE). Instead, we now have a single image with the option to pick your DE during installation. This means there isn’t a download link for Xfce (which is our default option since [2019.4](https://www.kali.org/news/kali-linux-2019-4-release/)), GNOME, KDE, MATE or LXDE DEs. Just one image to rule them all.

At install time, you may [select the tools included](https://www.kali.org/docs/general-use/metapackages/) with Kali (or **none at all**)! This gives you more control over what **you** what. We understand that Kali comes with more tools than some people use, or they have their own select tools they use. Now they can install Kali without any metapackages, giving them a bare Kali installation, so they can **individually select what tools they want** (rather than groups).

The default image contains the `kali-desktop-xfce` and `kali-tools-default` packages, allowing for an offline installation of Kali (as it always has been). Selecting any non-default tools will require a network connection.

Note: “Kali Live” is not included in this image. If you wish to use live mode, you’ll need the live image.

[![Kali Setup Screen](https://www.kali.org/wp-content/uploads/2020/01/tasksel_first_0.png)](https://www.kali.org/wp-content/uploads/2020/01/tasksel_first_0.png)

**Network Install Image**

*   Smallest image to download
*   This requires a network connection to install
*   During setup, it will download the latest packages every time it’s used
*   Able to select desktop environment to install
*   Able to select tools to install
*   Can’t be used to boot a live system. This is just an installer image.
*   Filename:
    *   `kali-linux-2020.1-installer-netinst-.iso`

It’s a very small image, containing only enough to install the base system, but behaving exactly like the full installer image, allowing you to install everything that Kali offers, provided that you have enabled network connectivity.

**Live Image**

*   Its primary use is to be able to run Kali, without installing it
*   But it also contains an installer, behaving like the “Network Install Image” described above
*   Filename:
    *   `kali-linux-2020.1-live-.iso`

“Kali Live” hasn’t been forgotten about – it’s just moved to its own image. This allows you to try Kali without installing it and is perfect for running off a USB stick. You can install from this image, however, it will require a network connection (this is why we suggest the stand-alone install image for most users).

Alternatively, you can [generate your own image](https://www.kali.org/docs/development/dojo-mastering-live-build/), in particular if you want to use another desktop environment instead of our default Xfce. It’s not as hard as it sounds!.

ARM Images
----------

You will probably notice a bit of a change in the ARM images starting with our 2020.1 release. There are fewer images available for download, due to both manpower and hardware constraints, some images won’t be posted without community assistance.  
The scripts are still updated, so if an image doesn’t exist for a machine you use, you will have to create it by running the [build script](http://gitlab.com/kalilinux/build-scripts/kali-arm) on a Kali machine.

ARM images for 2020.1 will still run as root by default.

The sad news that a lot of people didn’t want to hear… an image for the Pinebook Pro isn’t included in the 2020.1 release. We are still working on getting it added, and as soon as it is ready we will post it.

NetHunter Images
----------------

Our mobile pen-testing platform, Kali NetHunter, has also had some new improvements. You are now no longer required to root your phone in order to run Kali NetHunter, but that does come with some limitations.

To suit everybody’s needs, Kali NetHunter now comes in the following three editions:

*   **NetHunter** – Needs rooted devices with custom recovery and patched kernel. Has no restrictions. Device specific images are available [here](https://www.offensive-security.com/kali-linux-nethunter-download/).
*   **NetHunter Light** – Needs rooted devices with custom recovery but no custom kernel. Has minor restrictions, i.e. no WiFi injection or HID support. Architecture specific images are available [here](https://www.offensive-security.com/kali-linux-nethunter-download/).
*   **NetHunter Rootless** – Installable on all stock standard, unmodified devices using Termux. Some limitations, like lack of db support in Metasploit and no root permissions. Installation instruction is available [here](https://www.kali.org/docs/nethunter/nethunter-rootless/).

The [NetHunter documentation page](https://www.kali.org/docs/nethunter/#1-0-nethunter-editions) includes a more detailed comparison.  
Each NetHunter edition comes with both the new “kali” user as well as root. KeX now supports multiple sessions so you can opt to run your pentest in one whilst writing a report in another.

Please note that due to how Samsung Galaxy devices function, the non-root user might not be able to run `sudo` but has to use `su -c` instead.

One of the peculiarities of the new “NetHunter Rootless” edition is that the default non-root user has almost full privileges in the chroot due to how proot containers work.

[![Kali Nethunter](https://www.kali.org/wp-content/uploads/2020/01/release-2020.1-nethunter1-scaled.jpg)](https://www.kali.org/wp-content/uploads/2020/01/release-2020.1-nethunter1-scaled.jpg) [![Kex Manager](https://www.kali.org/wp-content/uploads/2020/01/release-2020.1-nethunter2.jpg)](https://www.kali.org/wp-content/uploads/2020/01/release-2020.1-nethunter2.jpg)

Theming
-------

With our last release, we made a major change switching from GNOME to Xfce. That wasn’t the end for us; we have kept on going with the design work, and have more updates:

**GNOME** There is now a new theme for GNOME users and as an additional bonus, there is a light and dark theme!

[![Shell Overview](https://www.kali.org/wp-content/uploads/2020/01/release-2020.1-gnome-shell-overview.png)](https://www.kali.org/wp-content/uploads/2020/01/release-2020.1-gnome-shell-overview.png)

[![Light Theme](https://www.kali.org/wp-content/uploads/2020/01/release-2020.1-gnome-shell-light.png)](https://www.kali.org/wp-content/uploads/2020/01/release-2020.1-gnome-shell-light.png)

[![Dark Theme](https://www.kali.org/wp-content/uploads/2020/01/release-2020.1-gnome-shell-dark.png)](https://www.kali.org/wp-content/uploads/2020/01/release-2020.1-gnome-shell-dark.png)

**Tools** We are giving the tools that you are very fond of a makeover too! We are slowly working through our collection, refreshing them and adding in new icons.

[![Kali Tools Icons](https://www.kali.org/wp-content/uploads/2020/01/release-2020.1-icons.png)](https://www.kali.org/wp-content/uploads/2020/01/release-2020.1-icons.png)

**Menu** Eagle-eyed users may also notice the icons used in the menu have also been replaced.

[![Kali Menu](https://www.kali.org/wp-content/uploads/2020/01/release-2020.1-menu.jpeg)](https://www.kali.org/wp-content/uploads/2020/01/release-2020.1-menu.jpeg)

**Setup** And if you opt to use the graphical installer of Kali, it’s also been updated _(Before and after shots)_

[![Kali Setup Options](https://www.kali.org/wp-content/uploads/2020/01/release-2020.1-setup.png)](https://www.kali.org/wp-content/uploads/2020/01/release-2020.1-setup.png)

Kali-Undercover
---------------

We were not expecting the community’s overwhelming response to kali-undercover. So carrying on from [Kali 2019.4 release](https://www.kali.org/news/kali-linux-2019-4-release/), Kali-undercover now starts to feel even more like Windows to help blend in.

![Kali Undercover](https://www.kali.org/wp-content/uploads/2020/01/release-2020.1-undercover.png)

New Packages
------------

Kali Linux is a rolling distribution, so it gets updates as soon as they are available, rather than waiting for “the next release”. So since the last release, we have the normal tool upgrades as well as a few new tools added, such as: `cloud-enum`, `emailharvester`, `phpggc`, `sherlock`, `splinter`.

We have a few new (`kali-community-wallpapers`) and old (`kali-legacy-wallpapers`) wallpapers to offer up if you want to customize or are feeling a little a little nostalgic.

_@g0tmi1k – show a overview of the folder. GNOME view?_

Python 2 End Of Life
--------------------

As a reminder, [Python 2 has reached “end of life”](https://www.kali.org/news/python-2-end-of-life/) on the 1st of January 2020. What this means is, we are removing tools that depend on Python 2. Why? Because they are no longer being maintained, they are not receiving updates, and they need replacing. The pentesting landscape is a dynamic field that is forever changing. It’s time to keep up. We will be doing our best to find alternatives that are actively worked upon.

Giving A Helping Hand
---------------------

If you want to [contribute to Kali](https://www.kali.org/docs/community/contribute/) please do! If you have an area, idea of something YOU would like to work on, please dig in. If you want to help, but don’t know where to start, please see [our docs page](//www.kali.org/docs/community/contribute/)). If you have a suggestion for a feature, please record it on the [bug tracker](https://bugs.kali.org/).

Note: the bug tracker is for [bugs & suggestions](https://www.kali.org/docs/community/submitting-issues-kali-bug-tracker/). Its not a place to get help or support – that’s for the [forums](https://forums.kali.org/).

Download Kali Linux 2020.1
--------------------------

**Fresh images** Why are you waiting? Start [downloading](https://www.kali.org/downloads/) now!

**Existing Upgrades** If you already have an existing Kali installation, remember you can always do a quick update:

kali@kali:~$ cat <deb https://ift.tt/16Fqw4e kali-rolling main non-free contrib  
EOF  
kali@kali:~$  
kali@kali:~$ sudo apt update && sudo apt -y full-upgrade  
kali@kali:~$  
kali@kali:~$ \[ -f /var/run/reboot-required \] && sudo reboot -f  
kali@kali:~$

You should now be on Kali Linux 2020.1. We can do a quick check by doing:

kali@kali:~$ grep VERSION /etc/os-release  
VERSION="2020.1"  
VERSION\_ID="2020.1"  
VERSION\_CODENAME="kali-rolling"  
kali@kali:~$  
kali@kali:~$ uname -v  
#1 SMP Debian 5.4.13-1kali1 (2020-01-20)  
kali@kali:~$  
kali@kali:~$ uname -r  
5.4.0-kali3-amd64  
kali@kali:~$

NOTE: The output of `uname -r` may be different depending on [architecture](https://pkg.kali.org/pkg/linux-latest).

As always, should you come across any bugs in Kali, please submit a report on our [bug tracker](https://bugs.kali.org/main_page.php). We’ll never be able to fix what we don’t know is broken.

  
  
from Kali Linux https://ift.tt/2O5SJhT