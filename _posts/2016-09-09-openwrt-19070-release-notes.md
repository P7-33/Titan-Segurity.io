---
title: 'OpenWrt 19.07.0 Release Notes'
date: 2020-01-11T08:47:00+01:00
draft: false
---

OpenWrt 19.07.0 - First Stable Release - 6 January 2020
=======================================================

```
 \_\_\_\_\_\_\_ \_\_\_\_\_\_\_\_ \_\_ | |.-----.-----.-----.| | | |.----.| |\_ | - || \_ | -\_\_| || | | || \_|| \_| |\_\_\_\_\_\_\_|| \_\_|\_\_\_\_\_|\_\_|\_\_||\_\_\_\_\_\_\_\_||\_\_| |\_\_\_\_| |\_\_| W I R E L E S S F R E E D O M ----------------------------------------------------- OpenWrt 19.07.0, r10860-a3ffeb413b -----------------------------------------------------
```

The OpenWrt Project is a Linux operating system targeting embedded devices. It is a complete replacement for the vendor-supplied firmware of a wide range of wireless routers and non-network devices. See the [Table of Hardware](https://openwrt.org/toh/start "https://openwrt.org/toh/start") for supported devices. For more information about OpenWrt project organization, see the [About OpenWrt pages](https://openwrt.org/about "https://openwrt.org/about").

An upgrade from OpenWrt 18.06 to OpenWrt 19.07 is supported in many cases with the help of the sysupgrade utility which will also attempt to preserve the configuration. A configuration backup is advised nonetheless when upgrading to OpenWrt 19.07.

Get OpenWrt Firmware at: [https://downloads.openwrt.org/releases/](https://downloads.openwrt.org/releases/ "https://downloads.openwrt.org/releases/")

Highlights in OpenWrt 19.07
---------------------------

The OpenWrt community is proud to announce the first stable release of the OpenWrt 19.07 stable version series. It incorporates [3954 commits](https://openwrt.org/releases/19.07/changelog-19.07.0 "releases:19.07:changelog-19.07.0") since the [previous release 18.06.0](https://openwrt.org/releases/18.06/notes-18.06.0 "releases:18.06:notes-18.06.0") and [85 commits](https://openwrt.org/releases/19.07/changelog-19.07.0-final "releases:19.07:changelog-19.07.0-final") since the [previous release candidate 19.07.0-rc2](https://openwrt.org/releases/19.07/notes-19.07.0-rc2 "releases:19.07:notes-19.07.0-rc2").

With this release, the OpenWrt project brings all supported targets back to a single common kernel version and further refines and broadens existing device support. It also introduces a new `ath79` target and brings support for WPA3.

### Target transition from ar71xx to ath79

This release provides initial support for the new `ath79` target, the future device tree based successor of the popular `ar71xx` target. For 19.07, both targets are still built, but it is recommended to switch to the `ath79` target whenever possible: future releases of OpenWrt will drop support for the `ar71xx` target.

Please read the known issues below before upgrading.

### WPA3 support

The 19.07 release brings initial support for WPA3. However, WPA3 is not enabled by default and **requires** installing specific packages: to run WPA3 as an access point, `hostapd-openssl` is needed. For use as a Wi-Fi station, you need either `wpa-supplicant-openssl` (station support only) or `wpad-openssl` (AP + station). Due to their large size, these packages are not installed by default, and it is impossible to install them on devices with less than 8MB flash.

It should also be noted that many existing client devices will never support WPA3, and that there are client devices that support WPA2 but cannot connect to an AP configured with WPA2+WPA3 mixed mode. Please only file bugs if you are sure the problem is not client related.

To configure your device as a WPA3 access point, see [wpa\_modes](https://openwrt.org/docs/guide-user/network/wifi/basic#wpa_modes "docs:guide-user:network:wifi:basic")

### Client-side rendering of the LuCI web interface

The new version of LuCI, the integrated web interface for OpenWrt, implements client-side rendering of views. This improves performance by offloading some work that was done on the device (Lua code) to the client browser (Javascript code)

The LuCI ecosystem is large, and not all LuCI apps have been adapted to this change, which may result in crashes involving `cbi.lua`. In that case, install the `luci-compat` package.

With this step, Lua usage in LuCI is reduced and LuCI effectively comes closer to the goals of the experimental [LuCI2](https://openwrt.org/docs/techref/luci2 "docs:techref:luci2") without having to rewrite everything from scratch.

### Known issues

Main changes in OpenWrt 19.07.0
-------------------------------

The main changes in this release since the previous OpenWrt 18.06 version are:

A full list of all changes and security fixes is available in the [detailed changelog](https://openwrt.org/releases/19.07/changelog-19.07.0 "releases:19.07:changelog-19.07.0").

As always, a big thank you goes to all our active package maintainers, testers, documenters, and supporters.

Have fun!

The OpenWrt Community

This website uses cookies. By using the website, you agree with storing cookies on your computer. Also you acknowledge that you have read and understand our Privacy Policy. If you do not agree leave the website.

[More information about cookies](https://en.wikipedia.org/wiki/HTTP_cookie)

  
  
from Hacker News https://ift.tt/35CwjuN