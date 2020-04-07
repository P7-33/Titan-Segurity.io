---
title: 'Play That Funky 3D Printer…'
date: 2020-01-19T13:14:00+01:00
draft: false
---

Human brains are wired for music. Scientists think the oldest musical instruments were flutes that date back somewhere between 67,000 and 37,000 years ago. We assume though that people were banging on wood or their thighs, or knocking two rocks together long before that. Almost anything can be a musical instrument. A case in point: \[elifer5000\] walked into a room containing a lot of running 3D printers, and though it seemed musical. Next thing you know, he harnessed [3D printers as a MIDI instrument](https://www.instructables.com/id/Printesizer-a-3D-Printer-Synthesizer/).

At a hackathon, he found some software that converts a MIDI file to GCode. The only problem is a common printer has three axes and, therefore, can only produce (at most) three notes at once. The obvious answer to this problem is to use more printers, and that’s what he did, as you can see below.

Apparently the speed the stepper motor moves is proportional to the pitch of the tone it emits. Of course, the distance of travel at a given speed corresponds to how long the tone will endure. Given that, it is a pretty simple math problem to figure out the parameters of the note.

Common printers have a slow Z axis, so the final product only uses the X and Y axis on each printer. That means you might even be able to use a CNC machine or a plotter as part of your printer orchestra.

One problem arose when trying to handle a MIDI file in realtime. When you start a note, you don’t know how long it will last. You will only know the note has ended when it stops. That makes sense when you remember that a MIDI keyboard won’t know how long you will press a key when you first push on it. The code uses a small “micronote” of 50 milliseconds and plays it until the stop signal arrives.

The Python code takes a bit of calibration because every printer is a little different. The result is — as you might expect — a bit electronic, but pleasing enough and sure beats two rocks. We’ve seen music played on [floppy drives](https://hackaday.com/2014/01/05/the-most-beautiful-floppy-disk-jukebox-ever/) and hard drives before. Or, you can go the other way and use [a hard drive as a microphone](https://hackaday.com/2019/03/13/hackers-turn-hard-drive-into-microphone-that-can-listen-in-on-your-computers-fan-whine/).

  
  
from Hackaday https://ift.tt/2NFzXO9  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)