---
title: 'Emacs: Abbrev Mode Tutorial'
date: 2019-10-12T04:23:00+01:00
draft: false
---

Emacs: Abbrev Mode Tutorial
===========================

By Xah Lee. Date: 2010-09-29. Last updated: 2018-06-20.

Emacs's abbrev feature lets you type a short word and expand into a full word or code template.

For example:

*   `bg` → `background`
*   `fed` → `find . -depth -empty -type d`
*   `f` → `function f () { return 3; }`
*   `hrt` → `♥`

Alt+x `abbrev-mode` to turn it on. Call again to turn off.

To turn on globally when emacs starts, put this in emacs init:

```
(setq-default abbrev-mode t)
```

Define Abbrev
-------------

Suppose you want to define “bg” → “background”.

1.  Type “background”.
2.  Alt+x `add-global-abbrev` 【Ctrl+x a g】, in the prompt, type “bg”.

Now, when you type “bg” followed by a space or return, it'll expand to “background”.

If you want the abbrev only for the current major mode,

Alt+x `add-mode-abbrev` 【Ctrl+x a l】 → Define abbrev for current mode.

If the expanded text is more than one word, for example, suppose you want to define “faq” → “frequently asked questions”.

1.  Type “frequently asked questions”.
2.  Select the text.
3.  Alt+x `universal-argument` 【Ctrl+u】, type “0”.
4.  Alt+x `add-global-abbrev` 【Ctrl+x a g】, in the prompt, type “faq”.

Undefine Abbrev
---------------

To remove a definition, give a negative argument to `add-global-abbrev` or `add-mode-abbrev`.

For example, to undefine the abbrev “bg”.

1.  Alt+x `universal-argument` 【Ctrl+u】, type “-1”.
2.  Alt+x `add-global-abbrev` 【Ctrl+x a g】, in the prompt, type “bg”.

Save Abbrev
-----------

When you quit, emacs will ask you if you want to save.

Put this in emacs init to auto save:

```
(setq save-abbrevs 'silently)
```

Abbrev File Location
--------------------

The abbrevs is saved in a file at a path specified by the variable

abbrev-file-name

By default, it's at 〔~/.emacs.d/abbrev\_defs〕

You can change it, for example, put this in emacs init:

```
(setq abbrev-file-name "~/emacs\_abbre.el")
```

List Abbrevs
------------

Alt+x `list-abbrevs` → Display a list of defined abbrevs.

Edit Abbrevs
------------

You can edit abbrevs. This is the best way to add or remove abbrevs.

Alt+x `edit-abbrevs` to edit abbrev.

Emacs will display it like this:

![emacs edit abbrev 65513](http://ergoemacs.org/emacs/i/emacs_edit_abbrev_65513.png)

emacs edit abbrev screen.

The number in the middle column is the number of times you've used (expanded) the abbrev.

*   To remove a abbrev, just delete the line.
*   To add a abbrev, just add a line.

When done, to load and or save, call any of:

*   `edit-abbrevs-redefine` 【Ctrl+c Ctrl+c】 → Redefine abbrevs according to current buffer contents.
*   `abbrev-edit-save-buffer` 【Ctrl+x Ctrl+s】 → Redefine and save to abbrev file.
*   `abbrev-edit-save-to-file` 【Ctrl+x Ctrl+w】 → Redefine and save to abbrev file, but ask for new location.

Abbrev Example
--------------

You can use abbrev for:

*   Long English words, e.g. “comm” for “communication”.
*   Programing language function templates.
*   emoji, such as “omg” for 😂
*   math symbols such as “ra” for →
*   Templates, such as license header.
*   Address, url, telephone number, company name, etc.

I have about 8 hundred abbrevs from all modes. Here's a example:

```
"zin" 0 "∈" "znin" 0 "∉" "zinf" 0 "∞" "zluv" 0 "♥" "zsmly" 0 "☺" "zme" 0 "someone@example.com" "zwp" 0 "Wikipedia" "zms" 0 "Microsoft" "zg" 0 "Google" "zit" 0 "IntelliType" "zmsw" 0 "Microsoft Windows" "zwin" 0 "Windows" "zie" 0 "Internet Explorer" "zahk" 0 "AutoHotkey" "zalt" 0 "alternative" "zchar" 0 "character" "zdef" 0 "definition" "zbg" 0 "background" "zkb" 0 "keyboard" "zex" 0 "example" "zkbd" 0 "keybinding" "zenv" 0 "environment" "zvar" 0 "variable" "zev" 0 "environment variable" "zcp" 0 "computer" "zxl" 0 "Xah Lee" "zuxl" 0 "http://xahlee.info/" "zd" 0 "\\\\(\[0-9\]+?\\\\)" "zstr" 0 "\\\\(\[^\\"\]+?\\\\)\\"" "zf" 0 "find . -type f -size 0 -exec rm {} ';'"
```

I put “z” in the beginning of my abbrevs. This way, i don't have to worry about clash with short words that i don't want to expand.

Manual Load/Save Abbrev File
----------------------------

*   `read-abbrev-file` → Read abbrev definitions from file written with \`write-abbrev-file'.
*   `write-abbrev-file` → Write all user-level abbrev definitions to a file of Lisp code.

Emacs Abbrev Frequently Asked Questions
---------------------------------------

### Make Abbrev Not Add Space

How to make abbrev not add the space?

Define this function:

```
(defun xah-abbrev-h-f () "Abbrev hook function, used for \`define-abbrev'. Our use is to prevent inserting the char that triggered expansion. Experimental. the “ahf” stand for abbrev hook function. Version 2016-10-24" t) (put 'xah-abbrev-h-f 'no-self-insert t)
```

And for each of the abbrev that you don't want space added after expansion, add the function there as third argument, like this:

```
(define-abbrev-table 'global-abbrev-table '( ("addr" "address" xah-abbrev-h-f) ))
```

  
  
from Hacker News https://ift.tt/2nFTILZ