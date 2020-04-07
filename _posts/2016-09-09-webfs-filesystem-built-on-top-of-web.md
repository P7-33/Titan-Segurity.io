---
title: 'Webfs: A Filesystem Built on Top of the Web'
date: 2020-01-05T01:38:00+01:00
draft: false
---

[](https://github.com/brendoncarroll/webfs#webfs)WebFS
======================================================

WebFS is a filesystem built on top of the web.

This project started after looking for a way to use IPFS as a Dropbox replacement, and not finding any really solid solutions. I also wanted to be able to fluidly move my data between traditional storage providers like Dropbox, MEGA, or Google Drive while testing the waters of new p2p storage systems, like Swarm or Filecoin.

If you have ever thought "x can probably be used as a file system", but didn't want to actually write the file system part, WebFS might be of benefit to you. You can probably turn x into a file system with WebFS by writing a new `Store` or `Cell` implementation.

[](https://github.com/brendoncarroll/webfs#examples)Examples
------------------------------------------------------------

There are examples in the `/examples` directory. The examples assume you have the `webfs` executable on your `$PATH`.

You can also use `go run ../../cmd/webfs` instead of `webfs` if you don't want to set that up.

[](https://github.com/brendoncarroll/webfs#architecture)Architecture
--------------------------------------------------------------------

WebFS depends on two interfaces: `Stores` and `Cells`.

### [](https://github.com/brendoncarroll/webfs#stores)Stores

Stores support two operations:

```
Get(key string) (data []byte, err error) Post(prefix string, data []byte) (key string, err error) 
```

Stores must guarantee fidelity of the data. The key given by the store should be related to the data cryptographically. For example, an FTP server would make a fine store, provided the files are named with the hash of their contents. IPFS paths provide this guarentee.

Store implementations can be found in `pkg/stores`

### [](https://github.com/brendoncarroll/webfs#cells)Cells

Cells in WebFS are like cells in a spreadsheet, a holder of a data which can change over time. The compare-and-swap operation (`CAS(current, next)`) allows writes which will be synchronized with other WebFS instances writing to the same cell.

Cells provide two operations:

```
Get() (data []byte, err error) CAS(current, next []byte) (success bool, err error) 
```

Cell implementations can be found in `pkg/cells`

### [](https://github.com/brendoncarroll/webfs#data-model)Data Model

WebFS takes a typical copy-on-write merkle tree approach similar to git or IPFS. There are 3 objects that make up the data model.

*   Files. Just a btree from file offsets to data.
*   Directories. A btree from strings to other WebFS objects.
*   Volumes. An authority on part of the file system. The contents of volumes are mutable and they can contain any other WebFS object. Volumes will be invisible to a client of the file system, and can only be manipulated with the WebFS tooling. A Volume wraps a cell implementation.

All of the configuration in WebFS is modelled as objects in the file system. Everything needed to start a WebFS instance is contained a file called the "superblock". The superblock is just a `Cell` implemented as a single file on disk.

The model is analagous to a web of git repositories/submodules (similar to WebFS volumes). WebFS directories are similar to git trees. The main difference is that WebFS files and directories do not have one to one mappings with blobs. Instead, they are tree structures that span multiple blobs. This allows them to support much larger files than is practical in git.

[](https://github.com/brendoncarroll/webfs#goalsroadmap)Goals/Roadmap
---------------------------------------------------------------------

*   FUSE Adapter
*   Snapshots. Transform `Volume`s into snapshot objects recursively and output a root snapshot.
*   RAID, Reed-Solomon, Compression `Webref`s
*   Check/Scrub. To repair or move data as needed. This will enable easy migrations between storage providers. Changing store-A to 0 replicas and store-B to 1 replica and running scrub should be all that's required.
*   Sharded and Union Directories (across multiple cells)
*   Gain adoption by data-curators. Become a sound way to distribute large datasets which update over time.
*   Create a simple workflow for group archiving.
*   High quality CLI UX
*   Create a more competitive market for file storage and synchronization, by reducing the problem to implementing a `Store` or `Cell`.

Contributions are welcome

[](https://github.com/brendoncarroll/webfs#non-goals)Non-Goals
--------------------------------------------------------------

*   Create a p2p network based `Store` or `Cell`, which runs in the WebFS process. Those should run separately and expose an API which this project will be eager to integrate.

[](https://github.com/brendoncarroll/webfs#community)Community
--------------------------------------------------------------

Questions and Discussion happening on Matrix.

[![Matrix](https://camo.githubusercontent.com/276d85f5b6965b7e51f5c7717b10bec7fdf8c2f6/68747470733a2f2f696d672e736869656c64732e696f2f6d61747269782f77656266733a6d61747269782e6f72673f6c6162656c3d25323377656266732533416d61747269782e6f7267266c6f676f3d6d6174726978)](https://camo.githubusercontent.com/276d85f5b6965b7e51f5c7717b10bec7fdf8c2f6/68747470733a2f2f696d672e736869656c64732e696f2f6d61747269782f77656266733a6d61747269782e6f72673f6c6162656c3d25323377656266732533416d61747269782e6f7267266c6f676f3d6d6174726978)

  
  
from Hacker News https://ift.tt/2FisqAA