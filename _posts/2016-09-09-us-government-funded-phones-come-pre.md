---
title: 'US government-funded phones come pre-installed with unremovable malware'
date: 2020-01-11T05:47:00+01:00
draft: false
---

A US-funded government assistance program is selling budget-friendly mobile phones that come pre-installed with unremovable malicious apps. Malwarebytes Labs investigates the malware's origins.

**UPDATE: January 10, 2020**

At time of original publication, we were not yet able to replicate the malware Android./Trojan.HiddenAds being dropped on our test device, though multiple users had reported that a variant of HiddenAds suddenly installed on their UMX mobile phone.

As of today, we are now able to report that our UMX U686CL test phone has become infected with a variant of HiddenAds we detect as Android/Trojan.HiddenAds.WRACT. This variant has been observed in the wild since spring 2019. It runs silently in the background and does not create an app icon. Evidence of its running in the background can be seen in the mobile device’s notifications. A notification box that changes its title name is highlighted below in red.

![](https://blog.malwarebytes.com/wp-content/uploads/2020/01/HiddenAds2-337x600.png)

![](https://blog.malwarebytes.com/wp-content/uploads/2020/01/HiddenAds3-337x600.png)

The app runs in the background without an icon, though a space remains where it would be.

The notification bar cannot be swiped out in notifications. It stubbornly remains running in the background.

Fortunately, there is a way to find and uninstall this app. If you press and hold the notification, it will give the option to go to _MORE SETTINGS._

![](https://blog.malwarebytes.com/wp-content/uploads/2020/01/HiddenAds4-337x600.png)

After clicking _MORE SETTINGS,_ it will take you to the app’s notification settings. From there, press the app’s icon at the top.

![](https://blog.malwarebytes.com/wp-content/uploads/2020/01/HiddenAds5-337x600.png)

Lastly, it will take you to the app’s _App info_, where you can uninstall.

![](https://blog.malwarebytes.com/wp-content/uploads/2020/01/HiddenAds6-337x600.png)

Of course, [Malwarebytes for Android](http://www.malwarebytes.com/android) takes care of this as well.

\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

A United States–funded mobile carrier that offers phones via the Lifeline Assistance program is selling a mobile device pre-installed with not one, but two nefarious applications. Assurance Wireless by Virgin Mobile offers the UMX U686CL phone as their most budget conscious option. At only $35 under the government-funded program, it’s an attractive offering. However, what it comes installed with is appalling.

### Not just malicious, but pre-installed

In October 2019, we saw several complaints in our support system from users with a government-issued phone reporting that some of its pre-installed apps were malicious. We purchased a UMX U686CL to better assist our customers and verify their claims.  

We informed Assurance Wireless of our findings and asked them point blank why a US-funded mobile carrier is selling a mobile device infected with pre-installed malware? After giving them adequate time to respond, we unfortunately never heard back. Here’s what we discovered.

The first questionable app found on the UMX U686CL poses as an updater named Wireless Update. Yes, it is capable of updating the mobile device. In fact, it’s the only way to update the mobile device’s operating system (OS). Conversely, it is also capable of auto-installing apps without user consent.

Thus, we detect this app as [Android/PUP.Riskware.Autoins.Fota.fbcvd](https://blog.malwarebytes.com/detections/android-pup-riskware-autoins-fota/), a detection name that should sound familiar to Malwarebytes for Android customers. That’s because the app is actually a variant of [Adups](https://blog.malwarebytes.com/cybercrime/2017/12/mobile-menace-monday-upping-the-ante-on-adups-fwupgradeprovider/), a China-based company caught collecting user data, creating backdoors for mobile devices and, yes, developing auto-installers.

From the moment you log into the mobile device, Wireless Update starts auto-installing apps. To repeat: There is no user consent collected to do so, no buttons to click to accept the installs, it just installs apps on its own. While the apps it installs are initially clean and free of malware, it’s important to note that these apps are added to the device with zero notification or permission required from the user. This opens the potential for malware to unknowingly be installed in a future update to any of the apps added by Wireless Update at any time. 

### Not just pre-installed, but unremovable

It’s with great frustration that I must write about another [unremovable pre-installed app](https://blog.malwarebytes.com/cybercrime/2019/01/the-new-landscape-of-preinstalled-mobile-malware-malicious-code-within/) found on the UMX U686CL phone: the mobile device’s own _Settings_ app functions as a heavily-obfuscated malware we detect as [Android/Trojan.Dropper.Agent.UMX](https://blog.malwarebytes.com/detections/android-trojan-dropper/). Because the app serves as the dashboard from which settings are changed, removing it would leave the device unusable.

Android/Trojan.Dropper.Agent.UMX shares characteristics with two other variants of known mobile Trojan droppers. The first characteristic is that it uses the same receiver and service names. The receiver name ends with _ALReceiver_ and the service name ends with _ALAJobService._ These names alone are too generic to make a solid correlation. But, coupled with the fact that the code is almost identical, and we can confidently confirm a match. 

The only difference between the two codes are their variable names. The more discernible variant of this malware uses Chinese characters for variable names. Therefore, we can assume the origin of this malware is China.

![](https://blog.malwarebytes.com/wp-content/uploads/2019/12/2-2.png)

  
Variant of malware with Chinese variable names

The second characteristic it shares is containing an encoded string within the code. Decoding this string reveals a hidden library file named _com.android.google.bridge.LibImp._

![](https://blog.malwarebytes.com/wp-content/uploads/2019/12/b64-02_edit.jpg)

  
Decoded string with  
_com.android.google.bridge.LibImp_

Let’s take some time to look at how the code flows while decoding _com.android.google.bridge.LibImp_. It first grabs the encoded string and decodes using Base64 decoding.

![](https://blog.malwarebytes.com/wp-content/uploads/2019/12/flow1-600x89.png)

  
Encoded string

![](https://blog.malwarebytes.com/wp-content/uploads/2019/12/flow2.png)

  
Base64 decoding

It then loads the decoded library into memory using _DexClassLoader_.

![](https://blog.malwarebytes.com/wp-content/uploads/2019/12/flow3.png)

  
_DexClassLoader_ loading decoded string

After the library is loaded into memory, it then drops another piece of malware known as [Android/Trojan.HiddenAds](https://blog.malwarebytes.com/android/2020/01/united-states-government-funded-phones-come-pre-installed-with-unremovable-malware/Android/Trojan.HiddenAds).

Although we have yet to reproduce the dropping of additional malware ourselves, our users have reported that indeed a variant of HiddenAds suddenly installs on their UMX mobile device.

### The malware origin

In addition to the malware being of Chinese origin, it’s noteworthy to mention that this UMX mobile device is made by a Chinese company as well. This could simply be a coincidence rather than explicit malcontent—we cannot confirm if the makers of the device are aware there is Chinese malware pre-installed.

### No current resolution

Although we do have a way to [uninstall pre-installed apps for current Malwarebytes users](https://forums.malwarebytes.com/topic/216616-removal-instructions-for-adups/), doing so on the UMX has consequences. Uninstall Wireless Update, and you could be missing out on critical updates for the OS. We think that’s worth the tradeoff, and suggest doing so. 

But uninstall the _Settings_ app, and you just made yourself a pricey paper weight. We do offer an attempt to remediate such pre-installed malware in our blog: [The new landscape of pre-installed mobile malware: malicious code within](https://blog.malwarebytes.com/cybercrime/2019/01/the-new-landscape-of-preinstalled-mobile-malware-malicious-code-within/). See section: _Attempting to remediate._

### Pre-installed malware getting worse, as foreshadowed

As I have highlighted in this blog and blogs past, pre-installed malware continues to be a scourge for users of mobile devices. But now that there’s a mobile device available for purchase through a US government-funded program, this henceforth raises (or lowers, however you view it) the bar on bad behavior by app development companies.

Budget should not dictate whether a user can remain safe on his or her mobile device. Shell out thousands for an iPhone, and escape pre-installed maliciousness. But use government-assisted funding to purchase a device and pay the price in malware? That’s not the type of malware-free existence we envision at Malwarebytes.

### Final words on UMX U686CL

Having an actual UMX U686CL in my hands, I can tell you it is not a bad phone. It feels solid in hand and runs smoothly. Sure, it’s not the fastest mobile device, but it’s a fully capable smart phone. In general, without the malware, this device is a good option for anyone on a budget. 

It’s important to realize that UMX isn’t alone. There are many reports of budget manufactures coming pre-installed with malware, and these reports are increasing in number. Although I don’t have the answer to this widespread issue, I can say that US citizens using the Lifeline Assistance Program and many others on a tight budget deserve more. Stay safe out there.

  
  
from Hacker News https://ift.tt/306Wl8s