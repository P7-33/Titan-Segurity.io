---
title: 'Apple’s Great GPL Purge (2012)'
date: 2019-11-28T01:09:00+01:00
draft: false
---

Apple’s great GPL purge
=======================

02012-02-05T00:31:59+00:00

\[Updated 2014-02-23 with figures for 10.7 and 10.8. The purge continues. Anyone still think it’s coincidence?\]

Apple obligingly allows you to [browse and download](http://opensource.apple.com/) the open source software they use in OS X. Since they have listings for each version of OS X, I decided to take a look at how much software they were using that was only available under the GNU public license. The results are illuminating:

*   10.5: 47 GPL-licensed packages.
*   10.6: 44 GPL-licensed packages.
*   10.7: 29 GPL-licensed packages.
*   10.8: 22 GPL-licensed packages.
*   10.9: 19 GPL-licensed packages.
*   10.10: 18 GPL-licensed packages.
*   10.11: 16 GPL-licensed packages.
*   10.12: 16 GPL-licensed packages.

As of 10.10 the remaining GPL-only packages seemed to be JavaScriptCore, bash, bc, emacs, efax, gnudiff, gnuserv, gnutar, groff, gpatch, keymgr, libstdcxx, man, nano, screen, texinfo, and uucp. I include this list as Apple have stopped listing the licenses on their download page, to make it harder to track their progress…

The trend supports the idea that Apple is trying to remove all GPL-licensed software from OS X. While the [removal of Samba](http://reviews.cnet.com/8301-13727_7-20046383-263.html) and GCC got some attention, the numbers show that there’s a more general purging going on. Apparently 10.10 they slacked off a bit, though.

The remaining GPL-licensed packages aren’t too healthy either. Mavericks ships with bash 3.2. That’s from 2006. The current version is 4.2.10. Why no upgrade? Because Apple’s shipping the last version of bash that was under the GPL version 2.

If anyone at Apple is reading, I’ve got some suggestions: Ship tmux with the control key rebound to ^A and probably nobody will care too much that you’ve removed screen; and there must be usable versions of `man` and `bc` in FreeBSD.

Anyway, the message is pretty obvious: Apple won’t ship anything that’s licensed under GPL v3 on OS X. Now, why is that?

There are two big changes in GPL v3. The first is that it explicitly prohibits patent lawsuits against people for actually using the GPL-licensed software you ship. The second is that it carefully prevents TiVoization, locking down hardware so that people can’t actually run the software they want.

So, which of those things are they planning for OS X, eh?

I’m also intrigued to see how far they are prepared to go with this. They already annoyed and inconvenienced a lot of people with the Samba and GCC removal. Having wooed so many developers to the Mac in the last decade, are they really prepared to throw away all that goodwill by shipping obsolete tools and making it a pain in the ass to upgrade them?

  
  
from Hacker News https://ift.tt/wRNha2