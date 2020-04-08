---
title: 'Improving CLIs with isatty'
date: 2019-11-30T01:59:00+01:00
draft: false
---

![](https://blog.jez.io/touch-icon.png "Improving CLIs with isatty - Bits, Bytes, and Words")  

One thing I like to do to improve the command-line programs I maintain is to make them aware of whether they’re being run interactively. In this post I’ll show off an easy trick to make programs running interactively more usable.

This always used to trip me up when I was first learning to use the terminal:

I’d drop this into the command-line and what happens? It hangs… Is it because it’s taking a long time to search? Nope—I’ve forgetten to tell `grep` what files to search in!

When `grep` is given only a pattern to search for and no files to search in, it assumes we want to search for that pattern on stdin. This is great for shell scripts and one-liners at the command-line, but it’s **super** annoying when we’re just grepping interactively.

The thing is, it’s super easy to detect when the user might have made this mistake: if we’re defaulting to reading from stdin **and** the file corresponding to stdin represents a terminal (more specifically, a [tty](https://unix.stackexchange.com/questions/4126/)). And once we’ve detected it, we can print a helpful message.

Here’s how I did it when writing [`diff-locs`](https://github.com/jez/diff-locs), one of the command-line programs I’ve been working on lately:

Check if stdin is a tty in Haskell

```
fileIn <- case inputStyle of  InputFromFile filename -> IO.openFile filename IO.ReadMode  InputFromStdin -> do  isTTY <- hIsTerminalDevice IO.stdin  when isTTY $ do  errPutStrLn "Warning: reading from stdin, which is a tty."  return IO.stdin
```

If we’ve been given a file explicitly, just open it. Otherwise, fall back to reading from stdin. But first, check if `IO.stdin` is a terminal device and when it **is**, print a warning.[1](https://blog.jez.io/cli-tty/#fn:1) The complete file containing the snippet above is [on GitHub](https://github.com/jez/diff-locs/blob/743bff5cb1abb6e405b0369b195614aea6ec018d/app/Main.hs#L17-L24).

I’ve implemented `diff-locs` as a standard Unix filter—it takes input on stdin and emits output on stdout. Normal usage looks something like this, where we pipe `git diff` into `diff-locs`:

But if someone is just playing around at the terminal (maybe, trying to get the help output to show up), they might run `diff-locs` without args, and then be greeted with this message:

```
❯ diff-locs Warning: reading from stdin, which is a tty. █
```

This is much better than just sitting there appearing to hang!

`isatty` in other languages
---------------------------

The trick above works in pretty much every language that supports Unix programming. Under the hood, the Haskell snippet above is powered by the `isatty` function in the C standard library (`man 3 isatty`), which most other languages wrap in some way. For example, three other languages I’ve done this in recently:

Ruby

```
if STDIN.isatty? STDERR.puts 'Warning: reading from stdin, which is a tty.' end
```

Bash

```
if [ -t 0 ]; then  echo 'Warning: reading from stdin, which is a tty.' >&2 end
```

OCaml

```
if Unix.isatty Unix.stdin then prerr_endline "Warning: reading from stdin, which is a tty." else ()
```

And again, a quick search for `isatty` should suffice for any language that supports Unix programming. It’s little things like this that add up and make certain command-line utilities delightful to use.

June 11, 2019

  
  
from Hacker News https://ift.tt/34zoNkC