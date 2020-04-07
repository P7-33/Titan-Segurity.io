---
title: 'Cursedfs – Make a disk image formatted with both ext2 and FAT at once'
date: 2020-01-21T05:53:00+01:00
draft: false
---

![](https://avatars3.githubusercontent.com/u/23580910?s=400&v=4 "GitHub - NieDzejkob/cursedfs: Make a disk image formatted with both ext2 and FAT at once")  

[](https://github.com/NieDzejkob/cursedfs#cursedfs)cursedfs
===========================================================

Make a disk image formatted with both ext2 and FAT, at once.

```
~/cursedfs% wget 'https://github.com/NieDzejkob/cursedfs/releases/download/v1.0/cursed.img' ~/cursedfs% sudo mount -o loop -t ext2 cursed.img mountpoint/ ~/cursedfs% ls mountpoint/ mkfs.cursed ~/cursedfs% sudo umount mountpoint/ ~/cursedfs% sudo mount -o loop -t msdos cursed.img mountpoint/ ~/cursedfs% ls mountpoint/ gudnuse.ogg
```

[](https://github.com/NieDzejkob/cursedfs#why)Why?
==================================================

[I got nerd-sniped](https://twitter.com/Foone/status/1217162186130198529?s=20)

[](https://github.com/NieDzejkob/cursedfs#how)How?
==================================================

It turns out this is surprisingly simple to do: just create a FAT volume with a lot of reserved sectors and put the ext2 into the reserved sectors. This works because the filesystems choose different places to put their superblock: FAT uses the very first sector, while ext2 leaves the first kilobyte unused.

[](https://github.com/NieDzejkob/cursedfs#can-i-write-to-the-filesystems)Can I write to the filesystems?
========================================================================================================

Yes! When I first decided to do this, I thought writing to the image would surely break everything, but as it turns out, the method I've found means the filesystems don't conflict.

  
  
from Hacker News https://github.com/NieDzejkob/cursedfs