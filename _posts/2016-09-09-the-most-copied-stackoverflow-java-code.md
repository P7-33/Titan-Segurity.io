---
title: 'The most copied StackOverflow Java code snippet contains a bug'
date: 2019-12-05T02:23:00+01:00
draft: false
---

![so.png](https://zdnet1.cbsistatic.com/hub/i/2019/12/04/11e5ae23-9066-4dbb-b360-12eee42a7b2b/a8b7846fa9650d633e2b0b2bf648f55d/so.png)

The most copied StackOverflow Java code snippet of all time contains a bug.

The admission comes from the author of the snippet itself, Andreas Lundblad, a Java developer at Palantir, and one of the highest-ranked contributors to StackOverflow, a Q&A website for programming-related topics.

An academic paper \[[PDF](https://arxiv.org/pdf/1802.02938.pdf)\] published in 2018 identified a code snippet Lundblad posted on the site as the most copied Java code taken from StackOverflow and then re-used in open source projects.

The code snippet was provided as an answer to a StackOverflow question [posted in September 2010](https://stackoverflow.com/questions/3758606/how-to-convert-byte-size-into-human-readable-format-in-java/3758880#3758880). The code snippet printed byte counts (123,456,789 bytes) in a human-readable format, like 123.5 MB.

Academics found that this code had been copied and embedded in more than 6,000 GitHub Java projects, more than any other StackOverflow Java snippet.

![so-code.png](https://www.zdnet.com/article/the-most-copied-stackoverflow-java-code-snippet-contains-a-bug/#ftag=RSSbaffb68)

<span><img src="https://zdnet1.cbsistatic.com/hub/i/2019/12/04/a74f193a-463f-4ac9-8a2d-0c0d50e13166/f74743bc9a08f99b83252072cda8453d/so-code.png" alt="so-code.png" /></span>

Image: Baltes et al.

In [a blog post](https://programming.guide/worlds-most-copied-so-snippet.html) published last week, Lundblad admitted that the code was flawed and that it incorrectly converted byte counts into human-readable formats.

Lundblad said he revisited the code after learning of the academic paper and its results. He looked at the code again and published a corrected version on his blog.

### StackOverflow code sometimes contains security bugs

But while Lundblad's code snippet contained a trivial conversion bug that only resulted in slightly inaccurate file size estimations, things could have been much worse.

The code could have contained a security flaw, for example. If it did, then fixing all the vulnerable applications would have taken months or years, leaving users exposed to attacks.

Even if it is universally understood that copy-pasting code from StackOverflow is a bad idea, developers still do it.

The 2018 research paper showed just how widespread this practice was in the Java ecosystem, revealing that the vast majority of developers who copied popular StackOverflow answers didn't even bother to credit their source.

Software developers who copy code from StackOverflow without attribution are effectively hiding from fellow coders that they've introduced unvetted code inside a project.

This might sound like an overly alarmistic statement, but a different academic research project published in October 2019 \[[PDF](https://arxiv.org/pdf/1910.01321.pdf)\] showed that StackOverflow code snippets do contain vulnerabilities -- and that this is not just an urban myth that developers use to scare each other.

The research paper found major security flaws in 69 of the most popular C++ code snippets posted on StackOverflow in the past ten years.

Researchers said they found these 69 vulnerable code snippets in a total of 2,859 GitHub projects, showing how one bad StackOverflow answer could wreak damage across an entire ecosystem of open source apps.

  
  
from Latest Topic for ZDNet in... https://ift.tt/33Pjdcz