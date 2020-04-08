---
title: 'Pack Your Bags – Systemd Is Taking You To A New Home'
date: 2019-10-16T15:05:00+01:00
draft: false
---

Home directories have been a fundamental part on any Unixy system since day one. They’re such a basic element, we usually don’t give them much thought. And why would we? From a low level point of view, whatever location `$HOME` is pointing to, is a directory just like any other of the countless ones you will find on the system — apart from maybe being located on its own disk partition. Home directories are so unspectacular in their nature, it wouldn’t usually cross anyone’s mind to even consider to change anything about them. [And then there’s Lennart Poettering](https://cfp.all-systems-go.io/ASG2019/talk/VSQRXA/).

In case you’re not familiar with the name, he is the main developer behind the `systemd` init system, which has nowadays been adopted by the majority of Linux distributions as replacement for its oldschool, Unix-style init-system predecessors, essentially changing everything we knew about the system boot process. Not only did this change personally insult every single Perl-loving, Ken-Thompson-action-figure-owning grey beard, it engendered contempt towards `systemd` and Lennart himself that approaches Nickelback level. At this point, it probably doesn’t matter anymore what he does next, _haters gonna hate_. So who better than him to disrupt everything we know about home directories? Where you \_live\_?

Although, home directories are just one part of the equation that his latest creation — [the `systemd-homed` project](https://github.com/poettering/systemd/tree/homed) — is going to make people hate him even more tackle. The big picture is really more about the whole concept of user management as we know it, which sounds bold and scary, but which in its current state is also a lot more flawed than we might realize. So let’s have a look at what it’s all about, the motivation behind `homed`, the problems it’s going to both solve and raise, and how it’s maybe time to leave some outdated philosophies behind us.

A Quick Introduction To Systemd
-------------------------------

[![](https://hackaday.com/wp-content/uploads/2019/10/Systemd_components2.png?w=400)](https://hackaday.com/wp-content/uploads/2019/10/Systemd_components2.png)

Just one more module… Image: Shmuel Csaba Otto Traian \[[CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0)\], [via Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Systemd_components.svg)

Before we get into the `homed` part of the endeavor, let’s bring everyone on the same page about `systemd` itself. In simple words, `systemd` handles everything that lies beyond the kernel’s tasks to start up the system: setting up the user space and providing everything required to get all system processes and daemons running, and managing those processes along the way. It’s both replacing the old `init` process running with PID 1, and providing an administrative layer between the kernel and user space, and as such, is coming with a whole suite of additional tools and components to achieve all that: system logger, login handling, network management, IPC for communication between each part, and so on. So, what was once handled by all sorts of single-purpose tools has since become part of `systemd` itself, which is one source of resentment from people latching on to the “one tool, one job” philosophy.

Technically, each tool and component in `systemd` is still shipped as its own executable, but due to interdependency of these components they’re not really that standalone, and it’s really more just a logical separation. `systemd-homed` is therefore one additional such component, aimed to handle the user management and the home directories of those users, tightly integrated into the `systemd` infrastructure and all the additional services it provides.

But why change it at all? Well, let’s have a look at the current way users and home directories are handled in Linux, and how `systemd-homed` is planning to change that.

The Status Quo Of $HOME And User Management
-------------------------------------------

Since the beginning of time, users have been stored in the `/etc/passwd` file, which includes among other things the username, a system-unique user id, and the home directory location. Traditionally, the user’s password was also stored in hashed form in that file — and it might still be the case on some, for example embedded systems — but was eventually moved to a separate `/etc/shadow` file, with more restricted file permissions. So, after successfully logging in to the system with the password found in the shadow file, the user starts off in whichever location the home directory entry in `/etc/passwd` is pointing to.

[![](https://hackaday.com/wp-content/uploads/2019/10/8549350013_33bfbb74cc_b.jpg?w=400)](https://hackaday.com/wp-content/uploads/2019/10/8549350013_33bfbb74cc_b.jpg)

Sure you want to live here? [“Rosedale home”](https://www.flickr.com/photos/34534185@N00/8549350013)by [Sheba\_Also](https://www.flickr.com/photos/34534185@N00), [CC BY-SA 2.0](https://creativecommons.org/licenses/by-sa/2.0/?ref=ccsearch&atype=html)

In other words, for the most fundamental process of logging in to a system, three individual parts that are completely independent and separated from each other are required. Thanks to well-defined rules that stem from simpler times and have since remained mostly untouched, and which every system and tool involved in the process commendably abides by, this has worked out just fine. But if we think about it: is this really the best possible approach?

Note that this is just the most basic local user login. Throw in some network authentication, additional user-based resource management, or disk encryption, and you will notice that `/etc/passwd` isn’t the place for any of that. And well, why would it be — _one tool, one job_, right? As a result, instead of configuring everything possibly related to a user in one centralized user management system that is flexible enough for any present and future considerations, we just stack dozens of random configurations on top of and next to each other, with each one of them doing their own little thing. And we are somehow perfectly fine and content with that.

Yet, if you had to design a similar system today from scratch, would you really opt for the same concept? Would your system architect, your teacher, or even you yourself really be fine with duplicate database entries (usernames both in `passwd` and shadow file), unenforced relationships (home directory entry and home directory itself), and just random additional data without rhyme or reason: resource management, PAM, network authentication, and so on? Well, as you may have guessed by now, Lennart Poettering isn’t much a fan of that, and with `systemd-homed` he is aiming to unite all the separate configuration entities around user management into one centralized system, flexible enough to handle everything the future might require.

Knock Knock – It’s Systemd
--------------------------

So instead of each component having its own configuration for all users, `systemd-homed` is going to collect all the configuration data of each component based on the user itself, and store it in a user-specific record in form of a JSON file. The file will include all the obvious information such as username, group membership, and password hashes, but also any user-dependent system configurations and resource management information, and essentially really just _anything_ relevant. Being JSON, it can virtually contain whatever you want to put there, meaning it is easily extendable whenever new features and capabilities are required. No need to wonder anymore which of those three dozen files you need to touch if you want to change something.

In addition to user and user-based system management, the home directory itself will be linked to it as a LUKS encrypted container — and this is where the interesting part comes, even if you don’t see a need for a unified configuration place: the encryption is directly coupled to the user login itself, meaning not only is the disk automatically decrypted once the user logs in, it is equally automatic encrypted again as soon as the user logs out, locks the screen, or suspends the device. In other words, your data is inaccessible and secure whenever you’re not logged in, while the operating system can continue to operate independently from that.

There is, of course, one downside to that.

Chicken / Egg Problem With SSH
------------------------------

If the home directory requires an actively logged-in user to decrypt the home directory, there’s going to be a problem with remote logins via SSH that depend on the SSH decryption key found inside the (at that point encrypted) home directory. For that reason, SSH simply won’t work without a logged in local user, which of course defies the whole point of remote access.

[![](https://hackaday.com/wp-content/uploads/2019/09/OpenSSH_logo.png?w=194)](https://hackaday.com/wp-content/uploads/2019/09/OpenSSH_logo.png)

The OpenSSH logo.

That being said, it’s worth noting that at this stage, `systemd-homed` is focusing mostly on regular, real human users on a desktop or laptop, and not so much system or service-specific users, or anything running remotely on a server. That sounds of course like a bad excuse, but keep also in mind that `systemd-homed` will change the very core of user handling, so it’s probably safe to assume that future iterations will diminish that separation and things will work properly for either type of user. I mean, no point to reinvent the wheel if you need to keep the old one around as well — but feel free to call me naive here.

Ideally, the SSH keys would be migrated to the common-place user management record, but that would require some work on SSH’s side. This isn’t happening right now, but then again, `systemd-homed` itself is also just a semi-implemented idea in a git branch at this point. It’s unlikely going to be widely adapted and forced onto you by the evil Linux distributions until this issue in particular is solved — but again, maybe I’m just overly optimistically naive.

Self-Contained Users With Portable Homes
----------------------------------------

But with user management and home directory handling in a single place and coupled together, you can start to dream of additional possible features. For instance, portable home directories that double as self-contained users. What that means is that you could keep the home directory for example on a USB stick or external disk, and seamlessly move it between, say, your workstation at home and your laptop whenever you’re on the move. No need to duplicate or otherwise sync your data, it’s all in one place with you. This brings security and portability benefits.

[![](https://hackaday.com/wp-content/uploads/2019/10/14707274736_fa6b738f2c_b.jpg?w=250)](https://hackaday.com/wp-content/uploads/2019/10/14707274736_fa6b738f2c_b.jpg)

Or would you rather live here? By [ltenney1225](https://www.flickr.com/photos/57545119@N04/14707274736) CC BY-NC 2.0

But that’s not all. It wouldn’t have to be your own device you can attach your home directory to, it could be a friend’s device or the presenter laptop at a conference or really _any_ compatible device. As soon as you plug in your home directory into it, your whole user will automatically exist on that device as well. Well, sort of automatically. Obviously, no one would want some random people roaming around on their system, so the system owner / superuser will still have to grant you access to their system first, with a user and resource configuration based on their own terms, and signed to avoid tempering.

Admittedly, for some of you, this might all sound less like amazing new features and more like a security nightmare and mayhem just waiting to happen. And it most certainly will bring a massive change to yet another core element of Linux where a lot could possibly go wrong. How it will all play out in reality remains to be seen. Clearly it won’t happen over night, and it won’t happen out of nowhere either — the changes are just too deep and fundamental. But being part of `systemd` itself, and seeing its influence on Linux, one has to entertain the idea that this _might_ happen one day in the not too distant future. And maybe it should.

Times Are Changing
------------------

Yes, this will disrupt everything we know about user management. And yes, it goes against everything Unix stands for. But it also gets rid of an ancient concept that goes against everything the software engineering world has painfully learned as best practices over all these decades since. After all, it’s neither the 70s nor the 80s anymore. We don’t have wildly heterogeneous environments anymore where we need to find the least capable common denominator for each and every system anymore. Linux is the dominant, and arguably the only really relevant open source “Unix” system nowadays — even Netflix and WhatsApp running FreeBSD is really more anecdotal in comparison. So why should Linux really care about compatibility with “niche” operating systems that are in the end anyway going to do their own thing? And for that matter, why should we still care about Unix altogether?

It generally begs the question, why do we keep on insisting that computer science as a discipline has reached its philosophical peak in a time the majority of its current practitioners weren’t even born yet? Why are we so frantically holding on to a philosophy that was established decades before the world of today with its ubiquitous internet, mobile connectivity, cloud computing, Infrastructure/Platform/Software/Whatnot-as-a-Service, and everything on top and below that has become reality? Are we really that nostalgic about the dark ages?

I’m not saying that the complexity we have reached with technology is necessarily an outcome we should have all hoped for, but it is where we are today. And it’s only going to get worse. The sooner we accept that and move on from here, and maybe adjust our ancient philosophies along the way, the higher the chance that we will actually manage to tame this development and keep control over it.

Yes, change is a horrible, scary, and awful thing if it’s brought upon us by anyone else but ourselves. But it’s also inevitable, and `systemd-homed` might just be the proverbial broken egg that will give us a delicious omelette here. Time will tell.

  
  
from Hackaday https://ift.tt/2MljSgA  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)