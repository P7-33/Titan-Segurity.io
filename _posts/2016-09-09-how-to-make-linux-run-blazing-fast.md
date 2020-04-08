---
title: 'How to make Linux run blazing fast (again) on Intel CPUs'
date: 2019-10-13T09:14:00+01:00
draft: false
---

It's just been one security disaster after another for Intel the last few years. Meltdown, Spectre variant after variant and this week the "Microarchitectural Data Sampling" aka Zombieload attack have all required performance-degrading fixes and workarounds. There is no way around turning hyperthreading off to be safe from MDS/Zombieload and this is a rather high performance-price to pay. So what if you don't want to?

[Disabling SMT/HyperThreading to get full protection against MDS/Zombieload](https://linuxreviews.org/Microarchitectural_Data_Sampling:_The_Latest_Side-Channel_Vulnerability_In_Intel_CPUs#Full_protection_requires_SMT.2FHyperThreading_to_be_disabled "Microarchitectural Data Sampling: The Latest Side-Channel Vulnerability In Intel CPUs") _on top_ of the mitigation code for "meltdown", several "spectre" variants and other security-issues discovered on Intel CPUs is a high price to pay for security on Intel CPUs. The total performance-penalty in many workloads is adding up. Unfortunately **there is no safe and secure way** around the performance-penalties - so you may want to..

TAKE THE RISK?
--------------

If you're not into currency trading or high finance or military contracting or anything of that nature and you'd just like to get maximum performance for your [Steam](https://linuxreviews.org/Steam "Steam") games then adding this is rather long one-liner to your kernel parameters will leave you wide open to _all the security risks_ for maximum excitement and squeeze back every bit of performance you used to get from your Intel CPU:

`**noibrs noibpb nopti nospectre_v2 nospectre_v1 l1tf=off nospec_store_bypass_disable no_stf_barrier mds=off mitigations=off**`

Just add that to your `/etc/sysconfig/grub` and re-generate grub's configuration file with `grub2-mkconfig` (your distributions procedure will vary) and you're all set.

Here is what the above kernel command options do, one by one:

*   `noibrs` - We don't need no _restricted_ indirect branch speculation
*   `noibpb` - We don't need no indirect branch prediction barrier either
*   `nospectre_v1` and `nospectre_v2`: Don't care if some program can get data from some other program when it shouldn't
*   `l1tf=off` - Why would we be flushing the L1 cache, we might _need_ that data. So what if anyone can get at it.
*   `nospec_store_bypass_disable` - Of course we want to use, not bypass, the stored data
*   `no_stf_barrier` - We don't need no barriers between software, they could be friends
*   `mds=off` - Zombieload attacks are fine
*   `mitigations=off` - Of course we don't want no mitigations

**You are (probably) an adult. You can and should wisely decide just how much risk you are willing to take.** Do or don't try this at home. You do not want to try this at work.

**Note:** How much of the above you actually need depends on your kernel version. The flag `mitigations=off`is all you need to turn _all_ mitigations off on kernel 5.1.13. Earlier kernels do not have a `mitigations=off` parameter. Using the long line above will disable everything on _any_ kernel and unsupported parameters will simply be ignored.

You can look at the file **Documentation/admin-guide/kernel-parameters.txt** in the kernel source for the kernel you are using to see what parameters are actually available on the kernel you are using.

  
_last edited 2019-05-20_

  
  
from Hacker News https://ift.tt/2LkUCrx