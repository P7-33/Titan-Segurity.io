---
title: 'Learn to write a simple OS kernel with keyboard/screen support (2014)'
date: 2020-01-26T06:12:00+01:00
draft: false
---

[](https://github.com/arjun024/mkeykernel#mkeykernel)mkeykernel
===============================================================

This is a kernel that can read the characters `a-z` and `0-9` from the keyboard and print them on screen.

See the repo [mkernel](http://github.com/arjun024/mkernel) which is a minimal kernel that prints a string on the screen. mkeykernel just extends this to include keyboard support.

#### [](https://github.com/arjun024/mkeykernel#blog-post)Blog post

[Kernel 201 - Let’s write a Kernel with keyboard and screen support](http://arjunsreedharan.org/post/99370248137/kernel-201-lets-write-a-kernel-with-keyboard-and)

#### [](https://github.com/arjun024/mkeykernel#build-commands)Build commands

```
nasm -f elf32 kernel.asm -o kasm.o 
``````
gcc -m32 -c kernel.c -o kc.o 
``````
ld -m elf_i386 -T link.ld -o kernel kasm.o kc.o 
```

If you get the following error message:

```
kc.o: In function `idt_init': kernel.c:(.text+0x129): undefined reference to `__stack_chk_fail' 
```

compile with the `-fno-stack-protector` option:

```
gcc -fno-stack-protector -m32 -c kernel.c -o bin/kc.o 
```

#### [](https://github.com/arjun024/mkeykernel#test-on-emulator)Test on emulator

```
qemu-system-i386 -kernel kernel 
```

#### [](https://github.com/arjun024/mkeykernel#get-to-boot)Get to boot

GRUB requires your kernel executable to be of the pattern `kernel-`.

So, rename the kernel:

```
mv kernel kernel-701 
```

Copy it to your boot partition (assuming you are superuser):

```
cp kernel-701 /boot/kernel-701 
```

Configure your grub/grub2 similar to what is given in `_grub_grub2_config` folder of [mkernel repo](http://github.com/arjun024/mkernel).

Reboot.

Voila!

[![kernel screenshot](https://camo.githubusercontent.com/cd88fa80cb4c3f4b263f538b517bcac25e008629/687474703a2f2f33312e6d656469612e74756d626c722e636f6d2f31616664373562343333623133646636313366613063323330313937373839332f74756d626c725f696e6c696e655f6e63793170306b53476a317269767271632e706e67 "Screenshot")](https://camo.githubusercontent.com/cd88fa80cb4c3f4b263f538b517bcac25e008629/687474703a2f2f33312e6d656469612e74756d626c722e636f6d2f31616664373562343333623133646636313366613063323330313937373839332f74756d626c725f696e6c696e655f6e63793170306b53476a317269767271632e706e67)

  
  
from Hacker News https://ift.tt/1GqUGOk