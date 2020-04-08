---
title: 'Tor Snowflake turns your browser into a proxy for users in censored countries'
date: 2019-10-17T06:02:00+01:00
draft: false
---

![tor-snowflake-chrome-extension.png](https://zdnet4.cbsistatic.com/hub/i/2019/10/16/1a9bbb51-8cdd-482c-b319-7b2d572fc767/e674cb7ad69695f4363225676e6ba27d/tor-snowflake-chrome-extension.png)

Image: Tor Project

The Tor Project has published Chrome and Firefox extensions over the summer to help users in censored countries connect to the Tor network.

**The extensions are not meant to be installed by users living in oppressive countries** that block access to the Tor network. **They're meant for those living in free countries**, where governments don't block Tor access.

Users who want to help those living under oppressive regimes can install the Tor Snowflake extensions -- for [Chrome](https://chrome.google.com/webstore/detail/snowflake/mafpmfcccpbjnhfhjnllmmalhifmlcie) or [Firefox](https://addons.mozilla.org/en-US/firefox/addon/torproject-snowflake/).

The two extensions effectively transform a user's browser into a proxy, allowing users in oppressive countries to connect through the extension (and the user's computer) to the Tor network.

![tor-snowflake-schematic.png](https://www.zdnet.com/article/tor-snowflake-turns-your-browser-into-a-proxy-for-users-in-censored-countries/#ftag=RSSbaffb68)

<span><img src="https://zdnet4.cbsistatic.com/hub/i/2019/10/17/caf845d1-8412-4122-ba87-30b53b20b8fe/105f79e3ac61e6f09bd49a92b0c82113/tor-snowflake-schematic.png" alt="tor-snowflake-schematic.png" /></span>

Image: Tor Project

To better understand how Tor Snowflake works, one must first understand the intricacies of the Tor network itself, and it's current anti-censorship solutions (the Tor bridges system).

The Tor network is a collection of servers that encrypt and bounce traffic between each other, to anonymize a user's real location.

This network has multiple types of servers. There are Tor "guard" servers that serve as entry points to the Tor network. There are Tor "relays" that bounce the traffic inside the network and help anonymize the user's location. And then there are Tor "exit" servers, through which Tor traffic reconnects to the regular internet.

Due to their nature, the IP addresses of Tor guard servers are public, listed on the Tor website, so Tor clients (usually the Tor Browser) can read the list and connect to the Tor network through a safe server.

Over the years, countries have realized that they can block access to these servers, and effectively block a user from accessing Tor.

The Tor Project fought back by developing another type of Tor server, called a [Tor bridge](https://2019.www.torproject.org/docs/bridges.html.en). These are Tor guard servers that don't have their IP addresses listed publicly.

Users in oppressive regimes can configure their Tor Browser to request a Tor bridge server IP address, and use this as their entry point into the Tor network.

However, Tor bridges aren't a foolproof solution. Oppressive regimes have realized they can also request access to Tor bridges as well, and compile a list of IP addresses to block alongside the regular Tor guards.

Tor Snowflake is the Tor Project's reaction to governments that have managed to block Tor bridges.

Tor Snowflake helps the Tor Project create a constantly moving mesh of proxies that no government could ever block.

Once users install the Chrome or Firefox extensions, users in countries like Iran or China can connect to regular Tor bridges through users' browsers.

The more users install the extensions, the more proxies are available.

### How to use Tor Snowflake

For users living in free countries, all they have to do is install the Tor Snowflake extensions -- for Chrome or Firefox.

If they don't want to install an extension, they can also access [this web page](https://snowflake.torproject.org/embed), enable Snowflake, and keep the tab open.

For users living in oppressive countries, all they have to do is modify the Tor Browser's network settings to use the "snowflake" bridge setting, as in the image below.

![tor-settings.png](https://www.zdnet.com/article/tor-snowflake-turns-your-browser-into-a-proxy-for-users-in-censored-countries/#ftag=RSSbaffb68)

<span><img src="https://zdnet4.cbsistatic.com/hub/i/2019/10/17/7680d9fa-0a32-454c-aebc-7164dcaf7cbe/63600d8fd2d6bff1eecc2bc251044cb6/tor-settings.png" alt="tor-settings.png" /></span>

Image: Tor Project

The only downside to Tor Snowflake is the fact that another user's traffic now flows through your browser, taking up your bandwidth. Users on metered connections are advised against activating Snowflake, as this will incur additional costs.

### Windows support coming soon

Work on the [Tor Snowflake project](https://snowflake.torproject.org/) started years ago, [in 2016](https://lists.torproject.org/pipermail/tor-dev/2016-January/010310.html).

Initially, Snowflake was only available for Tor Browser users on Linux, and later Mac. There were also no browser extensions, but only the Snowflake web page that needed to be left open in a tab at all times.

But while the project looked dead for a while, things kicked back into gear over the summer, when Tor developers published the two browser extensions.

Things moved along even further this month when Tor devs also added support for "snowflake" connections to the Tor Browser for Windows.

[Snowflake Windows support](https://blog.torproject.org/new-release-tor-browser-90a7) is only available in Tor Browser alpha releases, but Snowflake should make its way into the stable version of the Tor Browser sometime next year.

  
  
from Latest Topic for ZDNet in... https://ift.tt/2OVQu1Y