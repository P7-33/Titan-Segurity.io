---
title: 'WordPress Automatic Plugin v3.46.11 nulled'
date: 2020-01-10T09:31:00+01:00
draft: false
---

\[the\_ad id='1307'\]  
  

  

While macOS always seems complete to me in more ways than one, there are a few shortcomings that disappoint me at times. If the unavailability of simple [dark/light mode](https://beebom.com/how-quickly-switch-between-dark-light-mode-mac/) and [Turbo Boost](https://beebom.com/how-disable-turbo-boost-prevent-mac-heating/) toggles seem hard to explain, the lack of a straightforward way to conceal confidential files has never failed to baffle me. In an age where an [extra layer of shield against prying eyes](https://beebom.com/best-antivirus-for-mac/) has become the need of the hour, there has to be a quick way to keep sensitive files under the wraps, hasn’t it? So, what’s the workaround? Turns out, there is a viable trick to hide or unhide files and folders with Terminal on Mac. If you feel comfortable using Terminal commands, you may find this hack quite helpful. Let’s unravel it!  

Hide, View, and Unhide Files and Folders with Terminal on macOS
---------------------------------------------------------------

  

Clearing out a few doubts right at the beginning is always better, especially when you are dealing with a hack like this one.  

### Is There Any Complexity involved?

  

Nope. So, long as you have easy access to the [Terminal commands](https://beebom.com/mac-terminal-commands-access-hidden-features/) (or remember them), you can quickly keep any files out of sight on your Mac. If you ever want to revert and make those files show up again or view the hidden files, you will have to go through the same route – albeit with different commands (direct path can also work for viewing). As these commands work pretty well and that too without any complexities, you can master them without any hassle. And yes, you also don’t need to be running the [latest iteration of macOS](https://beebom.com/macos-catalina-features/) to use this hack.  

1.  Launch **Terminal app** on your Mac. You can use the Spotlight search to dive into the app right away.
  

![Open Terminal app on your Mac](https://beebom.com/wp-content/uploads/2020/01/Open-Terminal-app-on-your-Mac-.jpg)

2\. Now, enter the **below-given command.** Make sure not to press the Return key as yet.  

```
chflags hidden
```  

![Enter terminal command on your macOS device](https://beebom.com/wp-content/uploads/2020/01/Enter-terminal-command-on-your-macOS-device-.jpg)

3\. Next, give **space** after **“hidden”. **  

![Give some space after Hidden](https://beebom.com/wp-content/uploads/2020/01/Give-some-space-after-Hidden-.jpg)

4\. Next up, **navigate to the file or folder** you wish to hide and then **drag it to the end of the command** in the Terminal window.

  
  

  

![Drag the file to the Terminal command window](https://beebom.com/wp-content/uploads/2020/01/Drag-the-file-to-the-Terminal-command-window.jpg)

![Drag the folder to the Terminal Window](https://beebom.com/wp-content/uploads/2020/01/Drag-the-folder-to-the-Terminal-Window.jpg)

5\. Finally, **press the Return key. **  

![Press the Return Key](https://beebom.com/wp-content/uploads/2020/01/Press-the-Return-Key.jpg)

Voila! The fill has disappeared on your Mac.  

_**Note:** While this command comes into effect immediately, at times it might not work as expected. In this case, you might need to relaunch the Finder to make the file disappear. _  

View Hidden Files and Folders on macOS
--------------------------------------

  

Wondering where has the file gone and how you can access it? Well, it’s just as straightforward.  

1.  Open the **Terminal app** on your macOS device and then **enter the following command**.
  

```
defaults write com.apple.finder AppleShowAllFiles -boolean true ; killall Finder
```  

2\. Hit the **Return key.**  Now, you can view all of your hidden files in Finder.  

![Check out hidden file on macOS](https://beebom.com/wp-content/uploads/2020/01/Check-out-hidden-file-on-macOS-.jpg)

  
  

  

Unhide Files or Folders on macOS
--------------------------------

  

If you wish to unhide the specific files you had concealed earlier, you can do so with ease.  

1.  Launch the **Terminal** app on your Mac and then enter the below-given command. Be sure not to hit the Return key as yet.
  

```
chflags nohidden
```  

2\. Next, make sure to include a space at the end of the command. Then, drag the file to the end of the command and then press the **Return key. **  

Check out, your file has once again begun to show up in the Finder. That’s pretty much it!  

Hide and Unhide Files on Mac with Ease
--------------------------------------

  

So, these are the quick ways to keep all of your private files away from the prying eyes. While they work efficiently, I wish Apple offered an easier way to hide files on the macOS operating system. It would be better if the option existed inside the [customization setting](https://beebom.com/how-customize-file-folder-icons-mac/) or the contextual menu itself. Well, I say it because I don’t think everyone likes to indulge with Terminal commands – barring a few pro-Mac users. What’s your take on it? Feel free to shoot your thoughts in the comments below.  

   

  
  
\[the\_ad id='1307'\]  
  
[Source link](https://beebom.com/how-hide-unhide-files-folders-using-terminal-mac/)  
\[the\_ad id='1307'\]