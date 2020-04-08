---
title: 'A Look at PureDarwin – An OS Based on the Open Source Core of macOS'
date: 2019-11-27T02:24:00+01:00
draft: false
---

A Look at PureDarwin - an OS based on the open source core of macOS
===================================================================

* * *

**Wednesday 27th November 2019**

PureDarwin is a community project to make [Darwin](https://en.wikipedia.org/wiki/Darwin_(operating_system)), the open source operating system developed by _Apple Inc._ that macOS is built upon, more usable by providing bootable ISOs and documentation.

![](https://www.jamieweb.net/blog/a-look-at-puredarwin/puredarwin-org.png)

_The [puredarwin.org](https://www.puredarwin.org/) homepage, showing the Hexley the Platypus mascot._

The project was founded in 2007, and is seen as the informal successor to the OpenDarwin project (which closed down in 2006). PureDarwin is a downstream project of [Darwinbuild](https://github.com/macosforge/darwinbuild), combining the open source Darwin base with other FOSS tools (such as X.org) to produce a usable system.

![](https://www.jamieweb.net/blog/a-look-at-puredarwin/puredarwin-xmas-vmware-window-maker-desktop.png)

_The Window Maker desktop environment running in the 'PureDarwin Xmas' release from December 2008._

**Skip to Section:**

```
**A Look at PureDarwin - an OS based on the open source core of macOS** ┣━━ [A Brief History of Darwin OS](https://www.jamieweb.net/blog/a-look-at-puredarwin/#a-brief-history-of-darwin-os) ┣━━ [PureDarwin Xmas](https://www.jamieweb.net/blog/a-look-at-puredarwin/#puredarwin-xmas) ┣━━ [Booting PureDarwin Xmas in VMware](https://www.jamieweb.net/blog/a-look-at-puredarwin/#booting-puredarwin-xmas-in-vmware) ┣━━ [PureDarwin 17.4 Beta](https://www.jamieweb.net/blog/a-look-at-puredarwin/#puredarwin-17-4-beta) ┣━━ [Booting PureDarwin 17.4 Beta in VirtualBox](https://www.jamieweb.net/blog/a-look-at-puredarwin/#booting-puredarwin-17-4-beta-in-virtualbox) ┗━━ [Conclusion](https://www.jamieweb.net/blog/a-look-at-puredarwin/#conclusion)
```

A Brief History of Darwin OS
----------------------------

Darwin itself was originally released by Apple in November 2000. It is a fork of [Rhapsody](https://en.wikipedia.org/wiki/Rhapsody_(operating_system)), which was the codename used for Apple's next-generation operating system after the purchase of [NeXT](https://en.wikipedia.org/wiki/NeXT) in 1998. Darwin utilises the [XNU](https://en.wikipedia.org/wiki/XNU) kernel, and currently runs on modern x86-64 processors, as well as 32-bit ARM processors in the case of older iOS devices (e.g. the iPhone 5C).

Many well-known elements of macOS such as the [Cocoa](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/CocoaFundamentals/WhatIsCocoa/WhatIsCocoa.html) framework and the famous [Aqua](https://en.wikipedia.org/wiki/Aqua_(user_interface)) graphical user interface are not included in Darwin, and unfortunately remain closed source.

![](https://www.jamieweb.net/blog/a-look-at-puredarwin/unix-timeline.png)

_A timeline of Unix-based operating systems, showing the common ancestors between different systems. [Source](https://en.wikipedia.org/wiki/File:Unix_timeline.en.svg) (Public Domain)_

The PureDarwin project was founded not to create a drop-in replacement for macOS. Instead it strives to be a usable implementation of Darwin which remains faithful to Apple's open source core, but without closed source components ('Pure'). Some example use cases of PureDarwin include an Apple-compatible build environment without using official Apple hardware, or to facilitate low-level testing of the Darwin kernel, without the limitations of macOS.

PureDarwin Xmas
---------------

The first developer preview release of PureDarwin is called '[PureDarwin Xmas](https://github.com/PureDarwin/PureDarwin/wiki/Xmas)', and was [released in December 2008](https://www.osnews.com/story/20696/puredarwin-xmas-developer-preview-released/) (hence the name 'Xmas'). It is based on Darwin 9, which corresponds to Mac OS X Leopard (10.5.x).

PureDarwin Xmas is a 'complete' operating system featuring a desktop environment and various GUI applications. However, as it is just a developer preview, some features such as networking and hardware support are quite limited.

![](https://www.jamieweb.net/blog/a-look-at-puredarwin/puredarwin-xmas-vmware-window-maker-desktop-with-applications.png)

_PureDarwin Xmas, showing the applications xcalc, xclock, xterm and xfontsel running in the Window Maker desktop window manager._

The menu controls in the top left control which workspace is currently on show. The menu on the right hand side is the application launcher, and the buttons at the bottom show the currently running applications. You can minimise, restore and resize windows using the available controls.

PureDarwin Xmas runs Bash 3.2.17, utilises the XFree86 4.7.0 display server and uses Window Maker 0.92.0 as the desktop window manager. `uname -a` yields the following:

```
Darwin PureDarwin.local 9.5.0 Darwin Kernel Version 9.5.0: Thu Sep 18 14:14:00 PDT 2008; root:xnu-1228.7.58.obj/RELEASE\_I386 i386
```

Many command-line and GUI applications come pre-installed in PureDarwin Xmas, including xedit, nano and vim. However, some applications such as Firefox and OpenOffice don't work out-of-the-box due to lack of driver support or missing files.

![](https://www.jamieweb.net/blog/a-look-at-puredarwin/puredarwin-xmas-vmware-window-maker-desktop-with-application-menus.png)

_Each of the primary application menus, showing the various programs and tools that are available in PureDarwin Xmas._

For example, the basic word processing tool 'xedit' is available and can be used to write, save and load documents.

![](https://www.jamieweb.net/blog/a-look-at-puredarwin/puredarwin-xmas-vmware-xedit.png)

_The 'xedit' tool with a new document being written._

The Window Maker environment can be heavily customised, and a magnification tool is included too.

![](https://www.jamieweb.net/blog/a-look-at-puredarwin/puredarwin-xmas-vmware-window-maker-preferences.png)

_The Window Maker configuration tool, with the magnifier showing a zoomed-in segment._

Networking support is very limited in PureDarwin Xmas, and unfortunately isn't supported at all when using VMware Workstation Player. This is because VMware uses an 'Intel e1000' device as the emulated ethernet controller, which requires the `AppleIntel8245XEthernet.kext` driver. This driver is closed source and not available for redistribution in any form.

Booting PureDarwin Xmas in VMware
---------------------------------

PureDarwin Xmas can be run as a virtual machine or on native Intel hardware, subject to relevant driver support. VirtualBox isn't supported as it isn't possible to fully emulate the required CPU type. However, VMware and QEMU can successfully boot PureDarwin Xmas when the correct configuration is used.

Modern versions of QEMU cannot boot the original PureDarwin Xmas image, due to incompatibilities with the Apple Partition Map file system used for the bootloader. Luckily, a [fixed version](https://github.com/PureDarwin/LegacyDownloads/releases/tag/PDXMASNBE01) has been released where the original bootloader has been 'transplanted' with an alternate one, where the file system is adequately supported in QEMU (x86 MBR).

In my case, I used VMware Workstation Player, as the PureDarwin Xmas image is distributed primarily in the VMware virtual machine format.

**In order to boot PureDarwin Xmas in VMware Workstation Player, the following steps can be used:**

1.  Download `puredarwinxmas.tar.xz` from the [Google Code repository](https://code.google.com/archive/p/puredarwin/downloads). Check the download against the SHA-256 checksum `5dad4c534ec475a87e204361cd510fec511acb655484c00ff7ce8ca41cb55f86`. Extract the file to yield the `puredarwinxmas.vmwarevm` directory.
2.  Download and install the appropriate version of VMware Workstation Player for your system from the [downloads page](https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/15_0). Verify your download against the checksums provided.
3.  Open VMware and import the `.vmx` file from the `puredarwinxmas.vmwarevm` directory. Keep the directory structure intact, as the configuration files in the directory are required in order to load the now-unsupported 'Mac OS Server' VM profile into VMware.
4.  Boot the VM. PureDarwin Xmas will boot directly to the desktop. On modern hardware, the total boot time is around 10 seconds.

The PureDarwin Xmas VMware configuration assigns only 1 virtual CPU core and 128 MB of RAM, but this is comfortably enough to run the lightweight Window Maker desktop and multiple applications.

![](https://www.jamieweb.net/blog/a-look-at-puredarwin/puredarwin-xmas-vmware-library.png)

_The PureDarwin Xmas virtual machine in the VMware library._

Interestingly, the VM profile used is 'Mac OS Server 10.5'. This isn't supported in modern versions of VMware, as full Apple operating systems can only be virtualised on official Apple hardware. However, as the VMware VM was created in a much older version of VMware (in 2008), the profile is saved in the exported configuration and can still be used for booting PureDarwin Xmas in the latest VMware releases (it will generate a warning though).

PureDarwin 17.4 Beta
--------------------

At the time of writing, the latest release of PureDarwin is [17.4 Beta](https://github.com/PureDarwin/PD-17.4-Beta). This was released in 2018, and is based on Darwin 17, which corresponds to macOS High Sierra (10.13.x).

Unlike PureDarwin Xmas, the 17.4 Beta release is a more lightweight/stripped-down OS, which doesn't feature a full GUI or display server. However, it has much improved driver support for modern hardware and hypervisors, and allows for basic networking when used in specific environments.

![](https://www.jamieweb.net/blog/a-look-at-puredarwin/puredarwin-17_4-beta-virtualbox-bash.png)

_The Bash 3.2 shell prompt in PureDarwin 17.4 Beta, showing the output of the commands `hostinfo`, `df -h`, `ps aux` and `ifconfig`._

The 17.4 Beta release runs Bash 3.2.57, and `uname -a` yields the following:

```
Darwin PureDarwin-17.4.local 17.4.0 Darwin Kernel Version 17.4.0: Mon 12 Feb 2018 00:19:58 GMT; ethan:xnu-4570.41.2/obj/RELEASE\_X86\_64 x86
```

Booting PureDarwin 17.4 Beta in VirtualBox
------------------------------------------

Unlike PureDarwin Xmas, the 17.4 Beta release of PureDarwin can be successfully booted in modern versions of VirtualBox and QEMU if the correct settings are used. VMware cannot be used, as it doesn't support modern macOS-esque guests unless you are running on official Apple hardware.

In my case, I used VirtualBox to allow for easy configuration of the relevant settings. **The following steps can be used to boot PureDarwin 17.4 Beta in VirtualBox:**

1.  Download `pd_17_4.vmdk.xz` from the [PureDarwin Devs site](https://www.pd-devs.org/Beta/pd_17_4.vmdk.xz). Check the download against the SHA-256 checksum `f2bb10f2fdb309a9a4fc77083c17b5a145db132551449a01b115f470d86c317c`. Extract the file to yield `pd_17_4.vmdk`.
2.  Download and install the appropriate version of VirtualBox for your system, either from your system package manager or from the [downloads page](https://www.virtualbox.org/wiki/Downloads). Verify your download against the checksums provided.
3.  Create a new virtual machine using type '**Mac OS X -> macOS 10.13 High Sierra (64-bit)**', without an attached disk. Set the chipset mode to **ICH9** and enable **I/O APIC**, then add an IDE controller in **ICH6** mode. Attach the `.vmdk` virtual disk file to the IDE controller.
4.  Boot the VM. PureDarwin 17.4 Beta will boot to a Bash 3.2 shell prompt. On modern hardware, the boot time is around 20 seconds.

There are some common errors that you may encounter if the virtual machine settings are not configured correctly. I have documented a couple of these below.

### `Still waiting for root device`:

This error occurs when the root file system cannot be recognised during the boot process. This seems to be related to the fact that the root file system is a virtual file system within the VMDK image, rather than one that was created using physical hardware.

```
Waiting on IOProviderClassIOResourcesIOResourcesMatchboot-uuid-media Still waiting for root device Still waiting for root device Still waiting for root device
```

This will occur around half way through the boot process, and the error will be printed repeatedly:

![](https://www.jamieweb.net/blog/a-look-at-puredarwin/puredarwin-17_4-beta-virtualbox-still-waiting-for-root-device.png)

_PureDarwin 17.4 Beta running in VirtualBox, showing the '`Still waiting for root device`' error._

In order to resolve this error, ensure that your virtual disk is using an IDE controller in ICH6 mode, and that the chipset mode is set to ICH9, as shown below:

![](https://www.jamieweb.net/blog/a-look-at-puredarwin/puredarwin-17_4-beta-virtualbox-ide-disk-controller-setup.png)

_The VirtualBox IDE disk controller settings._

![](https://www.jamieweb.net/blog/a-look-at-puredarwin/puredarwin-17_4-beta-virtualbox-motherboard-setup.png)

_The VirtualBox motherboard settings._

Once you have configured these options, PureDarwin should boot successfully.

### `Mach-O (i386) file has bad magic number`:

This error occurs if you try to boot PureDarwin 17.4 Beta in 32-bit mode, as currently only 64-bit is supported:

```
Mach-O (i386) file has bad magic number Decoding kernel failed. Press a key to continue...
```![](https://www.jamieweb.net/blog/a-look-at-puredarwin/puredarwin-17_4-beta-virtualbox-bad-magic-number.png)

_PureDarwin 17.4 Beta running in VirtualBox, showing the '`bad magic number`' error._

Ensure that the virtual machine type in VirtualBox is set to either 'Mac OS X -> macOS 10.13 High Sierra (64-bit)' or 'Other -> Other/Unknown (64-bit)', as shown below:

![](https://www.jamieweb.net/blog/a-look-at-puredarwin/puredarwin-17_4-beta-virtualbox-general-basic-settings.png)

_The VirtualBox general/basic settings._

Once you have done this, PureDarwin 17.4 Beta should be able to boot successfully.

Conclusion
----------

Overall I am impressed with the PureDarwin project and have enjoyed conducting my research around it. They have achieved a lot, considering that the project is funded by community donations and run by volunteers. It definitely isn't a production-ready system, but for developers it has the potential to come in very useful.

The PureDarwin team have been able to successfully install MacPorts in PureDarwin, allowing many software packages such as Apache HTTPd, Git and even XFCE to be installed. Unfortunately this is non-trivial to achieve without strong networking support, but it shows the potential use cases of PureDarwin.

Please check out the project at [www.puredarwin.org](https://www.puredarwin.org), and support their work by contributing if you are able to.

  
  
from Hacker News https://ift.tt/2KRRqBN