---
title: 'CircuitPython 5.0.0 Alpha 5 released! @adafruit @circuitpython'
date: 2019-11-04T05:11:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/08/circuitpython_5_poster-360x480.jpg)

This is an Alpha Release
------------------------

This is the fifth alpha release of CircuitPython 5.0.0. Alpha releases are meant for testing. Use the [latest stable 4.x release](https://circuitpython.org/downloads) when first starting with CircuitPython.

When you find a bug please [check the current known issues](https://github.com/adafruit/circuitpython/issues) and [file an issue](https://github.com/adafruit/circuitpython/issues/new) if something isn’t already known.

5.0.0
-----

5.0.0 is the latest major revision of CircuitPython. It features many improvements and enhancements to `displayio`, including grayscale OLED and e-paper displays, extensive additions and changes to BLE support, support for the STM32F4 and Sony Spresense microcontrollers, and PWM audio support.

Download from circuitpython.org
-------------------------------

Downloads are available from [circuitpython.org](https://circuitpython.org)! The site makes it easy to select the correct file and language for your board. The downloads page is [here](https://circuitpython.org/downloads).

Installation
------------

To install follow the instructions in our new [Welcome to CircuitPython!](https://learn.adafruit.com/welcome-to-circuitpython/installing-circuitpython) guide. To install the latest libraries, see [this page](https://learn.adafruit.com/welcome-to-circuitpython/circuitpython-libraries) in that guide.

Try [the latest version of the Mu editor](https://learn.adafruit.com/welcome-to-circuitpython/installing-mu-editor) for creating and editing your CircuitPython programs and for easy access to the CircuitPython serial connection (the REPL).

New Features, Updates, and Fixes since 5.0.0 Alpha 4
----------------------------------------------------

*   Circuit Playground Bluefruit: disable onboard speaker by default. Thanks @jepler.
*   Adjust on-board DotStar brightness to accommodate different inherent brightnesses for different versions of DotStars. Thanks @dhalbert.
*   Add `microprocessor.cpu.voltage` to measure voltage supplied to chip. Thanks @dhalbert.
*   Better PyPortal Titano display support. Thanks @brentru and @ladyada.
*   Allocate two available I2C objects on Circuit Playground Bluefruit and Arduino Nano 33 BLE to accommodate on-board I2C sensors. This is at the expense of dropping down to a single SPI peripheral.
*   Remember original specified PWMOut duty cycle and use when recalculating to avoid accumulating errors. Thanks @theacodes.
*   Allow setting max USB packet size for MSC. Thanks @kamtom480.
*   Parameterize stack location and limits. Thanks @kamtom480.
*   Support `__bytes__()` builtin. Thanks @tannewt.
*   Improve `unix` build support for undefined architectures. Thanks @jerryneedell.
*   Fix various minor code problems found by automated code-scanning tool. Thanks @jepler.
*   Update `lib/tinyusb` to fix HID issues. Thanks @dhalbert and @hathach.
*   Update frozen modules. Thanks @tannewt.
*   On nrf, deactivate PWM on `PWMOUT.deinit()`. Thanks @jepler.
*   nrf: use analog reference voltage that matches other ports. Thanks @jepler.
*   Additional German translations. Thanks @Retoc, @Senuros, and @kickbutts.
*   Addition Pinyin translations. Thanks @hexthat.
*   Improve `rtc` documentation. Thanks @theacodes.
*   Improve automation of module support matrix in documentation. Thanks @sommersoft.
*   Improve `README.rst`. Thanks @darkmusic.
*   atmel-samd: Fixes for `AnalogOut` and `AudioOut`. Thanks @jepler.
*   Remove unsupported ports from `ports` source tree. Thanks @dhalbert.
*   Stop running unneeded thread tests, which sometimes break the builds. Thanks @jepler.
*   Always build certain modules needed by all ports. Thanks @hierophect.
*   Improve release build handling. Thanks @tannewt.
*   Make build fail when boards are missing. Thanks @tannewt.
*   Do not re-upload release assets already uploaded. Thanks @tannewt.

New and Improved Boards
-----------------------

Find all boards at [https://circuitpython.org/downloads](https://circuitpython.org/downloads).

*   **itsybitsy\_nrf52840\_express**. Thanks @dhalbert and @ladyada.
*   **arduino\_nano\_33\_ble**. Thanks @dhalbert and @ladyada.
*   **serpente**. Thanks @arturo182.
*   **stringcar\_m0\_express**. Thanks @CGrover.
*   **sparkfun\_qwiic\_micro\_no\_flash** and **sparkfun\_qwiic\_micro\_with\_flash**. Thanks @edspark.
*   **circuitplayground\_express\_displayio**: `displayio` turned on for CPX. Thanks @tannewt.
*   **pyboard\_v11**. Thanks @hierophect.
*   **feather\_stm32f405\_express**. Thanks @hierophect.
*   **spresense**. Thanks Sony @kamtom480.
*   **robohat\_mm1\_m4**. Thanks @wallarug.
*   **hallowing\_m4**. Pin additions. Thanks @makermelissa.
*   **monster\_m4sk**. Fix pin errors. Thanks @kattni.

Upcoming BLE Changes
--------------------

This release does not include a substantial and breaking revamp of the APIs presented by `_bleio` native module and `adafruit_ble` library. These BLE changes will be merged into `master` soon after this 5.0.0-alpha.5 release. We expect the next alpha or first beta release to include these breaking changes.

Breaking Changes and Deprecations from 4.x!
-------------------------------------------

*   The `displayio` refresh API has been revamped to be simpler. `wait_for_frame` and `refresh_soon` have been removed. In both 4.x and 5.x, auto refresh will automatically refresh the display so they can be removed. The new `auto_refresh` property and `refresh()` function can be used to control when the screen refreshes and at a specific rate.
*   The `bleio` module has been renamed to `_bleio` to indicate that it is meant to be used only for writing BLE libraries, and that its API may change between CircuitPython minor versions. There are many incompatible changes since 4.0.0. The `_bleio` API is a work in progress and will change as 5.0.0 progresses. Please use the latest [pre-release `adafruit_ble` library](https://github.com/adafruit/Adafruit_CircuitPython_BLE/releases) for end-user BLE programming. The `adafruit_ble` library is evolving too but will hide underlying changes in `_bleio`.
*   Move `audioio.Mixer` to `audiomixer.Mixer` and is only available on M4s. Move `audioio.RawSample`, and `audioio.WaveFile` to the new module `audiocore`. However, for backwards compatibility, they are still available in `audioio`. They will be removed from `audioio` in 6.0.0. Thanks @jepler.
*   Add `I2C.writeto_then_readfrom()`. Deprecate `stop=` arg which will be removed in 6.x. Use `I2C.writeto_then_readfrom()` instead.

Known Issues
============

*   See [https://github.com/adafruit/circuitpython/issues](https://github.com/adafruit/circuitpython/issues).

Thanks
------

Thank you to all who used, tested, [contributed](https://github.com/adafruit/circuitpython/graphs/contributors?from=2019-09-16&to=2019-11-03&type=c), helped out, and participated on GitHub and/or Discord,including @3ach, @ATMakersBill, @AdinAck, @Anton-2, @CedarGroveStudios, @CollinCunningham, @DavePutz, @Mr-Coxall, @Retoc, @Senuros, @TG-Techie, @ThomasAtBBTF, @alexwhittemore, @anecdata, @arturo182, @brentru, @darkmusic, @ddiminnie, @deshipu, @dhalbert, @dmopalmer, @dunkmann00, @edspark, @gallaugher, @hexthat, @hierophect, @iayanpahwa, @iraytrace, @jedgarpark, @jepler, @jerryneedell, @jpecor, @kamtom480, @kattni, @kdb424, @kevinjwalters, @kickbutts, @ladyada, @loganwedwards, @makermelissa, @nis, @rdagger, @santaimpersonator, @shazz, @siddacious, @sommersoft, @tannewt, @theacodes, @timvgso, @wallarug and surely more we have missed. Join us on the [Discord chat](https://adafru.it/discord) to collaborate.

Documentation
-------------

Documentation is available [in readthedocs.io](https://circuitpython.readthedocs.io/en/latest/).

Here are all the [changes since 5.0.0-alpha.4](https://github.com/adafruit/circuitpython/compare/5.0.0-alpha.4...5.0.0-alpha.5).

This release is based on [MicroPython 1.9.4 @25ae98f](https://github.com/micropython/micropython/commit/25ae98f07cb3c4488cb955403dfe56b8bb8db6f0). Support upstream MicroPython by purchasing [a PyBoard](https://store.micropython.org/#/store) (from Adafruit [here](https://www.adafruit.com/product/2390)).

Troubleshooting
---------------

Check out [this guide](https://learn.adafruit.com/welcome-to-circuitpython/troubleshooting) for info on common problems with CircuitPython. If you are still having issues, then post to the [Adafruit Support Forums](https://forums.adafruit.com/viewforum.php?f=60) and join [Discord](https://adafru.it/discord).