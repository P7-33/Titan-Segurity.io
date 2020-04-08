---
title: 'Install Exaile 4.0.0 Music Player on Ubuntu (18.10/18.04) & Linux Mint '
date: 2019-10-06T14:25:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-1wCyAwkCQfc/XZno9sdk0LI/AAAAAAAAMqw/73TcCQKSObo12YKFHAxd5uWd0tyWVnpYACLcBGAsYHQ/s400/ex.png)](https://1.bp.blogspot.com/-1wCyAwkCQfc/XZno9sdk0LI/AAAAAAAAMqw/73TcCQKSObo12YKFHAxd5uWd0tyWVnpYACLcBGAsYHQ/s1600/ex.png)

  
[**Exaile**](https://github.com/exaile/exaile) is a music player with a simple interface and powerful music management capabilities. Features include automatic fetching of album art, lyrics fetching, streaming internet radio, tabbed playlists, smart playlists with extensive filtering/search capabilities, and much more.  
  
Exaile is written using Python and GTK+ and is easily extensible via plugins. There are over 50 plugins distributed with Exaile that include advanced track tagging, last.fm scrobbling, support for portable media players, podcasts, internet radio such as icecast and Soma.FM, ReplayGain, output via a secondary output device (great for DJs!), and much more.  
  
  

### Exaile 4.0 [release notes](https://github.com/exaile/exaile/wiki/Exaile-4.0-release-notes)

This document details changes made to the Exaile music player between its 3.x series and the new version 4.0.0, released on 2019-06-06.  
  
The major change in Exaile 4 is that it uses GTK+ 3 and GStreamer 1. Existing users are strongly recommended to upgrade because GStreamer 0.10, used in earlier versions, is unmaintained and may contain security issues.  
  
The move to GTK+ 3 means Exaile is now able to use dark GTK+ themes and work well with HiDPI displays. There are minor UI differences between Exaile 3 and 4 to accommodate the toolkit upgrade, but the overall layout of the app is still exactly the same.  
  
**Fixes and improvements**  

*   Exaile's playback engine has been rewritten. There is only one engine now, which supports gapless, fade in/out, and crossfade features (the latter is still experimental).
*   Massive speed improvements, can handle 50000+ song library (#457, #458, #465).
*   On RTL locales, keep playback controls in LTR order (#144).
*   Disallow mouse scrolling on numeric tags in the tag editor to prevent accidental changes (#6).
*   Ogg Opus tags can now be read correctly (#150).
*   Show loading indicator when opening large playlists (#135).
*   Fixed bug on tracklist selection when a new track plays while the tracklist is being filtered (#80).
*   New tracklist columns: Year (#127), Language (#252, tagger support in #208), Website.
*   Save the Track Properties dialog location and size (#212, #236).
*   MP3 transcoding now uses the lamemp3enc GStreamer plugin instead of lame (#214).
*   Smart playlists can now be correctly exported (#216).
*   The progress bar now seeks on mouse scroll (#230).
*   Fixed Track Properties dialog not showing up when the BPM tag is non-numeric (#209, #235).
*   Unknown tags are now shown as empty instead of "Unknown", except in the title field (#250).
*   Matroska files with no TimecodeScale are now supported.
*   Fixed showing of Matroska discnumber and tracknumber tags.
*   Exaile now includes a 128x128 icon.
*   When going up the directory hierarchy in the Files panel, the previous directory is selected.
*   Searching on the collection and tracklist can be done regardless of diacritics (#176).
*   Fixed intermittent segfault when quickly browsing through menus (#97, #283).
*   Support for .aac files.
*   Fixed reading certain wav files.
*   Improved support for reading .aif/.aiff/.aifc files (#463).
*   Fixed failure on deleting tags from certain formats (#152, #286).
*   Smart playlist now supports filtering by bitrate (#274).
*   Smart playlist now supports matching by a whole word (#486).
*   Smart playlist now supports a user-specified default sort order (#469).
*   The search language now supports the "contains word" (w=) and "does not contain word" (!w=) operators. They have also been added to the smart playlist dialog.
*   A lot of dialog windows that were previously parentless are now properly attached to an Exaile window.
*   When using PulseAudio, other PA clients such as volume controls will classify Exaile's stream as music and correctly show Exaile's application name and icon (#324).
*   Exaile now comes with Bash and Fish completion scripts (#132 for Bash).
*   When Exaile fails to play a file due to missing GStreamer plugin, it tries to give the option to install the plugin using gstpbutils (#35).
*   New dialog to list available shortcuts: Help → Shortcuts.
*   A few new keyboard shortcuts have been added.
*   New menu entry: Help → Open error logs.
*   Pressing Spacebar on the tracklist now triggers the play/pause action (#441).
*   Covers are now associated with album+artist+date instead of just album; if the musicbrainz\_albumid tag is available then it is used instead (#306, #501). This may require covers to be re-fetched.
*   Playlist widget: implement sorting across multiple columns (#510).
*   Fixed track and disc number parsing on remote tracks (#520).
*   There is an option to tell GTK to use a dark theme if available.
*   New shuffle mode: random playback.
*   When editing smart playlists, entries with spin button + combo box are now loaded correctly (#582).
*   The Collection panel has new options for grouping by album artists (#576).
*   Added Album Artist tracklist column (#576).
*   Many track tags are now directly editable in the playlist view by clicking the cell twice or pressing F2 (#594, #614)

###   

### How to Install Exaile 4.0.0 Music Player on Ubuntu (18.10/18.04) & Linux Mint :

To install/update Exaile 4.0.0 Music Player on Ubuntu 18.04 Bionic Beaver, Ubuntu 18.10, Ubuntu 19.04 Disco Dingo, Cosmic Cuttlefish, Ubuntu 16.04 Xenial Xerus, Linux Mint 19.1, Elementary OS 5 'Juno', Peppermint, Deepin 15.8, Deepin 15.9, Linux Lite 4.2 and other Ubuntu derivative systems, open a new Terminal window and bash (get it?) in the following commands:

  
Before running the make and installation commands in the source folder, some packages are needed:  
```
sudo apt install python-dbus python-mutagen python-gi-cairo make 
```Download source code :  
  

[![](https://1.bp.blogspot.com/-9hjHdsCW6X4/XZno-E0zKOI/AAAAAAAAMq4/Dv3VpDXbXb485IWMxks3GMEyVSzrAZACwCLcBGAsYHQ/s400/exaile1.png)](https://1.bp.blogspot.com/-9hjHdsCW6X4/XZno-E0zKOI/AAAAAAAAMq4/Dv3VpDXbXb485IWMxks3GMEyVSzrAZACwCLcBGAsYHQ/s1600/exaile1.png)

```
wget -c https://github.com/exaile/exaile/releases/download/4.0.0/exaile-4.0.0.tar.gz
```  
Extract source file :  
```
sudo tzr xfz exaile-4.0.0.tar.gz  
cd exaile-4.0.0/
```

[![](https://1.bp.blogspot.com/-KTIYwZq7AaM/XZno99EY0GI/AAAAAAAAMq0/YGeGLLugl1Iyh3QPPwHzj8-cPtDPRNRagCLcBGAsYHQ/s400/Screenshot%2Bfrom%2B2019-10-06%2B19-55-48.png)](https://1.bp.blogspot.com/-KTIYwZq7AaM/XZno99EY0GI/AAAAAAAAMq0/YGeGLLugl1Iyh3QPPwHzj8-cPtDPRNRagCLcBGAsYHQ/s1600/Screenshot%2Bfrom%2B2019-10-06%2B19-55-48.png)

  

Make and install file source :  
```
$ make  
\# make install
```

[![](https://1.bp.blogspot.com/-kj6NXAMefg4/XZnpAgyM_6I/AAAAAAAAMrA/PRaWEwHOHSg3UCSztq_Rb8V6bPvVnYOtQCLcBGAsYHQ/s400/make.png)](https://1.bp.blogspot.com/-kj6NXAMefg4/XZnpAgyM_6I/AAAAAAAAMrA/PRaWEwHOHSg3UCSztq_Rb8V6bPvVnYOtQCLcBGAsYHQ/s1600/make.png)

  

[![](https://1.bp.blogspot.com/-1i8-2iNW_sU/XZnpA317XzI/AAAAAAAAMrE/mkmxtbQhL1YTDyMt1etPFQS8dQ3syIo8ACLcBGAsYHQ/s400/screentest.png)](https://1.bp.blogspot.com/-1i8-2iNW_sU/XZnpA317XzI/AAAAAAAAMrE/mkmxtbQhL1YTDyMt1etPFQS8dQ3syIo8ACLcBGAsYHQ/s1600/screentest.png)

  
  
After installation is completed, check on ubuntu menu dashboard