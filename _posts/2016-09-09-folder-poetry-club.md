---
title: 'Folder Poetry Club'
date: 2019-12-02T04:29:00+01:00
draft: false
---

[](https://github.com/melaniehoff/folderpoetry#--folder-poetry-club--)β‘ π Folder Poetry Club π β‘
==================================================================================================

Workshop taught by [Melanie Hoff](https://melanie-hoff.com/), co-organized by the [School for Poetic Computation](https://sfpc.io) and [Detroit Community Technology Project](https://detroitcommunitytech.org/). Zine by [Neta Bomani](https://netabomani.com) and [Taeyoon Choi](http://taeyoonchoi.com)

[](https://github.com/melaniehoff/folderpoetry#links)Links
----------------------------------------------------------

[![A drawing of a blob like character popping out of a folder icon and passing a file icon to an open latop with hands and a smile on it face.](https://github.com/melaniehoff/folderpoetry/raw/master/_assets/img/folder_poetry_open.png)](https://github.com/melaniehoff/folderpoetry/blob/master/_assets/img/folder_poetry_open.png)

[](https://github.com/melaniehoff/folderpoetry#disclamier)Disclamier
--------------------------------------------------------------------

This workshop assumes no coding experience and simultaneously takes the position that everyone who interacts with computers in some way is already a programmer.

### [](https://github.com/melaniehoff/folderpoetry#coding-isnt-something-that-just-happens-behind-your-screen)Coding isnβt something that just happens behind your screen.

Coding _can be_ a holistic computer practice, a new relationship you have with your computer & your computers habits - from the way you name your files or organize your folders, to completely changing how you perform routine tasks on your computer, such as moving a file.

* * *

[](https://github.com/melaniehoff/folderpoetry#agenda)Agenda
------------------------------------------------------------

*   Introductions
    *   What is the story of your folder name?
*   Intentions
*   Longer Introductions
*   History of SFPC
*   Reintroduction to computers & computing
*   Handy shortcuts
*   Sentence activity
*   House folder activity
*   Bash
*   Folder Poetry Club

[](https://github.com/melaniehoff/folderpoetry#vocabulary)Vocabulary
--------------------------------------------------------------------

**Word**

**Definition**

folder

(also referred to as directory) is an organizational regime imposed on your computer used to store and organize files and other folders

file

is an object on a computer which stores data, information, settings, or commands to be used with various computer programs

file types/formats/extensions

indicate how data has been stored and how to read or open files in specific programs. for example, `.txt` files open in a text editor, `.jpg` files open in an image viewer/editor. full list of file formats and extensions [here](https://en.wikipedia.org/wiki/List_of_file_formats)

file path

tells you the location of a file in a system. for example `users/username/desktop/folder_poetry_club`

terminal

is a way to get text based access to your operating system

terminal commands

give you the ability to control your computer using command prompts. for example, terminal commands on mac computers are written in a language called bash

bash

is the programming language we use in the terminal, often one line at a time, but we can also put bash code in a file and run that file

[](https://github.com/melaniehoff/folderpoetry#file-organization)File organization
----------------------------------------------------------------------------------

*   Naming files and folders
    *   All lowercase
    *   No spaces, under scores and dashes are ok (for example, `my_folder` or `my-folder`)
*   File types
*   Mind your file path

[](https://github.com/melaniehoff/folderpoetry#handy-shortcuts-to-sharpen-computer-habits)Handy Shortcuts to sharpen computer habits
------------------------------------------------------------------------------------------------------------------------------------

Keyboard Shortcuts for Mac

Description

cmd + Tab

Switch between applications

Cmd + Spacebar

Spotlight search

Cmd + S

Save file

Cmd + Shift + N

New Folder

Cmd + Ctl + Spacebar

Emoji Keyboard

[](https://github.com/melaniehoff/folderpoetry#command-line-activity)Command line activity
------------------------------------------------------------------------------------------

### [](https://github.com/melaniehoff/folderpoetry#open-terminal)Open terminal

**What is terminal?**

Terminal is a way to get root level, text based access to your operating system.

**How do you access it?**

*   Type `command + spacebar` to open search
*   Type 'terminal' into the search field to open the application

### [](https://github.com/melaniehoff/folderpoetry#bash)Bash

**What is bash?**

Bash is the programming language that we use in the terminal, often one line at a time, but we can also put bash code in a file and run that file.

[](https://github.com/melaniehoff/folderpoetry#commands-codes-spells)Commands, codes, spells
============================================================================================

[](https://github.com/melaniehoff/folderpoetry#bash-commands)Bash Commands
--------------------------------------------------------------------------

Command

Description

Verb

`cd`

change directory

move

`cd ..`

change directory one level back

return

`ls`

list contents of directory

look

`pwd`

parent working directory

where

`open .`

open folder with finder

open

`open filename.txt`

opens file in Text Edit

open

`cat`

print contents

print

`touch filename.txt`

create a file named filename.txt

create

`mkdir foldername/`

create a folder named filename.txt

create

`rm filename.txt`

remove file

remove

`rm foldername/`

remove folder

remove

`cp filename.txt filename2.txt`

copy file .

copy

`say "hello, what is poetic computation"`

say words out loud

speak

`man cd`

show the manual for 'cd'. Press q to quit

define

[](https://github.com/melaniehoff/folderpoetry#keyboard-terminal-commands)Keyboard Terminal Commands
----------------------------------------------------------------------------------------------------

Command

Description

Verb

Up + Down Arrow keys

scroll through history

scroll

Tab Key

autocomplete

complete

[](https://github.com/melaniehoff/folderpoetry#other-useful-code)Other useful code
----------------------------------------------------------------------------------

Code

Description

`open ~/.bash_profile`

opens your bash profile in a text editor

`source ~/.bash_profile`

reloads your bash profile (for after making changes)

`export PS1="πΈ \h βΈ \w β’ "`

to change your bash prompt

`for i in {1..2000}; do printf ' β‘ π β β© βͺ β« β¬ β­ β? '; done;`

to make an emoji for loop

`bash myfile.sh`

to run a bash file

`curl sfpc.io`

prints the html of a website

### [](https://github.com/melaniehoff/folderpoetry#alias-to-put-in-bash_profile)Alias to put in bash\_profile

An alias (shortcut) to put in your .bash\_profile for viewing folder tree structure:

`alias tree="find . -print | sed -e 's;[^/]*/;|;g;s;|; |;g'"`

An alias to put in your .bash\_profile to automatically run an emoji for loop:

`alias folderpoetry="for i in {1..2000}; do printf ' β‘ π β β© βͺ β« β¬ β­ β? '; done;"`

[](https://github.com/melaniehoff/folderpoetry#folder-poetry-activity)Folder Poetry Activity
--------------------------------------------------------------------------------------------

### [](https://github.com/melaniehoff/folderpoetry#download-the-house)Download the house

Download the [house](https://drive.google.com/drive/folders/19U9G9hNCWdiwFbkfna20nlhDOoB8uHHg) folder and put it in your computer's home folder. Your home folder or directory on a mac is represented by a house icon π  in finder and by the `~` symbol in terminal. This folder is located near the root of your computer's entire system. Explore the house.

### [](https://github.com/melaniehoff/folderpoetry#what-is-the-house)What is the house?

The house as an example folder structure poem because **using the command line and computing in general is a relational practice**. You are never using the command line from a βglobalβ perspective. When you issue commands from the command line, you are doing so, from a particular position within the hierarchy of your computerβs file system.

Similarly, when we are inside a house, we are never simultaneously in the kitchen and the bedroom. If we tried to βget into bedβ while in the kitchen, we would not be able to. However if we wanted to wash dishes while standing in the kitchen, we would be able to.

From the command line, if we have navigated to the Desktop folder but try to perform an action on a file thatβs inside your home directory, this would not work. You would have to navigate to the home folder by navigating your file path.

### [](https://github.com/melaniehoff/folderpoetry#make-your-own-file-path-or-file-tree)Make your own file path or file tree

1.  After exploring the house together, consider what other narratives you would like to explore with folder structures. Using the worksheet template or a blank piece of paper in the [zine](https://github.com/melaniehoff/folderpoetry/blob/master/assets/pdf/folder_poetry_zine_pages.pdf), take a few minutes to come up with some ideas that are meaningful or interesting to you. For example, [a folder of one's own](http://folderpoetry.club/a/folder/of/ones/own/) and [my fears](http://folderpoetry.club/my-fears/).
2.  Share with a partner
3.  Using terminal alone, create the folders and files that make up your folder poem
    *   Your files can be `.txt`, `.html`, or `.sh`
    *   The contents of your files can be words, ideas, thoughts, feelings, emojis, or bash scripts
    *   To include emoji icons in your poems, the file must be a `.html` file with the following line included at the top: 
4.  Upload your folder to: [Folder Poetry Club](https://drive.google.com/drive/folders/1U8IcCOcDpxOcaweu5qovpnPAM1KQU8VN?usp=sharing) π
5.  Soon, you should see your folder poem live on [folderpoetry.club](https://github.com/melaniehoff/folderpoetry/blob/master/folderpoetry.club)

[](https://github.com/melaniehoff/folderpoetry#full-credits)Full credits
------------------------------------------------------------------------

  
  
from Hacker News https://github.com/melaniehoff/folderpoetry