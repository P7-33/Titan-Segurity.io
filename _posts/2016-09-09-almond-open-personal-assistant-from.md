---
title: 'Almond: Open Personal Assistant from Stanford'
date: 2019-12-02T04:01:00+01:00
draft: false
---

The current state of virtual personal assistants — Alexa, Cortana, Google, and Siri — leaves something to be desired. The speech recognition is mostly pretty good. However, customization options are very limited. Beyond that, many people are worried about the privacy of their data when using one of these assistants. Stanford Open Virtual Assistant Lab has rolled out [Almond](https://almond.stanford.edu/), which is open and is reported to have better privacy features.

Like most other virtual assistants, Almond has skills that determine what it can do. You can use Almond in a browser, on a Google phone, or as a command line application. It all lives on [GitHub](https://github.com/stanford-oval), so if you don’t like something you are free to fix it.

The skills are on a market-like thing known as Thingpedia. There are a surprising number, although not nearly as many as commercial devices. The assistant can integrate with Nest, GNOME, Gmail, Twitter, Slack, and many more services.

The natural language processing is impressive. Here are some examples from the web site:

*   When the New York Times has an article about China, translate the headline to Chinese, then email it to my friend.
*   When I leave home, turn off the heating.
*   When I post to Twitter, copy the post to Facebook.
*   Get the Bitcoin price and then send it to my colleague on Slack.

The web site is a little glitzy and the GitHub will take some time to parse. However, the [documentation](https://almond.stanford.edu/doc/getting-started.md) is very readable.

Almond is begging to be run on a smart speaker and there is [a way to do it](https://github.com/stanford-oval/almond-server). You can even run it using a docker image that is already configured.

What we really want to do is build Almond [into a robot](https://hackaday.com/2019/08/11/diy-personal-assistant-robot-hears-and-sees-all/). For now, we may just repurpose a [Google Raspberry Pi](https://hackaday.com/2017/05/16/sudo-google-assistant/).

  
  
from Hackaday https://ift.tt/33CE0Qz  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)