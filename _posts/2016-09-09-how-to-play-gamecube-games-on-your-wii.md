---
title: 'How to Play GameCube Games on Your Wii U With Nintendont'
date: 2019-12-07T01:10:00+01:00
draft: false
---

![gamecube-wii-u-nintendont](https://static.makeuseof.com/wp-content/uploads/2016/08/gamecube-wii-u-nintendont.jpg)

Nintendo consoles always seem to leave a lasting impression on their fans. And the GameCube is no exception. However, while the Wii featured backwards-compatibility, the Wii U did not.

Which is where Nintendont comes in. Nintendont being Homebrew software that restores backwards compatibility for GameCube games to your Wii U, and adds additional features to boot.

Here’s how to play GameCube games on your Wii U with Nintendont.

What Is Nintendont?
-------------------

Nintendont isn’t an emulator, because it doesn’t need to emulate the GameCube’s hardware. When Nintendo ditched GameCube support on the Wii U, they effectively flipped a virtual switch to turn the feature off.

Nintendont turns that switch back on again, allowing you to run GameCube natively at full speed. This exploit is possible as the “final” firmware used on the original Wii and in vWii mode on the Wii U is susceptible to tampering.

By installing the Homebrew Channel, it’s possible to install and run all sorts of additional applications on your Wii, inluding these [great emulators to run on your Wii](//www.makeuseof.com/tag/4-great-emulators-run-wii/).

Nintendont is a bootloader for GameCube games. The only difference is that the Wii U cannot play the original GameCube discs. As a result, you’ll need to resort to disc images.

Do You Need to Install Nintendont on Your Wii U?
------------------------------------------------

Nintendont is an excellent option for Nintendo Wii U owners. The platform’s comparatively limited library is instantly bolstered by an additional 600-plus titles. That’s a massive advantage that adds to the existing Wii U titles and most of the Wii library.

Nintendont also brings some useful new features to the Wii U:

*   Memory card emulation, allowing local save game storage
*   Support for Bluetooth controllers like the Sony PS3 and PS4 controllers
*   Support for common USB controllers
*   You’ll also be able to use a [GameCube controller adaptor](https://www.amazon.com/Switch-Gamecube-Controller-Adapter-Nintendo/dp/B07Q459FBQ) for the Wii U
*   Force games to use higher video resolution and output in 16:9
*   Access to a cheat database

Nintendont can also be installed on the Nintendo Wii, which allows you to use original GameCube discs. Conversely, the Wii U spits out the small 8cm discs.

For Wii U owners, GameCube titles need to be ripped to a disk image file. Just make sure you own the originals, as piracy IS illegal.

For Wii owners, installing Nintendont adds support for new controllers and graphical enhancements. Similarly, Wii owners can use original GameCube memory cards.

Essentially, installing Nintendont means you get to use your console in a new way.

Install the Homebrew Channel on Your Wii or Wii U
-------------------------------------------------

To install Nintendont on your Wii U or Wii you’ll first need to install the Homebrew Channel.

There are a few different ways to do this, but it’s smartest to stick to the most recent options. The process has gotten easier over the years—the less time you spend hacking your Nintendo, the more time you’ll have for gaming.

The important thing to remember is that Nintendont doesn’t require any additional USB loaders, cIOS revisions, or other tweaks. You just need to get your console to a state where the Homebrew Channel has been installed.

Regardless of which console you have, you’ll need to download a few files and put them on a regular SD card. This should not be an SDHC or SDXC and should be less than 8GB in most cases. Once you’ve installed the Homebrew Channel, you can use larger SD cards and even USB sticks with your console.

If you already have the Homebrew Channel installed, you can skip this step. Check our other articles to learn how to install Homebrew on your Nintendo Wii and Nintendo Wii U.

*   [Install the Homebrew Channel on the Nintendo Wii](//www.makeuseof.com/tag/set-wii-homebrew-letterbomb/)
*   [Hack your Nintendo Wii U by installing the Homebrew Channel](//www.makeuseof.com/tag/make-wii-u-useful-with-homebrew/)

Install Nintendont on the Nintendo Wii U
----------------------------------------

With Homebrew installed on your Nintendo, follow these steps:

*   Format an SD card, maximum 8GB, to FAT32
*   Head to [the Nintendont project at GitHub](https://github.com/FIX94/Nintendont) and download:
    *   [icon.png](https://github.com/FIX94/Nintendont/blob/master/nintendont/icon.png?raw=true)
    *   [meta.xml](https://github.com/FIX94/Nintendont/blob/master/nintendont/meta.xml?raw=true)
    *   [loader.dol](https://github.com/FIX94/Nintendont/blob/master/loader/loader.dol?raw=true)
*   Save these to a folder on the SD card called **apps/nintendont/**
*   Rename loader.dol as boot.dol
*   In the root of the SD card, create a new folder called **/games**
*   Copy GameCube game files to the **/games/** directory
    *   For two-disc games, place both disc images in a subdirectory, **/games/TITLE** (where TITLE should be the name of the game) and rename disc 1 to **game.iso** and disc2 to **disc2.iso**
*   Insert the SD card in the Wii U
*   Start the Homebrew Channel, select Nintendont, and load the GameCube title

Nintendont Features and Tweaks
------------------------------

With Nintendont running you are given the choice of SD or USB storage, as well as original media (disc drive).

However, there’s also a settings menu to explore. A few settings you might want to enable include:

*   **Memcard Emulation:** Uses your USB or SD device to store games (turn this off to use physical memory cards)
*   **Force Widescreen:** Self-explanatory, may break things
*   **Force Progressive:** Always use 480p, again, may break things
*   **Auto Boot:** Allows you to resume the last game you were playing when you launch Nintendont (hold B on your WiiMote at startup to bypass)
*   **Native Control:** Enables support for real GameCube accessories on a Wii, like the Game Boy Advance link cable. Disable this to use other USB controllers with Nintendont
*   **Patch PAL50:** Worth trying if you can’t get certain games working, for example, Super Mario Sunshine

From the **Settings** screen you can access the **Update** menu. Choose **Download controllers.zip** to use USB controllers like the PS4 controller with your console.

Once installed, Nintendont should detect any USB controller you attach.

Playing Nintendo GameCube Games on the Wii
------------------------------------------

As noted earlier, Nintendont can also run in Homebrew on the Nintendo Wii. In some ways, this is preferable. The original Wii will play the GameCube discs, whereas they’re incompatible with the Wii U.

So, you can install the Homebrew Channel, and set up Nintendont on your SD card as described above. Then simply insert your favorite old GameCube disc and start playing.

This also means that if you have both consoles you can use the Nintendo Wii to rip your own GameCube discs. Use a tool called [CleanRip](http://wiibrew.org/wiki/CleanRip) to do this, saving the ZIP file to the /apps/ directory as with Nintendont.

Launch CleanRip in Nintendont on the Wii with the GameCube game disc inserted. The disc will be ripped and saved to the SD card.

Can Your Wii U Play GameCube Games? Yes It Can!
-----------------------------------------------

The GameCube was a celebrated system, with many exclusives that are worth checking out or revisiting.

Some GameCube games you might want to play are Super Mario Sunshine, Super Smash Bros. Melee, and The Legend of Zelda: The Wind Waker. All of which are absolute classics.

Do you want to play GameCube games but don’t own a Nintendo Wii or Wii U? Then here’s [how to play Nintendo GameCube games on PC](//www.makeuseof.com/tag/play-nintendo-gamecube-games-pc/).

Read the full article: [How to Play GameCube Games on Your Wii U With Nintendont](https://www.makeuseof.com/tag/play-gamecube-games-wii-u-nintendont/)

  
  
from MakeUseOf https://ift.tt/2rniYIv  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)