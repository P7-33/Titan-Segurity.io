---
title: 'CircuitPython 5.0.0 Beta 4 release! @adafruit @circuitpython'
date: 2020-01-22T16:32:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/11/112619cp5b.jpg)

This is a Beta Release
----------------------

This is release 5.0.0 beta.4. Beta releases are largely feature-complete, but are meant for testing. Use the [latest stable 4.x release](https://circuitpython.org/downloads) when first starting with CircuitPython.

When you find a bug please [check the current known issues](https://github.com/adafruit/circuitpython/issues) and [file an issue](https://github.com/adafruit/circuitpython/issues/new) if something isn’t already known.

5.0.0
-----

5.0.0 is the latest major revision of CircuitPython. It features many improvements and enhancements to `displayio`, including grayscale OLED and e-paper displays, extensive additions and improvements to BLE support, support for the STM32F4, iMX RT10xx and Sony Spresense microcontrollers, and PWM audio support.

Download from circuitpython.org
-------------------------------

Downloads are available from [circuitpython.org](https://circuitpython.org)! The site makes it easy to select the correct file and language for your board. The downloads page is [here](https://circuitpython.org/downloads).

Installation
------------

To install follow the instructions in our new [Welcome to CircuitPython!](https://learn.adafruit.com/welcome-to-circuitpython/installing-circuitpython) guide. To install the latest libraries, see [this page](https://learn.adafruit.com/welcome-to-circuitpython/circuitpython-libraries) in that guide.

Try [the latest version of the Mu editor](https://learn.adafruit.com/welcome-to-circuitpython/installing-mu-editor) for creating and editing your CircuitPython programs and for easy access to the CircuitPython serial connection (the REPL).

New Features, Updates, and Fixes since 5.0.0 Beta 3
---------------------------------------------------

*   Add BLE bonding. Thanks @dhalbert.
*   Fix tuple subscripting regression. Thanks @rhooper.
*   STM32: Fix I2C and clean up `busio`. Thanks @hierophect.
*   Make buffer handling more robust for `urandom`. Thanks to @jepler
*   Updates for Capable Robot USB Hub. Thanks @capableRobot.
*   `mimxrt1011` updates. Thanks to arturo182.
*   Add `Dxx` pin names to Feather M4 Express. Thanks @scs217.
*   Spresense: use source files instead of preocmpiled binaries for `mkspk`. Thanks @kamtom480.
*   Spresense: fix `board_timerhook`. Thanks @kamtom480.
*   Use Python 3 to run all Python scripts. Thanks @theodox.
*   Fix support matrix generation. Thanks @deshipu.
*   Requiring I2C pullups can now be turned off for a build. Thanks @dhalbert.

New Boards
----------

Find downloads for all boards, including these, at https://ift.tt/2Tx6WJB.

### New since 5.0.0-beta.3

*   [Ohs2020 badge](https://circuitpython.org/board/ohs2020_badge/). Thanks @mwelling.
*   [Seeduino XIAO](https://circuitpython.org/board/seeeduino_xiao/). Thanks @dalegrover
*   [Open Book](https://circuitpython.org/board/openbook_m4/). Thanks @joeycastillo.
*   AramCon Badge 2019. Thanks @bmeisels.

Breaking Changes and Deprecations from 4.x
------------------------------------------

*   **5.0.0 improves our internal filesystem definitions and may overwrite your existing files so make sure to back them up before updating!**
*   The `bleio` module has been renamed to `_bleio` to indicate that it is meant to be used only for writing BLE libraries, and that its API may change between CircuitPython minor versions. There are many incompatible changes in `_bleio` since 4.0.0. Please use the latest [`adafruit_ble` library](https://github.com/adafruit/Adafruit_CircuitPython_BLE/releases) for end-user BLE programming.
*   The `displayio` refresh API has been revamped to be simpler. `wait_for_frame` and `refresh_soon` have been removed. In both 4.x and 5.x, auto refresh will automatically refresh the display so they can be removed. The new `auto_refresh` property and `refresh()` function can be used to control when the screen refreshes and at a specific rate.
*   Moved `audioio.Mixer` to `audiomixer.Mixer`, which is only available on M4s. Moved `audioio.RawSample`, and `audioio.WaveFile` to the new module `audiocore`. However, for backwards compatibility, they are still available in `audioio`. They will be removed from `audioio` in 6.0.0. Thanks @jepler.
*   Added `I2C.writeto_then_readfrom()`. Deprecate `stop=` arg which will be removed in 6.x. Use `I2C.writeto_then_readfrom()` instead.
*   Removed `re` from CircuitPlayground Express Display build.
*   Removed `gamepad` from CircuitPlayground Express Crickit build.

Known Issues
------------

*   See https://ift.tt/2j1euBi.

Thanks
------

Thank you to all who used, tested, [contributed](https://github.com/adafruit/circuitpython/graphs/contributors?from=2020-01-08&to=2020-01-21&type=c), helped out, and participated on GitHub and/or Discord,including @ATMakersBill, @AnneB, @CGrover, @Dar-Scott, @DrewFustini, @KittenCanaveral, @TG-Techie, @arturo182, @bmeisels, @brentru, @caternuson, @codeNsolder, @cschmitz, @dalegrover, @deshipu, @deshipu, @dglaude, @dhalbert, @dherrada, @foamyguy, @geekguy, @hathach, @hierophect, @hukuzatuna, @jepler, @jerryn, @joeycastillo, @kamtom480, @kattni, @kevinjwalters, @ladyada, @madbodger, @maholli, @makermelissa, @mwelling, @nickzoic, @osterwood, @rhooper, @scs217, @siddacious, @tannewt, @theacodes, @theodox, @wallarug and surely more we have missed. Join us on the [Discord chat](https://adafru.it/discord) to collaborate.

Documentation
-------------

Documentation is available [in readthedocs.io](https://circuitpython.readthedocs.io/en/latest/).

Here are all the [changes since 5.0.0-beta.3](https://github.com/adafruit/circuitpython/compare/5.0.0-beta.3...5.0.0-beta.4).

This release is based on [MicroPython 1.9.4 @25ae98f](https://github.com/micropython/micropython/commit/25ae98f07cb3c4488cb955403dfe56b8bb8db6f0). Support upstream MicroPython by purchasing [a PyBoard](https://store.micropython.org/#/store) (from Adafruit [here](https://www.adafruit.com/product/2390)).

Troubleshooting
---------------

Check out [this guide](https://learn.adafruit.com/welcome-to-circuitpython/troubleshooting) for info on common problems with CircuitPython. If you are still having issues, then post to the [Adafruit Support Forums](https://forums.adafruit.com/viewforum.php?f=60) and join [Discord](https://adafru.it/discord).

  
  
from Adafruit Industries – Makers, hackers, artists, designers and engineers! https://ift.tt/2tGRvmq  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)