---
title: 'Reverberations: An 8-bit approach to J.S. Bach'
date: 2020-01-21T05:53:00+01:00
draft: false
---

About the music
---------------

### 01\. Toccata and Fugue in D minor

_Two 6581 chips._

The toccata is perhaps the most well-known work in the entire organ repertoire. Like many toccatas, it is probably a transcribed improvisation. It has been postulated that this was a test tune that Bach would play when trying out new organs. That would explain its crude character and the various hops between heavy chords and rapid melodic parts.

The [fugue](http://wikipedia.org/wiki/Fugue) is written for four voices, and the subject resembles a passage in the toccata.

### 02\. Ich ruf' zu dir, Herr Jesu Christ

_One 6581 chip._

This is a chorale prelude from _Orgelbüchlein_. The chorale itself is a very simple melody, so the praxis is to embellish it with trills and other ornaments. Thus, my interpretation will be different from other recordings you may have heard.

This piece of music was featured in Tarkovsky's film _Solaris_.

### 03. Contrapunctus 1 from Die Kunst der Fuge

_Two 8580 chips._

_Die Kunst der Fuge_ is a terribly clever suite of fourteen fugues and four canons, of increasing complexity, all based on the same theme. This is the first piece in the suite, so it is a comparatively simple four-part fugue.

### 04\. Allein Gott in der Höh' sei Ehr'

_Two 6581 chips._

Bach has based at least ten different works on this melody (BWV numbers 662, 663, 664, 675, 676, 677, 711, 715, 716, 717), presumably quite varying in style and harmonic content. This version is a chorale prelude.

### 05. Passacaglia and Fugue in C minor

_Two 8580 chips._

The grand finale!

A passacaglia is based on a short melody which is repeated throughout the piece, mostly in the bass, sometimes with variations. In classical music, this type of prolonged repetition of a single theme is called an _ostinato_. In contemporary music, it's not called anything at all, because it is implied.

The fugue is quite advanced. The subject is the first half of the ostinato from the passacaglia. Everytime the subject sounds, two counter-subjects can also be heard (except in the very beginning of the fugue), while the fourth voice joins the others in free counterpoint. These four roles — playing the subject, playing the first counter-subject, playing the second counter-subject and playing free counterpoint — can be distributed among the four voices in 24 different permutations. This happens eleven times throughout the fugue, and Bach picks a different permutation every time according to a mathematical formula. Can you find it?

About the technology
--------------------

It struck me that, at least in theory, organ pipes should generate quite primitive sound waves. If so, how come a church organ doesn't sound like a chip tune, which is also built up from simple waveforms? Well, actually it will, if you remove the church. And if you connect a Commodore 64 home computer to a loudspeaker in a large hall, it will sound like an organ.

So the music on this album is not performed on a pipe organ. Instead, what you hear is the sound of one or two [SID chips](https://www.linusakesson.net/music/sidstuff/index.php) (controlled by a Commodore 64), enhanced by a [convolution reverb](http://wikipedia.org/wiki/Convolution_reverb) to simulate church acoustics.

### Quantization

There is already an abundance of SID tunes based on sheet music, in particular by J. S. Bach. The problem is that all those SID tunes are terrible. Apparently, people have merely typed in the notes from the sheet music. This leads to quantized timing (where e.g. every quarter note lasts exactly 500 milliseconds, always), and while quantized timing may be perfectly fine for modern genres, it simply won't do for classical music.

The goal is not to play the right notes in the right order; that's the starting point. Then you have to adjust the timing of every single note, listening and re-listening, making sure that it doesn't sound mechanical. You have to add movement, energy, and emphasis (which, on an organ, has to be implemented by varying the duration of the notes, and the pauses between them, because there's no dynamic response). You need fermatas and ornaments. You have to realize that some jumps cannot be performed unless the organist lifts his hand, and so on, and so forth.

This album is an attempt to demonstrate that classical music can indeed be performed by a computer. But the amount of work that goes into programming the computer will never be less than the work that a traditional performer would put into studying the same piece of music.

Registration
------------

In general, I've opted for fixed-width pulse waves for the manual voices, and a pulse hard-synced with a triangle wave one octave below for the pedal voice. Some waveforms are run through a combined low-pass and band-pass filter with moderate resonance. In _Allein Gott_ and _Ich ruf zu dir_, I use a narrow pulse wave for the cantus firmi and unfiltered triangle waves for the accompaniment.

### Discuss this page

Disclaimer: I am not responsible for what people (other than myself) write in the forums. Please report any abuse, such as insults, slander, spam and illegal material, and I will take appropriate actions. Don't feed the trolls.

Jag tar inget ansvar för det som skrivs i forumet, förutom mina egna inlägg. Vänligen rapportera alla inlägg som bryter mot reglerna, så ska jag se vad jag kan göra. Som regelbrott räknas till exempel förolämpningar, förtal, spam och olagligt material. Mata inte trålarna.

Anonymous  
Thu 17-Jul-2008 06:32

This is amazing. Congrats on your work.

Anonymous  
Sun 20-Jul-2008 21:09

Can't wait to see this performed live!

Anonymous  
Wed 23-Jul-2008 11:46

Haha. En cyborgel! :)  
  
Riktigt coolt.

Anonymous  
Wed 30-Jul-2008 04:40

Great, Great, Great. Congratulations for this.

Anonymous  
Mon 4-Aug-2008 02:12

Helt fantastisk rättvisa åt musiken, undras om man kan få låna domkyrkan en natt för att uppnå perfekt rumstemporal spridning och spela in alltsammans där? Linus Walleij

Anonymous  
Sat 9-Aug-2008 14:01

Mycket bra genomfört! Jag har spelat de flesta av dessa verken på just kyrkorgel, och håller kanske inte med om all interpretation, men det är ju givetvis personligt. Ljudet är fantastiskt bra! /F. Segerfalk aka Moppe

Anonymous  
Thu 11-Sep-2008 11:21

I find it unfortunate that you didn’t also put up unprocessed files – that would have been extremely interesting.  
  
Still though, this is really awesome. Thanks for sharing.  
  
—ap

Anonymous  
Fri 12-Sep-2008 02:11

I'm assuming this uses modern equal temperament? \[half step up = x \* 2^(1/12) \]  
  
You should experiment with some temperaments that were popular during Bach's time.  
  
\-Andy

Anonymous  
Fri 12-Sep-2008 13:03

\> Well, actually it will, if you remove the church.  
  
I'm still laughing at this :-)  
  
The result is impressive. Thanks man.  
  
Pygy

Anonymous  
Sat 13-Sep-2008 04:33

This is lovely. Thank you very much for sharing. Of course I too would like to play with the original files, but I'm glad you've seen fit to share even the MP3s. Do we have a license to copy them around as well?

Anonymous  
Sat 13-Sep-2008 04:56

This is lovely. Thank you very much for sharing. Of course I too would like to play with the original files, but I'm glad you've seen fit to share even the MP3s. Do we have a license to copy them around as well?

Oops, forgot to sign that — I'm Kragen Javier Sitaker, kragen@canonical.org.

**lft**  
Linus Åkesson  
Tue 16-Sep-2008 22:04

I'm assuming this uses modern equal temperament? \[half step up = x \* 2^(1/12) \]  
  
You should experiment with some temperaments that were popular during Bach's time.  
  
\-Andy

That's an excellent suggestion. Thanks!

**lft**  
Linus Åkesson  
Tue 16-Sep-2008 22:06

This is lovely. Thank you very much for sharing. Of course I too would like to play with the original files, but I'm glad you've seen fit to share even the MP3s. Do we have a license to copy them around as well?

Oops, forgot to sign that — I'm Kragen Javier Sitaker, kragen@canonical.org.

Yes, do copy them around. Sharing is caring.

Anonymous  
Mon 20-Oct-2008 23:39

This is most impressive, great work!  
\-- Jonas Norberg

Anonymous  
Mon 13-Apr-2009 22:08

Great idea and great interpretation :)

Anonymous  
Mon 13-Apr-2009 22:49

shocking.

Anonymous  
Sun 25-Jul-2010 19:42

impressive indeed, I hope you'll do some equivalent played LIVE with your chippophone (and with either the spring-reverb box put back in.. or a real church around) :)  
  
\-barzoule

Anonymous  
Sat 7-Aug-2010 00:03

Wow. Just wow. This will go together just great with the Wendy Carlos stuff and the Brad Smith 8-bit version of "Dark Side of the Moon" I've been listening to recently. Also loved your YouTube clips featuring the Chipophone. Keep it up, Linus. The world needs nerds like you! :D  
  
Ben, from Germany

Anonymous  
Fri 24-Sep-2010 00:37

Promise me that one day you will demonstrate this live. I might even learn Swedish and fly to Sweden to witness it. I am in awe.....

Anonymous  
Fri 24-Sep-2010 00:41

Thinking about it, the one part of the acoustics of the organ you're missing is that every pipe is in a different location, so affected differently by the room.  
  
Theoretically speaking, if you were to try it live, you could have seperate amplification for each chip, split into bands using several band-pass filters, and then individual speakers each representing a bundle of related pipes.  
  
But I'm thinking too much now, amn't I?

**lft**  
Linus Åkesson  
Fri 8-Oct-2010 09:25

Thinking about it, the one part of the acoustics of the organ you're missing is that every pipe is in a different location, so affected differently by the room.  
  
Theoretically speaking, if you were to try it live, you could have seperate amplification for each chip, split into bands using several band-pass filters, and then individual speakers each representing a bundle of related pipes.  
  
But I'm thinking too much now, amn't I?

How can thinking too much ever be a problem? =)

Anonymous  
Thu 29-Nov-2012 21:44

I just recently found this ( Via the Chipophone, again, of course ) and I must say that it's a very well done reinterpretion, especially compared to the Midi versions I have heard so far, which appear to be directly transcribed notes without much else.  
  
//D.S.

**Alex-BK**  
Mon 6-Nov-2017 13:35

Cool! But sounds more like 60's Farfisa electronic organ in medium size church!

Anonymous  
Sat 20-Oct-2018 04:30

This is wonderful, but it seems like a missed opportunity to use some kind of adaptive just temperament to make the intervals more pleasing. It seems to me that the pure tones here really bring out the weaknesses of equal temperament.

  
  
from Hacker News https://ift.tt/37cRaGD