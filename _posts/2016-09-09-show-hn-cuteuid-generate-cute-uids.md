---
title: 'Show HN: CuteUID – Generate Cute UIDs'
date: 2019-12-15T04:11:00+01:00
draft: false
---

![](https://avatars2.githubusercontent.com/u/20774517?s=400&v=4 "GitHub - alexdredmon/cuteuid: Generate cute UIDs")  

[](https://github.com/alexdredmon/cuteuid#cuteuid)CuteUID
=========================================================

Generate cute UIDs, i.e. unique(ish) identifiers that are similar in appearance to [UUIDs](https://en.wikipedia.org/wiki/Universally_unique_identifier).

[](https://github.com/alexdredmon/cuteuid#install)Install
---------------------------------------------------------

View on PyPi via [https://pypi.org/project/cuteuid/](https://pypi.org/project/cuteuid/)

[](https://github.com/alexdredmon/cuteuid#usage)Usage
-----------------------------------------------------

```
from cuteuid import generate\_cuteuid generate\_cuteuid() # 1337 UID # 3xampl3a-boy1-goa1-5ucc33dd3p7h # d1v151on-5ho3-1w31-d1571ngu15ha # 7ak351h3-k33p-175a-5ympa7h371c1 generate\_cuteuid(hex\_only\=True) # 1337 UID (hex only) # 10adca9a-4057-5a13-901171ca1136 # 0ff1c1a1-50f7-f33d-43517a73b3d1 # ad01053a-9057-7311-c411d400da50 generate\_cuteuid(emoji\=True) # EmojiUID # ⛹‍♂️🧜‍♂️⬜️3️⃣📏🧹🤴🗾➖🇵🇰📔💹🌳➖🇮🇴🐅🛂🇹🇱➖🇧🇱🗾🕣💿👱‍♀️💞❗️👷🇸🇪🤤🏄‍♂️🍲 # 🏅🧫🏋‍♂️🇹🇱👫🇦🇱🇹🇩🇪🇺➖😚🤽‍♂️👂💮➖👩‍🔬😨👭🇦🇩➖🦏🔷🇵🇦🎁😓🥗🥵🤾‍♀️🧗‍♀️😽🛵🗺 # 👅🏧🙅‍♂️🚇📘🚕👭⛹️‍♀️➖🤽‍♀️🕵️‍♂️🏌‍♀️🦘➖🏄‍♂️👨‍💻🈴🎗➖💕💂‍♂️🏳️🧐😥🇬🇳💀🤕🔻🙆🍟🇵🇼 generate\_cuteuid( # EmojiUID (flags only) emoji\=True, flags\_only\=True ) # 🇱🇧🇼🇸🇮🇹🇲🇳🇬🇹🇦🇲🇬🇶🇬🇾➖🇸🇧🇲🇺🇧🇬🇸🇱➖🇮🇸🏁🇪🇺🇱🇻➖🇿🇲🏴󠁧󠁢󠁳󠁣󠁴󠁿🇸🇸🇵🇲🇬🇶🇧🇬🇳🇮🇲🇰🇿🇼🇸🇭🇬🇶🇮🇴 # 🇱🇮🇮🇸🇼🇫🇹🇩🇵🇫🚩🇧🇫🇬🇶➖🇨🇰🇲🇪🇫🇯🇿🇦➖🇬🇱🇹🇬🇶🇦🇳🇨➖🇿🇼🇲🇬🇸🇮🇬🇭🇺🇬🇧🇦🏴󠁧󠁢󠁥󠁮󠁧󠁿🇹🇹🇻🇺🇳🇴🇧🇶🇹🇻 # 🇲🇦🇬🇶🇧🇱🏴󠁧󠁢󠁳󠁣󠁴󠁿🇹🇻🇱🇷🇻🇳🇲🇾➖🇪🇬🇸🇦🇧🇫🇨🇺➖🇨🇻🇻🇨🇺🇿🇫🇷➖🇹🇩🇲🇷🇸🇰🏴‍☠️🇷🇸🎌🇰🇪🇹🇲🇨🇲🇨🇴🇬🇸🏁 generate\_cuteuid( # EmojiUID (smileys only) emoji\=True, smileys\_only\=True ) # 😇😠😲😢😚😐😝😌➖🙁🤮😣🙁➖🥰😑🤡🤥➖🙁😞😐🤢🤢🤬😂😒🤢😚😰😍 # 😥🤫😨🤢😔😧😩😶➖😰😙🥴😄➖😑😨😲🥴➖😰😲🥳😭🙁😟😚😀😶🤠🤥😄 # 😬🤢🤓🤠🤢😥😪😑➖🥴🙄😠😢➖🙃😆😊🤥➖🤯😒😢🥶😨😌😧🙁😮😣🤭😔
```

[](https://github.com/alexdredmon/cuteuid#preprocess)Preprocess
---------------------------------------------------------------

To rerun 1337 text preprocesing (translating word list into 1337 and hex 1337), update `preprocess.py` to point `WORDLIST_URL` to a URL containing a valid JSON list of words and run:

[](https://github.com/alexdredmon/cuteuid#disclaimer)Disclaimer
---------------------------------------------------------------

This project is intended for entertainment purposes only - it is _not_ recommended for use in your production or intended as a replacement to existing UUID generation mechanisms. It _might_ be a fun thing to include in your non-mission critical personal project(s), provided you're the right kind of weird.

[](https://github.com/alexdredmon/cuteuid#license)License
---------------------------------------------------------

The MIT License (MIT)

Copyright (c) 2019 [Alex Redmon](http://www.alexredmon.com/)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

  
  
from Hacker News https://ift.tt/2RS54sR