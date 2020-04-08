---
title: 'A phonetic writing system based on cellular automata (2011)'
date: 2019-10-21T02:47:00+01:00
draft: false
---

In thinking about how to bridge the world of ideograms with the world of alphabets, I began thinking about how cellular automata perform fairly complex operations over time. The starting state of a cellular automaton with a known ruleset contains all the information necessary to produce all further states. So, I figured that a description of a state in some simple known system of cellular automata may, given a well-defined stopping state, both stand in for the word and guide the reader in its pronunciation, without merely being a phonetic representation devoid of non-phonetic content.

As a proof of concept, I considered the ruleset of otomata, remapped onto a new grid and with a slight change in rules. The grid is five by five, and there are five possible cell states: one for each of the primary orientations (up, down, left, right) and one for blank. At a constant rate, cell states indicating directions (denoted by arrows) move across the grid in the direction specified. If at any step a cell is required to be in two states (which is to say that two arrows collide) the cell in which the collision takes place is evaluated as a sound and pronounced, and the state of that cell is set to blank.

This is a fairly irritating thing to try to phrase in english, so I will give an example.

Here is a blank grid:

Here is a glyph:

On the first step, the arrow currently located at te and the arrow currently located at ka collide at ta, the arrow located at mo moves to mi, and the arrow located at si moves to si. So, the first syllable is 'ta'.

\>td><

On the second step, the arrows located at si and mo collide at mi. So, the second syllable is 'mi'. All remaining cells are blank, so this glyph is pronounced 'tami'.

As for some way to quickly write these glyphs, I figured that the easiest thing to do was to put lines on both sides of the arrow heads and have meeting or intersecting lines for each blank position. So, in ascii, the above might be represented as:

+<+-+^+|+||+v+||+|+|+-+-<

  
  
from Hacker News https://ift.tt/2BulBtG