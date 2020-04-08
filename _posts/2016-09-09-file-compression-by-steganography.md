---
title: 'File Compression By Steganography'
date: 2019-10-19T09:04:00+01:00
draft: false
---

In a world with finite storage and an infinite need for more storage space, data compression becomes a very necessary problem. Several algorithms for data compression may be more familiar – Huffman coding, LZW compression – and some a bit more arcane.

\[Labunsky\] decided to put to use his knowledge of steganography to [create a wholly unique form of file compression](https://medium.com/@labunskya/about-a-strange-data-compression-method-4d0d9d2e5714), perhaps one that may gain greater notoriety among other information theorists.

Steganography refers to the method of concealing messages or files within another file, coming from the Greek words _steganos_ for “covered or concealed” and _graphe_ for “writing”. The practice has been around for ages, from writing in invisible ink to storing messages in moon cakes. The methods used range from hiding messages in images to evade censorship to hiding viruses in files to cause mayhem.

![](https://hackaday.com/wp-content/uploads/2019/10/xkcd.png?w=373)

\[via xkcd\]

The developer explains that since every file is just a bit sequence, observing files leads to the realization that a majority of bits will be equal on the same places. Rather than storing all of the bits of a file, making modifications to the hard drive at certain locations can save storage space. What is important to avoid, however, is lossy file compression that can wreak havoc on quality during the compression stage.

The [compression technique](https://github.com/LabunskyA/f5ar) they ended up implementing is based on the [F5 algorithm](https://link.springer.com/chapter/10.1007%2F3-540-45496-9_21) that embeds binary data into JPEG files to reduce total space in the memory. The compression uses `libjpeg` for JPEG decoding and encoding, `pcre` for POSIX regular expressions support, and `tinydir` for platform-independent filesystem traversal. One of the major modifications was to save computation resources by disabling a password-based permutative straddling that uniformly spreads data among multiple files.

One caveat – changing even one bit of the compressed file could lead to total corruption of all of the data stored, so use with caution!

  
  
from Hackaday https://ift.tt/2MWwxFE  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)