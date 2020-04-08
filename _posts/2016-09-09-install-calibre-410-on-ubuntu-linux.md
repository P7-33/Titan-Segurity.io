---
title: 'Install Calibre 4.1.0 on Ubuntu & Linux Mint system'
date: 2019-10-09T18:57:00+01:00
draft: false
---

[![](https://1.bp.blogspot.com/-QJwrPztpo6E/XZ4d6FzYVaI/AAAAAAAAMsg/A3YQtUqoRyItc91P17__aJx4NAe_o374gCLcBGAsYHQ/s400/cal_home.png)](https://1.bp.blogspot.com/-QJwrPztpo6E/XZ4d6FzYVaI/AAAAAAAAMsg/A3YQtUqoRyItc91P17__aJx4NAe_o374gCLcBGAsYHQ/s1600/cal_home.png)

  
**Calibre** is an open source e-book library management application designed for the 21th century, for the digital world that were are living in right now. It lets users to manipulate digital books in any way possible. It helps users to easily read ebooks on their personal computer, convert ebooks from one format to another, create electronic books based on recipes of your very own ideas.  
Features at a glance  
  
The software can download news from a sleuth of various sources, and comes with a content server for online access. Syncing ebooks to a supported mobile reader device is also possible with Calibre. E-book library management is the the main component of the application, displayed every time you open the application. From here, you can convert and organize e-books in a simple manner. It imports and exports many ebook formats, including ePub, MOBI, AZW, DOC, XML, etc. Just like any other software that can be extended via plugins, Calibre features an internal collection of add-ons, which provide support for editing metadata of ebooks, or add support for various ebook readers.  

  

### [What](https://calibre-ebook.com/whats-new)'s new in Calibre 4.1.0

*   **New features:**
*   Viewer: Add an option to have a scrollbar (under Scrolling in the viewer preferences)
*   Viewer: Allow showing the 'position in book', as was displayed in the top left of the viewer in calibre 3, in the header or footer of the viewer.
*   Viewer: Add options to control scrolling using the mouse in paged mode.
*   Viewer: Allow copying images by right clicking on them.
*   Viewer: Add a preference under Miscellaneous to allow only a single instance of the viewer
*   Viewer: Add keyboard shortcuts to toggle between paged mode and flow mode and to quit
*   Content server: Make the book size useable in custom book list templates.
*   Edit metadata: Use a border rather than background color to indicate correct title and author sort values. Works better with dark themes.
*   Kobo driver: Support for new firmware

*   **Bug fixes:**
*   Viewer: Fix a couple of bugs in flow mode. Scrolling to anchors was not working and remembering last read position was not working
*   Viewer: Fix text after comments not being rendered. Note that the book has to be reloaded if already viewed for the fix to apply.
*   Viewer: Fix loading progress screen sometimes getting stuck if changing pages rapidly.
*   Viewer: Fix failing to open books if path to cache contains symbolic links.
*   Viewer: When restoring from fullscreen go back to maximized state if window was maximized when entering full screen.
*   Viewer: Fix shortcut changes not being applied after pressing OK if shortcut list is closed by pressing Esc.
*   Fix a regression that broke reading metadata from ODT files that do not have keywords.
*   PDF Output: Fix a bug that prevented the first style property in the header or footer template from being applied
*   PDF Output: Fix error with a few embedded TTF fonts.
*   Edit book: Font manager: Fix removing embedded font failing if @font-face rule has no src.
*   Viewer: Hide the browser provided scrollbar that flashes momentarily on page load.
*   Viewer: Fix clicking on margins causing keyboard shortcuts to not work until the main text is clicked on again
*   Comments editor: Workaround for Qt converting ids into anchors
*   Possible workaround for some windows machines where the viewer is getting access denied errors while renaming a directory
*   Viewer: When there is empty text for an header footer section render it as blank instead of moving the remaining sections to the left

  

### How to Install Calibre 4.1.0  on Ubuntu (18.10/18.04) & Linux Mint :

To install/update Calibre 4.1.0  on Ubuntu 18.04 Bionic Beaver, Ubuntu 18.10, Ubuntu 19.04 Disco Dingo, Cosmic Cuttlefish, Ubuntu 16.04 Xenial Xerus, Linux Mint 19.1, Elementary OS 5 'Juno', Peppermint, Deepin 15.8, Deepin 15.9, Linux Lite 4.2 and other Ubuntu derivative systems, open a new Terminal window and bash (get it?) in the following commands:  
  
To install Calibre 4.1.0 you must run this simple script :  
```
sudo -v && wget -nv -O- https://download.calibre-ebook.com/linux-installer.sh | sudo sh /dev/stdin
```

[![](https://1.bp.blogspot.com/-0fIrQZVpQo0/XZ4d6eBbkiI/AAAAAAAAMsk/Tm-irhvgx2gbD5xGdUU8FYevbtXell3zgCLcBGAsYHQ/s400/callibre1.png)](https://1.bp.blogspot.com/-0fIrQZVpQo0/XZ4d6eBbkiI/AAAAAAAAMsk/Tm-irhvgx2gbD5xGdUU8FYevbtXell3zgCLcBGAsYHQ/s1600/callibre1.png)

  
Automatic download library and wait a few minutes  
  

[![](https://1.bp.blogspot.com/-sz-EWjCH1HU/XZ4d6jCQ6hI/AAAAAAAAMso/eA-toc78QSEnrDzpPuotF7CBVZZULzzPgCLcBGAsYHQ/s400/callibre2.png)](https://1.bp.blogspot.com/-sz-EWjCH1HU/XZ4d6jCQ6hI/AAAAAAAAMso/eA-toc78QSEnrDzpPuotF7CBVZZULzzPgCLcBGAsYHQ/s1600/callibre2.png)

  
and finish, run 'calibre' on ubuntu terminal like this  
  

[![](https://1.bp.blogspot.com/-pS5A5AthM28/XZ4d5BXJV0I/AAAAAAAAMsU/cJD6FBIhCxoh6omqaLQHx1Cn2M79vAnuwCLcBGAsYHQ/s400/cal1.png)](https://1.bp.blogspot.com/-pS5A5AthM28/XZ4d5BXJV0I/AAAAAAAAMsU/cJD6FBIhCxoh6omqaLQHx1Cn2M79vAnuwCLcBGAsYHQ/s1600/cal1.png)

  
next :  
  

[![](https://1.bp.blogspot.com/-b6ZDYpRMZFU/XZ4d5CXfvDI/AAAAAAAAMsY/GwaNnKpO608tKtcHb4jkldO9FysKQtcbwCLcBGAsYHQ/s400/cal2.png)](https://1.bp.blogspot.com/-b6ZDYpRMZFU/XZ4d5CXfvDI/AAAAAAAAMsY/GwaNnKpO608tKtcHb4jkldO9FysKQtcbwCLcBGAsYHQ/s1600/cal2.png)

[![](https://1.bp.blogspot.com/-mcuU6PS4wF4/XZ4d5N13JoI/AAAAAAAAMsc/W_MtOAinc104EQvRvJwggOmrcgb-ZlykACLcBGAsYHQ/s400/cal3.png)](https://1.bp.blogspot.com/-mcuU6PS4wF4/XZ4d5N13JoI/AAAAAAAAMsc/W_MtOAinc104EQvRvJwggOmrcgb-ZlykACLcBGAsYHQ/s1600/cal3.png)

  
or seach calibre on ubuntu menu dashboard :  
  

[![](https://1.bp.blogspot.com/-Tij4P036cjc/XZ4d7IUAlCI/AAAAAAAAMss/RBnoDA6S054qZHXUhCuMErT2uq-qDm7vgCLcBGAsYHQ/s400/callibre3.png)](https://1.bp.blogspot.com/-Tij4P036cjc/XZ4d7IUAlCI/AAAAAAAAMss/RBnoDA6S054qZHXUhCuMErT2uq-qDm7vgCLcBGAsYHQ/s1600/callibre3.png)