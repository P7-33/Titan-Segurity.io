---
title: 'CircuitPython 5.0.0 Beta 5 release! @adafruit @circuitpython'
date: 2020-02-05T04:35:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/11/112619cp5b.jpg)

This is a Beta Release
----------------------

This is release 5.0.0 beta.5. Beta releases are largely feature-complete, but are meant for testing. Use the [latest stable 4.x release](https://circuitpython.org/downloads) when first starting with CircuitPython.

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

New Features, Updates, and Fixes since 5.0.0 Beta 4
---------------------------------------------------

*   Fix BLE reinitialization on soft reload, preventing some hangs and crashes. Thanks @dhalbert.
*   Increase maximum number of BLE connection from 2 to 5. Thanks @dhalbert.
*   Fixed `_bleio.PacketBuffer.packet_size` returning wrong value. Thanks @dhalbert.
*   Most `OSError` exceptions that involve filenames will print the filenames, so you know which filename can’t be found, etc. (on vfat only). Thanks @dhalbert.
*   Fix use and exposure of internal buffers for `PixelBuf`. Thanks @tannewt.
*   `displayio.Palette` now takes tuples and lists as color values in addition to integers. Thanks @kattni for noticing the issue and @jepler and @dhalbert for the fix.
*   Improve DMA for stereo `AudioOut`. Thanks @jepler.
*   Increase stack size on Circuit Playground Express builds to accommodate updated CP library. Thanks @dmopalmer for noticing the issue, and @kattni and @dhalbert for the fix.
*   Turn off on-board user NeoPixels after soft reload on Circuit Playground Bluefruit, PyBadge, and PyGamer. Thanks @dhalbert.
*   Update and improve CLUE `board` definition. Thanks @ladyada and @dhalbert.
*   Use hardware rotation to speed up CLUE display. Thanks @ladyada.
*   Allow specifying background color for `stage` library and `_stage` native module. Thanks @deshipu.
*   Add `gamepad` to CPX crickit and displayio builds; needed for updated CP library. Thanks @dhalbert.
*   Update all frozen libraries. Thanks @dhalbert.
*   Update handling of bad nRF fuse setting. Thanks @dhalbert.
*   Fix on-board display initialization code pin handling. Thanks @dhalbert.
*   Fix compilation of native micropython on OS X. Thanks @tsupplis.
*   Add automatic builds of `mpy-cross` to GitHub actions. Thanks @jepler.
*   Fix native module support matrix generation. Thanks @deshipu.
*   Improve README documentation of differences from MicroPython. Thanks @deshipu.

New Boards
----------

Find downloads for all boards, including these, at https://ift.tt/2Tx6WJB.

### New since 5.0.0-beta.4

*   ndGarage Ndbit6. Thanks @ndGarage.
*   Feather Bluefruit Sense. Thanks @ladyada.
*   meowbit\_v121. Thanks @hierophect.
*   teensy40. Thanks @tannewt.
*   imxrt1060\_evk. Thanks @tannewt.
*   imxrt1020\_evk. Thanks @tannewt.

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

*   `displayio` operations that read from an SD card (e.g., `OnDiskBitmap`) will interfere with other SD card operations and can cause lockup. To work around this problem, do not read or write files on the SD while the display is updating, and _vice versa_.
*   See [https://github.com/adafruit/circuitpython/issues](https://github.com/adafruit/circuitpython/issues) for other issues.

Thanks
------

Thank you to all who used, tested, [contributed](https://github.com/adafruit/circuitpython/graphs/contributors?from=2020-01-21&to=2020-02-03&type=c), helped out, and participated on GitHub and/or Discord,including @tsupplis, @timvictor, @theacodes, @tannewt, @sommersoft, @Shane, @rhooper, @pdp7 (Drew Fustini), @ntoll, @ndGarage, @Mr. Certainly, @makermelissa, @maholli, @madbodger, @ladyada, @kevinjwalters, @kattni, @joey, @jerryneedell, @jepler, @jasonp, @hierophect, @geekguy, @Frank.H, @foamyguy, @Duewester, @dherrada, @dhalbert, @deshipu, @dcbricetti, @DavidGlaude, @dastels, @Dar-Scott, @CudaCoreRoo, @codeNsolder, @CGrover, @carternuson, @callmeraffiq, @brentru, @bitbank Mr. Optimization, @Becky-lou, @ATMakersBill, @arturo182, @ardnew, @anecdata, @Aine, and surely more we have missed. Join us on the [Discord chat](https://adafru.it/discord) to collaborate.

Documentation
-------------

Documentation is available [in readthedocs.io](https://circuitpython.readthedocs.io/en/latest/).

Here are all the [changes since 5.0.0-beta.4](https://github.com/adafruit/circuitpython/compare/5.0.0-beta.4...5.0.0-beta.5).

This release is based on [MicroPython 1.9.4 @25ae98f](https://github.com/micropython/micropython/commit/25ae98f07cb3c4488cb955403dfe56b8bb8db6f0). Support upstream MicroPython by purchasing [a PyBoard](https://store.micropython.org/#/store) (from Adafruit [here](https://www.adafruit.com/product/2390)).

Troubleshooting
---------------

Check out [this guide](https://learn.adafruit.com/welcome-to-circuitpython/troubleshooting) for info on common problems with CircuitPython. If you are still having issues, then post to the [Adafruit Support Forums](https://forums.adafruit.com/viewforum.php?f=60) and join [Discord](https://adafru.it/discord).

  
  
from Adafruit Industries – Makers, hackers, artists, designers and engineers! https://ift.tt/2tyEGdS  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)