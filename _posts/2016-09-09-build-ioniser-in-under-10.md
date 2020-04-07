---
title: 'Build an Ioniser in Under $10'
date: 2019-12-29T07:07:00+01:00
draft: false
---

This is a project which I wanted to do around 2 years back but never got around to building it. It’s nothing too fancy or super high tech. Anyone with some DIY capabilities should be able to pull this off without breaking a sweat. I have open-sourced the entire design, Bill of materials and you should be to order the parts and build one for yourselves in under $10. You can download the hardware files [here](http://amaldev.blog/wp-content/uploads/2019/12/Ioniser-hardware-files-1.zip). Do email me pictures of your build at amaldev.000@gmail.com if you happen to make one. 😀

#### Back Story

My current apartment in [Mumbai](https://en.wikipedia.org/wiki/Mumbai) is right next to a decently busy road. Ever since I moved in, I have always had the issue of dust settling in every week on everything if I open the windows. Cleaning that up every week is a pain. So I wanted to buy an air purifier for the room. Then I thought, “How hard will be it to build one myself?”. Did some quick research and concluded that I needed to make myself an ionizer(By the way, there is a big difference between an ioniser and a purifier, more on that later in the post). Heck, then life and my other projects got in the way and I never got to build one. 

Few people over the last few months have approached me asking how I go about designing and building devices and complex systems(I do take up technology consultancy projects on the side for companies). So I thought I should detail out a relatively simple project, taking everyone through my thought process while building something from scratch.

So let’s start. Let’s build an Ioniser.

#### **Research phase:**

_To be completely honest, I did this 2 years ago and I sort off knew what I needed to build. But play along with me on this one._ 🙂

Start searching on Google on what you want to build. First let’s learn what an ioniser is, what its fundamental principle of operation is.  [Wiki](https://en.wikipedia.org/wiki/Air_ioniser) says

An air ioniser (or negative ion generator or Chizhevsky’s chandelier) is a device that uses high voltage to ionise (electrically charge) air molecules. Negative ions, or anions, are particles with one or more extra electrons, conferring a net negative charge to the particle.

That’s easy enough. If you go on to read the rest of the article, you will find that air ionisers are used to remove particles from the air by imparting a negative charge to the particles and these negatively charged particles get attracted to a positively charged surface(like a wall/ground). Then particles easily settle down(removing itself from the air). That’s cool. That’s exactly what we wanted to do. Remove dust particles from the air so that you don’t breathe that much in.

So from the first 5 mins of searching around, we know that we need to create a high voltage system to impart a negative charge to particles. This information was slightly unsettling to me initially because I haven’t built high voltage systems before and things can go wrong pretty fast if I am not cautious playing with it.

Next, we go ahead and search for devices which are already there in the market based on the same technology. What I am trying to see here is to look at what sort of circuits people have used to build this before. If there is a device in the market using the same tech, learn from it.

People would have put in a lot of engineering man-hours to build that. Learn from that so that you build your system to atleast similar or rather learn from their mistakes and make it better.

Here also, Google is your best resource. I keep seeing that ionisers have been built even in the 1980s. If this tech is that old, then I should look at teardowns of products using this. Search then on google for ioniser teardowns and voila there are lots of videos showing the insides of the device. I would recommend checking [BigClive’s](https://www.youtube.com/user/bigclivedotcom) videos on this. They are really good.

From these videos, I was able to conclude that a high voltage system can be built with a voltage multiplier and it’s not that intimidating to build one. With this info, lets move on the electrical system design.

#### **Electrical system design:**

Voltage multipliers are the way to go. First learn everything which you can from the content out there for free.

Never Ever build something without learning everything which you can learn for free.  This is very important.

You need to spend time researching, else you end up making the same mistakes.  I spent a couple of hours learning about voltage multipliers. The most common and easiest solution is [Cockcroft–Walton multiplier](https://en.wikipedia.org/wiki/Cockcroft%E2%80%93Walton_generator).

One principle which I try to adhere to even while designing complex solution is Keep IT Simple Stupid! Or KISS in short.

So for me then **Cockcroft–Walton** multiplier is the way ahead. It was designed in 1932 and it has been used in hundreds of devices so far. So it’s a stable solution for us to implement. More googling helps me find this Dave Jones from [EEVblog’s video](https://www.youtube.com/watch?v=ep3D_LC2UzU) explaining how the circuit works. I highly recommend you checking out the video to learn it in detail.  For those who don’t have the time, here is a very brief explanation of its functioning.

The circuit basically consists of two diodes and two capacitors connected back to back. Input to this circuit is an AC signal with a voltage peak of _Vp_. So the single stage of the circuit shifts up the input AC signal with a bias such that its output will be at _2Vp_ DC compared to the input. Now if you add the same second stage to this output, the output will be pushed up to _4Vp_ with respect to the initial input. Now you might think that it will increase to _8Vp_ by adding a third stage, but it just makes it _6Vp_. 

So adding more stages will increase the output DC voltage. It will _2Vp, 4Vp, 6Vp, 8Vp, 10 Vp, 12Vp_ etc when measured with respect to the input. Although theoretically, this is what we expect practically we will find losses in the circuit and output won’t be this high but for our purposes, we don’t need it to be super accurate.

Coming to designing our system, we want to produce a high voltage DC at the output(Around 6-7KV). To keep the circuit simple, I want to feed it directly with a 230V mains AC input(Indian voltages are at 230V AC). Let’s assume to put 15 stages of the multiplier, hence effectively DC output at the end will be around _230V x 2 x 15 = 6900V_ (Theoretically, but practically it should be much lower because of losses. Read up more about it [here](http://home.earthlink.net/~jimlux/hv/cw1.htm)). This is good enough for ionisation to occur.

I could have potentially added a transformer in the input to increase the output drastically with lesser number of stages but wanted to keep it simple for the first prototype. So let’s keep the circuit at 15 stages for now for a 230V mains AC input.

Now comes the selection of components. Circuit for us is very simple, its just two capacitors and two diodes per stage. Now how do we start to choose its values and more importantly its ratings?

This is where you need to understand the circuit’s working, properly. If you see carefully, we will see that at each stage, the voltage across the diodes or the capacitor doesn’t exceed _2Vp_. A differential is always at _2Vp_ hence we don’t have to spend more money on getting high voltage rating capacitors or diodes.  Since our inputs are at 230V, any capacitor rated 500V or above should suffice. Value of capacitor really doesn’t matter in this design, so I am choosing a capacitance of 0.1uF with 630V rating. For a choice of selecting SMD vs through-hole, I want to use SMD because I am used to soldering SMD parts. Eventually, if it ever needs to be picked and placed in the future, SMD parts are the obvious route to go. For diodes, I choose, 1N4001 with a 1000V rating. So major parts are selected. Entire Bill of Materials is uploaded with the [hardware files](http://amaldev.blog/wp-content/uploads/2019/12/Ioniser-hardware-files-1.zip).

#### **PCB design:**

Now that we have chosen the critical components, let’s select the other parts. We want this device to be plugged into an AC supply so at the output side we want to keep a resistor with a large value to avoid any catastrophe(Accidental touching the circuit and preventing a large current flow through you).  I also would like to reduce the current flow to the absolute minimum so that the device doesn’t consume that much amount of power when turned ON. I am choosing two 10M**Ω**(0.25W rated, Tolerance ±1%, 1206 package) resistor which equates to a current flow in microamps(μA) when the device is turned ON.

I these days use [LCSC.com](https://lcsc.com) to buy all my generic parts. Great selection at a great price. It’s way cheaper than Digikey or Mouser.  Basic Search there gives me this resistor [1206W4F1005T5E](https://lcsc.com/product-detail/Chip-Resistor-Surface-Mount_Uniroyal-Elec-1206W4F1005T5E_C26119.html) which fits our bill.

I also would like to have a small LED indicator which should light up when the device is plugged into AC to indicate that the power is ON. Design constraint is that forward current of the LED should be very small.  I have used [this red LED](https://lcsc.com/product-detail/Light-Emitting-Diodes-LED_Wuxi-ARK-Tech-Elec-D-060306R1-SS2-L_C118330.html) before in my other projects, it glows reasonably well at a forward current of 2mA. To limit the current, I am choosing two 51k**Ω** (230V/2mA gives me 115k**Ω** approx) resistors. I choose 2 resistors as they give a larger power dissipation through two small parts. (P=I2R: (2mA)2x51k**Ω** =0.2W). So I choose 0.5W resistors for 51k**Ω**. The part from LCSC is [CR1210J51K0P05Z](https://lcsc.com/product-detail/Chip-Resistor-Surface-Mount_Ever-Ohms-Tech-CR1210J51K0P05Z_C174650.html)(51K**Ω** ±5% 0.5W, 1210 package)

Now, all we need to figure out is the output stage. In the teardown’s which we saw earlier we find that for a proper transfer of negative ions to dust particles, we need a sharp endpoint which helps in ionisation. So what I am thinking is to use sewing needles and solder those on a large pad at the output to increase points of ionisation. I picked an assorted needle list from a local market for INR 30($0.4) Any conducting sharp edge material would do. Carbon fibres with sharp tips are an excellent replacement. More sharp points, more ionisation and dust settling is much faster.

![](http://amaldev.blog/wp-content/uploads/2019/12/Needles-1024x927.jpg)

With these points in mind, let’s start the PCB design. I am using Eagle for this project. I build up the schematic as follows. (Click on it for a larger view)

It contains the 2 pads to solder the AC inputs. 15 multiplier stages, resistors to reduce the current flow, large pad at the output and Power-ON LED indicator circuit. As a good practice, always use attributes in parts to mention the part numbers which you are going to use, such that it becomes easier in the future to look it up and order the parts. You can download the files part list [here](http://amaldev.blog/wp-content/uploads/2019/12/Ioniser-hardware-files-1.zip). Electronic parts will cost you _$7.8_, with SMD capacitors taking up the bulk of the pricing.

Now on the layout side, I am choosing to do it as a long PCB. Considerations you need to take are that there should be mounting holes to mount the PCB on standoffs at the end prototype. I am using M3 drill holes for mounting.  My PCB dimensions are 145mm x 40mm with input on the left end and a large output pad to solder the pointed needles. Make sure your diode directions are properly marked as it will make your soldering process so much simpler during assembly.

![](http://amaldev.blog/wp-content/uploads/2019/12/Layout-1024x284.png)

Create the PCB Gerber files and send them to the PCB manufacturer. I use JLCPCB these days. It’s as cheap as it can get in terms of pricing for prototyping. PCB will cost you approx $0.8(excluding shipping) if you buy 10 of them. Gerber zip files are attached with the [hardware files](http://amaldev.blog/wp-content/uploads/2019/12/Ioniser-hardware-files-1.zip). You can upload them directly onto JLCPCB for a quote.

If you want to remove my name, date and PCB name from the files, edit the Eagle Board files and replace them with whatever text you want and then re-export the Gerber files in Eagle.

This is how your PCB is going to look.

![](http://amaldev.blog/wp-content/uploads/2019/12/Ioniser_V0.1-1024x322.png)

Importing it to Fusion 360, we get an awesome view of the PCB.

![](http://amaldev.blog/wp-content/uploads/2019/12/Ioniser-v0.1-3D-1024x587.png)

So what I did is combined the PCB order from JLCPCB and electronics part order from LCSC. You get a $15 shipping discount if you order together. Part cost + PCB costs approx $9(Excluding shipping).  I had to wait a week and half to get it delivered. I like to do the assembly myself hence I didn’t go with the JLC’s pick and place service.

#### **Assembly and Testing:**

This is how the PCB looked from JLCPCB. (I went with an ENIG-RoHS finish for the looks. HASL finish will be the cheapest and it will work fine).

![](http://amaldev.blog/wp-content/uploads/2019/12/PCB1-1024x327.jpg)

I went ahead assembled the board by soldering the SMD parts. Took me a around an hour. I went ahead and got myself 2m copper wire and plug from a local hardware store to connect it to my AC outlet. I put a Knot in the wire to prevent the wire from getting pulled out from the plug.

![](http://amaldev.blog/wp-content/uploads/2019/12/Plug-1024x673.jpg)

Following part is optional(**but highly recommended**). I went to a laser cutter shop and took a 3mm thick transparent acrylic which was lying around and cut it to the dimensions of the board. This part is recommended as when I was testing the PCB with the AC powered on, I got quite a few shocks from touching the capacitors accidentally. 😅 They do carry a good amount of charge. Acrylic will isolate you from touching the circuit. DXF file for the acrylic cover is also included in the [download files](http://amaldev.blog/wp-content/uploads/2019/12/Ioniser-hardware-files-1.zip).

![](http://amaldev.blog/wp-content/uploads/2019/12/Acrylic-1024x334.jpg)

Mount the acrylic and PCB with [Nylon/Plastic screws](https://lcsc.com/product-detail/Screw_HIWA-PF3-5N-M3-5_C194616.html)(M3 x 5mm length) and 20mm long [spacers/standoffs](https://lcsc.com/product-detail/Spacers_KSS-KAI-SUH-SUH-ENTERPRISE-HTP-320_C242804.html) to keep it standing with respect to the table.

![](http://amaldev.blog/wp-content/uploads/2019/12/Assembled-1024x688.jpg)

I soldered 7 needles on the output pad as follows. More the merrier. Ignore the height differences, it doesn’t matter.

![](http://amaldev.blog/wp-content/uploads/2019/12/Needles-soldered-768x1024.jpg)

Time to turn it ON by plugging it your AC outlet and test it. Red LED should turn ON and the device should ideally be functional.

![](http://amaldev.blog/wp-content/uploads/2019/12/turnOn-1024x560.jpg)

For a quick test to know if it’s functional, slightly wet your palms with water and bring it close to your needles(Close but DON’T TOUCH). You should get a good waft of a cool air blowing from the needles. That’s the ionisation which is happening. Negative ions repel and are constantly pushed away from the needle tip.

Now to prove that this device indeed can precipitate smoke and dust particles, I quickly setup a transparent glass jar and filled it with incense smoke and inserted the needles of the device into the jar and turned it on and voila, the smoke particles settled in no time. Check it out in action below.

Smoke particulates captured in a jar is cleared as soon as the device is turned ON.

Although in the video, it appears as if smoke is moving about as if the air is blowing across it, there is no airflow at all. Its a closed jar. The effect is created by negative ions pushing each other due to electrostatic repulsion and it circulates very quickly through the jar to settle down the smoke particulates.

Now that we proved it works. I just connect the device to AC and leave it running. It should precipitate most dust particles in its vicinity without any trouble. Ideal mounting space for this would be near windows where the wind blows in so that it ionises all particles as it goes across the needles. I plan to keep it running all the time.

But what about the power consumption when you leave it on forever? It’s very small, Actually, the indicator LED is the power-hungry part in the whole system. It takes around 2mA. Calculating the power over a year, it would correspond to 230Vx 2mA x 24hrsx 365 days = 4KWh. Based on the electricity rates, it would add a cost INR 4($0.05) per year to your electricity bill. If you want to save even on that, then go ahead and remove that LED, power consumption would be 1000 times smaller as the rest of the circuit just utilises only a few µAs and I doubt it will even register on your house meter. So there is absolutely no(or negligible) running charges.

There you go, you have build yourselves an ioniser in under $10. Hopefully, this will reduce the dust particles going into your lungs.

Please note: After using it for a couple of weeks, you will find that a lot of dust would have settled around the device. This is very common. You want the dust to settle down rather than breathing it in.

For US and countries using 110V AC input, the output DC will be much lesser but should still work(much slower action) as the theoretical output will be around 3KV.

Potential improvements to the device in the future would include replacing needles with a fine conducting carbon fibre brushes. More the number of fine tips, more the ionisation. If you spread these tips across a large region chance of ionising air across a large volume is more. Hence better cleansing.

Hope you enjoyed reading about this one. If you did, do let me know what project or tech-related stuff I should take on next in the comments below.

Until next time… 🙂

If you enjoyed this post you may want to check out my other posts too…

[From an Idea to Hardware Product Cycle](http://amaldev.blog/idea-to-a-hardware-product/)  
[A Smart Chair: For those Lazy Workaholics](http://amaldev.blog/smart-chair-for-lazy-workaholics/)  
[Hacking Indian Electronic Voting Machines](http://amaldev.blog/hacking-indian-evms/)  
[Christmas LED Lights Teardown](http://amaldev.blog/christmas-led-light-teardown/)  
[How to electronically track your Currency Notes](http://amaldev.blog/tracking-rs2000-currency-note/)

If you liked the post, Share it with your friends!

  
  
from Hacker News https://ift.tt/2rFPshu