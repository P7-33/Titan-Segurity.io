---
title: 'A detailed look at Ubuntu’s new experimental ZFS installer'
date: 2019-10-15T10:19:00+01:00
draft: false
---

![](https://cdn.arstechnica.net/wp-content/uploads/2019/10/eoan-install-4-760x380.png "A detailed look at Ubuntu’s new experimental ZFS installer | Ars Technica")  

[119 with 50 posters participating, including story author](https://arstechnica.com/information-technology/2019/10/a-detailed-look-at-ubuntus-new-experimental-zfs-installer/?comments=1 "50 posters participating, including story author")

Yesterday brought exciting news on the ZFS and Ubuntu fronts—experimental ZFS root support in the installer for Ubuntu's upcoming interim release, Eoan Ermine. The feature [appeared](https://twitter.com/popey/status/1181547646378500096) in the 2019-10-09 daily build of Eoan—it's not in the regular beta release and, in fact, wasn't even in the "current daily" when we first went to download it. It's that new! (Readers wanting to play with the new functionality can find it in _today's_ daily build, available [here](http://cdimage.ubuntu.com/daily-live/current/).)

*   Time to install the 2019-10-09 daily build of Eoan Ermine on a fresh new VM!
    
    Jim Salter
    
*   Our first choice during the Eoan install is a basic one. Yeah yeah yeah, let's get to the ZFS please...
    
    Jim Salter
    
*   WHEEEE! Now that we've got the correct daily build .iso, we have the experimental ZFS install option available.
    
    Jim Salter
    
*   Minor bug: even though we chose a ZFS root, Eoan's installer is still telling us it will use ext4. Welcome to alpha software!
    
    Jim Salter
    
*   Now that we've selected our ZFS root, Eoan Ermine is on its merry way to installation.
    
    Jim Salter
    

For the ZFS newbies
-------------------

If you're new to the [ZFS](https://arstechnica.com/information-technology/2014/02/ars-walkthrough-using-the-zfs-next-gen-filesystem-on-linux/) hype train, you might wonder why a new filesystem option in an OS installer is a big deal. So here's a quick explanation: ZFS is a copy-on-write filesystem, which can take [atomic snapshots](https://arstechnica.com/information-technology/2014/01/bitrot-and-atomic-cows-inside-next-gen-filesystems/) of entire filesystems. This looks like sheer magic if you're not used to it—a snapshot of a 10TB filesystem can be taken instantly without interrupting any system process in the slightest. Once the snapshot is taken, it's an immutable record of the exact, block-for-block condition of the filesystem at the moment in time the snapshot was taken.

When a snapshot is first taken, it consumes no additional disk space. As time goes by and changes are made to the filesystem, the space required to keep the snapshot grows by the amount of data that has been deleted or altered. So let's say you snapshot a 10TB filesystem: the snapshot completes instantly, requiring no additional room. Then you delete a 5MB JPEG file—now the snapshot consumes 5MB of disk space, because it still has the JPEG you deleted. Then you change 5MB of data in a database, and the snapshot takes 10MB—5MB for the JPEG you deleted and another 5MB for the data that you altered in the database.

That's just one awesome ZFS feature. There's also the ability to manage multiple disks in a native RAID-like system, inline compression with selectable algorithms, rapid asynchronous incremental [replication](https://arstechnica.com/information-technology/2015/12/rsync-net-zfs-replication-to-the-cloud-is-finally-here-and-its-fast/), and more. But we're going to focus mostly on the snapshots here, because one _other_ thing you can do with a snapshot is roll it back.

*   A simple test of undoing an operation: first, take a snapshot. Then, do something you regret (in this case, uninstalling Firefox).
    
    Jim Salter
    
*   The rollback is instantaneous, and Firefox is back—but things still look a little wonky due to orphaned filehandles. We need to reboot now.
    
    Jim Salter
    
*   We rolled back, we rebooted, and everything's golden. Hello again, Firefox old friend!
    
    Jim Salter
    

Although there isn't any support built into Eoan's apt package manager for automatically taking snapshots yet, we can demonstrate a snapshot—oops—rollback moment manually. In the above gallery, first we take a ZFS snapshot. Eoan has split our root filesystem into tons of little datasets (more on that later), so we use the `-r` option for `zfs snapshot` to recursively take snapshots throughout the entire tree.

Now that we've insured ourselves against mistakes, we do something we're going to regret. For the purposes of this demo, we're just removing Firefox—but we could really recover from anything up to and including an `rm -rf --no-preserve-root /` this way with a little extra legwork. After removing Firefox, we need to roll back our snapshots to restore the system to its original condition.

Since the root filesystem is scattered through a _bunch_ of individual datasets, we need to roll them all back individually. Although this is a pain for the casual user without additional tooling, it does make it possible to do more granular restore operations if we're feeling picky—like rolling back the root filesystem without rolling back `/home`. Ubuntu will undoubtedly eventually have tooling to make this easier, but for the moment, we do a bit of sysadmin-fu and pipe `zfs list` to `grep` to `awk` to `xargs`, oh my.

The command line acrobatics might have been obnoxious, but the rollback itself was instantaneous, and Firefox has returned. It still doesn't work quite right, though, due to [orphaned filehandles](https://unix.stackexchange.com/questions/290116/what-is-an-orphaned-inode/290119#290119)—we rolled back a live mounted root filesystem, which is kind of a cowboy thing to do. To make things entirely right, a reboot is necessary—but after the reboot, everything's the way it once was, and without the need to wait through any lengthy Windows Restore Point-style [groveling](http://catb.org/jargon/html/G/grovel.html) over the filesystem.

For the ZFS enthusiasts
-----------------------

In this section, we're going to take a detailed look at just how Ubuntu is carving up the filesystems in Eoan's experimental installer. The version in our daily build is 0.8.1, so this is great news for the ZFS fans among us, even without the experimental root installer—assuming the final version of Eoan follows this one, we'll get native encryption, TRIM, device removal, and zpool checkpoints. These [features](https://arstechnica.com/gadgets/2019/06/zfs-features-bugfixes-0-8-1/) have been in the ZFS on Linux [master](https://github.com/zfsonlinux/zfs) since 0.8, but this is the first time they've shown up in Ubuntu's native ZFS.

*   A peek at /dev/vda's partition table shows us a small UEFI boot partition, a 2G partition for bpool, and the remainder of the disk as rpool.
    
    Jim Salter
    
*   Eoan's experimental ZFS installer creates two zpools, rpool and bpool. Bpool contains boot files only; all the interesting stuff is in rpool, shown here.
    
    Jim Salter
    
*   Taking a look at the ZFS dataset properties of my home directory, as set by the installer.
    
    Jim Salter
    

So far—remember, this is alpha software in a daily build—the installer doesn't give you any control over how it carves up the disk when you select a ZFS install; it just does what it wants to do. The Eoan VM I created has a single 20GB virtual disk. Eoan's installer carved this into one primary partition and two logical—a small UEFI boot partition and partitions for two separate ZFS storage pools, named `bpool` and `rpool`.

Bpool is pretty boring; it's just where the system's /boot directory gets mounted. Eoan made this pool 2GB, which is twice what a conservative `/boot` is normally provisioned to; this is probably to allow headroom to maintain a fairly deep archive of snapshots in the future. `rpool` gets all the remaining disk space after the UEFI and `bpool` partitions are created; it's where all the fun stuff goes, including your root filesystem, home directory, and so forth.

Beneath `rpool`, you'll find a pretty bewildering array of small datasets, all of which correspond to particular vital areas in what would normally be a single root filesystem. This appears to us to be an inherited BSD-ism—most Linux distributions left the concept of heavily partitioned disks with multiple filesystems behind twenty years ago, but FreeBSD—which has had root ZFS options in its installer for many years now—was a lot more stubborn about it.

The good thing about carving up the root filesystem into so many separate datasets is that you can snapshot and roll them back individually. In some cases, this is great—there's an obvious, clear, and useful distinction between rolling back the root filesystem as a whole and rolling back your own home directory, for example. Most users—even pretty competent sysadmin types—will be a lot more confused about how and why you might want to roll back `/usr` without rolling back, say, `/var/lib/AccountServices`, though. It's nice that you _can_ if you really want to, but we're not so sure the capability outweighs the utility of a simpler approach.

*   Have I mentioned that this is a daily build, and therefore alpha software? It's a daily build, and therefore alpha software. Both bpool itself and the boot dataset beneath it have /boot as a mountpoint. Oops. =)
    
    Jim Salter
    
*   Taking a look at the ZFS dataset properties of my home directory, as set by the installer.
    
    Jim Salter
    
*   Eoan's ZFS support doesn't yet include automatically creating new ZFS datasets for new user accounts' homedirs.
    
    Jim Salter
    
*   A peek into root's crontab and the jobs in /etc/cron.\* show that no automatic snapshot creation is present in Eoan's ZFS support yet; only an automatic scrub once monthly.
    
    Jim Salter
    

Peeking a little deeper, we can see that Eoan isn't setting any significant per-dataset properties on all these separate datasets. It is setting compression=lz4 on across the entire pool, though. This is a good thing—many people worry that compressed filesystems are slow filesystems, but LZ4 stream compression is so lightweight that it's effectively "free." We've done extensive testing across years of ZFS experience and have never seen a situation where LZ4 wasn't a good idea. Even a $50 tinkertoy APU from several years ago can compress and decompress LZ4 faster than a pair of fast SSDs can keep up, with no significant CPU utilization.

We did spot a bug pretty quickly while looking over the pools and datasets. Both `bpool` itself and `bpool/BOOT/ubuntu_oalrlu` (we think the string of random-seeming characters is intended to be a unique system identifier) have `/boot` set as their mountpoint. This clearly isn't causing any significant problems right now, and we're sure it will get ironed out well before Eoan goes live. (**Edit:** a Canonical core admin [clarified](https://twitter.com/didrocks/status/1182329263913082880) that this is not a bug; `bpool` is set `canmount=no`. The reason for `bpool`'s unmountable mountpoint is so that any new datasets created under `bpool` will automatically mount at `/boot/newdataset`, not at `/bpool/newdataset.)`

Although Eoan created datasets automatically for both my real user account homedir and root's, the `adduser` command didn't create one for a new test user. This is something we also expect to get ironed out reasonably quickly—even if `adduser` itself never takes those steps, the GUI for adding new users likely will, if it doesn't already. This is also pretty simple to do manually; in the above example, where new user test is _not_ logged in, we could upgrade test to a zfs dataset homedir like this:

```
root@eoan:~$ zfs create rpool/ROOT/ubuntu\_oal4lu/test\_twm547  
 root@eoan:~$ rsync -ha /home/test/ /rpool/ROOT/ubuntu\_oal4lu/test\_twm547/  
 root@eoan:~$ rm -r /home/test  
 root@eoan:~$ chown test.test /rpool/ROOT/ubuntu\_oal4lu/test\_twm547  
 root@eoan:~$ zfs set mountpoint=/home/test rpool/ROOT/ubuntu\_oal4lu/test\_twm547  
 root@eoan:~$ zfs mount rpool/ROOT/ubuntu\_oal4lu/test\_twm547
```

... and that would be that.

The next big thing we looked for was a mechanism for automatically taking snapshots. You can't roll back to a snapshot you never took, so a safe ZFS system should automatically take snapshots pretty regularly. There's nothing in Eoan to take snapshots for you yet—the only cron job is the standard one that scrubs the pool once per month—but there are a few general purpose ZFS snapshot orchestration tools readily available; these include [zfs-auto-snapshot](https://manpages.ubuntu.com/manpages/bionic/man8/zfs-auto-snapshot.8.html) and my own [sanoid](https://github.com/jimsalterjrs/sanoid).

Alpha software is alpha!
------------------------

In conclusion, we want to remind readers that while ZFS itself is very stable, Ubuntu's ZFS-enabled installer and use of it as a root filesystem are still _alpha_ quality. We do not recommend that you attempt to use the new ZFS installer on systems you care deeply about until the installer makes it past alpha, past beta, and all the way to full release quality. This also means you should be kind about any bugs you find playing with it in the meantime—again, this is _alpha_ software and bugs are not only possible, they're to be expected.

With all that said, we're extremely excited about ZFS on root making visible progress in Ubuntu—and we hope these features and more will make it into Eoan Ermine's expected end-of-the-month release.

_Listing image by Jim Salter_

  
  
from Hacker News https://ift.tt/35hHV7z