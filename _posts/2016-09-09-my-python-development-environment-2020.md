---
title: 'My Python Development Environment, 2020 Edition'
date: 2019-11-12T01:43:00+01:00
draft: false
---

My Python Development Environment, 2020 Edition
-----------------------------------------------

For years I’ve noodled around with various setups for a Python development environment. A couple of years ago [I wrote about a setup I finally liked](https://jacobian.org/2018/feb/21/python-environment-2018/); this is an update to that post.

Bad news: this stuff still isn’t stable, and I’ve had to make some changes. Good news: the general concepts still hold, and the new tools a generally a bit better. If you’re curious about the changes and why I made them, there’s a [section at the very end](https://jacobian.org/2019/nov/11/python-environment-2020/#changes-since-2018) about that.

My setup pieces together [pyenv](https://github.com/pyenv/pyenv), [poetry](https://poetry.eustace.io/), and [pipx](https://pypi.org/project/pipx/). It’s probably a tad more complex that is ideal for most Python users, but for the things I need, it’s perfect.

### My Requirements

I do have somewhat specific (maybe unusual?) requirements:

*   I need to develop against multiple Python versions - various Python 3 versions (3.6, 3.7, 3.8, mostly), PyPy, and occasionally Python 2.7 (less and less often, thankfully).
*   I work on many projects simultaneously, each with different sets of dependencies, so some sort of virtual environment or isolation is critical.
*   I use multiple OSes: macOS at work, and Linux (well, Linux-ish - actually it’s [WSL](https://docs.microsoft.com/en-us/windows/wsl/about)) at home.
*   I want to avoid using the System-provided Python. On macOS it’s too outdated. On Linux, the system Python is used by the OS itself, so if you hose your Python you can hose your system.
*   I use a bunch Python-based CLI stuff, like [youtube-dl](https://rg3.github.io/youtube-dl/), [awscli](https://aws.amazon.com/cli/), [doc2dash](https://doc2dash.readthedocs.io/en/stable/), etc. I want to be able to install and use them without fussing around with activating environments, but I also don’t want their dependencies to clutter up a global installation.
*   I usually deploy through a Docker-based deployment, either to Heroku, AWS, or GCP.
*   Although Docker meets all these requirements, I don’t really like using it. I find it slow, frustrating, and overkill for my purposes.

### The Setup

**Why?** I need to run multiple Python versions, isolated from the system Python. `pyenv` makes it easy to install, manage, and switch between those multiple Pythons.

On my Mac, I installed `pyenv` from Homebrew (`brew install pyenv`). On Linux, I used the [Github installation technique documented in the installation instructions](https://github.com/pyenv/pyenv#basic-github-checkout), which was easy and went smoothly.

Then, I installed some Python versions:

```
$ pyenv install 3.8.0  
 $ pyenv install 3.7.4  
 $ pyenv install 3.6.9  
 $ pyenv install 2.7.16  
 $ pyenv install pypy3.6-7.1.1 
```

And made sure my default Python was set to the latest and greatest:

```
$ pyenv global 3.8.0 
```

**Why?** `pipx` lets me install Python-based CLI stuff ([youtube-dl](https://rg3.github.io/youtube-dl/), [awscli](https://aws.amazon.com/cli/), [doc2dash](https://doc2dash.readthedocs.io/en/stable/), etc.) without those projects’ dependencies messing up my global Python.

Installing `pipx` is easy:

```
$ python -m pip install pipx 
```

(The documentation suggests installing with `--user`. That’s probably a good idea for most people. I didn’t because I know I’m going to keep my global namespace clean, but YMMV.)

From there, I can easily install isolated CLI utils:

```
$ pipx install visidata 
```

`pipx` protiop: if you have tools with optional dependencies, like [visidata](http://visidata.org/), you can inject them into the `pipx` virtualenv like so:

```
$ pipx inject visidata pandas 
```

Why? Poetry handles dependency- and virtual-environment-management in a way that’s very intuitive (to me), and fits perfectly with my desired workflow.

[The documentation covers a few different ways to install Poetry](https://poetry.eustace.io/docs/#installation). Because I’m using `pipx`, I use that:

```
$ pipx install poetry==1.0.0b4 
```

Note that I’m using the 1.0 pre-release (`1.0.0b4` at the time of this writing). It’s a tradeoff: the pre-releases have generally better ergonomics and fewer bugs, but are bleeding edge. I’ve already had one bug break some automated releases. So think carefully about using the stable version vs the new shiny.

To start new projects, I just make a directory and type `poetry init`. This guides me to create a `pyproject.toml`. Then I’ll run `poetry install`, which’ll create a managed virtualenv for me and install stuff into it.

To work on existing projects, I clone a repository and then run `poetry install`.

If you’re new to Poetry, and want to see an example of what a project using it looks like, my [pinboard-to-sqlite](https://github.com/jacobian/pinboard-to-sqlite) repo is a good fairly simple example.

Converting to Poetry from a `requirements.txt` is a bit frustrating: I have to manually consult the requirements file, and run `poetry add {package}`, possibly with a version specifier, until I get an appropriate `pyproject.toml`.

If I need to switch Python versions, I run `pyenv local` in my project directory.

#### Deployment

When it comes time to deploy, Heroku’s native buildpacks don’t understand `pyproject.toml` 😠. However, I’m increasingly moving to Docker-based deploys, even to Heroku. Getting Poetry going in a Docker image is a bit finicky, but it’s not bad. I do something like this:

```
FROM python:3.7  
   
 WORKDIR /code  
   
 RUN pip install -U pip && \  
 pip install poetry  
   
 COPY poetry.lock pyproject.toml ./  
 COPY src/ ./src/  
   
 # Install poetry globally - with the current version of  
 # poetry, there is a known issue where poetry config will  
 # not create config.toml: https://github.com/sdispater/poetry/issues/1179  
 # As such, we create it ourselves.  
 RUN mkdir -p ${HOME}/.config/pypoetry/ && \  
 touch ${HOME}/.config/pypoetry/config.toml && \  
 poetry config settings.virtualenvs.create false && \  
   
 # Set PRODUCTION to anything to invoke installation with --no-dev  
 ARG PRODUCTION  
 RUN poetry install ${PRODUCTION:+--no-dev} 
```

### Changes since 2018

If you read my [2018 version](https://jacobian.org/2018/feb/21/python-environment-2018/), you’ll note that while the general architecture remains the same, two out of the three tools have changed:

*   [pipsi](https://github.com/mitsuhiko/pipsi/) → [pipx](https://pypi.org/project/pipx/). This change is simple: `pipsi` is no longer maintained. `pipx` does the same thing, but is actively maintained.
*   [pipenv](https://pipenv.readthedocs.io/en/latest/) → [poetry](https://poetry.eustace.io/). This move’s more complex. I stoped using Pipenv for a couple of reasons:
    
    *   Governance: the lead of Pipenv was someone with a history of not treating his collaborators well. That gave me some serious concerns about the future of the project, and of my ability to get bugs fixed.
    *   Bugs and rapid API changes. About a year ago, Pipenv had lots of bugs, and a rapid pace of change introducing or changing APIs. I ran into minor issues at least once a week. Nothing was seriously bad, but it generally felt fairly unstable. I kept having to update various automated deploy workflows to work around issues or changes to Pipenv.
    
    Between the two, I lost confidence in Pipenv and switch to Poetry. Since then, the governance issue has been fixed — the person I was concerned about stepped away. The quality issues may have been fixed as well, I’m not sure. Poetry works fine, so I’m sticking with it for now. Watch for the 2022 version of this post when I switch back. (I really hope I’m joking!)
    

  
  
from Hacker News https://ift.tt/2CAFWhm