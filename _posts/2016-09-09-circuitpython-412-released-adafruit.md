---
title: 'CircuitPython 4.1.2 Released — @adafruit @circuitpython'
date: 2019-12-19T02:18:00+01:00
draft: false
---

![https://www.adafruit.com/product/3333](https://cdn-blog.adafruit.com/uploads/2019/06/cpx-circuitpython-banner-600x193.png)

4.1.2 is a minor stable release. Most notably, it updates the `adafruit_circuitplayground` frozen library for Circuit Playground Express. It shouldn’t break any code compatible with previous 4.x releases. If you don’t have a Circuit Playground Express or a PyRuler, or a board with frozen libraries, there is no strong reason to update to 4.1.2.

Download it now from [circuitpython.org](https://circuitpython.org/downloads). See [here](https://github.com/adafruit/circuitpython/releases/tag/4.1.2) for the full release notes.

(In case you’re wondering, release 4.1.1 was built incorrectly and was deleted.)

Over 60 boards are now supported by CircuitPython 4.1.2. Check out the new [circuitpython.org/downloads](https://circuitpython.org/downloads) page for full list of all available versions.

Contribute to CircuitPython! Check out [this guide](https://learn.adafruit.com/contribute-to-circuitpython-with-git-and-github) for details. Subscribe to the Python for Microcontrollers newsletter on [adafruitdaily.com](https://adafruitdaily.com) for the latest news for all things Python.

circuitpython.org
-----------------

Downloads are now available from [circuitpython.org](https://circuitpython.org)! This site makes it much easier to select the correct file and language for your board. The downloads page is [here](https://circuitpython.org/downloads).

Installation
------------

To install follow the instructions in our new [Welcome to CircuitPython!](https://learn.adafruit.com/welcome-to-circuitpython/installing-circuitpython) guide. To install the latest libraries, see [this page](https://learn.adafruit.com/welcome-to-circuitpython/circuitpython-libraries) in that guide.

Try [the latest version of the Mu editor](https://learn.adafruit.com/welcome-to-circuitpython/installing-mu-editor) for creating and editing your CircuitPython programs and for easy access to the CircuitPython serial connection (the REPL).

New Fixes and Features since 4.1.0
----------------------------------

*   On Circuit Playground Express (CPX) builds, the frozen-in `adafruit_circuitplayground` library now supports:  
    `from adafruit_circuitplayground import cp`  
    in addition to the previous standard import:  
    `from adafruit_circuitplayground.express import cpx`  
    This allows uniform library support for the the Circuit Playground Bluefruit (which requires CircuitPython 5.x). The [library examples](https://github.com/adafruit/Adafruit_CircuitPython_CircuitPlayground/tree/master/examples) have all been updated to use `cp` instead of `cpx`. The names `cp` and `cpx` can be used identically: only the `import` is different. You do not need to change your existing code. Thanks @kattni.
*   The stack size on CPX builds has been increased slightly to accommodate the restructured library. Thanks @dhalbert and @jepler.
*   Other frozen libraries have been updated to their latest versions. Thanks @dhalbert.
*   The PyRuler now displays correct colors on its on-board DotStar RGB LED. Thanks @dhalbert.
*   `PWMOut.deinit()` on nrf builds was now releases the pin. Thanks @jepler.
*   The library freezing process now makes sure not to include subdirectories of excluded directories. Thanks @jepler.
*   Translated messages are now compressed more effectively, preventing certain translated builds from being too large. Thanks @jepler.

Thanks
------

Thank you to all who contributed and tested to this release: @dhalbert, @jepler, @kattni, @ladyada, @tannewt.  
Join us on the [Discord chat](https://adafru.it/discord) to collaborate.

Documentation
-------------

Documentation is available [in readthedocs.io](https://circuitpython.readthedocs.io/en/4.x/).

Here are all the [changes since 4.1.0](https://github.com/adafruit/circuitpython/compare/4.1.0...4.1.2).

This release is based on [MicroPython 1.9.4 @25ae98f](https://github.com/micropython/micropython/commit/25ae98f07cb3c4488cb955403dfe56b8bb8db6f0). Support upstream MicroPython by purchasing [a PyBoard](https://store.micropython.org/#/store) (from Adafruit [here](https://www.adafruit.com/product/2390)).

Troubleshooting
---------------

Check out [this guide](https://learn.adafruit.com/welcome-to-circuitpython/troubleshooting#for-non-express-boards-with-a-uf2-bootloader-gemma-m0-trinket-m0) for info on common problems with CircuitPython. If you are still having trouble, then post to the [Adafruit Support Forums](https://forums.adafruit.com/viewforum.php?f=60) and join [Discord](https://adafru.it/discord).

  
  
from Adafruit Industries – Makers, hackers, artists, designers and engineers! https://ift.tt/38Og68J  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)