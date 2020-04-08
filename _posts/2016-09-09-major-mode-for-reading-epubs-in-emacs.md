---
title: 'Major Mode for Reading EPUBs in Emacs'
date: 2019-11-02T09:32:00+01:00
draft: false
---

[](https://github.com/wasamasa/nov.el#novel)nov.el
==================================================

[![https://raw.github.com/wasamasa/nov.el/master/img/novels.gif](https://camo.githubusercontent.com/721e72577653ded4295ff4643c2df7c41426a1e6/68747470733a2f2f7261772e6769746875622e636f6d2f776173616d6173612f6e6f762e656c2f6d61737465722f696d672f6e6f76656c732e676966)](https://camo.githubusercontent.com/721e72577653ded4295ff4643c2df7c41426a1e6/68747470733a2f2f7261772e6769746875622e636f6d2f776173616d6173612f6e6f762e656c2f6d61737465722f696d672f6e6f76656c732e676966)

[](https://github.com/wasamasa/nov.el#about)About
-------------------------------------------------

`nov.el` provides a major mode for reading EPUB documents.

Features:

*   Basic navigation (jump to TOC, previous/next chapter)
*   Remembering and restoring the last read position
*   Jump to next chapter when scrolling beyond end
*   Renders EPUB2 (.ncx) and EPUB3 (
    
    ) TOCs
    
*   Hyperlinks to internal and external targets
*   Supports textual and image documents
*   View source of document files
*   Metadata display
*   Image rescaling

[](https://github.com/wasamasa/nov.el#screenshot)Screenshot
-----------------------------------------------------------

[![https://raw.github.com/wasamasa/nov.el/master/img/scrot.png](https://camo.githubusercontent.com/67def9936bc2fd262cc8e03bc0588dcd1922f9b4/68747470733a2f2f7261772e6769746875622e636f6d2f776173616d6173612f6e6f762e656c2f6d61737465722f696d672f7363726f742e706e67)](https://camo.githubusercontent.com/67def9936bc2fd262cc8e03bc0588dcd1922f9b4/68747470733a2f2f7261772e6769746875622e636f6d2f776173616d6173612f6e6f762e656c2f6d61737465722f696d672f7363726f742e706e67)

[](https://github.com/wasamasa/nov.el#installation)Installation
---------------------------------------------------------------

Set up the [MELPA](https://melpa.org/) or [MELPA Stable](https://stable.melpa.org/) repository if you haven't already and install with `M-x package-install RET nov RET`.

[](https://github.com/wasamasa/nov.el#setup)Setup
-------------------------------------------------

Make sure you have an `unzip` executable on `PATH`, otherwise the extraction of EPUB files will fail. If you for some reason have `unzip` in a non-standard location, customize `nov-unzip-program` to its path. You'll also need an Emacs compiled with `libxml2` support, otherwise rendering will fail.

Put the following in your init file:

```
(add-to-list 'auto-mode-alist '("\\\\.epub\\\\'" . nov-mode))
```

[](https://github.com/wasamasa/nov.el#customization)Customization
-----------------------------------------------------------------

While the defaults make for an acceptable reading experience, it can be improved with any of the following changes:

### [](https://github.com/wasamasa/nov.el#default-font)Default font

To change the default font, use `M-x customize-face RET variable-pitch`, pick a different family, save and apply. If you dislike globally customizing that face, add the following to your init file:

```
(defun my-nov-font-setup () (face-remap-add-relative 'variable-pitch :family "Liberation Serif" :height 1.0)) (add-hook 'nov-mode-hook 'my-nov-font-setup)
```

To completely disable the variable pitch font, customize `nov-variable-pitch` to `nil`. Text will be displayed with the default face instead which should be using a monospace font.

### [](https://github.com/wasamasa/nov.el#text-width)Text width

By default text is filled by the window width. You can customize `nov-text-width` to a number of columns to change that:

It's also possible to set it to `t` to inhibit text filling, this can be used in combination with `visual-line-mode` and packages such as `visual-fill-column` to implement more flexible filling:

```
(setq nov-text-width t) (setq visual-fill-column-center-text t) (add-hook 'nov-mode-hook 'visual-line-mode) (add-hook 'nov-mode-hook 'visual-fill-column-mode)
```

### [](https://github.com/wasamasa/nov.el#rendering)Rendering

In case you're not happy with the rendering at all, you can either use `nov-pre-html-render-hook` and `nov-post-html-render-hook` to adjust the HTML before and after rendering or use your own rendering function by customizing `nov-render-html-function` to one that replaces HTML in a buffer with something nicer than the default output.

Here's an advanced example of text justification with the [justify-kp](https://github.com/Fuco1/justify-kp) package:

```
(require 'justify-kp) (setq nov-text-width t) (defun my-nov-window-configuration-change-hook () (my-nov-post-html-render-hook) (remove-hook 'window-configuration-change-hook 'my-nov-window-configuration-change-hook t)) (defun my-nov-post-html-render-hook () (if (get-buffer-window) (let ((max-width (pj-line-width)) buffer-read-only) (save-excursion (goto-char (point-min)) (while (not (eobp)) (when (not (looking-at "^\[\[:space:\]\]\*$")) (goto-char (line-end-position)) (when (\> (shr-pixel-column) max-width) (goto-char (line-beginning-position)) (pj-justify))) (forward-line 1)))) (add-hook 'window-configuration-change-hook 'my-nov-window-configuration-change-hook nil t))) (add-hook 'nov-post-html-render-hook 'my-nov-post-html-render-hook)
```

This customization yields the following look:

[![https://raw.github.com/wasamasa/nov.el/master/img/justify-kp.png](https://camo.githubusercontent.com/57a42e6d9fd52096d4a1823b034fe71a394e0f33/68747470733a2f2f7261772e6769746875622e636f6d2f776173616d6173612f6e6f762e656c2f6d61737465722f696d672f6a7573746966792d6b702e706e67)](https://camo.githubusercontent.com/57a42e6d9fd52096d4a1823b034fe71a394e0f33/68747470733a2f2f7261772e6769746875622e636f6d2f776173616d6173612f6e6f762e656c2f6d61737465722f696d672f6a7573746966792d6b702e706e67)

[](https://github.com/wasamasa/nov.el#usage)Usage
-------------------------------------------------

Open the EPUB file with `C-x C-f ~/novels/novel.epub`, scroll with `SPC` and switch chapters with `n` and `p`. More keybinds can be looked up with `F1 m`.

[](https://github.com/wasamasa/nov.el#contributing)Contributing
---------------------------------------------------------------

See [CONTRIBUTING.rst](https://github.com/wasamasa/nov.el/blob/master/CONTRIBUTING.rst).

[](https://github.com/wasamasa/nov.el#alternatives)Alternatives
---------------------------------------------------------------

The first one I've heard of is [epubmode.el](https://www.emacswiki.org/emacs/epubmode.el) which is, well, see for yourself. You might find [ereader](https://github.com/bddean/emacs-ereader) more useful, especially if you're after Org integration and annotation support.

  
  
from Hacker News https://ift.tt/2vKIL9R