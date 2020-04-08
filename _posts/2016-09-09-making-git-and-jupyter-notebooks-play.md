---
title: 'Making Git and Jupyter Notebooks play nice'
date: 2019-11-29T01:39:00+01:00
draft: false
---

**Summary:** [jq](https://stedolan.github.io/jq/) rocks for speedy JSON mangling. Use it to make powerful git clean filters, e.g. when stripping out unwanted cached-data from Jupyter notebooks. You can find the documentation of git 'clean' and 'smudge' filters buried in [the page on git-attributes](https://git-scm.com/book/en/v2/Customizing-Git-Git-Attributes#filters_a), or see my example setup below.

* * *

The trouble with notebooks
--------------------------

For a year or so now I've been using [Jupyter](https://jupyter.readthedocs.io/en/latest/tryjupyter.html) notebooks as a means to produce tutorials and other documentation (see e.g. the [voeventdb.remote](https://voeventdbremote.readthedocs.io) [tutorial](https://voeventdbremote.readthedocs.io/en/latest/tutorial/quickstart.html)). It's a powerful medium, providing a good compromise between ease-of-editing and the capability to interleave text, code, intermediate results, plots, and even nicely-typeset LaTeX-encoded equations. I've even gone to far as to urge its adoption in recent [conference talks](https://github.com/timstaley/sustainable-software-in-astro/blob/master/README.md).

However, this powerful interface inherits the age-old curse of [WYSIWYG](https://en.wikipedia.org/wiki/WYSIWYG) editors - the document-files tend to contain more than just plain-text, and therefore are not-so-easy to handle with standard version-control tools. In the case of Jupyter, the format doesn't stray too far from comfortable plain-text territory - the [ipynb format](https://nbformat.readthedocs.io/) is just a custom JSON data-structure, with the occasional base-64 encoded blob for images and other binary data. Which means version-control systems such as Git _can_ handle it quite well, but diff-comparing different versions of a complex notebook quickly becomes a chore as you scroll past long blocks of unintelligible base-64 gibberish.

This is a problem when working with long-lived, multiple-revision or (especially) multiple-coauthor projects. What can we do about this? First, it's worth mentioning the initial "I'll figure this out later" solution which has served many users sufficiently well for a while - if you're typically only working from one machine, and you just want to keep your notebooks vaguely manageable, you can get by for a long time by manually hitting _Cell -> All Output -> Clear_ (followed by a Save) before you commit your notebooks. This wipes the slate clean with regards to cell outputs (plots, prints, whatver), so you'll need to re-run any computation next time you run the notebook.

The problems with this approach are that

A. it's _manual_, so you'll have to painstakingly open up every notebook you recently re-ran and clear it before you commit, and

B. it doesn't even fully solve the 'noise-in-the-diffs' problem, since every notebook also contains a 'metadata' section, which looks a bit like this:

```
{ "metadata": { "kernelspec": { "display\_name": "Python 2", "language": "python", "name": "python2" }, "language\_info": { "codemirror\_mode": { "name": "ipython", "version": 2 }, "file\_extension": ".py", "mimetype": "text/x-python", "name": "python", "nbconvert\_exporter": "python", "pygments\_lexer": "ipython2", "version": "2.7.12" } } 
```

Note the metadata section is [effectively a blank slate](https://nbformat.readthedocs.io/en/latest/format_description.html#metadata), and has a myriad of possible uses, but for most users it will just contain the above. This is useful for checking a previously run notebook, but is mostly unwanted information when checking-in files to a multi-user project where everyone's using a slightly different Python version - it just generates more diff-noise.

Possible Pythonic solutions
---------------------------

### nbdime - an nbformat diff-GUI

We clearly need some tooling, and there are some Python projects out there trying to address exactly this problem. First, it's worth mentioning [nbdime](https://nbdime.readthedocs.io), which picks up the ball from where the (now defunct) [nbdiff](https://github.com/tarmstrong/nbdiff) project left off and attempts to provide “content-aware” diffing and merging of Jupyter notebooks - a [meld](http://meldmerge.org/) (GUI) diff-tool equivalent for the nbformat, if you will. I think nbdime has the potential to be a really good beginner-friendly, general purpose notebook-handling tool and I want to see it succeed. However; it's currently somewhat of a beta, and more importantly it only fills one role in the notebook editing toolbox - viewing crufty diffs. What I really want to do is automatically clear out all the cruft and _minimize the diffs in the first place_.

### nbstripout - does what it says on the tin

A little searching then leads to [nbstripout](https://github.com/kynan/nbstripout), which is a one-module Python script wrapping the nbformat processing functions, and adding some automagic for setting up your git config (on which more in a moment). This effectively automates the 'clear all output' manual process described above. However, this doesn't suit me for a couple of reasons; it leaves in that problematic 'metadata' section and also it's [\*\*slowww\*\*](https://github.com/kynan/nbstripout/issues/33). Running a script manually and expecting a short delay is fine, but we're going to integrate this into our git setup. That means it will run every time we hit git diff! One of the few things I love about git is that it's typically blazing fast; so a delay of nearly a fifth of a second every time I try to interact with it gets old pretty quickly:

```
time nbstripout 01\-parsing.ipynb real 0m0.174s user 0m0.152s sys 0m0.016s 
```

(Note, this is a small notebook-file, on a fairly beefy laptop with an SSD). This not a criticism of nbstripout so much as an inherent flaw in using Python for low-latency tasks - that cold-startup overhead on the CPython interpreter is a killer. (Which in turn harks back to ancient history of mercurial vs git!)

Enter jq
--------

Fortunately, we have another option (thanks to Jan Schulz for the [tip-off](https://janschulz.github.io/windows-dev-environment.html) on this). Since the nbformat is just JSON, we can make use of [jq](https://stedolan.github.io/jq/), 'a lightweight and flexible command-line JSON processor' ('sed for JSON data'). There's a modicum of set-up overhead as jq has its very own query / filter language, but the documentation is good and the hard work has been done for you already. Here's the jq invocation I'm currently using:

```
jq --indent 1 \\ '  (.cells\[\] | select(has("outputs")) | .outputs) = \[\]  | (.cells\[\] | select(has("execution\_count")) | .execution\_count) = null  | .metadata = {"language\_info": {"name":"python", "pygments\_lexer": "ipython3"}}  | .cells\[\].metadata = {}  ' 01\-parsing.ipynb 
```

Each line inside the single-quotes defines a filter - the first selects any entries from the 'cells' list, and blanks any outputs. The second resets any execution counts. The third wipes the notebook metadata, replacing it with the minimum of required information for the notebook to still run without complaints [\[\*\]](http://timstaley.co.uk/posts/making-git-and-jupyter-notebooks-play-nice/#id2) and work correctly when formatted with [nbsphinx](https://nbsphinx.readthedocs.io/). The fourth filter-line,

> .cells\[\].metadata = {}

is a matter of preference and situation - in recent versions of Jupyter every cell can be marked hidden / collapsed / write-protected, etc. I'm not interested in that metadata usually but of course you may want to keep it for some projects.

We now have a fully stripped-down notebook that should contain only the common information needed to execute with whatever local Python installation is available (assuming Python2/3 compatibility, correctly set-up library installs and all the rest).

Note you'll need jq version 1.5 or greater, since the \--indent option was only recently implemented and is necessary to conform with the nbformat. Fortunately that should only be a small binary-download away, even if you're on ancient linux or OSX.

That's a bit of a handful to type, but you can set it up as an alias in your _.bashrc_ with a bit of careful quotation-escaping:

```
alias nbstrip\_jq\="jq --indent 1 \\  '(.cells\[\] | select(has(\\"outputs\\")) | .outputs) = \[\] \\  | (.cells\[\] | select(has(\\"execution\_count\\")) | .execution\_count) = null \\  | .metadata = {\\"language\_info\\": {\\"name\\": \\"python\\", \\"pygments\_lexer\\": \\"ipython3\\"}} \\  | .cells\[\].metadata = {} \\  '" 
```

Which can then be used conveniently like so:

```
nbstrip\_jq 01\-parsing.ipynb > stripped.ipynb 
```

Not only does this give us full control to wipe that pesky metadata, it's pretty damn quick, taking something like a tenth of the time of nbstripout in my (admittedly ad-hoc) testing:

```
nbstrip\_jq 01\-parsing.ipynb \# (JSON contents omitted) real 0m0.015s user 0m0.008s sys 0m0.004s 
```

Automation: Integrating with git
--------------------------------

So we're all tooled up, but the question remains - how do we get git to run this automatically for us? For this, we dive into 'gitattributes' functionality, specifically the [filter](https://git-scm.com/docs/gitattributes#__code_filter_code) section. This describes how to define 'clean' and 'smudge' (reverse of clean) filters, which are operations that transform our data as it is checked in or out of the git-repository, so that (for example) our notebook-output cells are always stripped away from the JSON-data before it's added to the git repository:

![Clean-filter illustration](https://git-scm.com/book/en/v2/images/clean.png)

In the general case you can also define a smudge-filter to take your repository contents and do something with it to make it local to your system, but we'll not be needing that here - we'll just use the cat command as a placeholder. The easiest way to explain how to configure this is with an example. Personally, I want notebook-cleaning behaviour to be the default across all my git-repositories, so I have the following entries in my global _~/.gitconfig_ file:

```
\[core\] attributesfile \= ~/.gitattributes\_global \[filter "nbstrip\_full"\] clean \= "jq --indent 1 \\  '(.cells\[\] | select(has(\\"outputs\\")) | .outputs) = \[\] \\  | (.cells\[\] | select(has(\\"execution\_count\\")) | .execution\_count) = null \\  | .metadata = {\\"language\_info\\": {\\"name\\": \\"python\\", \\"pygments\_lexer\\": \\"ipython3\\"}} \\  | .cells\[\].metadata = {} \\  '" smudge \= cat required \= true 
```

And then in _~/.gitattributes\_global_:

```
\*.ipynb filter\=nbstrip\_full 
```

(Note, once you've defined your filter you can just as easily assign it to files in a repository specific [.gitattributes](https://git-scm.com/docs/gitattributes#_description) file if you prefer a fine-grained approach.)

That's it! You're all set to go version control notebooks like a champ! Well, almost.

Getting started and gotchas
---------------------------

Note that we're into git-powertool territory here, so things might be a little less polished compared to the (_cough_) usual intuitive git interface you're used to.

To start off with, assuming a pre-existing set of notebooks, you'll want to add a 'do-nothing' commit, where you simply pull in the newly-filtered versions of your notebooks and trim out any unwanted metadata. Just git add your notebooks, noting that you may need to touch them first, so git picks up on the timestamp-modification and actually looks at the files for changes. Then,

to see the patch removing all the cruft. Commit that, then go ahead, run your notebooks, leave uncleaned outputs all over the place. Unless you change the actual code-cell contents, your git diff should be blank!

Great. Except. If you have executed a notebook since your last commit, git status may show that file as 'modified', despite the fact that when you git diff, the filters go into action and no differences-to-HEAD are found. So you have to 'tune out' these false-positive modified flags when reading the git-status. Another issue is that if you use a diff-GUI such as [meld](http://meldmerge.org/), then beware: unlike git diff, git difftool will **not** apply filters to the working directory before comparing with the repo HEAD - so your command-line and GUI diffs have suddenly diverged! The logic behind this difference in behaviour is that GUI programs give the option to edit the local working-copy directly, as discussed at length in [this thread](http://git.661346.n2.nabble.com/Using-clean-smudge-filters-with-difftool-td7633427.html). This has clearly [caught out others before](http://www.softec.lu/site/DevelopersCorner/GitSmudgeCleanCorrupted).

If they bother you, these false-positives and diff-divergences can easily be resolved by manually applying the jq-filters before you run your diffs. For convenience, my _~/.bashrc_ also defines the following command to apply the filters to all notebooks in the current working directory:

```
function nbstrip\_all\_cwd { for nbfile in \*.ipynb; do echo "$( nbstrip\_jq $nbfile )" > $nbfile done unset nbfile } 
```

Addtionally, let me note that **clean/smudge filters often do not play well with rebase operations**. Things get very confusing if you try to rebase across commits before / after applying a clean-filter. The simplest way to work around this is to simply comment out the relevant filter-assignment line in _.gitattributes\_global_ while performing a rebase, then uncomment it when done.

As a parting note, if you also choose to configure your gitattributes globally, you may want to know how to 'whitelist' notebooks in a particular repository (for example, if you're checking-in executed notebooks to a github-pages documentation branch). This is dead easy, just add a local _.gitattributes_ file to the repository and 'unset' the filter attribute, like so:

Or you could replace the \*.ipynb with a path to a specific notebook, etc.

Hope that helps! Comments or corrections very welcome via [Twitter](http://timstaley.co.uk/#contact-details).

  
  
from Hacker News https://ift.tt/2u0NtnH