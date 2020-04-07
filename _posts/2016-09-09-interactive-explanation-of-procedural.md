---
title: 'Interactive explanation of a procedural music system'
date: 2020-01-13T01:17:00+01:00
draft: false
---

Announcement

Technical

Graphics

Music

This article is an in-depth interactive explanation of how the procedural music in The Sapling works. Furthermore, we see how I had to give up my preference for clear hummable melodies, but got my way in the end.

The arrow button above plays a short excerpt of what the music in The Sapling sounds like. I hesitated a long time before I settled on this musical style. Normally, I prefer memorable, hummable melodies over soundscapes, but for The Sapling I couldn't figure how this would work. This was mainly for two reasons: firstly, every melody I came up with didn't really seem to match with the rest of game's style. Many other simulation games feature either jazzy (like SimCity) or bright and jumpy (Equilinox, Planet Coaster) soundtracks, but both styles somehow seemed to clash with a more serious game about nature. Secondly, I was afraid that I simply would not be able to come up with enough material, meaning that the same melodies would be repeating over and over.

* * *

I was afraid that I simply would not be able to come up with enough material, meaning that the same melodies would be repeating over and over

* * *

The solution came from an unexpected direction: during experimentation with ambient background music to get into a more productive programming mood (which by the way didn't work for me), I noticed that ambient music videos on Youtube often used a slideshow of pretty nature photos as 'background visuals'. Would it also work the other way around? If nature makes a good background visual for ambient music, is ambient music good background music for nature visuals?

Accepting this - and thus giving up hummable melodies in favor of long slow 'ambient' notes to evoke a relaxed feeling in the listener - was a slow process, but ultimately lead to a second discovery: a lot of ambient music rarely changes chords. Instead, all notes throughout the whole song are from the same musical scale. This is convenient, because a general (and oversimplified) rule of thumb is that two pieces of music that use notes from the same musical scale are likely to sound good together. Creating an ambient sounding soundtrack could simply be a matter of creating a large pool of musical fragments that only use notes from the same scale, and mixing them at random. How well this works is exemplified by the project [In B Flat](http://inbflat.net) (which, as the name suggests, uses B Flat as this one scale).

* * *

Creating an ambient sounding procedural soundtrack could simply be a matter of creating a large pool of musical fragments that only use notes from the same scale

* * *

This idea solved my two problems in one go: (1) the genre of ambient music fit the game's feel and (2) I could endlessly combine small musical fragments, giving you a fresh sounding soundtrack every time. The result is available for you to play with below. Feel free to click some play buttons at random, and decide for yourself if you think they sound good together.

![](https://thesaplinggame.com/devlogs/music/quiet.svg)

Background

![](https://thesaplinggame.com/devlogs/music/quiet.svg)

Background

![](https://thesaplinggame.com/devlogs/music/quiet.svg)

Background

![](https://thesaplinggame.com/devlogs/music/quiet.svg)

Bass

![](https://thesaplinggame.com/devlogs/music/quiet.svg)

Bass

![](https://thesaplinggame.com/devlogs/music/quiet.svg)

Bass

![](https://thesaplinggame.com/devlogs/music/quiet.svg)

Color

![](https://thesaplinggame.com/devlogs/music/quiet.svg)

Color

![](https://thesaplinggame.com/devlogs/music/quiet.svg)

Foreground

![](https://thesaplinggame.com/devlogs/music/quiet.svg)

Foreground

![](https://thesaplinggame.com/devlogs/music/quiet.svg)

Foreground

![](https://thesaplinggame.com/devlogs/music/quiet.svg)

Foreground

![](https://thesaplinggame.com/devlogs/music/quiet.svg)

Victory

![](https://thesaplinggame.com/devlogs/music/quiet.svg)

Victory

My own conclusion, after playing with this for some time, was that although everything indeed sounded good together, some combinations were better for videogame background music than others. In the end, I identified five categories of fragments:

*   The background, with long, sleepy tones. These are what gives the music its ambient feel. Strings are the most typical example.
    
*   The foreground, played by a single instrument with short notes, grabbing the listener's attention. I most often use the piano or the celesta for this.
    
*   The color, which is somewhere in between: they are played by a single instrument, but use long notes. These give a bit of flavour to a background that would otherwise always sound similar. This can for example be a clarinet or a trombone.
    
*   The bass, often played by double bases or base clarinets.
    
*   Victory sounds, that temporarily grab the player's attention and give them a satisfactory feeling.
    

Furthermore, I discovered that using strings in _unisono with octave intervals_ (playing the low and high versions of the same note at the same time) worked quite well to give the mix a more epic feel. In the end, I used this together with the bass as the player is looking at his/her creations from a distance: as the player zooms out, the bass and _unisono_ fade in.

The button below categorizes the musical fragments above, and for the fragments in the background category adds an option to 'switch on' the epic version. If you make sure that for every category only one fragment is playing, you get something that could also be played in game.

One final question you might have is whether these musical fragments are completely random sequences of notes chosen by chance from a static scale. The answer is 'of course not': to satisfy my own desire for hummable melodies I actually did write a main theme for the game, and to give the game some musical coherence I echo parts of this theme in various fragments. This button below plays the main theme as you hear it in the main menu. Can you identify which of the musical fragments contain hints of this theme?

![](https://thesaplinggame.com/devlogs/music/quiet.svg)

And that's all there is to it! By the way, if you want to do more with these pieces of music, you can! Both [the individual fragments](https://thesaplinggame.com/static/procedural_music_pieces.zip) and [the layers of the main theme](https://thesaplinggame.com/static/separate_layers_main_theme.zip) are availale to be used in your own projects, as is the [sheet music](https://thesaplinggame.com/static/main_theme_sheet_music.pdf) for the main theme. See [this devlog](https://thesaplinggame.com/devlogs/playercontent.html) for more info on that.

Want more like this? I write articles like this roughly once per month; you can subscribe for email reminders below! If you want more fine-grained info on my game development work, there also is a [Twitter account](https://twitter.com/thesaplinggame).

Published Sunday 12 January 2020

  
  
from Hacker News https://ift.tt/2Njd6Il