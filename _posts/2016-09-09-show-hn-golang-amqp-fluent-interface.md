---
title: 'Show HN: Golang AMQP Fluent Interface'
date: 2020-01-09T04:47:00+01:00
draft: false
---

[](https://github.com/reddec/fluent-amqp#fluent-amqp)Fluent AMQP
================================================================

[![FA](https://github.com/reddec/fluent-amqp/raw/master/docs/logo.svg?sanitize=true)](https://github.com/reddec/fluent-amqp/blob/master/docs/logo.svg)

[![Docker Automated build](https://camo.githubusercontent.com/ab65e5bac40e526831d467eadcb97d3121a719e8/68747470733a2f2f696d672e736869656c64732e696f2f646f636b65722f6275696c642f7265646465632f666c75656e742d616d71702e737667)](https://hub.docker.com/r/reddec/fluent-amqp/) [![Telegram Sender](https://camo.githubusercontent.com/d0c46d62715fc19ba97484297017ff3cd98cbf11/68747470733a2f2f696d672e736869656c64732e696f2f646f636b65722f6175746f6d617465642f7265646465632f666c75656e742d616d71702d74656c656772616d2d73656e6465722e737667)](https://hub.docker.com/r/reddec/fluent-amqp-telegram-sender/) [![Snap Status](https://camo.githubusercontent.com/6f5c59ea3c4c86ba95b39dca1af87defc6fc4107/68747470733a2f2f6275696c642e736e617063726166742e696f2f62616467652f7265646465632f666c75656e742d616d71702e737667)](https://build.snapcraft.io/user/reddec/fluent-amqp)

[![](https://camo.githubusercontent.com/4f540be3ecd45ffdf93f9a4399da27b2cf60cb7f/68747470733a2f2f676f646f632e6f72672f6769746875622e636f6d2f7265646465632f666c75656e742d616d71703f7374617475732e737667)](https://godoc.org/github.com/reddec/fluent-amqp)

Library that provides fluent and easy wrapper over [streadway-amqp](https://github.com/streadway/amqp) API. Adds such features like:

*   Reconnectiong. Will restore all defined infrastructure
*   Non-blocking processing of messages
*   Optional auto-requeue (with delay)
*   Signing and verifiying messages by public/private pair

[API documentation](https://godoc.org/github.com/reddec/fluent-amqp)

[](https://github.com/reddec/fluent-amqp#signing-and-verification)Signing and verification
------------------------------------------------------------------------------------------

Hash algorithm (x509) SHA512 with RSA, sign - SHA512.

The signer (producer) should use private key to sign content of message body and message id.

The validator (consumer) should use public certificate to validate content of message and message id against signature and should drops invalid or duplicated messages.

The sign should be put to a header (`X-Signature` by default: see `DefaultSignatureHeader` constant in godoc) as **binary** object (**not hex or base64 encoded**).

```
DATA = BYTES(ID) ... BYTES(BODY) # SIGN via PKCS#1 v1.5 SIGN_HEADER_BODY = SIGN_SHA512(PRIVATE_KEY, DATA) 
```

[](https://github.com/reddec/fluent-amqp#default-message)Default message
------------------------------------------------------------------------

Message by default has:

*   Delivery type - persistent
*   Time - current time in UTC

[](https://github.com/reddec/fluent-amqp#templates)Templates
------------------------------------------------------------

`amqp-recv` supports templating output `-o template`. Template content read from STDIN.

Root template object is a [amqp.Delivery](https://github.com/streadway/amqp/blob/dcfad599551a8042d2e1971a496f31624a7f4738/delivery.go#L28) with functions from [Sprig](http://masterminds.github.io/sprig/) plus additional methods like:

*   `asText` - converts bytes to string

1.  Basic example:

Print same as `-o plain`.

```
echo '' | amqp-recv -o template ... 
```

2.  Notification to telegram

Use combination of basic CLI utils and templates.

```
TOKEN="xxxyyyy" # BotFather token for Telegram (see here: https://t.me/BotFather) CHAT\_ID="1234567" # Target Telegram chat ID (find yours: https://t.me/MyTelegramID\_bot) QUEUE="notification" # queue name should be defined if persistent required EXCHANGE="amqp.topic" # source of notification TYPE="topic" # exchange type TOPIC="#" # specify subject that will be sent over telegram (# - everything) while true; do echo -n -e 'Subject: \\n\\n' | amqp-recv -o template -Q $QUEUE -e $EXCHANGE -k $TYPE "$TOPIC" \> message.txt curl -f -X POST --data "text=$(cat message.txt)" --data "chat\_id=${CHAT\_ID}" "https://api.telegram.org/bot${TOKEN}/sendMessage" || exit 1 done
```

[](https://github.com/reddec/fluent-amqp#command-line-utilities)Command line utilities
--------------------------------------------------------------------------------------

*   [amqp-exec](https://github.com/reddec/fluent-amqp/blob/master/cmd/amqp-exec) - CGI like daemon to listen message and run executable (and send reply)
*   [amqp-recv](https://github.com/reddec/fluent-amqp/blob/master/cmd/amqp-recv) - Receive message from AMQP (like `cat` command)
*   [amqp-send](https://github.com/reddec/fluent-amqp/blob/master/cmd/amqp-send) - Send message to AMQP (like `wall` command)

### [](https://github.com/reddec/fluent-amqp#installation)Installation

[![Get it from the Snap Store](https://camo.githubusercontent.com/7775b8304b868ad9b82b7e92aa390f4dec6a6928/68747470733a2f2f736e617063726166742e696f2f7374617469632f696d616765732f6261646765732f656e2f736e61702d73746f72652d626c61636b2e737667)](https://snapcraft.io/fluent-amqp)

  
  
from Hacker News https://ift.tt/36AHF3N