---
title: 'FBI recommends that you keep your IoT devices on a separate network'
date: 2019-12-06T05:53:00+01:00
draft: false
---

![google-home-mini-smartphone.jpg](https://zdnet3.cbsistatic.com/hub/i/2019/12/06/11f7bb7b-0a8b-4ded-b3c9-3509a45f8657/425e6e16c888ea95fe28a30f534fb212/google-home-mini-smartphone.jpg)

Image:Bence Boros

The FBI says owners of IoT (Internet of Things) devices should isolate this equipment on a separate WiFi network, different from the one they're using for their primary devices, such as laptops, desktops, or smartphones.

"Your fridge and your laptop should not be on the same network," the FBI's Portland office said [in a weekly tech advice column](https://www.fbi.gov/contact-us/field-offices/portland/news/press-releases/tech-tuesday-internet-of-things-iot). "Keep your most private, sensitive data on a separate system from your other IoT devices," it added.

The same advice -- to keep devices on a separate WiFi network or LAN -- has been shared in the past by multiple IT and security experts \[[1](https://www.ckd3.com/blog/2018/10/15/home-network-segmentation-a-must-in-the-iot-era), [2](https://community.ui.com/questions/Creating-a-separate-IOT-network-looking-for-best-practice/137ef556-e12b-4270-88e0-a5b01bab9b3f), [3](https://robpickering.com/ubiquiti-configure-micro-segmentation-for-iot-devices/), [4](https://vninja.net/2019/08/12/unifi-iot-networks/)\].

The reasoning behind it is simple. By keeping all the IoT equipment on a separate network, any compromise of a "smart" device will not grant an attacker a direct route to a user's primary devices -- where most of their data is stored. Jumping across the two networks would require considerable effort from the attacker.

However, placing primary devices and IoT devices on separate networks might not sound that easy for non-technical users. The simplest way is to use two routers.

The smarter way is to use "micro-segmentation," a feature found in the firmware of most WiFi routers, which allows router admins to create virtual networks ([VLANs](https://en.wikipedia.org/wiki/Virtual_LAN)). VLANs will behave as different networks; even they effectively run on the same router.

While isolating IoT devices on their own network is the best course of action for both home users and companies alike, this wasn't the FBI's only advice on dealing with IoT devices. See below:

*   Change the device's factory settings from the default password. A simple Internet search should tell you how—and if you can't find the information, consider moving on to another product.
*   Passwords should be as long as possible and unique for IoT devices.
*   Many connected devices are supported by mobile apps on your phone. These apps could be running in the background and using default permissions that you never realized you approved. Know what kind of personal information those apps are collecting and say "no" to privilege requests that don't make sense.
*   Make sure all your devices are updated regularly. If automatic updates are available for software, hardware, and operating systems, turn them on.

Last week, the same FBI branch office in Portland also gave out similarly good advice on dealing with smart TVs by recommending that device owners [put a piece of black tape over their smart TV's camera lens](https://www.fbi.gov/contact-us/field-offices/portland/news/press-releases/tech-tuesdaysmart-tvs).

The FBI claimed that hackers who take over one of today's fully-featured smart television sets would be able to spy on device owners through the built-in cameras.

While this is prudent advice, it is worth mentioning that there have not been any known cases of this happening -- with hackers taking over a smart TV and spying on its owner.

  
  
from Latest Topic for ZDNet in... https://ift.tt/2qvd33W