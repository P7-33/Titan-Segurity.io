---
title: 'How Kali deals with the upcoming Python 2 End-of-Life'
date: 2019-12-16T16:28:00+01:00
draft: false
---

Five years ago, the Python developers announced that they will [stop supporting Python 2 in 2020](https://pythonclock.org/). For a long time, nobody cared and Python 3 adoption was slow. But things have changed a lot lately as the deadline is right around the corner (1st January).

Debian is removing Python 2 support
-----------------------------------

Debian is planning to get rid of [Python 2 entirely for their next stable release](https://wiki.debian.org/Python/2Removal) so they are progressively getting rid of Python 2 code. They filed release critical bugs on leaf packages (i.e. packages without reverse dependencies) asking them to be ported to Python 3. If the Python 3 port is not happening soon enough, these packages will be removed from [Debian Testing](https://wiki.debian.org/DebianTesting) _(which is what Kali is based on)_.

Consequences for Kali
---------------------

### Applications disappearing

As Kali is a rolling distribution, it continuously receives updates from Debian Testing. This includes when packages “go away” because they have been dropped from Debian. However, they can always come back later, provided that someone ports them to Python 3.

We have already experienced this in the case of `zenmap` which is no longer maintained by the [nmap developers](https://nmap.org/zenmap/). Thus, it’s no longer built by [Debian’s nmap source](https://packages.debian.org/search?keywords=zenmap) package, and as a result no longer appears in Kali.

### Broken applications

We have many Python 2 applications in Kali that use modules which are packaged in Debian. When Debian drops the Python 2 version of such a module, the application is broken in [kali-dev](https://www.kali.org/docs/general-use/kali-linux-sources-list-repositories/). kali-rolling is not affected due to the way it’s managed but the growing divergence between kali-dev and kali-rolling is making our job more difficult: we don’t get updates for such packages and there are other (recent) applications that will likely require new versions of those packages!

Kali must remove Python 2 code too
----------------------------------

Due to this change in the ecosystem, Kali has no other choice than to follow Debian’s lead and remove Python 2 code as well. This giant effort is tracked with [many GitLab issues](https://gitlab.com/groups/kalilinux/-/issues?label_name%5B%5D=Project%3A%3APy2Removal) against all packages depending on Python 2 in some way. We have already filed upstream bug reports for all the packages where there’s no Python 3 support yet.

How we handle each case depends on many factors:

*   If upstream is working on Python 3 support, then we just wait until it’s ready.
*   If upstream is inactive or is not interested into porting its code to Python 3, then we have few choices:
    *   either we remove the package;
    *   or we find some fork/patch that adds Python 3 support;
    *   or we do the porting work ourselves (rather unlikely except for trivial scripts).

It also depends on the kind of packages:

*   For a Python library, it’s a two step process: first we add Python 3 support; Python 2 support is removed later, once all reverse dependencies have been updated to use Python 3.
*   For a Python application, a single update might be enough but that update might depend on having dependencies be ported to Python 3 first.

We don’t like to remove software, but sometimes when they are no longer maintained, we have no other choices. For important packages, we are waiting longer thus letting more time for the community to add the required Python 3 support. We might even patch them so that they display a warning inviting users to contribute, or at least understand the application may be removed in the near future.

For packages that no longer add much value, or that have viable alternatives in Kali, we might remove them at any point in time.

How you can contribute
----------------------

If one of your favorite applications appears among the [affected Kali packages](https://gitlab.com/groups/kalilinux/-/issues?label_name%5B%5D=Project%3A%3APy2Removal) or among the [affected packages from Debian’s pkg-security team](https://bugs.debian.org/cgi-bin/pkgreport.cgi?tag=py2removal;users=debian-python@lists.debian.org;maint=team%2Bpkg-security@tracker.debian.org), then you should review its situation and possibly help the upstream developer(s) by submitting a pull request adding Python 3 support. Even if upstream is not very active, we will be able to merge your changes in Kali and keep the package for longer until upstream becomes active again.

If you don’t have the coding skills required for this, you can still try to find a Python 3 fork/patch written by someone else and point it out to us in the corresponding GitLab issue or Debian bug report. Or, tell the developers how much you like their application and that you would like to continue to make use of it, so they should port over to Python 3.

  
  
from Kali Linux https://ift.tt/2PPxGjJ