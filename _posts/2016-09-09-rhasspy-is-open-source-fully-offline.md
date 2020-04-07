---
title: 'Rhasspy is an open source, fully offline voice assistant toolkit'
date: 2020-01-01T02:55:00+01:00
draft: false
---

![](https://rhasspy.readthedocs.io/en/latest/img/rhasspy.svg "Rhasspy logo")

Rhasspy (pronounced RAH-SPEE) is an [open source](https://github.com/synesthesiam/rhasspy), fully offline voice assistant toolkit for [many languages](https://rhasspy.readthedocs.io/en/latest/#supported-languages) that works well with [Home Assistant](https://www.home-assistant.io/), [Hass.io](https://www.home-assistant.io/hassio/), and [Node-RED](https://nodered.org).

You specify voice commands in a [template language](https://rhasspy.readthedocs.io/en/latest/training/):

```
[LightState] states = (on | off) turn (){state} [the] light 
```

and Rhasspy will produce [JSON](https://json.org) events that can trigger actions in [home automation software](https://www.home-assistant.io/docs/automation/trigger/#event-trigger) or [Node-RED flows](https://rhasspy.readthedocs.io/en/latest/usage/#node-red):

```
{ "text": "turn on the light", "intent": { "name": "LightState" }, "slots": { "state": "on" } } 
```

Rhasspy is **optimized for**:

Getting Started
---------------

Ready to try Rhasspy? Follow the steps below and check out the [tutorials](https://rhasspy.readthedocs.io/en/latest/tutorials/).

1.  Make sure you have the [necessary hardware](https://rhasspy.readthedocs.io/en/latest/hardware/)
2.  Choose an [installation method](https://rhasspy.readthedocs.io/en/latest/installation/)
3.  Access the [web interface](https://rhasspy.readthedocs.io/en/latest/usage/#web-interface) to download a profile
4.  Author your [custom voice commands](https://rhasspy.readthedocs.io/en/latest/training/) and train Rhasspy
5.  Connect Rhasspy to [Home Assistant](https://rhasspy.readthedocs.io/en/latest/usage/#home-assistant) or a [Node-RED](https://rhasspy.readthedocs.io/en/latest/usage/#node-red) flow

Getting Help
------------

If you have problems, please stop by the [Rhasspy community site](https://community.rhasspy.org) or [open a GitHub issue](https://github.com/synesthesiam/rhasspy/issues).

Supported Languages
-------------------

Rhasspy supports the following languages:

*   English (`en`)
*   German (`de`)
*   Spanish (`es`)
*   French (`fr`)
*   Italian (`it`)
*   Dutch (`nl`)
*   Russian (`ru`)
*   Greek (`el`)
*   Hindi (`hi`)
*   Mandarin (`zh`)
*   Vietnamese (`vi`)
*   Portuguese (`pt`)
*   Swedish (`sv`)
*   Catalan (`ca`)

Intended Audience
-----------------

Rhasspy is intended for advanced users that want to have a voice interface to Home Assistant, but value **privacy** and **freedom** above all else. There are many other voice assistants, but none (to my knowledge) that:

1.  Can function **completely disconnected from the Internet**
2.  Are entirely free/open source
3.  Work well with Home Assistant, Hass.io, and Node-RED

If you feel comfortable sending your voice commands through the Internet for someone else to process, or are not comfortable with rolling your own Home Assistant automations to handle intents, I recommend taking a look at [Mycroft](https://mycroft.ai).

  
  
from Hacker News https://ift.tt/2QEtKTD