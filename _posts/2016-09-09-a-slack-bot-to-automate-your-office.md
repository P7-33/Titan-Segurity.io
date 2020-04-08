---
title: 'A slack bot, to automate your office using a Raspberry Pi'
date: 2019-10-31T07:42:00+01:00
draft: false
---

[](https://github.com/vitorverasm/slackbot-iot#slack-bot-with-internet-of-things)Slack Bot with internet of things
==================================================================================================================

This is a project of a slack bot, to automate your office/room/lab using some Raspberry Pi GPIO pins.

Usage: [Youtube](https://youtu.be/oNQft1fzo-o)

### [](https://github.com/vitorverasm/slackbot-iot#set-up-your-slack-workspace)Set up your slack workspace

Go to [https://slack.com/](https://slack.com/) . First you'll need to create a new slack workspace to use in this project(or just get the API token from a existing bot in the workspace). Then, go to [https://my.slack.com/services/new/bot](https://my.slack.com/services/new/bot) and choose a username for your bot.

After submit, we now have an API key. Copy this somewhere we'll need later.

[![api key example](https://camo.githubusercontent.com/ed8fcfa1d5b4fe22cfb64d265bcd872595415880/68747470733a2f2f692e696d6775722e636f6d2f4c5055717561462e706e67)](https://camo.githubusercontent.com/ed8fcfa1d5b4fe22cfb64d265bcd872595415880/68747470733a2f2f692e696d6775722e636f6d2f4c5055717561462e706e67)

### [](https://github.com/vitorverasm/slackbot-iot#requirements)Requirements

Now, on your Pi you'll need to install some dependencies:

*   Python3
*   pip3
*   python3-rpi.gpio

```
sudo apt-get install python3 python3-pip python3-dev python3-rpi.gpio -y 
```

And then some packages:

```
pip3 install slackclient 
``````
pip3 install psutil 
```

And download the repository:

```
git clone https://github.com/vitor-veras/slackbot_iot.git 
```

[](https://github.com/vitorverasm/slackbot-iot#configuring-the-python-file)Configuring the python file
------------------------------------------------------------------------------------------------------

After downloading slackbot\_iot.py file there's some things you'll need to adapt to your bot, like your API token that we generated earlier.

```
slack_client = SlackClient("your-api-token-here") 
```

In this next step, we fetch our bot User ID. We will use this later to know when somebody is talking to our bot. We keep it in `slack_user_id`.

```
user_list = slack_client.api_call("users.list") for user in user_list.get('members'): if user.get('name') == "your-bot-name": slack_user_id = user.get('id') break 
```

### [](https://github.com/vitorverasm/slackbot-iot#personalize)Personalize

Now you can personalize your bot with some GPIO pins(any doubts about GPIO pins go to [RPI.GPIO Documentation](https://pypi.python.org/pypi/RPi.GPIO)):

```
from slackclient import SlackClient #GPIO SETUP GPIO.setmode(GPIO.BOARD) GPIO.setwarnings(False) GPIO.setup(8,GPIO.OUT) 
```

And some methods:

```
def lightOn(): GPIO.output(8, 1) print ("light on!") def lightOff(): GPIO.output(8, 0) print ("light off!") 
```

And then link the methods you've created to the bot's matching text part.

```
if re.match(r'.*(light off).*', message_text, re.IGNORECASE): //words you want your bot to recognize lightOff() //the gpio method to execute slack_client.api_call( "chat.postMessage", channel=message['channel'], text="Light off!", //bot response as_user=True) 
```

[](https://github.com/vitorverasm/slackbot-iot#now-run-it)Now, run it!
======================================================================

```
python3 slackbot_iot.py 
```

[![yeeeeah](https://camo.githubusercontent.com/8a7574f099aa0614138b6c2136dd219abd1b1ae7/68747470733a2f2f692e696d6775722e636f6d2f6d764b627963662e706e67)](https://camo.githubusercontent.com/8a7574f099aa0614138b6c2136dd219abd1b1ae7/68747470733a2f2f692e696d6775722e636f6d2f6d764b627963662e706e67)

### [](https://github.com/vitorverasm/slackbot-iot#physical-gpio-setup-example)Physical gpio setup example

This is an example configuration, of how you can use the GPIO pins to turn on a Led.

I'm using a Raspberry Pi B+ model 1 and the GPIO pins 6(Ground) and 8(GPIO). All the pins of this Raspberry that i'm using can be found in this picture: [![gpio-pin](https://camo.githubusercontent.com/c48f312a66dc8aedca2e6a7270155ee9072ad5c4/68747470733a2f2f692e696d6775722e636f6d2f346251346267792e706e67)](https://camo.githubusercontent.com/c48f312a66dc8aedca2e6a7270155ee9072ad5c4/68747470733a2f2f692e696d6775722e636f6d2f346251346267792e706e67)

Now a picture of the physical setup:

`Raspberry Pi + relay board with a Led`

[![setup1](https://camo.githubusercontent.com/195745030a582963fed0105c6950794310670fff/68747470733a2f2f692e696d6775722e636f6d2f764635485451462e6a7067)](https://camo.githubusercontent.com/195745030a582963fed0105c6950794310670fff/68747470733a2f2f692e696d6775722e636f6d2f764635485451462e6a7067)

#### [](https://github.com/vitorverasm/slackbot-iot#more-information-about-the-relay-board-can-be-found-on-relay-board)More information about the relay board can be found on [relay-board](https://github.com/vitor-veras/relay_board.git)

[](https://github.com/vitorverasm/slackbot-iot#links)Links
----------------------------------------------------------

Some useful links :)

Credits to : [http://blog.benjie.me/building-a-slack-bot-to-talk-with-a-raspberry-pi/](http://blog.benjie.me/building-a-slack-bot-to-talk-with-a-raspberry-pi/)

[https://www.raspberrypi.org/documentation/usage/gpio-plus-and-raspi2/](https://www.raspberrypi.org/documentation/usage/gpio-plus-and-raspi2/)

[https://www.digitalocean.com/community/tutorials/how-to-use-rsync-to-sync-local-and-remote-directories-on-a-vps](https://www.digitalocean.com/community/tutorials/how-to-use-rsync-to-sync-local-and-remote-directories-on-a-vps)

[https://www.raspberrypi.org/documentation/remote-access/ssh/](https://www.raspberrypi.org/documentation/remote-access/ssh/)

[](https://github.com/vitorverasm/slackbot-iot#author)Author
------------------------------------------------------------

  
  
from Hacker News https://github.com/vitorverasm/slackbot-iot