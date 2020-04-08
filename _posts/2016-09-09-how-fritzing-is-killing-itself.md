---
title: 'How Fritzing is killing itself'
date: 2019-11-14T01:23:00+01:00
draft: false
---

It is logical that Open Source organizations also like to earn money. Free software does not mean that there is no money to be made with it. After all, these developers must also be able to feed their families.

Strange methods of making money from open source software have been seen before. For example, [OpenCollective](https://github.com/opencollective/opencollective) is a collective that tries to support open source. One way is to persuade users to advertise by means of a message in the terminal.

![](https://bowero.nl/blog/wp-content/uploads/2019/11/ad2.png)

This is an innocent way, of course. Funding had another approach. A developer named [Feross Aboukhadijeh](https://feross.org/about/) said that he had already spent 3,000 unpaid hours developing open source software and he wanted to see something in return. An understandable point of view.

To achieve this, he started with [Funding](https://github.com/feross/funding), an experiment in which he placed advertisements in the terminals of the users of his software.

![](https://bowero.nl/blog/wp-content/uploads/2019/11/ad.png)

Image: William Hilton

Of course, this caused a lot of commotion in the open source software world. A developer even went so far as to build an [adblocker for the terminal](https://github.com/kethinov/no-cli-ads). The turmoil was of course exactly what he wanted. He raised an important issue: how can we support the developers of the open source software?

After a few days Feross thought it was enough and he stopped the project. You can read his explanation [on his blog](https://feross.org/funding-experiment-recap/).

Donations are still the best accepted way to make money from open source software. Unfortunately, donations are not made just like that, which is why creative ways need to be devised. For example, you can use donations to obtain extra content, “buy someone a coffee”, etc.

Many companies try to encourage you to donate, either by clearly displaying the button or by initiatives such as those of OpenCollective. One of the companies that strongly encourages donations is Fritzing, but they do so very misleadingly.

If you click on “Download”, you will not receive the download file, but will be automatically redirected to Paypal. You could then cancel the payment via Paypal to be sent back to the page, but then the Fritzing download still doesn’t load.

If you dive into the code, you’ll soon find out why. Fritzing has deliberately made sure that users who pay in this confusion, will see a different page than other users. This is the code of this form:

As you can see, the parameters “return” and “cancel\_return” have two different values. This nonsense from Fritzing makes it very difficult to download this software in a normal way.

As a result, there will undoubtedly be more people looking at the alternatives to Fritzing. As the alternatives are very good, the number of users will gradually decrease. Furthermore, this will clearly reduce sympathy for the developers, which will undoubtedly reduce the number of donations in the long term.

Are you annoyed about this behaviour, but do you need software to draw your schematics? Take a look at [one of the more than 50 alternatives](https://alternativeto.net/software/fritzing/).

  
  
from Hacker News https://ift.tt/2qLNBHc