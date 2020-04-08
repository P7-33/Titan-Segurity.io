---
title: 'How to Change the Default Shell to Bash on macOS Catalina'
date: 2019-10-18T13:11:00+01:00
draft: false
---

![Terminal window on a macOS Catalina desktop.](https://www.howtogeek.com/wp-content/uploads/2019/10/img_5da794546f243.jpg)

With [macOS Catalina](https://www.howtogeek.com/439830/whats-new-in-macos-10.15-catalina-available-fall-2019/), Apple is [now using](https://support.apple.com/en-us/HT208050) Zsh as the default shell. [We love Zsh](https://www.howtogeek.com/362409/what-is-zsh-and-why-should-you-use-it-instead-of-bash/), but the trusty old Bash shell is still included with macOS, and you can quickly switch back to Bash if you prefer.

Zsh is only the default shell on newly created user accounts, so any existing accounts you have on an upgraded  Mac will still use Bash by default unless you change it. Each user account has its own default shell preference.

From the Terminal
-----------------

To change a user account’s default shell on macOS, simply run the `chsh -s` (change shell) command in a Terminal window.

Change the default shell to Bash by running the following command:

```
chsh -s /bin/bash
```

You’ll have to enter your user account’s password. Finally, close the Terminal window and reopen it. You’ll be using Bash instead of Zsh.

![Changing the default shell to Bash on macOS Catalina.](https://www.howtogeek.com/wp-content/uploads/2019/10/img_5da7924c44e87.png)

Change the default shell back to Zsh by running this command:

```
chsh -s /bin/zsh
```

Enter your password when prompted. After you close the terminal window and reopen it, you’ll be using Zsh.

### [Read the remaining 14 paragraphs](https://www.howtogeek.com/444596/how-to-change-the-default-shell-to-bash-in-macos-catalina/)