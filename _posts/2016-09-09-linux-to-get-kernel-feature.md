---
title: 'Linux to get kernel ''lockdown'' feature'
date: 2019-09-30T01:16:00+01:00
draft: false
---

![Linux Tux](https://zdnet1.cbsistatic.com/hub/i/2019/09/29/48b231e1-e790-446c-899a-e5f53296387f/f5dec279f0fedc5badc32aae3fa7c967/tux.png)

After years of countless reviews, discussions, and code rewrites, Linus Torvalds approved on Saturday a new security feature for the Linux kernel, named "lockdown."

The new feature will ship as a LSM (Linux Security Module) in the soon-to-be-released Linux kernel 5.4 branch, where it will be turned off by default; usage being optional due to the risk of breaking existing systems.

### Putting a leash on the root account

The new feature's primary function will be to strengthen the divide between userland processes and kernel code by preventing even the root account from interacting with kernel code -- something that it's been able to do, by design, until now.

When enabled, the new "lockdown" feature will restrict some kernel functionality, even for the root user, making it harder for compromised root accounts to compromise the rest of the OS.

"The lockdown module is intended to allow for kernels to be locked down early in \[the\] boot \[process\]," said Matthew Garrett, the Google engineer who proposed the feature a few years back.

"When enabled, various pieces of kernel functionality are restricted," said Linus Torvalds, Linux kernel creator, and the one who put the [final stamp of approval](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=aefcf2f4b58155d27340ba5f9ddbe9513da8286d) on the module yesterday.

This includes restricting access to kernel features that may allow arbitrary code execution via code supplied by userland processes; blocking processes from writing or reading /dev/mem and /dev/kmem memory; block access to opening /dev/port to prevent raw port access; enforcing kernel module signatures; and many more others, [detailed here](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/patch/?id=aefcf2f4b58155d27340ba5f9ddbe9513da8286d).

### Two lockdown modes

The new module will support two lockdown modes, namely "integrity" and "confidentiality." Each is unique, and restricts access to different kernel functionality.

"If set to integrity, kernel features that allow userland to modify the running kernel are disabled," said Torvalds.

"If set to confidentiality, kernel features that allow userland to extract confidential information from the kernel are also disabled."

If necessary, additional lockdown modes can also be added on top, but this will require an external patch, on top of the lockdown LSM.

### A long time coming

Work on the kernel lockdown feature started in the early 2010s, and was spearheaded by now-Google engineer, Matthew Garrett.

The idea behind the kernel lockdown feature was to create a security mechanism to prevent users with elevetated permissions -- even the vaunted "root" account -- from tampering with the kernel's code.

Back then, even if Linux systems were employing secure boot mechanisms, there were still ways that malware could abuse drivers, root accounts, and user accounts with special elevated privileges to tamper with the kernel's code, and by doing so, gain boot persistence and a permanent foothold on infected systems.

Many security experts have asked across the years that the Linux kernel support a more potent way to restrict the root account and improve kernel security.

The [main opposition came from Torvalds](https://arstechnica.com/information-technology/2013/02/linus-torvalds-i-will-not-change-linux-to-deep-throat-microsoft/), who was one of the feature's most ardent critics, especially in its early days.

As a result, many Linux distros, such as Red Hat, developed their own Linux kernel patches that added a lockdown feature on top of the mainline kernel. However, the two parties reached a middleground [in 2018](https://lwn.net/Articles/751061/), and work progressed on the lockdown feature this year.

"The majority of mainstream distributions have been carrying variants of this patchset for many years now, so there's value in providing a doesn't meet every distribution requirement, but gets us much closer to not requiring external patches," Torvalds said yesterday.

"Applications that rely on low-level access to either hardware or the kernel may cease working as a result - therefore this should not be enabled without appropriate evaluation beforehand."

The news that a kernel lockdown module has been finally approved has been greeted positively in the Linux and cyber-security communities.

> Windows Vista: Let’s lock down the kernel  
> Linux 3.x: lul root is kernel brah  
> ...  
> Windows 10: Kernel arbitrary writes from Admin are not bugs, there’s a party in ring0 and the bouncer is off duty  
> Linux 5.x: hey, let’s lock down the kernel [https://t.co/ex8p8tCLmR](https://t.co/ex8p8tCLmR)
> 
> — Alex Ionescu (@aionescu) [September 29, 2019](https://twitter.com/aionescu/status/1178353010109321216?ref_src=twsrc%5Etfw)

  
  
from Latest Topic for ZDNet in... https://ift.tt/2op0hSZ