---
title: 'Arch Linux is now using Zstandard instead of xz for package compression'
date: 2020-01-05T03:08:00+01:00
draft: false
---

As announced on the [mailing list](https://lists.archlinux.org/pipermail/arch-dev-public/2019-December/029752.html), on Friday, Dec 27 2019, our package compression scheme has changed from xz (.pkg.tar.xz) to [zstd (.pkg.tar.zst)](https://lists.archlinux.org/pipermail/arch-dev-public/2019-December/029778.html).

zstd and xz trade blows in their compression ratio. Recompressing all packages to zstd with our options yields a total ~0.8% increase in package size on all of our packages combined, but the decompression time for all packages saw a ~1300% speedup.

We already have more than 545 zstd-compressed packages in our repositories, and as packages get updated more will keep rolling in. We have not found any user-facing issues as of yet, so things appear to be working.

As a packager, you will automatically start building .pkg.tar.zst packages if you are using the latest version of devtools (>= 20191227).  
As an end-user no manual intervention is required, assuming that you have read and followed the news post [from late last year](https://www.archlinux.org/news/required-update-to-recent-libarchive/).

If you nevertheless haven't updated libarchive since 2018, all hope is not lost! Binary builds of pacman-static are available from Eli Schwartz' [personal repository](https://wiki.archlinux.org/index.php/Unofficial_user_repositories#eschwartz), signed with their Trusted User keys, with which you can perform the update.

  
  
from Hacker News https://ift.tt/37vksjo