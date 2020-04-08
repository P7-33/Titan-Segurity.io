---
title: ' Upgrade to Linux Kernel 5.4 RC1 on Ubuntu and Linux Mint System '
date: 2019-10-06T13:02:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-5JtrGr3SMnI/XZnXv-3BcpI/AAAAAAAAMqY/92u3owCxaOQn0UDi19eB3ULK42ESNF3PQCLcBGAsYHQ/s400/wkesofyj0lm31.jpg)](https://1.bp.blogspot.com/-5JtrGr3SMnI/XZnXv-3BcpI/AAAAAAAAMqY/92u3owCxaOQn0UDi19eB3ULK42ESNF3PQCLcBGAsYHQ/s1600/wkesofyj0lm31.jpg)

**  
[Linux kernel](https://www.kernel.org/)** [](https://www.kernel.org/) is the essential part of any Linux operating system. It is responsible for resource allocation, low-level hardware interfaces, security, simple communications, basic file system management, and more. Written from scratch by Linus Torvalds (with help from various developers), Linux is a clone of the UNIX operating system. It is geared towards POSIX and  
 Single UNIX Specification compliances.  
  
The heart of a Linux distribution  
  
The Linux kernel is the heart of a Linux distribution. If you are a long time Linux user, you may have stumbled across upgrades to the default Linux kernel packages, which lead to better support for certain hardware components or peripherals.  
  
Includes powerful features  
  
Linux provides users with powerful features, such as true multitasking, multistack networking, shared copy-on-write executables, shared libraries, demand loading, virtual memory, and proper memory management.  
  
Initially designed only for 386/486-based computers, now Linux supports a wide range of architectures, including 64-bit (IA64, AMD64), ARM, ARM64, DEC Alpha, MIPS, SUN Sparc, PowerPC, as well as Amiga and Atari machines.  
  

### What new on Linux Kernel 5.4 ?

The first Linux kernel 5.4 Release Candidate build is now available to download from kernel.org or through our free Linux software portal if you want to take it for test drive, but please be aware that this is an early development release that should not be installed on production machines.  
  
As for the new features that will be implemented in the Linux 5.4 kernel series, we can mention the controversial lockdown functionality, AMD DRM improvements, the usual updated drivers, mostly for GPU, networking, sound, staging, as well as documentation and filesystems changes.  
  
”Nothing major stands out, the most notable may be the long-pending lockdown patches that weren't all that big, but that now finally aren't tied to just EFI secure boot, so you can test them out other ways too,” said Linus Torvalds in a mailing list announcement.  
  
**"Linux kernel 5.4 expected to be released in mid-November"**  
  
The final release of the Linux 5.4 kernel series is expected to be released sometime in November, either on the 17th if Linus Torvalds will publish only seven RC (Release Candidate) builds,  or on the 24th if the development process takes longer and there's need for an eighth Release Candidate.  
  
Either way, users will be able to upgrade their computers to the Linux kernel 5.4 most probably in early December when the first point release hits the streets and marks the series as ready for mass deployments. Until then, go out and test the latest Release Candidate and report any issue you may encounter with your hardware \[[source](https://news.softpedia.com/news/linus-torvalds-kicks-off-development-of-linux-kernel-5-4-first-rc-is-out-now-527631.shtml)\].  

### How to install Linux Kernel 5.4 RC1 on Ubuntu and Linux Mint System :

To install/update [Linux Kernel 5.4 RC1](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.4-rc1/) on Ubuntu 18.04 Bionic Beaver, Ubuntu 18.10, Ubuntu 19.04 Disco Dingo, Cosmic Cuttlefish, Ubuntu 16.04 Xenial Xerus, Linux Mint 19.1, Elementary OS 5 'Juno', Peppermint, Deepin 15.8, Deepin 15.9, Linux Lite 4.2 and other Ubuntu derivative systems, open a new Terminal window and bash (get it?) in the following commands:  
  
Download kernel for official site :  
```
wget -c https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.4-rc1/linux-headers-5.4.0-050400rc1\_5.4.0-050400rc1.201909301433\_all.deb \\\\ https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.4-rc1/linux-headers-5.4.0-050400rc1-generic\_5.4.0-050400rc1.201909301433\_amd64.deb \\\\ https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.4-rc1/linux-headers-5.4.0-050400rc1-lowlatency\_5.4.0-050400rc1.201909301433\_amd64.deb \\\\ https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.4-rc1/linux-image-unsigned-5.4.0-050400rc1-generic\_5.4.0-050400rc1.201909301433\_amd64.deb \\\\ https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.4-rc1/linux-image-unsigned-5.4.0-050400rc1-lowlatency\_5.4.0-050400rc1.201909301433\_amd64.deb \\\\ https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.4-rc1/linux-modules-5.4.0-050400rc1-generic\_5.4.0-050400rc1.201909301433\_amd64.deb \\\\ https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.4-rc1/linux-modules-5.4.0-050400rc1-lowlatency\_5.4.0-050400rc1.201909301433\_amd64.deb
```

[![](https://1.bp.blogspot.com/-Q-7hOTa7k4k/XZnUPxvb5oI/AAAAAAAAMp8/U3HwWoBcVFE1cpI_Wf7ILQmr57h_fUU-QCLcBGAsYHQ/s400/kernel1.png)](https://1.bp.blogspot.com/-Q-7hOTa7k4k/XZnUPxvb5oI/AAAAAAAAMp8/U3HwWoBcVFE1cpI_Wf7ILQmr57h_fUU-QCLcBGAsYHQ/s1600/kernel1.png)

  
  
install latest kernel 5.4 RC1:  
  
```
sudo dpkg -i linux-headers-5.4.0-050400rc1\_\*.deb linux-image-unsigned-5.4.0-\*.deb linux-modules-5.4.0-050400rc1-\*.deb
```

[![](https://1.bp.blogspot.com/-mx5aytEbycc/XZnUaR5GmZI/AAAAAAAAMqE/CshxiE1tcQo6-_orNoQL1ySxM7IHG6FogCLcBGAsYHQ/s400/ere.png)](https://1.bp.blogspot.com/-mx5aytEbycc/XZnUaR5GmZI/AAAAAAAAMqE/CshxiE1tcQo6-_orNoQL1ySxM7IHG6FogCLcBGAsYHQ/s1600/ere.png)

  

[![](https://1.bp.blogspot.com/-0PcvCYn5ZEs/XZnUaS3jE9I/AAAAAAAAMqA/AAf2ppQOrRAvaUmygChFbDCYr-UeznrJwCLcBGAsYHQ/s400/kk.png)](https://1.bp.blogspot.com/-0PcvCYn5ZEs/XZnUaS3jE9I/AAAAAAAAMqA/AAf2ppQOrRAvaUmygChFbDCYr-UeznrJwCLcBGAsYHQ/s1600/kk.png)

  
After installation is finished, reboot your ubuntu system :  
```
$ sudo reboot
```  
  
And Check linux kernel version :  
```
$ uname -a
```

[![](https://1.bp.blogspot.com/-fHz3QUQz0QU/XZnb4aKCsmI/AAAAAAAAMqk/qSAi3md4OvwY5z8SuUT1KDsY_iyVHBo7wCLcBGAsYHQ/s400/ss.png)](https://1.bp.blogspot.com/-fHz3QUQz0QU/XZnb4aKCsmI/AAAAAAAAMqk/qSAi3md4OvwY5z8SuUT1KDsY_iyVHBo7wCLcBGAsYHQ/s1600/ss.png)

  
The source is [available](https://git.kernel.org/torvalds/t/linux-5.4-rc1.tar.gz) now. Binary packages are in the process of being built, and will appear soon at their respective download locations.