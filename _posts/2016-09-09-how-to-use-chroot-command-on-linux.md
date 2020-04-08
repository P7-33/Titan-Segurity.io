---
title: 'How to Use the chroot Command on Linux'
date: 2019-09-26T14:10:00+01:00
draft: false
---

![A terminal prompt on a Linux laptop's screen.](https://www.howtogeek.com/wp-content/uploads/2019/03/img_5c94224b1cfd7.png)

[Fatmawati Achmad Zaenuri/Shutterstock.com](https://www.shutterstock.com/image-vector/linux-interface-screen-notebook-world-map-321627716)

The `chroot` command can send you to jail, keep your development or test environments isolated, or just improve your system’s security. We show you the easiest way to use it.

What’s a chroot?
----------------

If you try to measure the usefulness of a command, you must take into account the functionality it provides and its ease of use. If it is too complicated for people to use or too long-winded to make them want to try to use it, the functionality might as well be zero. If no one uses it, it doesn’t provide any functionality.

In discussions with Linux users—in person and on forums—it seems that the `chroot` command is one that is pegged as being difficult to use, or too persnickety and tedious to setup. It seems this terrific utility isn’t used as much as it might be.

With `chroot` you can set up and [run programs or interactive shells](http://man7.org/linux/man-pages/man1/chroot.1.html) such as Bash in an encapsulated filesystem that is prevented from interacting with your regular filesystem. Everything within the `chroot` environment is penned in and contained. Nothing in the `chroot` environment can see out past its own, special, root directory without escalating to root privileges. That has earned this type of environment the nickname of a `chroot` jail. The term “jail” shouldn’t be confused with [FreeBSD’s](https://www.freebsd.org/) `jail` command, which creates a `chroot` environment [that is more secure](https://www.freebsd.org/cgi/man.cgi?query=jail) than the usual `chroot` environment.

But actually, there’s a very straightforward way to use `chroot`, which we’re going to step through. We’re using regular Linux commands which will work on all distributions. Some Linux distributions have dedicated tools to set up `chroot` environments, such as [debootstrap](http://manpages.ubuntu.com/manpages/trusty/man8/debootstrap.8.html) for Ubuntu, but we’re being distro-agnostic here.

When Should You Use a chroot?
-----------------------------

A `chroot` environment provides functionality similar to that of a virtual machine, but it is a lighter solution. The captive system doesn’t need a hypervisor to be installed and configured, such as [VirtualBox](https://www.virtualbox.org/wiki/Downloads) or [Virtual Machine Manager](https://virt-manager.org/). Nor does it need to have a kernel installed in the captive system. The captive system shares your existing kernel.

In some senses, `chroot` environments are closer to containers such as [LXC](https://linuxcontainers.org/) than to virtual machines. They’re lightweight, quick to deploy, and creating and firing one up can be automated. Like containers, one convenient way to configure them is to install just enough of the operating system for you to accomplish what is required. The “what is required” question is answered by looking at how you’re going to use your `chroot` environment.

Some common uses are:

**Software Development and Product Verification**. Developers write software and the product verification team (PV) tests it.  Sometimes issues are found by PV that can’t be replicated on the developer’s computer. The developer has all sorts of tools and libraries installed on their development computer that the average user—and PV—won’t have. Often, new software that works for the developer but not for others turns out to be using a resource on the developer’s PC that hasn’t been included in the test release of the software. `chroot` allows the developers to have a plain vanilla captive environment on their computer that they can sheep-dip the software in before giving it to PV. The captive environment can be configured with the bare minimum dependencies that the software requires.

### [Read the remaining 70 paragraphs](https://www.howtogeek.com/441534/how-to-use-the-chroot-command-on-linux/)