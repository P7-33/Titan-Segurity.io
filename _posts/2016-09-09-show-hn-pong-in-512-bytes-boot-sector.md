---
title: 'Show HN: Pong in 512 bytes (boot sector)'
date: 2020-01-04T01:36:00+01:00
draft: false
---

[](https://github.com/mat-sz/pongloader#pongloader)pongloader
=============================================================

[**Click here to open an online demo.**](https://matsz.dev/pongloader/)

[![Screenshot](https://raw.githubusercontent.com/mat-sz/pongloader/master/screenshot.png)](https://matsz.dev/pongloader/)

Bootloader version of pong, fits in 512 bytes.

**This project is optimized for the resulting binary size, not performance.**

You can download prebuilt binaries [here](https://github.com/mat-sz/pongloader/releases).

[](https://github.com/mat-sz/pongloader#running-in-qemu)Running in QEMU
-----------------------------------------------------------------------

```
make && qemu-system-x86_64 pong.bin 
```

  
  
from Hacker News https://github.com/mat-sz/pongloader