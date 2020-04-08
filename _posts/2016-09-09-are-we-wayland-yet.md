---
title: 'Are We Wayland Yet?'
date: 2019-11-25T02:44:00+01:00
draft: false
---

Prelude
-------

Yes, I know Wayland has made some controversial design choices. The fact is, Wayland is the only viable X11 successor, which will hopefully bring more security and stability to the Linux desktop. Regardless of how it pans out, there's nothing like a bit of competition to drive innovation. I won't discuss any more politics in this post.

Also a disclaimer: I'm no systems programming expert (though I aspire to be), neither am I an expert in X11, Wayland, or their associated protocols or codebases. This post merely draws on my experiences as an end user that enjoys a highly customised workflow.

Background
----------

I've been a long time user of the [i3](https://i3wm.org/) window manager, but also peering over the fence at this hyped and somewhat controversial modern X11 replacement called Wayland. Every year or so I do some mad web searching to determine the state of Wayland and whether it would be feasible to port my workflow to it yet.

In May (~5 months ago at time of writing), I realized that Wayland had come a long way, and discovered [sway](https://github.com/swaywm/sway/), a window manager leading the charge and advertised as a drop in replacement for i3. I was hooked.

This will be a tragedy in 3 parts:

1.  the switch
2.  the trial
3.  the switchback

followed by my answer to the question: are we Wayland yet?

The Switch
----------

Sway advertises itself as "i3-compatible". So it should be as easy as:

```
sudo pacman -S sway mkdir ~/.config/sway/ cp ~/.config/i3/config ~/.config/sway/ sway # instead of startx 
```

Not quite.

### Sway vs i3 config

So the major difference from i3/X11 is that that Wayland is more restrictive with what can interact with it, so Sway must directly manage things like displays, keyboard layouts, dpms, mouse cursor, etc. So config for these must be added to the sway config. I actually enjoyed this. It was more declarative and felt less hacky than playing with a bunch of X11 utilities. The downside is that none of that is portable; if you want to switch window managers, you must then hope that window manager implements support for configuring all this.

The config was in fact very close to being 100% i3 compatible. There was a [bug](https://github.com/swaywm/sway/issues/4216) that meant fullscreen scratchpads had to be implemented differently than for i3. It's behaviour is now closer to i3, but in my testing, isn't 100% the same.

### Wayland specific apps

Next was replacing everything else that was X11 specific from my workflow. This meant:

*   maim → slurp and grim (screenshots)
*   i3lock → swaylock (screen locking)
*   i3-msg → swaymsg
*   i3status → swaybar
*   redshift-gtk → redshift-wlr-gamma-control-git (red tinted screen)
*   xclip/xsel → wl-clipboard (no clipboard history software yet!)
*   dunst → mako (desktop notifications)
*   rofi → bemenu (popup fuzzy selector)

### All the other apps

On to general applications. Wayland has xwayland, which somehow provides mini embedded X server(s) for GUI apps that don't support wayland yet. I kept this disabled when switching, going for the "pure" Wayland experience.

The trial
---------

### XWayland

So the pure Wayland experience didn't last long. I soon discovered that many many apps either only supported X11, or crashed on Wayland. List of notable apps that required XWayland to work:

*   Anki (I checked more recently, and it works fine on pure Wayland now though)
*   Chromium
*   Insomnia
*   Virtualbox
*   Zoom

It appears that GTK and QT, the two most popular window toolkits, are still under heavy development to support Wayland fully.

Many apps also default to using XWayland if available unless forced to use Wayland through environment variables. I ended up forcing everything through Wayland globally, and individually unsetting the env vars for apps that didn't work with wayland. For example, I had this in my zshenv:

```
export MOZ_ENABLE_WAYLAND=1 export QT_QPA_PLATFORM=wayland-egl export GDK_BACKEND=wayland export CLUTTER_BACKEND=wayland export XDG_CURRENT_DESKTOP=Unity 
```

And various scripts that looked like:

```
#!/bin/bash unset QT_QPA_PLATFORM exec /usr/bin/zoom "$@" 
```

### Nice things

[Waybar](https://github.com/Alexays/Waybar/) was a very nice status bar. It was a bit on the heavy side, and had some bugs (issues with displaying the tray, crashes at times with various modules), but apart from that was very nice. It was easily stylable with CSS, came with sane defaults, plenty of modules and support for custom modules. My favourite feature was the [idle inhibitor](https://github.com/Alexays/Waybar/wiki/Module:-Idle-Inhibitor): a button on the bar to disable the screen idle (eg. to stop the screen turning off while watching a film). The best X11 equivalent appears to be the corners feature of xautolock (please let me know if there is a better way for X11!). The system tray only supports the appindicator type; most apps now support this, but something to note.

In general, things gave off the vibe of being more modern and designed more cohesively. Maybe it was how nicely Sway, Waybar, and related config (displays, peripherals, auto screenlocking) work out of the box. Maybe it was just an intangible feeling. I'm probably biased after reading about Wayland's design choices and how it aims to improve over X11 from technical and security points of view though… Take this as anecdotal evidence with a pinch of salt.

Most things worked perfectly, or well enough to overlook faults. After a week or two to settle in, I started to feel right at home knowing I was happy with about the same workflow and knowing I was running the latest in Linux desktop innovation.

So what happened…?

### Not so great

So, some things just didn't work nicely. The type of not nice that one consistently notices. The tiny little annoyances that you think you can overlook, but you never can.

I had consistent font rendering issues. There was this [painful issue](https://github.com/swaywm/sway/issues/4198) in sway relating to display scaling that caused fonts (among other things) to be missing, fuzzy, or just terrible in general. Thankfully these have been since fixed (mostly). Fonts in XWayland weren't as crisp as in windows rendered with Wayland - I put that down to display scaling issues too. I should mention I run 27" 4K monitors which isn't quick big enough for perfect 2x scaling, but way too small for 1x, forcing me to run with a fractional scaling, which isn't polished yet. YMMV.

Firefox on Wayland is so close. I would love to say it's perfect, but it isn't quite there yet. Mozilla have a [tracking issue](https://bugzilla.mozilla.org/show_bug.cgi?id=635134) for Wayland support, which is very active. At the time of writing, I still notice some minor issues, such as the Alt key isn't registered (which prevents use of some shortcuts) and context menus sometimes glitch. +1 to the Firefox team for their persistent work! Hopefully in a year or two (or sooner?) it will actually be perfect.

NetworkManager GUI tools were strangely buggy with wayland. It wouldn't always crash, but sometimes the only way I could get it to connect to a wifi network was to quit sway, launch i3, connect with nm-applet in i3, then switch back to sway. Bizarre.

Sometimes, on my desktop, everything would lock up for 10 seconds or so, the screen would blank, and then come back on and everything would be fine. It appeared to be some issue with the graphics drivers - I don't have that issue on i3, so something deep in Wayland is interacting strangely with it. ¯\\\_(ツ)\_/¯

### Actually really not good

These were ultimately the dealbreakers for me.

Screen recording or sharing apps just don't work. Zoom with XWayland _appeared_ to work, but in reality only shared a blank screen. This was kind of a deal breaker, because sooner or later I will need to use screen sharing in Zoom for work.

Sometimes, Sway would crash while the screen was locked, leaving my previously secured computer at a logged-in tty. Not great for security! I blame this on tracking git master for Sway and most other Wayland apps. I started with running stable releases, but soon switched to tracking git master to get fixes for other issues.

The switchback
--------------

So finally, about a week ago, I realized I needed to switch back to i3. The little annoyances and knowing that screensharing wouldn't work tipped me over the edge after 5 months. Note that I was a fairly contented user for 5 months, so Wayland/Sway wasn't _that_ bad.

I diffed my Sway and i3 config and ported back any recent changes. I also searching through my entire dotfiles for instances of wl-copy, wl-paste, and other wayland-specific tools. I edited them all where possible so they would work the same on Wayland or X11. Now my dotfiles has several instances of

```
# bash if [ -n "$WAYLAND_DISPLAY" ]; then # Wayland things else # X11 things fi 
```

and

```
# python if 'WAYLAND_DISPLAY' in os.environ: # Wayland things else: # X11 things 
```

### Things I brought back

I learnt a lot during my time on Wayland. Some config and workflow changes I ported back to my i3 config. Things like removing the clipboard manager. I realized I preferred entrusting data I didn't want to lose to a scratchpad, notes, and basically anywhere that was less ephemeral than a clipboard. Clipboard history is nice, but I found I was relying on it too much. Also I can't accidentally log passwords and keys to disk after copying them from a password manager… So I removed it. There were two reasons I used a clipboard manager: keep around things I wanted in my clipboard frequently (email address, various numbers, etc.) and record some interesting things I copied. Now I use a script to quickly find and copy common snippets for the former, and make more notes and use of scratchpad txt files for the latter.

xcape didn't work in Wayland, so instead of overloading capslock to ctrl and escape, I just use it for ctrl, and use or in Vim instead of reaching for escape. This is now ingrained and I can't be bothered re-re-training my muscle memory.

There are probably many other small things that I have brought back from Wayland, or that I enjoyed and are now part of my workflow. However, I probably won't remember without analyzing the changes to my config over the last 5 months…

### What did this achieve?

Some final notes on what I felt was achieved out of this whole experience, so I don't look back and think it was a waste of time:

*   I discovered that Wayland is finally a viable X11 competitor and worthy of being taken seriously.
*   I also discovered that the Wayland community is very active, responsive, and with great development speed (do not underestimate enthusiastic developers and users!).
*   My configuration and scripts are more portable now.
*   I have a greater understanding and intuition of the practical differences between Wayland and X11
*   I was able to be a guinea pig for several Wayland apps, and hopefully help the cause by reporting issues on the appropriate GitHub issue trackers.
*   [Ranger/rifle](https://github.com/ranger/ranger) now has Wayland support (clipboard and launching GUI apps on pure Wayland)!

So, are we Wayland yet?
-----------------------

I wish I could say yes. Everything is _so close_! There are many developers working hard to bring full support and stabilize everything. Unfortunately, I need to say that we're not quite Wayland yet.

I'll be back in a year or so to check out the landscape as always. I plan on maintaining my Sway configuration in parallel with i3, so I can easily check it out in future.

### Recommendations

If your use cases don't involve uncommon display configuration, screensharing, desktop automation/scripting (note that I don't use this; but it is a common limitation discussed about Wayland), you're ok with some rough edges, and keen to help advance Wayland development, then by all means Wayland is here and worthy of a look.

If you require advanced desktop scripting or other niche use cases, then Wayland probably won't be ready for a long time.

Likewise, if you prefer stability and knowing that standard X11 GUI apps will just work, then Wayland probably isn't ready for that yet either. Do come back for a look in a year or so though, because it is likely to be ready very soon!

2019-10-23 addendum
-------------------

One point that I totally forgot about, but is now painfully apparent now that I'm back on X11, is screentearing. On Wayland, screentearing is a thing of the past. Everything was so smooth, flicker-free, and tear-free. Now I need to mess around tweaking compositors to get a nice experience on X11 (i3)… So that's a big plus for Wayland.

  
  
from Hacker News https://ift.tt/2IRhWKC