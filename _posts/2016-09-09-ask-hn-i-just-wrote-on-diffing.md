---
title: 'Ask HN: I just wrote an O(N) diffing algorithm – what am I missing?'
date: 2019-10-29T01:47:00+01:00
draft: false
---

  
  
from Hacker News https://ift.tt/34aAKfQ

Hey folks,

I've been building a rendering engine for a code editor the past couple of days. Rendering huge chunks of highlighted syntax can get laggy. It's not worth switching to React at this stage, so I wanted to just write a quick diff algorithm that would selectively update only changed lines.

I found this article: https://ift.tt/2lIuVkG

With a link to this paper, the initial Git diff implementation: https://ift.tt/1GF9uI8

I couldn't find the PDF to start with, but read "edit graph" and immediately thought — why don't I just use a hashtable to store lines from LEFT\_TEXT and references to where they are, then iterate over RIGHT\_TEXT and return matches one by one, also making sure that I keep track of the last match to prevent jumbling?

The algorithm I produced is only a few lines and seems accurate. It's O(N) time complexity, whereas the paper above gives a best case of O(ND) where D is minimum edit distance.

```
 function lineDiff (left, right) { left = left.split('\n'); right = right.split('\n'); let lookup = {}; // Store line numbers from LEFT in a lookup table left.forEach(function (line, i) { lookup[line] = lookup[line] || []; lookup[line].push(i); }); // Last line we matched var minLine = -1; return right.map(function (line) { lookup[line] = lookup[line] || []; var lineNumber = -1; if (lookup[line].length) { lineNumber = lookup[line].shift(); // Make sure we're looking ahead if (lineNumber > minLine) { minLine = lineNumber; } else { lineNumber = -1 } } return { value: line, from: lineNumber }; }); } 
```RunKit link: https://ift.tt/2MTFXmv

What am I missing? I can't find other references to doing diffing like this. Everything just links back to that one paper.