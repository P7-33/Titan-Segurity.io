---
title: 'Andriller'
date: 2020-01-31T23:40:00+01:00
draft: false
---

**Kang Asu**

[![](https://1.bp.blogspot.com/-XIZmHselelU/XhVCgmqrhaI/AAAAAAAARaI/XHLPuR0b0Ow6eVEvMKh9SZTgjMvi8Q1QQCNcBGAsYHQ/s640/andriller.png)](https://1.bp.blogspot.com/-XIZmHselelU/XhVCgmqrhaI/AAAAAAAARaI/XHLPuR0b0Ow6eVEvMKh9SZTgjMvi8Q1QQCNcBGAsYHQ/s1600/andriller.png)

**Andriller - Software Utility With A Collection Of Forensic Tools For Smartphones**

  
Andriller - is software utility with a collection of [forensic](https://www.kitploit.com/search/label/Forensic "forensic") tools for smartphones. It performs read-only, forensically sound, non-destructive acquisition from Android devices. It has features, such as powerful Lockscreen [cracking](https://www.kitploit.com/search/label/Cracking "cracking") for Pattern, PIN code, or Password; custom decoders for Apps data from Android (some Apple iOS & Windows) databases for [decoding](https://www.kitploit.com/search/label/Decoding "decoding") communications. Extraction and decoders produce reports in HTML and Excel formats.

  
**Features**

*   Automated data extraction and decoding
*   Data extraction of non-rooted without devices by Android Backup (Android versions 4.x, varied/limited support)
*   Data extraction with root permissions: root ADB daemon, CWM [recovery](https://www.kitploit.com/search/label/Recovery "recovery") mode, or SU binary (Superuser/SuperSU)
*   Data parsing and decoding for Folder structure, Tarball files (from nanddroid backups), and Android Backup (_backup.ab_ files)
*   Selection of individual database decoders for Android apps
*   Decryption of encrypted [WhatsApp](https://www.kitploit.com/search/label/WhatsApp "WhatsApp") archived databases (.crypt to .crypt12, must have the right _key_ file)
*   Lockscreen cracking for Pattern, PIN, Password (not gatekeeper)
*   Unpacking the Android backup files
*   Screen capture of a device's display screen

  
**Python Requirements**

*   3.6+ (64-bit version recommended)

>  It is highly advised to setup a virtual environment to install Andriller and its dependencies in it. However, it is not essential, and the global environment can also be used. Depending on how Python was setup, it may be needed to substitute `python` and `pip` to `python3` and `pip3` retrospectively for the instructions below.

>  Windows only: when installing Python from [https://www.python.org](https://www.python.org/ "https://www.python.org"), make sure **Add Python to PATH** is ticked.

  
**System Dependencies**

*   `adb`
*   `python3-tk`

\[Ubuntu/Debian\] Install from Terminal:

```
$ sudo apt-get install android-tools-adb python3-tk
```

\[Mac\] Install from brew cask:

```
$ brew cask install android-platform-tools
```

\[Windows\] : _Included._  
  
**Installation (from PYPI, recommended)**

```
$ pip install andriller -U
```

  
**Installation (from source, editable)**

```
$ pip install -e .
```

  
**Quick Start (run GUI)**

```
$ python -m andriller
```

  

**[Download Andriller](http://ellevolaw.com/3smv "Download Andriller")**

**Regards**

**Kang Asu**