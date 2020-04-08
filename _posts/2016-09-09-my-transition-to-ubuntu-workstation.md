---
title: 'My Transition to an Ubuntu Workstation'
date: 2019-10-23T06:16:00+01:00
draft: false
---

I've been using Ubuntu as my workstation OS for several months now. Ubuntu Server with the i3 window manager to be specific. I love it, and I've had to change my workflow _a lot_ to make it work for me. But now that I've made the switch to it from Mac and Windows, I'm very happy with it.

I'll be honest, there's not a ton of hard evidence that working on a Linux distro is objectively better than working on Windows or Mac. I have almost equal amounts of time spent working on each of these platforms, and I think each one excels at something different. With that in mind, I think Ubuntu just feels right for the priorities I have now.

So what have I gained, what have I lost, and what did I learn along the way?

My physical computer now feels entirely replaceable.
----------------------------------------------------

There's pretty much nothing on this laptop I'm typing on right now that I wouldn't be able to recover if it suddenly stopped working. This document hasn't been pushed to git yet, and the contents of my `~/Downloads/` folder would be gone. That's it. Everything else lives somewhere online where I can easily get it back from.

There's a few tools I've loved using that help me pull this off:

*   **Git.** All my ideas and notes and writing are stored as markdown and csv files. I'm fanatical about saving my work often. I think I picked up that habit from years of using animation software that would randomly corrupt my project files and erase hours of finely-tuned work. For this reason, saving to git is perfectly suited to my paranoia; I can save often and even have a conveniently labeled history in case I mess things up in the future. Plus, I know I have copies both on my laptop and in the cloud.
*   **NextCloud.** Some things don't seem to belong in git repositories, especially non-text files or files that have been encrypted. For that, I rent a private server that runs an instance of NextCloud and regularly sends backups to S3. This is essentially what replaces my `~/Desktop/`, `~/Pictures/`, and `~/Documents/` folders on a traditional PC.
*   **Yubikey.** With this, I have access to my encrypted files and private servers anywhere I go. I don't have much to add here. Once I figured out how to use it, my Yubikey has felt like a natural part of my toolkit.
*   **Dotfiles.** It couldn't be easier for me to recover my settings for all my programs when I install a fresh copy of Ubuntu Server. I keep them all at [https://github.com/ryannjohnson/dotfiles](https://github.com/ryannjohnson/dotfiles), which makes them easy to use even on computers that aren't mine.

Even when I was running Windows, I would wipe my computer every few months. I kept a "Backup Image" handy with all my settings already installed. I've spent _far_ too many hours trying to undo damage I've done to my systems by installing random software from the internet onto my workstation; I've come to value the option of resetting my computer to a known, healthy state _immensely_.

Maybe I'm spoiled with Linux, but I like that I can install the OS without worrying about a license. Windows does this, and I don't know if it's the financial burden I don't like, the mental overhead of keeping track of where my licenses are, or perhaps even just the idea that I don't _really_ have full control of my software.

The biggest problem with Mac is it's just so expensive all around. Expensive things are harder to replace. I like working on dispensable hardware; it makes me worry less about being clumsy and physical accidents and more about whether my data is safe.

There are a smattering of other subjective benefits to using Linux as my primary OS:

*   It encourages me to get good at CLI tools. This means I'm more proficient at working on remote servers and have an easier time automating trivial tasks.
*   It encourages me to get good at free, open source tools. I can't use the Adobe Creative Suite on Linux, so I've had to get familiar with Krita, Gimp, and Inkscape, saving me more than $600 per year in subscription fees.
*   I'm able to focus better. I never get unprompted system popups on my screen except during boot. I also don't really have the option to install the games I like on this platform, so I never even crave them anymore.

As far as the shortcomings, there are a few. They're actually substantial enough that it took me several more years to ween myself off of Windows than I would have liked.

A lot of great software just isn't available on Linux.
------------------------------------------------------

The software that comes to mind for me is Adobe's After Effects. It's the animation program I used for most of my freelance career. Adopting Linux meant I had to leave that tool set behind, which was tough for me. I'm also proficient at related tools like Photoshop and Illustrator; those programs have viable alternatives on Linux, but switching still meant that I'd have to learn how to use them.

Things are different now. I've created only one animation in the past four years. Video games used to be much more important to me; now I go through a gaming phase once a year that lasts only a week or two. My livelihood and priorities no longer have anything to do with these kinds of software, so the switch has been easier. Plus, open source has come a _long_ way in terms of stability and reliability over the past 5-10 years; I'm not wanting for anything more than what I've got right now.

There are some other luxuries I've lost in the transition. For instance, if I want to plug in a USB microphone, headphones, and two displays to my computer all at once, I'll have to do some configuration through the command line to make them work correctly. Even getting the mouse to move the way I intend isn't as easy as Mac and Windows make it. Doing all these things is possible; it's just more work.

On the subject of screens, I haven't really figured out how to get rid of screen tearing while using entry-level hardware. Since Windows doesn't suffer from this issue on the same hardware, I chalk it up to the software support being different. This isn't a deal-breaker for me, but it does detract me from watching videos on my computer (which I actually _love_ in terms of ridding myself of distractions).

I learned that I value being able to use any computer easily instead of one computer perfectly.
-----------------------------------------------------------------------------------------------

All my conclusions about using Linux point me towards this finding. I just hate depending on a set of tools that are hard to replicate or that lock me into a particular vendor. When I see a finely-tuned workstation, I see a lot of time wasted in the future when a newer, better system becomes available or when that computer unexpectedly bites the dust.

I used to salivate over computers. News of the next most-powerful processor or RAM upgrade was irresistible for a period of my life. Those gains were immediate in my animation work, cutting down time that I'd have to wait for a render to finish. If I still played computer games today and created animations on a regular basis, I'd probably still value a single specialized machine a lot.

Now, though, commodity hardware works perfectly for my needs. If I need a lot of computing resources today, I can rent them in the cloud on a per-project basis. I'd rather have a long-lasting battery and silence than anything else. I much prefer the peace of mind that my laptop can be stolen or broken and the most I'll lose is about $400 and none of my data.

  
  
from Hacker News https://ift.tt/2ByVHoq