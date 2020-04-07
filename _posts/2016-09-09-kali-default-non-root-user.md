---
title: 'Kali Default Non-Root User'
date: 2019-12-31T18:21:00+01:00
draft: false
---

For years now, Kali has inherited the default root user policy from BackTrack. As part of our evaluation of [Kali tools](https://tools.kali.org/) and [policies](https://www.kali.org/docs/policy/) we have decided to change this and move Kali to a “traditional default non-root user” model. This change will be part of the 2020.1 release, currently scheduled for late January. However, you will notice this change in the [weekly images](https://cdimage.kali.org/kali-weekly/) starting now.

The History of Default Root User
--------------------------------

In the beginning, there was [BackTrack](https://www.backtrack-linux.org/). In its original form, BackTrack (v1-4) was a Slackware live based distro intended to be ran from a CDROM. Yes, we are go back a ways _(2006!)_.

In this model, there was no real update mechanism, just a bunch of pentesting tools living in the `/pentest/` directory, that you could use as part of assessments. It was the early days, so things were not very sophisticated, we were just all happy things worked. A lot of those tools back then either required root access to run or ran better when ran as root. With this operating system that would be ran from a CD, never be updated, and had a lot of tools that needed root access to run it was a simple decision to have a “everything as root” security model. It made complete sense for the time.

As time went by however, there were a number of changes. All of us that were around back then sort of remember things a little differently but on the broad strokes we saw people were installing BackTrack on bare metal so we felt like there should be an update mechanism, Especially after walking around Defcon and noticing how many people were using a version of BackTrack that was vulnerable to a certain exploit which came out a few weeks prior. That moved us to basing BackTrack 5 off of Ubuntu instead of Slackware live _(February 2011)_. Then as more time went by we were so busy fighting with Ubuntu that we felt like we needed to move onto something else.

That brought us to [Kali](https://www.kali.org/news/birth-of-kali/), and being an official [Debian derivative](https://wiki.debian.org/Derivatives/Census/Kali).

Modern Kali
-----------

Our move to be a Debian derivative brought with a whole host of advantages. So many in-fact its not worth reviewing them here, just look at the [early](https://www.kali.org/news/kali-linux-whats-new/) [Kali](https://www.kali.org/news/bleeding-edge-kali-repositories/) [blog](https://www.kali.org/news/kali-linux-accessibility-improvements/) [posts](https://www.kali.org/penetration-testing/kali-linux-penetration-testing-platform/) shortly after the launch and you will see a ton of [examples](https://www.kali.org/tutorials/tracking-fixing-installer-bugs/). But one advantage that we never really talked to much about is the fact that we are based on [Debian-Testing](https://wiki.debian.org/DebianTesting).

Debian has a well earned reputation for being one of the most stable Linux distros out there. Debian-Testing is the development branch of the next version of Debian, and realistically is still more stable than many mainstream Linux distros.

While we don’t encourage people to run Kali as their day to day operating system over the last few years more and more users have started to do so _(even if they are not using it todo penetration testing full time)_, including some members of the Kali development team. When people do so, they obviously don’t run as default root user. With this usage over time, there is the obvious conclusion that default root user is no longer necessary and Kali will be better off moving to a more traditional security model.

Why Some Tools Require Root Access
----------------------------------

Lets have a quick sidebar and review how some tools require root. For this, we will pick on [nmap](https://tools.kali.org/information-gathering/nmap).

Nmap is hands down the most popular portscanner in use today, and one of the most popular tools used on Kali. When ran by a non-root user doing a standard scan, nmap will default to running what is known as a connect scan (`-sT`). In this sort of scan, a full TCP three way handshake is conducted to identify if a given port is open or not. However, when ran as a root user nmap takes advantage of the additional privileges to utilize [raw sockets](http://man7.org/linux/man-pages/man7/raw.7.html) and will conduct a [syn scan](https://en.wikipedia.org/wiki/Port_scanner#SYN_scanning) (`-sS`), a far more popular scan type. This syn scan is not possible unless ran as root.

This aspect of security tools requiring root level permissions traditionally has not been uncommon. Running as a root user by default makes it easier to use these tools.

One of the, possibly surprising, conclusions we came too while looking at this issue is the number of tools that require root access has dropped over the years. This has made this default root policy less useful, bringing us to the point now where we are going to make this change.

Many Applications Require Non Root Accounts
-------------------------------------------

On the opposite direction, over the years a number of applications and services have been configured to forbid their usage as the `root` user. This has become either a maintenance burden for us (when we opted to patch out the check or reconfigure the service) or a nuisance for users that could not use their application (with [chrome/chromium](https://bugs.kali.org/view.php?id=5404) being a well known case).

Dropping this default root policy will thus simplify maintenance of Kali and will avoid problems for end-users.

Kali Non-Root User Implementation
---------------------------------

There are a number of changes you can expect to see as part of this change.

1.  Kali in live mode will be running as user `kali` password `kali`. No more `root`/`toor`. (Get ready to set up your IDS filters, as we are sure this user/pass combo will be being scanned for by bots everywhere soon).
2.  On install, Kali will prompt you to create a non-root user that will have administrative privileges (due to its addition to the `sudo` group). This is the same process as other Linux distros you may be familiar with.
3.  Tools that we identify as needing root access, as well as common administrative functions such as starting/stopping services, will interactively ask for administrative privileges (at least when started from the Kali menu). If you really don’t care about security, and if you preferred the old model, you can install kali-grant-root and run `dpkg-reconfigure kali-grant-root` to configure password-less root rights.

All-in-all, we don’t expect this will be a major change for most users. It is possible that some tools or administrative functions will be missed in our review, when that happens we would ask that you create a [bug report](https://bugs.kali.org) so it can be tracked and corrected. (And no, [tweeting](http://twitter.com/kalilinux) at us is not a bug report and won’t be tracked. Sorry, but that just does not scale).

Going Forward
-------------

All that said, we are still not encouraging people to use Kali as their day to day operating system. More than anything else, this is because we don’t test for that usage pattern and we don’t want the influx of bug reports that would come with it. However, for those of you that are familiar with Kali and want to run it as your day to day platform, this change should help you out a lot. For the rest of you, this should give you a better security model to operate under while you are doing assessments.

As we mentioned at the start, this change is currently available in the daily builds and will be in the next weekly build. Feel free to download and test early, as we would like to have as many potential issues shaken lose before release as possible. The more active users on this the better.

After a strong 2019 with Kali, this is a major change to start out our 2020 development cycle. Expect more as the [year goes on](https://www.kali.org/news/kali-linux-roadmap-2019-2020/). As always, feel free to join in on the [bug tracker](https://bugs.kali.org), [forums](https://forums.kali.org/forum.php), or [git](https://gitlab.com/kalilinux) to [contribute](https://www.kali.org/docs/community/contribute/) and be part of the future of Kali.

  
  
from Kali Linux https://ift.tt/2F7h2Hl