---
title: 'GitHub goes GUI-less'
date: 2020-02-16T07:10:00+01:00
draft: false
---

Git is a handy tool that many of us are using for more than just software development. Having a cloud-based upstream repository is also surprisingly useful, but until now using GitHub — the most common upstream server — meant firing up a web browser, at least for certain tasks. Now GitHub is releasing a beta version of [command-line tools](https://github.blog/2020-02-12-supercharge-your-command-line-experience-github-cli-is-now-in-beta/) made to [manipulate your GitHub repos](https://cli.github.com/).

The tools are early release so they mostly focus on issues and pull requests. Of course, git itself will do the normal things like clone and checkout — you’ve always been able to do that on the command line. The example given in the announcement blog post lists all issues with a help wanted label:

```
gh issue list --label "help wanted"
```

We noticed that asking to view the issue, while done on the command line, will still open a browser. The tools are still a little early, so this is an excellent time to let the developers know what you’d like or otherwise influence the project.

We were a little surprised it wouldn’t just consume git, so that you’d use the same commands for everything and it would just pass pre-formed commands to git. Of course, that would be pretty easy to write as a shell script wrapper if you were interested in such a thing.

You’d be forgiven for only thinking of git as a way to manage source code revisions, [but it’s actually capable of all sorts of interesting tricks](https://hackaday.com/2017/05/23/stupid-git-tricks/).

  
  
from Hackaday https://ift.tt/3bKSraK  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)