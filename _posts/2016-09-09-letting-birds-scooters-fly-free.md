---
title: 'Letting Birds scooters fly free'
date: 2019-10-24T06:41:00+01:00
draft: false
---

(Note: These issues were disclosed to Bird, and they tell me that fixes have rolled out. I haven't independently verified)

[Bird](https://bird.co)

produce a range of rental scooters that are available in multiple markets. With the exception of the Bird Zero\[1\], all their scooters share a common control board described in

[FCC filings](https://fccid.io/2AH4HATD300S)

. The board contains three primary components - a Nordic NRF52 Bluetooth controller, an STM32 SoC and a Quectel EC21-V modem. The Bluetooth and modem are both attached to the STM32 over serial and have no direct control over the rest of the scooter. The STM32 is tied to the scooter's engine control unit and lights, and also receives input from the throttle (and, on some scooters, the brakes).

The pads labeled TP7-TP11 near the underside of the STM32 and the pads labeled TP1-TP5 near the underside of the NRF52 provide Serial Wire Debug, although confusingly the data and clock pins are the opposite way around between the STM and the NRF. Hooking this up via an STLink and using OpenOCD allows dumping of the firmware from both chips, which is where the fun begins. Running strings over the firmware from the STM32 revealed "Set mode to Free Drive Mode". Challenge accepted.

Working back from the code that printed that, it was clear that commands could be delivered to the STM from the Bluetooth controller. The Nordic NRF52 parts are an interesting design - like the STM, they have an ARM Cortex-M microcontroller core. Their firmware is split into two halves, one the low level Bluetooth code and the other application code. They provide an SDK for writing the application code, and working through Ghidra made it clear that the majority of the application firmware on this chip was just SDK code. That made it easier to find the actual functionality, which was just listening for writes to a specific BLE attribute and then hitting a switch statement depending on what was sent. Most of these commands just got passed over the wire to the STM, so it seemed simple enough to just send the "Free drive mode" command to the Bluetooth controller, have it pass that on to the STM and win. Obviously, though, things weren't so easy.

It turned out that passing most of the interesting commands on to the STM was conditional on a variable being set, and the code path that hit that variable had some impressively complicated looking code. Fortunately, I got lucky - the code referenced a bunch of data, and searching for some of the values in that data revealed that they were the AES S-box values. Enabling the full set of commands required you to send an encrypted command to the scooter, which would then decrypt it and verify that the cleartext contained a specific value. Implementing this would be straightforward as long as I knew the key.

Most AES keys are 128 bits, or 16 bytes. Digging through the code revealed 8 bytes worth of key fairly quickly, but the other 8 bytes were less obvious. I finally figured out that 4 more bytes were the value of another Bluetooth variable which could be simply read out by a client. The final 4 bytes were more confusing, because all the evidence made no sense. It looked like it came from passing the scooter serial number to atoi(), which converts an ASCII representation of a number to an integer. But this seemed wrong, because atoi() stops at the first non-numeric value and the scooter serial numbers all started with a letter\[2\]. It turned out that I was overthinking it and for the vast majority of scooters in the fleet, this section of the key was always "0".

At that point I had everything I need to write a simple app to unlock the scooters, and it worked! For about 2 minutes, at which point the network would notice that the scooter was unlocked when it should be locked and sent a lock command to force disable the scooter again. Ah well.

So, what else could I do? The next thing I tried was just modifying some STM firmware and flashing it onto a board. It still booted, indicating that there was no sort of verified boot process. Remember what I mentioned about the throttle being hooked through the STM32's analogue to digital converters\[3\]? A bit of hacking later and I had a board that would appear to work normally, but about a minute after starting the ride would cut the throttle. Alternative options are left as an exercise for the reader.

Finally, there was the component I hadn't really looked at yet. The Quectel modem actually contains its own application processor that runs Linux, making it significantly more powerful than any of the chips actually running the scooter application\[4\]. The STM communicates with the modem over serial, sending it an AT command asking it to make an SSL connection to a remote endpoint. It then uses further AT commands to send data over this SSL connection, allowing it to talk to the internet without having any sort of IP stack. Figuring out just what was going over this connection was made slightly difficult by virtue of all the debug functionality having been ripped out of the STM's firmware, so in the end I took a more brute force approach - I identified the address of the function that sends data to the modem, hooked up OpenOCD to the SWD pins on the STM, ran OpenOCD's gdb stub, attached gdb, set a breakpoint for that function and then dumped the arguments being passed to that function. A couple of minutes later and I had a full transaction between the scooter and the remote.

The scooter authenticates against the remote endpoint by sending its serial number and IMEI. You need to send both, but the IMEI didn't seem to need to be associated with the serial number at all. New connections seemed to take precedence over existing connections, so it would be simple to just pretend to be every scooter and hijack all the connections, resulting in scooter unlock commands being sent to you rather than to the scooter or allowing someone to send fake GPS data and make it impossible for users to find scooters.

In summary: Secrets that are stored on hardware that attackers can run arbitrary code on probably aren't secret, not having verified boot on safety critical components isn't ideal, devices should have meaningful cryptographic identity when authenticating against a remote endpoint.

Bird responded quickly to my reports, accepted my 90 day disclosure period and didn't threaten to sue me at any point in the process, so good work Bird.

(Hey scooter companies I will absolutely accept gifts of interesting hardware in return for a cursory security audit)

\[1\] And some very early M365 scooters

\[2\] The M365 scooters that Bird originally deployed did have numeric serial numbers, but they were 6 characters of type code followed by a / followed by the actual serial number - the number of type codes was very constrained and atoi() would terminate at the / so this was still not a large keyspace

\[3\] Interestingly, Lime made a different design choice here and plumb the controls directly through to the engine control unit without the application processor having any involvement

\[4\] Lime run their entire software stack on the modem's application processor, but because of \[3\] they don't have any realtime requirements so this is more straightforward

  
  
from Hacker News https://ift.tt/33K1iUW