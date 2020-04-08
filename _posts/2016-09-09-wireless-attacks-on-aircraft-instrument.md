---
title: 'Wireless attacks on aircraft instrument landing systems'
date: 2019-09-28T09:17:00+01:00
draft: false
---

[Wireless attacks on aircraft instrument landing systems](https://www.usenix.org/conference/usenixsecurity19/presentation/sathaye) Sathaye et al., _USENIX Security Symposium 2019_

It’s been a while since we last looked at security attacks against connected real-world entities (e.g., [industrial machinery](https://blog.acolyer.org/2017/06/28/an-experimental-security-analysis-of-an-industrial-robot-controller/), [light-bulbs](https://blog.acolyer.org/2017/06/22/iot-goes-nuclear-creating-a-zigbee-chain-reaction/), and [cars](https://blog.acolyer.org/2016/11/11/error-handling-of-in-vehicle-networks-makes-them-vulnerable/)). Today’s paper is a good reminder of just how important it is becoming to consider cyber threat models in what are primary physical systems, especially if you happen to be flying on an aeroplane – which I am right now as I write this!

The first fully operational _Instrument Landing System_ (ILS) for planes was deployed in 1932. But assumptions we’ve been making since then (and until the present day, it appears!) no longer hold:

> Security was never considered by design as historically the ability to transmit and receive wireless signals required considerable resources and knowledge. However, the widespread availability of powerful and low-cost software-defined radio platforms has altered the threat landscape. In fact, today the majority of wireless systems employed in modern aviation have been shown to be vulnerable to some form of cyber-physical attacks.

Both sections 1 and 6 in the paper give some eye-opening details of known attacks against aviation systems, but to date no-one has published an attack model against one of the most critical of all the aircraft systems: the ILS. Landing is the most dangerous phase of an aircraft’s flight plan, responsible for 59% of all fatal accidents documented by Boeing.

Nearly all commercial flights take place under instrument flight rule (IFR) plans, in which flying by visual reference is either considered unsafe or just not allowed. ILS assists pilots in landing by guiding them on a safe path to the runway, and with autoland systems can even be used to land the plane without human involvement.

> …pilots are trained and instructed to trust the instruments more than their intuition. If the instruments ask them to fly right, the pilots will fly right. This is true especially when flying in weather conditions that force the pilots to follow the instruments. Detecting and recovering from any instrument failures during crucial landing procedures is one of the toughest challenges in modern aviation.

If we could send adversarial signals to make the plane’s ILS system give a reading other than the true one therefore, then that would be very bad indeed. You won’t be surprised to hear of course, that it turns out we can!

### A quick primer on ILS

> ILS play a key, de-facto role in providing precision landing guidance at the majority of airports today…

ILS is made up of three independent subsystems. The _localizer_ provides guidance on whether the plane is to the right or the left of the ideal centreline approach to the runway. The _glidescope_ provides guidance on whether the plane is above or below the ideal glide path onto the runway. The increasing obsolete (replaced by GPS) _marker beacon_ subsystem provides checkpoints that help determine distance to the runway.

![](https://adriancolyer.files.wordpress.com/2019/09/ils-fig-1.jpeg?w=540)

There are three operational standards (with further substandards) based on the maximum decision height for aborting a landing. For CAT I the decision height is 60m above ground, for CAT III it is only 15m. Commercial flights typically fly CAT II or CAT III approaches. Due to the low decision height, attacks on CAT IIII systems can have severe consequences.

ILS is based on radio frequency signals using _space modulation_ to provide horizontal and vertical positioning guidance. Multiple antennas transmit amplitude modulated signals with various powers and phases. Transmitted signals combine in the airspace to give resulting signals with differing depths of modulation (DDM) at different points in the airspace.

Carrier signals are generated with 90Hz and 150Hz tones. For the localisation subsystem, 150 Hz modulation predominates to the right of the centreline, and 90Hz modulation to the left. There’s a similar story in the vertical plane for glidescope.

> Each DDM value directly indicates a specific deviation of the aircraft from the correct touchdown position. For example, the signals combine in space to produce a signal with zero DDM along the center-line of the runway… \[Aircraft\] instruments are calibrated to show full-scale deflection if DDM > 0.155 or DDM < The overshadow attack is an attack where the attacker transmits specially crafted ILS signals at a power level such that the legitimate signals get overpowered by the attacker’s signal at the receiver. The main reason why such an attack works is that the receivers “lock” and process only the strongest received signal.

An attacker calculates amplitude differences between the 90 and 150 Hz tones based on the offset intended to be introduced at the aircraft. The result will cause the needle on the instrument to shift from the ground truth accordingly.

![](https://adriancolyer.files.wordpress.com/2019/09/ils-fig-3.jpeg?w=640)

To make this suitably effective in the cockpit, an _offset correction_ algorithm run by the attacker continuously monitors the current position of the aircraft and adjusts its spoofing signals accordingly. For example, to keep the plane consistently 15m to the left or right of the true centerline, or to cause the plane to be on a glidepath landing short of the runway or overshooting.

![](https://adriancolyer.files.wordpress.com/2019/09/ils-fig-11.jpeg?w=480)

A _spoofing zone detection_ algorithm figures out when to start generating the spoofed signal so that no abrupt change to the instrument readings is caused, thus avoiding detection by pilots. Attacker signals are triggered when the aircraft reaches the shaded region in the figure below.

![](https://adriancolyer.files.wordpress.com/2019/09/ils-fig-10.jpeg?w=480)

### The single-tone attack

The single-tone attack is less sophisticated and requires lower power. The attacker generates only one of the two sideband tones (i.e., 90 Hz _or_ 150 Hz) with appropriate amplitude levels depending on the desired offset. It’s much harder to precisely control the spoofing offset using this mechanism, but it has the advantage of needing much lower transmission power. The attacker could potentially be located inside the aircraft for example, and initiate a low power attack at the last moment before landing.

### Experimental setup and demonstration

Experiments are conducted in an RF shielded environment using the XPlane 11 flight simulator (which qualifies for FAA-certified flight training hours when used at appropriate frame rates), a commercial aviation grade handheld navigation receiver, and a laptop with software-defined radio hardware (USRP B210s). X-Plane was configured to land on the runway of a midsized airport in the US.

![](https://adriancolyer.files.wordpress.com/2019/09/ils-fig-9.jpeg?w=480)

Here’s a video demonstration of an attack in action:

The following figure shows successful localizer spoofing attacks moving a plan up to 50 m left or right of the runway centreline.

![](https://adriancolyer.files.wordpress.com/2019/09/ils-fig-12.jpeg?w=480)

And here are results of glidescope attacks making the plane touchdown too soon or too late on the runway.

![](https://adriancolyer.files.wordpress.com/2019/09/ils-fig-13.jpeg?w=480)

An accredited pilot also performed final approaches on X-Plane 11 using the attack configuration files and scripts, and did not notice anything untoward on any of the plane’s instruments.

> Through both simulations and experiments using aviation grade commercial ILS receivers and FAA recommended flight simulator, we showed that an attacker can precisely control the approach path of an aircraft without alerting the pilots, especially during low-visibility conditions.

### Are the attacks practical in the real world?

> The ideal location of an onground attacker is at a point along the centerline of the runway… In our context, the attacker has to identify locations on the ground such that the phase difference between the legitimate signal and the spoofing signal remains a constant along the line of approach… Attackers within the plane will have to deal with signal attenuation caused by the body of the aircraft itself and position the spoofing signal transmitter accordingly.

That ideal location is probably hard to achieve ;). Drone-mounted signal generator perhaps??

### Are there any easily deployable defences?

No.

All of the backup systems, including GPS, fail to provide sufficient security guarantees, and even supporting cryptographic authentication on ILS signals would still leave systems vulnerable to record and replay attacks.

> Therefore, through this research, we highlight **an open research challenge of building secure, scalable and efficient aircraft landing systems.**

(Emphasis mine). But hey, at least the airlines make sure you have your seatbelt fastened for taxi, take-off, and landing ;).

  
  
from Hacker News https://ift.tt/2n5D4Vg