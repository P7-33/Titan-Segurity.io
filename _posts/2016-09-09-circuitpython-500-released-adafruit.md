---
title: 'CircuitPython 5.0.0 released! @adafruit @circuitpython'
date: 2020-03-03T01:23:00+01:00
draft: false
---

![](https://cdn-blog.adafruit.com/uploads/2019/11/112619cp5b.jpg)

5.0.0
-----

This is CircuitPython **5.0.0**, the latest major revision of CircuitPython, and is a new stable release.

5.0.0 features many improvements and enhancements to `displayio`, including grayscale OLED and e-paper displays, extensive additions and improvements to BLE support, support for the STM32F4, iMX RT10xx and Sony Spresense microcontroller families, and PWM audio support.

Download from circuitpython.org
-------------------------------

Downloads are available from [circuitpython.org](https://circuitpython.org)! The site makes it easy to select the correct file and language for your board. The downloads page is [here](https://circuitpython.org/downloads). Downloads are no longer available from the GitHub release pages because of the large number of files for each release.

Installation
------------

To install follow the instructions in our new [Welcome to CircuitPython!](https://learn.adafruit.com/welcome-to-circuitpython/installing-circuitpython) guide. To install the latest libraries, see [this page](https://learn.adafruit.com/welcome-to-circuitpython/circuitpython-libraries) in that guide.

Try [the latest version of the Mu editor](https://learn.adafruit.com/welcome-to-circuitpython/installing-mu-editor) for creating and editing your CircuitPython programs and for easy access to the CircuitPython serial connection (the REPL).

New features and improvements since 4.1.2
-----------------------------------------

*   **Many improvements to `displayio`**
    *   Revamped refresh API
    *   Grayscale OLED support
    *   e-paper display support
    *   Groups can be hidden
*   **Many `_bleio` improvements**
    *   Renamed `bleio` to `_bleio` to emphasize one should use [the BLE library](https://github.com/adafruit/Adafruit_CircuitPython_BLE/) and that `_bleio`‘s API may change without a major CircuitPython version bump
    *   Central support
    *   Client support
    *   Pairing and bonding support
*   **Many audio fixes and improvements**
    *   MP3 decoding support
    *   PWM audio out
    *   nRF52840 I2S support
    *   Mixer moved to `audiomixer` and now supports per-voice volume
*   **Finalized `_pixelbuf` API for RGB pixel speedups**
*   **Additional chip families with beta support:**
    *   STM32F4
    *   iMX RT 10xx
    *   CXD56 (Sony Spresense)
*   **Added Korean translation**
*   **Many translation improvements**

Breaking Changes and Deprecations from 4.x
------------------------------------------

*   **5.0.0 improves our internal filesystem definitions and may overwrite your existing files so make sure to back them up before updating!**
*   The `bleio` module has been renamed to `_bleio` to indicate that it is meant to be used only for writing BLE libraries, and that its API may change between CircuitPython minor versions. There are many incompatible changes in `_bleio` since 4.0.0. Please use the latest [`adafruit_ble` library](https://github.com/adafruit/Adafruit_CircuitPython_BLE/releases) for end-user BLE programming.
*   The `displayio` refresh API has been revamped to be simpler. `wait_for_frame` and `refresh_soon` have been removed. In both 4.x and 5.x, auto refresh will automatically refresh the display so they can be removed. The new `auto_refresh` property and `refresh()` function can be used to control when the screen refreshes and at a specific rate.
*   Moved `audioio.Mixer` to `audiomixer.Mixer`, which is only available on M4s. Moved `audioio.RawSample`, and `audioio.WaveFile` to the new module `audiocore`. However, for backwards compatibility, they are still available in `audioio`. They will be removed from `audioio` in 6.0.0. Thanks @jepler.
*   Added `I2C.writeto_then_readfrom()`. Deprecate `stop=` arg which will be removed in 6.x. Use `I2C.writeto_then_readfrom()` instead.
*   Removed `re` from CircuitPlayground Express Display build.
*   Removed `gamepad` from CircuitPlayground Express Crickit build.

51 New boards since 4.1.2
-------------------------

*   [Adafruit Bluefruit Sense](https://circuitpython.org/board/feather_bluefruit_sense/)
*   [Adafruit Circuit Playground Bluefruit](https://circuitpython.org/board/circuitplayground_bluefruit/)
*   [Adafruit Circuit Playground Express with displayio](https://circuitpython.org/board/circuitplayground_express_displayio/)
*   [Adafruit Clue nRF52840 Express](https://circuitpython.org/board/clue_nrf52840_express/)
*   [Adafruit Edge Badge](https://circuitpython.org/board/edgebadge/)
*   [Adafruit Feather M7 1011](https://circuitpython.org/board/feather_m7_1011/)
*   [Adafruit Feather STM32F405 Express](https://circuitpython.org/board/feather_stm32f405_express/)
*   [Adafruit Itsy Bitsy nRF52840 Express](https://circuitpython.org/board/itsybitsy_nrf52840_express/)
*   [Adafruit Metro nRF52840 Express](https://circuitpython.org/board/metro_nrf52840_express/)
*   [Adafruit Monster M4SK](https://circuitpython.org/board/monster_m4sk/)
*   [Adafruit PyPortal Pynt](https://circuitpython.org/board/pyportal_pynt/)
*   [Adafruit PyPortal Titano](https://circuitpython.org/board/pyportal_titano/)
*   [Alethea Flowers Winterbloom Sol](https://circuitpython.org/board/winterbloom_sol/)
*   [ARAMCON Badge 2019](https://circuitpython.org/board/aramcon_badge_2019/)
*   [Arduino NANO 33 BLE](https://circuitpython.org/board/arduino_nano_33_ble/)
*   [Arduino NANO 33 IoT](https://circuitpython.org/board/arduino_nano_33_iot/)
*   [arturo182 Feather MIMXRT1011](https://circuitpython.org/board/feather_mimxrt1011/)
*   [arturo182 Feather MIMXRT1062](https://circuitpython.org/board/feather_mimxrt1062/)
*   [arturo182 Serpente](https://circuitpython.org/board/serpente/)
*   [Cedar Grove Studios StringCar M0 Express](https://circuitpython.org/board/stringcar_m0_express/)
*   [Elecrow PYB Nano v2](https://circuitpython.org/board/pyb_nano_v2/)
*   [Espruino Pico](https://circuitpython.org/board/espruino_pico/)
*   [Espruino WiFi](https://circuitpython.org/board/espruino_wifi/)
*   [George Robotics Pyboard](https://circuitpython.org/board/pyboard_v11/)
*   [keithp.com Snekboard](https://circuitpython.org/board/snekboard/)
*   [KittenBot Meowbit](https://circuitpython.org/board/meowbit_v121/)
*   [Null Bytes Labs CircuitBrains Basic](https://circuitpython.org/board/circuitbrains_basic_m0/)
*   [Null Bytes Labs CircuitBrains Deluxe](https://circuitpython.org/board/circuitbrains_deluxe_m4/)
*   [NXP MIMXRT1010 Eval Kit](https://circuitpython.org/board/imxrt1010_evk/)
*   [NXP MIMXRT1020 Eval Kit](https://circuitpython.org/board/imxrt1020_evk/)
*   [NXP MIMXRT1060 Eval Kit](https://circuitpython.org/board/imxrt1060_evk/)
*   [n°Garage Ndbit6](https://circuitpython.org/board/ndgarage_ndbit6/)
*   [Oddly Specific Objects Open Book](https://circuitpython.org/board/openbook_m4/)
*   [OSHWA Open Hardware Summit 2020 Badge](https://circuitpython.org/board/ohs2020_badge/)
*   [PJRC Teensy 4.0](https://circuitpython.org/board/teensy40/)
*   [Radomir Dopieralski PewPew M4](https://circuitpython.org/board/pewpew_m4/)
*   [Robot Exploration Lab PyCubed](https://circuitpython.org/board/pycubed/)
*   [Robotics Masters Robo HAT MM1 M4](https://circuitpython.org/board/robohatmm1_m4/)
*   [Seeed Seeeduino XIAO](https://circuitpython.org/board/seeeduino_xiao/)
*   [Sarfata shIRtty](https://circuitpython.org/board/shirtty/)
*   [Sony Spresense](https://circuitpython.org/board/spresense/)
*   [SparkFun Qwiic Micro w/o Flash](https://circuitpython.org/board/sparkfun_qwiic_micro_no_flash/)
*   [SparkFun Qwiic Micro w/Flash](https://circuitpython.org/board/sparkfun_qwiic_micro_with_flash/)
*   [SparkFun SAMD51 Thing Plus](https://circuitpython.org/board/sparkfun_samd51_thing_plus/)
*   [ST STM32F407 Discovery Kit](https://circuitpython.org/board/stm32f4_discovery/)
*   [ST STM32F411 Discovery Kit](https://circuitpython.org/board/stm32f411ve_discovery/)
*   [ST STM32F412 Discovery Kit](https://circuitpython.org/board/stm32f412zg_discovery/)
*   [Teknikio Bluebird](https://circuitpython.org/board/teknikio_bluebird/)
*   [TZT STM32F411CE Black Pill](https://circuitpython.org/board/stm32f411ce_blackpill/)
*   [XinaBox CC03](https://circuitpython.org/board/xinabox_cc03/)
*   [XinaBox CS11](https://circuitpython.org/board/xinabox_cs11/)

Known Issues
------------

*   `displayio` operations that read from an SD card (e.g., `OnDiskBitmap`) will interfere with other SD card operations and can cause lockup. To work around this problem, do not read or write files on the SD while the display is updating, and _vice versa_.
*   See https://ift.tt/2j1euBi for other issues.

Thanks
------

Thank you to all who used, tested, [contributed](https://github.com/adafruit/circuitpython/graphs/contributors?from=2019-07-18&to=2020-03-02&type=c), helped out, and participated on GitHub and/or Discord, including @3ach, @adafruit, @AdinAck, @aine, @albang, @alexwhittemore, @AndrewTribble, @anecdata, @anneb, @anne B, @AnthonyDiGirolamo, @Anton-2, @antonio, @ardnew, @arturo182, @ATMakersBill, @becky-lou, @bitbank Mr. Optimization, @bmeisels, @brentru, @C47D, @callmeraffiq, @CarlFK, @carternuson, @cater, @caternuson, @cbyr2401, @CedarGroveStudios, @cgrover, @charlesburnaford, @_cli_ninja, @codeNsolder, @CollinCunningham, @cr1901, @CSchmitz, @CudaCoreRoo, @curt Olson, @dalegrover, @Dar, @darkmusic, @Dar-Scott, @dastels, @davep, @DavePutz, @DavidGlaude, @dcbricetti, @ddiminnie, @deanm1278, @deshipu, @devoh, @dglaude, @dhalbert, @dherrada, @diegoMini+, @dmgrime, @dmopalmer, @dpgeorge, @DrewFustini, @DudeImOnly6, @Duewester, @dunkmann00, @dhalbert, @edspark, @fede2, @fgallaire, @FoamyGuy, @Frank.H, @gallaugher, @geekguy, @gotfredsen, @graham, @hathach, @hexthat, @hierophect, @hukuzatuna, @hybotics, @iayanpahwa, @iot49, @iraytrace, @jackdanielsmurphy, @jamesbowman, @jasonp, @jedgarpark, @jepler, @Jerryn, @jerryneedell, @JoeBakalor, @joey, @joeycastillo, @josh, @jp, @jpecor, @KalbeAbbas, @kamtom480, @kattni, @kdb424, @kevinjwalters, @kickbutts, @KingerNorth, @KittenCanaveral, @kjw, @klardotsh, @ladyada, @lgnashold, @loganwedwards, @madbodger, @maholli, @makermelissa, @marius\_450, @Marius-450, @matthewnewberg, @MikeB, @MrCertainly, @mr. Certainly, @Mr-Coxall, @mscosti, @mubes, @mwelling, @mytechnotalent, @ndGarage, @neubauek, @nickzoic, @nis, @ntavish, @ntoll, @OldCrow, @osterwood, @pdp7, @pdp7, @pigrew, @pt, @ptorrone, @rafa-gould, @rdagger, @reply2jh, @Retoc, @rhooper, @sajattack, @santaimpersonator, @sarfata, @scs217, @Senuros, @shane, @shazz, @siddacious, @s-light, @sommersoft, @SouthernDragon, @stargirl, @TammyMakesThings, @tannewt, @TG-Techie, @theacodes, @theodox, @ThomasAtBBTF, @timvgso, @timvictor, @tsupplis, @urish, @v923z, @wallarug and surely more we have missed. Join us on the [Discord chat](https://adafru.it/discord) to collaborate.

Documentation
-------------

Documentation is available [in readthedocs.io](https://circuitpython.readthedocs.io/en/5.0.x/).

This release is based on [MicroPython 1.9.4 @25ae98f](https://github.com/micropython/micropython/commit/25ae98f07cb3c4488cb955403dfe56b8bb8db6f0). Support upstream MicroPython by purchasing [a PyBoard](https://store.micropython.org/#/store) (from Adafruit [here](https://www.adafruit.com/product/2390)).

Troubleshooting
---------------

Check out [this guide](https://learn.adafruit.com/welcome-to-circuitpython/troubleshooting) for info on common problems with CircuitPython. If you are still having issues, then post to the [Adafruit Support Forums](https://forums.adafruit.com/viewforum.php?f=60) and join [Discord](https://adafru.it/discord).