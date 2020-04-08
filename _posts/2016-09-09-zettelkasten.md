---
title: 'Zettelkästen?'
date: 2019-10-11T02:48:00+01:00
draft: false
---

Not a great word, is it? Neither is its most typical English translation: “slip-box.” In German, it refers to a box for holding index cards. Despite how it sounds, I’m finding it a surprisingly good tool for tracking information and thinking.

Some brief googling, at least if your German is as bad as mine, will make it sound like a system of note-taking, with heavy linking between notes. My first thought (like many other people’s) was: Hang on, isn’t that just a wiki? But no, it’s more than a wiki — though it can be implemented in one.

Basically it’s a methodology for **thinking in writing**, developed by German sociologist [Niklas Luhmann](https://en.wikipedia.org/wiki/Niklas_Luhmann). It combines note-taking while reading, a bibliographic system, and a separate system of heavily linked individual thoughts. He dreamed the whole thing up on paper between the 1950s and his [death](https://www.independent.co.uk/arts-entertainment/obituary-professor-niklas-luhmann-1187758.html) in the 1990s, with over 100,000 index cards. He credits the system for his productivity — he wrote some seventy books along the way — though nobody took this claim too seriously until the formidable collection began to be [put online](https://niklas-luhmann-archiv.de/bestand/zettelkasten/inhaltsuebersicht#ZK_1_editor_I_45-11) (auf Deutsch, natürlich, though a few have translations) in the past few years. That project is planned out to [2030](https://niklas-luhmann-archiv.de/bestand/zettelkasten/auszuege).

Most of the writing about him and his system remains in German. The primary English resource is Sönke Ahrens’ book [_How to Take Smart Notes_](https://amzn.to/2Mv5nW2) (2017). It describes Zettelkästen as being **akin to GTD, but better suited to knowledge work**.

The book views academic/knowledge work as exploratory, in contrast to business, to which GTD is better suited because of business’ tendency towards pre-defined objectives. In that sense, you might say that Zettelkästen is to a wiki what GTD is to a todo list. Both are different ways of thinking about a rather flexible (potentially misused?) underlying tool.

I’ve had a go at implementing it in software, using [Gollum](https://github.com/gollum/gollum) (a git-based markdown wiki). The book also inspired me to try out the excellent [Zotero](http://zotero.com) (an open-source research tool) which is drastically better than my Goodreads/Workflowy hackjob for tracking my thoughts on books.

Although everyone seems to get hung up on Luhmann’s system of numbering and lettering items to link them together, that really doesn’t seem to matter all that much. Here’s how it differs from typical wiki usage:

*   Each “zettel” (aka note) can only contain a single thought. For index cards, that’s a limitation of its physical size. But software encourages short entries too, as well as the branching/splitting of zettels. This makes it unlike a Wikipedia page, which is more like a book chapter or article. You could think of Wikipedia articles as being molecular; zettel entries are atomic.
*   There is no automatic central index, and you refer to zettels by arbitrary slugs. You have to link things up as you think of them, manually, in both directions. You either have to search or traverse the tree a lot. This is by design and provides a lot of the benefits.
*   Massive interlinking. Of course Wikipedia does this too, but it’s interesting how manually maintaining links between single thoughts seems to accelerate lateral thinking and insights.
*   It’s intended to work similarly to your brain, and therefore Luhmann himself viewed using it as more like having a conversation with another consciousness than tool use. There’s a strong emphasis on _serendipity_ of connections.
*   The size limit encourages the recording of inchoate thoughts, to be developed by their relationships. If they’re not linked strongly enough, they may be lost forever in the network. (Less likely in software, but still possible, if you forget to link/search. Also sounds sort of like your brain, doesn’t it?)
*   All this facilitates and encourages thinking directly in writing, so that the thought can be dropped totally, and resumed exactly as it was, picking up the thread from whatever zettel you left it in, regardless of how far you have developed the thinking.
*   There is a strong focus on spatially arranging the zettels in order to write papers or books.

If you’re not up for reading the whole book mentioned above (which is a bit long for what it is, though still probably the best English resource), there are a few other things online:

*   Here’s a [LessWrong post](https://www.lesswrong.com/posts/NfdHG6oHBJ8Qxc26s/the-zettelkasten-method-1) that describes it (including the insight “I honestly didn’t think Zettelkasten sounded like a good idea before I tried it” which I also felt).
*   Here are two translations of [Luhmann’s own brief essays](http://luhmann.surge.sh).
*   There is also a Zettelkasten [blog](https://zettelkasten.de/), begun in 2013, and therefore somewhat intimidating to navigate; probably best to start with the [overview](https://zettelkasten.de/posts/overview/).

I’d be really interested to hear if you try it.

  
  
from Hacker News https://ift.tt/2p39ocy