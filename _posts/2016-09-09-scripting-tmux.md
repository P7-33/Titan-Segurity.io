---
title: 'Scripting Tmux'
date: 2020-01-04T03:06:00+01:00
draft: false
---

I often want to start similar workspaces in tmux; for example I always want to `tail` those two log files in a _pane_, or I always want to start both `vim` and `mysql` in a pane, etc.

If you try to find information about starting `tmux` workspaces you typically get advised to use wrapper programs such as [`tmuxinator`](https://github.com/tmuxinator/tmuxinator), [`tmux-resurrect`](https://github.com/tmux-plugins/tmux-resurrect), or [`tmux-continuum`](https://github.com/tmux-plugins/tmux-continuum). These programs may be great, but I like a simple approach.

* * *

Some `tmux` terminology:

*   A _pane_ is a view unto a terminal.
*   A _window_ is a collection of one or more _panes_, and always occupies the entire screen.
*   A _session_ is a collection of _windows_.

Every keybind in `tmux` except the prefix key () is implemented by sending a command to `tmux`. For example `c` sends the `new-window` command, and `n` sends the `next-window` command.

You can do the same by using these commands from the shell or tmux’s command mode:

```
$ tmux new-window :new-window 
```

Many commands accept parameters, for example for `new-window` we can use `-t` to specify the target index. You can use `?` (`list-keys` command) to get a list of all default key mappings.

This is a powerful concept, as it means that everything we do interactively with `tmux` can be scripted. Armed with this information we can create a shell script to start a workspace.

For this example I’ll create a script to start a workspace to write on my site, for this we need three windows: one with just a shell, one to start a web server, and one to start Jekyll.

First we want to start a new session:

```
$ tmux new-session -d -s site 
```

The `-d` flags prevents `tmux` from attaching the new session; this is what `-d` does for most commands, so I’ll not repeat it. `-s` sets the session name. You can’t have a _session_ without _windows_, so `new-session` also starts a _window_. Add `-n` if you want to name this window.

Create a new window with:

```
$ tmux new-window -d -t '=site' -n server -c _site $ tmux send-keys -t '=site:=server' 'python -mhttp.server' Enter 
```

`-t` sets the target window: in this case just a session name so tmux will use the next unused index; the `=` makes sure it’s an exact match. `-n` names the window and `-c` sets the directory.

I don’t use the shell command of `new-window` to start the program as I don’t want the pane to quit if I stop or restart it, hence starting it with `send-keys`.

We can now repeat this for the next window:

```
$ tmux new-window -d -t '=site' -n jekyll $ tmux send-keys -t '=site:=jekyll' 'JEKYLL_NO_BUNDLER_REQUIRE=1 jekyll build -w' Enter 
```

And finally, attach the new session:

```
$ [ -n "${TMUX:-}" ] && tmux switch-client -t '=site' || tmux attach-session -t '=site' 
```

The test is to ensure it works from both outside tmux and inside another tmux session.

Putting it all together:

```
#!/bin/sh set -euC cd ~/code/arp242.net att() { [ -n "${TMUX:-}" ] && tmux switch-client -t '=site' || tmux attach-session -t '=site' } if tmux has-session -t '=site' 2> /dev/null; then att exit 0 fi tmux new-session -d -s site tmux new-window -d -t '=site' -n server -c _site tmux send-keys -t '=site:=server' 'python -mhttp.server' Enter tmux new-window -d -t '=site' -n jekyll tmux send-keys -t '=site:=jekyll' 'JEKYLL_NO_BUNDLER_REQUIRE=1 jekyll build -w' Enter att 
```

Note that it will attach the `site` session if it already exists.

* * *

I found the commands by using `tmux list-keys -T prefix` to find out which command is being sent and then look up the documentation for that command in the [`tmux(1)`](http://man.openbsd.org/OpenBSD-current/man1/tmux.1) manpage by searching with `/command-name`.

One annoyance is that tmux only has short options (e.g. `-s`) and no long options (e.g. `-session-name`). Short options are great for typing on the commandline since it’s, well, short. But long options are much more useful for scripts, especially for options you don’t use every day. Compare:

```
$ tmux new-session -d -s site -n server $ tmux new-session -detached -session-name site -window-name server 
```

The second one has a self-documenting property that the first one lacks. I guess this is one important reason why there are so many wrapper scripts which use YAML config files and such.

**Feedback**

Contact me at [martin@arp242.net](mailto:martin@arp242.net), [GitHub](https://github.com/arp242/arp242.net/issues/new), or [@arp242\_martin](https://twitter.com/arp242_martin) for feedback, questions, etc.

  
  
from Hacker News https://ift.tt/2QHyesA