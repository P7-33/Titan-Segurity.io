---
title: 'Rethinkdb 2.4.0 – “Night of the Living Dead” Released'
date: 2020-01-04T05:06:00+01:00
draft: false
---

![](https://avatars1.githubusercontent.com/u/1229647?s=400&v=4 "Releases · rethinkdb/rethinkdb · GitHub")  

RethinkDB 2.4 introduces write hooks and bitwise operations besides bug fixes.

Read the [blog post](https://rethinkdb.com/blog/2.4.0-release) for more details.

### Compatibility

Data files from RethinkDB version 1.16 onward will be automatically  
migrated. As with any major release, back up your data files before  
performing the upgrade. Please read the [RethinkDB 2.4.0 release  
notes](https://github.com/rethinkdb/rethinkdb/releases/tag/v2.4.0) if you're upgrading from version 2.3.x or  
earlier.

RethinkDB 2.4.0 servers cannot be mixed with servers running RethinkDB  
2.3.x or earlier in the same cluster.

### Official Drivers

Except for JavaScript, the official drivers are now generally  
maintained as separate projects. But note that there is some coupling  
of RethinkDB console commands, like `rethinkdb dump`, with the Python  
driver. RethinkDB 2.4 contains some old copies of the drivers to keep  
`./test/run` working with minimal effort. The JavaScript driver is  
still used in the Web UI. However, the web assets are now  
pre-generated, at src/gen/web\_assets.cc, making the presence of the  
driver in the repository not strictly necessary.

Here are links to the official drivers:

### API-breaking changes

*   Write hooks add a new field to the table configuration.
*   A bugfix changes the `match` command's behavior on empty regexes.  
    It had previously been behaving incorrectly.

### Substantive Changes

(Issue numbers point into the [https://github.com/rethinkdb/rethinkdb](https://github.com/rethinkdb/rethinkdb)  
bugtracker.)

*   ReQL
    *   Added the `set_write_hook` and `get_write_hook` commands, which attach to  
        tables a function that can modify the behavior of any write. ([#5813](https://github.com/rethinkdb/rethinkdb/issues/5813))
    *   Added bitwise operators for number types: `bit_and`, `bit_not`, `bit_or`,  
        `bit_sal`, `bit_sar` and `bit_xor`. ([#6534](https://github.com/rethinkdb/rethinkdb/pull/6534))
    *   Permitted the hyphen character (`-`) to be used in table names. ([#5537](https://github.com/rethinkdb/rethinkdb/issues/5537))
    *   Users may be granted permissions on system tables. ([#5692](https://github.com/rethinkdb/rethinkdb/issues/5692))
    *   Make `iso8601` command round, not truncate. (#6909)
    *   Fix timestamp millisecond down-truncation bug. ([#6272](https://github.com/rethinkdb/rethinkdb/issues/6272))
*   Server
    *   Fixed crash with limit change feed `inserted` guarantee failure. ([#6710](https://github.com/rethinkdb/rethinkdb/pull/6710))
    *   Avoid using DNS resolution when finding network interface addresses. ([#6588](https://github.com/rethinkdb/rethinkdb/pull/6588))
    *   Removed update checker. ([#6791](https://github.com/rethinkdb/rethinkdb/issues/6791))
    *   Added experimental support for arm64/aarch64. ([#6438](https://github.com/rethinkdb/rethinkdb/pull/6438))
    *   Added experimental support for Power8/LE platform. ([#6317](https://github.com/rethinkdb/rethinkdb/pull/6317))
    *   Fixed race condition in the query cache. ([#6564](https://github.com/rethinkdb/rethinkdb/pull/6564))
    *   Avoid quadratic growth in segmented vector. ([#6385](https://github.com/rethinkdb/rethinkdb/pull/6385))
    *   Big-Endian fixes and s390x support. ([#6242](https://github.com/rethinkdb/rethinkdb/issues/6242))
*   Web UI
    *   Implemented a new table viewer widget for browsing the contents of tables. ([#6767](https://github.com/rethinkdb/rethinkdb/pull/6767))
    *   Improved table page performance in case with many databases. ([#6790](https://github.com/rethinkdb/rethinkdb/pull/6790))
*   Compilation
    *   The web assets are now pre-generated, so that macOS users can build them. ([#6770](https://github.com/rethinkdb/rethinkdb/pull/6770))
    *   Debian package building is now parallelized. ([#6780](https://github.com/rethinkdb/rethinkdb/pull/6780))
    *   Fixed extproc spawner bug. ([#5572](https://github.com/rethinkdb/rethinkdb/issues/5572))
    *   Allowed building against libressl. ([#6671](https://github.com/rethinkdb/rethinkdb/pull/6671))
*   JavaScript Driver
    *   Avoided mutating object passed to `r.connect`. ([#6575](https://github.com/rethinkdb/rethinkdb/pull/6575))
*   Python Driver
*   Other Drivers
    *   Changes omitted, as they're in separate repositories.

  
  
from Hacker News https://ift.tt/1bLBrsO