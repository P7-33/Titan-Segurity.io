---
title: 'User Agent Changes'
date: 2019-12-13T01:33:00+01:00
draft: false
---

![](https://vivaldi.com/wp-content/uploads/braydon-anderson-wOHH-NUTvVc-unsplash.jpg "User Agent Changes | Vivaldi Browser")  

### What is a User Agent

A browser’s User Agent is a line of text that is sent from the browser to the website when it connects, telling the site which platform (Operating System), architecture, and browser (including version) is being used.

When used properly, the User Agent allows a website to present a better experience for the user. For example on sites that offer software for download, the most appropriate option could be automatically suggested, or on pages that provide help configuring a browser’s settings, custom steps could be shown depending on what browser is being used.

### The problems

While all the above sounds great, over time the User Agent has been misused by some web developers and occasionally even abused by the bigger tech companies, in positions of power.

A fairly significant percentage of the bug reports we receive, actually have very little to do with our code. Vivaldi is frequently blocked, shown alternate (incorrect) versions of a website or spurious warnings are displayed, based solely on the User Agent.

Sometimes it could arguably be considered a mistake, with the development team of a website naïvely assuming that only browsers they have personally tested be given access to their site, blocking anything that isn’t. This is obviously wrong for a truly open web (as it limits the field to only the big players) but it seems to be a common mistake, dating back to the early days of the web. And thus, modern web browser User Agents typically include both their own information and additionally that of other browsers. Consider the (Linux x64) User Agent for our current Vivaldi stable. It reads like so:

`Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.99 Safari/537.36 Vivaldi/2.9.1705.41`

Most of the above we have just inherited from the Chromium project, who in turn inherited it from Safari and so on. Although it is a big hack job, it works surprisingly well in much the same way as providing someone else’s name can get you into an exclusive club. If you drop the right name, you can get in anywhere!

As well as listing names that help you bypass the virtual bouncer, you have to be careful not to list names that will get you into trouble. Consider the User Agents of modern Opera or (Chromium-based) Edge. Neither want to be incorrectly recognized as their former incarnations, so they don’t risk listing their real names in their current User Agents but rather choose to misspell their product names to “OPR” and “EDG” respectively. Users (understandably) often report such issues as bugs but they are fully intentional.

While the above types of problems could be labeled “mistakes”, some forms of blocking look more nefarious. We also often encounter websites that block the exact string “Vivaldi”, with no contact or warning to us. This is particularly problematic when the larger technology behemoths (some of whom we directly compete with in the browser space) do this. When this happens and error messages are displayed, or intentionally invalid copies of the website are sent our way, users typically assume Vivaldi has an issue, and even sometimes struggle to comprehend that anyone would target us. But target us, they do. This can be clearly seen by us in testing, by intentionally misspelling our name by one character in our User Agent, e.g. “Vivaldo” or “Vxvaldi”. Sadly a host of site-specific workarounds (let’s not call them “fixes”) have to be baked into the browser permanently.

Here are just a handful of current examples:

*   On Google.com if you present a Vivaldi user agent and arrive via a redirect, the search text box will be misaligned
*   On Google Docs if you present a Vivaldi user agent you will receive a warning
*   On Facebook’s WhatsApp web interface if you present a Vivaldi user agent, you cannot enter the site and are advised to switch to one of our competitors
*   On Microsoft Teams (chat and collaboration website), presenting a Vivaldi user agent will stop you from being able to use the website
*   On Netflix, presenting a Vivaldi user agent results in a suggestion to install Silverlight to play videos… yes… really… Silverlight!

If you want to test these issues you can do so in _any_ browser you like. Just set the User Agent to the Vivaldi one listed above and try for yourself.

In all such cases, we have tried via various means to get someone in the respective companies to stop breaking these sites for our users. Here, for example, is our [very first tweet to WhatsApp about the issue over](https://twitter.com/vivaldibrowser/status/644173304404836352), four years ago. Follow up requests have been made both by us and our more technical fans multiple times since then, via various contact channels but to no avail.

### Reversing the logic

For the next release of Vivaldi, we have decided to try something different. The problem with our current approach is that with the web being almost infinite, we can’t possibly discover all the websites who have blocks set against us. Thus maintaining a list of sites where we present a non-Vivaldi User Agent is difficult. Instead, we will try doing the reverse. For a handful of sites where we know the label Vivaldi (and our version number) is responsibly used, we will present our full User Agent. Those sites being our own and a handful of interesting alternative search engines: [duckduckgo.com](https://duckduckgo.com), [ecosia.org](https://ecosia.org), [qwant.com](https://qwant.com), and [startpage.com](https://startpage.com). Every other site will get a User Agent that appears to be identical to Chrome.

There is a downside for us in doing this since Vivaldi will effectively disappear from third party rankings of browser popularity (we will be indistinguishable from Chrome) but that is a price we will happily pay to provide the best website compatibility for our users.

P.S. On the bright side there is a recent [proposal to fix the problems with User Agents](https://github.com/WICG/ua-client-hints). We will certainly keep our eye on it and revisit the situation in the future.

_Main photo by [Braydon Anderson](https://unsplash.com/@braydona)_

  
  
from Hacker News https://ift.tt/35ayshF