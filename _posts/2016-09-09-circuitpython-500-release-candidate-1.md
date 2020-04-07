---
title: 'CircuitPython 5.0.0 Release Candidate 1! — @adafruit @circuitpython'
date: 2020-03-01T23:24:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/11/112619cp5b.jpg)

This is a 5.0.0 Release Candidate — please test
-----------------------------------------------

This is release **5.0.0-rc.1** (Release candidate 1). If this release does not have show-stopper issues, it will be re-released as 5.0.0, the first 5.x.x stable release.

If you find a bug please [check the current known issues](https://github.com/adafruit/circuitpython/issues) and [file an issue](https://github.com/adafruit/circuitpython/issues/new) if something isn’t already known.

5.0.0
-----

5.0.0 is the latest major revision of CircuitPython. It features many improvements and enhancements to `displayio`, including grayscale OLED and e-paper displays, extensive additions and improvements to BLE support, support for the STM32F4, iMX RT10xx and Sony Spresense microcontroller families, and PWM audio support.

Download from circuitpython.org
-------------------------------

Downloads are available from [circuitpython.org](https://circuitpython.org)! The site makes it easy to select the correct file and language for your board. The downloads page is [here](https://circuitpython.org/downloads). Downloads are no longer available from the GitHub release pages because of the large number of files for each release.

Installation
------------

To install follow the instructions in our new [Welcome to CircuitPython!](https://learn.adafruit.com/welcome-to-circuitpython/installing-circuitpython) guide. To install the latest libraries, see [this page](https://learn.adafruit.com/welcome-to-circuitpython/circuitpython-libraries) in that guide.

Try [the latest version of the Mu editor](https://learn.adafruit.com/welcome-to-circuitpython/installing-mu-editor) for creating and editing your CircuitPython programs and for easy access to the CircuitPython serial connection (the REPL).

New Features, Updates, and Fixes Since 5.0.0-rc.0
-------------------------------------------------

### i.MX

*   Fix I2C clock speed on i.MX boards. Thanks @mubes.
*   Freeze `adafruit_requests` and `adafruit_esp32spi` libraries into mimxrt1011 builds to save RAM. Thanks @arturo182.  
    
    ### Other board-specific fixes
    
*   Arduino M0 boards now have both `.bin` and `.uf2` downloads available. Thanks @dhalbert, and thanks to @fgallaire for pointing out the issue.  
    
    ### Build infrastructure
    
*   Release download links available at https://ift.tt/2Tx6WJB now point to AWS S3 instead of to GitHub release assets. Thanks @dhalbert, @jwcooper, and @sommersoft.

New Boards
----------

Find downloads for all boards, including these, at https://ift.tt/2Tx6WJB.

### New Since 5.0.0-rc.0

None.

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
*   See https://ift.tt/2j1euBi for other issues.@

Thanks
------

Thank you to all who used, tested, [contributed](https://github.com/adafruit/circuitpython/graphs/contributors?from=2020-02-27&to=2020-03-01&type=c), helped out, and participated on GitHub and/or Discord, including @arturo182, @bmeisels, @DavePutz, @dhalbert, @fgallaire, @hierophect, @jamesbowman, @jepler, @ladyada, @lgnashold, @maholli, @makermelissa, @mubes, @neubauek, @pdp7, @rhooper, @tannewt, @ATMakersBill, @AndrewTribble, @Anne B, @Antonio, @CGrover, @CarlFK, @Curt Olson, @Dar, @DaveP, @DavidGlaude, @DudeImOnly6, @Duewester, @KingerNorth, @SouthernDragon, @TG-Techie, @ThomasAtBBTF, @adafruit, @anecdata, @brentru, @cater, @charlesburnaford, @codeNSolder, @deshipu, @dherrada, @diegoMini+, @ednl, @foamyguy, @geekguy, @graham, @hexthat, @jasonp, @jerryn, @kattni, @kjw, @madbodger, @marius\_450, @mscosti, @ntoll, @siddacious, @sommersoft, @stargirl, @timvictor, @v923z and surely more we have missed. Join us on the [Discord chat](https://adafru.it/discord) to collaborate.

Documentation
-------------

Documentation is available [in readthedocs.io](https://circuitpython.readthedocs.io/en/latest/).

Here are all the [changes since 5.0.0-rc.0](https://github.com/adafruit/circuitpython/compare/5.0.0-rc.0...5.0.0-rc.1).

This release is based on [MicroPython 1.9.4 @25ae98f](https://github.com/micropython/micropython/commit/25ae98f07cb3c4488cb955403dfe56b8bb8db6f0). Support upstream MicroPython by purchasing [a PyBoard](https://store.micropython.org/#/store) (from Adafruit [here](https://www.adafruit.com/product/2390)).

Troubleshooting
---------------

Check out [this guide](https://learn.adafruit.com/welcome-to-circuitpython/troubleshooting) for info on common problems with CircuitPython. If you are still having issues, then post to the [Adafruit Support Forums](https://forums.adafruit.com/viewforum.php?f=60) and join [Discord](https://adafru.it/discord).