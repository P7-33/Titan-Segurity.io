---
title: 'Parallel Programming: December 2019 Update'
date: 2020-01-13T02:47:00+01:00
draft: false
---

![](https://l-files.livejournal.net/og_image/18342169/220?v=1578790294 "Parallel Programming: December 2019 Update - Paul E. McKenney's Journal — LiveJournal")  

There is a new release of

[Is Parallel Programming Hard, And, If So, What Can You Do About It?](https://www.kernel.org/pub/linux/kernel/people/paulmck/perfbook/perfbook.html)

.

This release features a number of formatting and build-system improvements by the indefatigible Akira Yokosawa. On the formatting side, we have listings automatically generated from source code, clever references, selective PDF hyperlink highlighting, and finally settling the old after-period one-space/two-space debate by mandating newline instead. On the build side, we improved checks for incompatible packages, SyncTeX database file generation (instigated by Balbir Singh), better identification of PDFs, build notes for recent Fedora releases, fixes for some multiple-figure page issues, and improved font handling, and a2ping workarounds for ever-troublesome Ghostscript. In addition, the .bib file format was dragged kicking and screaming out of the 1980s, prompted by Stamatis Karnouskos. The new format is said to be more compatible with modern .bib-file tooling.

On the content side, the “Hardware and its Habits”, “Tools of the Trade”, “Locking”, “Deferred Processing”, “Data Structures”, and “Formal Verification” chapters received some much needed attention, the latter by Akira, who also updated the “Shared-Variable Shenanigans” section based on a recent

[LWN](http://lwn.net)

article. SeongJae Park, Stamatis, and Zhang Kai fixed a large quantity of typos and addressed numerous other issues. There is now a full complement of top-level section epigraphs, and there are a few scalability results up to 420 CPUs, courtesy of a system provided by my new employer.

On the code side, there have been a number of bug fixes and updates from

ACCESS\_ONCE()

to

READ\_ONCE()

or

WRITE\_ONCE()

, with significant contributions from Akira, Junchang Wang, and Slavomir Kaslev.

A full list of the changes since the

[previous release](https://paulmck.livejournal.com/52308.html)

may be found

[here](http://kernel.org/pub/linux/kernel/people/paulmck/perfbook/Changes.2019.12.22a.txt)

, and as always, git://git.kernel.org/pub/scm/linux/kerne

l/git/paulmck/perfbook.git will be updated in real time.

  
  
from Hacker News https://ift.tt/2ZYqcQ6