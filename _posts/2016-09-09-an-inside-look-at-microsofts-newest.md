---
title: 'An Inside Look at Microsoft’s Newest Flight Simulator'
date: 2019-10-07T06:07:00+01:00
draft: false
---

_Note: EAA politely declined Microsoft’s offer of travel and lodging considerations for this preview event._

There’s no way I can write about the return of Flight Simulator without sharing just a little bit of my own story for context, as there are deep intersections. Not only did I start using version 1.0 of the product when I was about 12 years old (nearly 40 years ago, if you must know), but I worked on it at Microsoft for more than 10 years before it was canceled in 2009. The shutdown was a blow not just to those of us who relied on the product to pay our mortgages, but to millions of pilots and aviation enthusiasts around the world.

**In the Meantime**
-------------------

The last major release was Flight Simulator X (FSX) in 2006, followed by an expansion pack the following year. After the shutdown, variations of the product lived on here and there, including the enterprise edition, which Lockheed Martin now develops and publishes as Prepar3D, and a version that was licensed by Dovetail Games in the United Kingdom and sold on the Steam marketplace. Dovetail pursued further development with a product called Flight Sim World, and Microsoft itself briefly returned to the genre in 2012 with a limited product called Flight. But it was the community of hardcore simmers and add-on developers who truly kept the product alive for the past 10 years. Then, in May of 2019, Microsoft surprised almost everybody with a bombshell announcement: Flight Simulator, the oldest franchise in Microsoft’s history (Windows and Office weren’t even a gleam in Bill’s eye back then), is coming back in a big way, first to the PC, then to the Xbox console.

**A Surprise Invitation**
-------------------------

I was extremely lucky to be able to represent EAA at a special invitation-only preview event that Microsoft hosted recently at an FBO at the Renton Municipal Airport (KRNT), southeast of Seattle. Several members of the product team, including key players from Asobo Studio, the French development house that Microsoft is partnering with on the project, were on hand for presentations and one-on-one discussions, before we were turned loose on a pre-alpha (very early technical preview) build of the sim at our own customized cockpit workstations. Microsoft also subsidized introductory flight lessons in Rainier Flight Service’s fleet of Cessna 172s so that the diverse collection of about 50 bloggers, vloggers, and influencers, not to mention one slightly grizzled senior editor, who attended the event from around the world could compare simulation to reality.

![](https://i0.wp.com/inspire.eaa.org/wp-content/uploads/2019/09/Hal-Workstation.jpg?fit=740%2C987)

This was my office for the day. I wanted to steal it.

**How We Got Here**
-------------------

Longtime Microsoft employee Jorg Neumann was working with developers from Asobo on a project for Microsoft HoloLens, a wearable display that offers immersive “mixed reality” experiences. The project was a virtual tour of Machu Picchu in Peru using imagery from Bing to completely re-create the famous site. This gave Jorg an idea: If they could create convincing real-world scenery of one area, could they do that for the whole planet? If they could, then they’d have the basis for a remarkable and long-awaited return of Flight Simulator.

That was about three years ago. And, as it turned out, yes, they could model the entire planet, and that scenery looks, in a word, stunning. Jorg discussed the idea with one of Microsoft’s general managers, Shannon Loftis, a longtime pilot who told him to go for it. Jorg’s team started to grow, it produced a demo using Seattle scenery, and, with Shannon’s support, a pitch became a product team that has since grown to nearly 200 people.

“Everybody was super supportive,” Jorg said. “That’s just the way it is. I think there is a true love in Microsoft for Flight Sim, and maybe it’s subconscious, but it is who we are. It is in the fiber of the company’s being. It is older than Windows. I think there is a pride that comes with it, and I think seeing it come back in a meaningful way, I think makes lots of people proud.”

Asobo’s second step was to review all of the existing code in FSX to determine what to adapt, what to upgrade, what to emulate, and how to integrate a simulation system with its visualization engine. And Asobo’s first step? To buy everyone in the company an introductory flight lesson to make sure they had a firsthand taste for what they were going to build. Now the company estimates that something like 60 percent of the team is actively involved in flight training.

This was especially important to Asobo CEO and Co-Founder — not to mention avid pilot — Sebastian Wloch.

“Having spent so many hours flying in real life, I think it totally changed the picture,” he said. “When you are in the gaming industry, you are tweaking the reality in order to make something interesting. Here, we have to be as close as possible to the reality to bring something interesting. … The first thing and the most important thing I understood is flying in the real world is fun and interesting. It’s actually a great experience, and this immediately triggered the fact that if we just emulate reality in the best way possible, we don’t have to add anything …. There’s no need to make it a game.”

**A Whole New World**
---------------------

Like many of its predecessors, the new simulator models the entire planet, including something like 40,000 airports worldwide. I used to brag in presentations about FSX that we started with 2 terabytes of scenery data, and then compressed that to fit onto a couple of DVDs in a box. The world in the new version consists of 2 petabytes of data — yes, that’s one thousand times bigger. The scenery is built on Bing satellite and aerial imagery, augmented with cool buzzwordy stuff like photogrammetric 3D modeling and multiple other data sources, all of which is streamed via Microsoft’s Azure cloud service. Yes, the word streaming means you’ll need an internet connection, but you can download and pre-cache scenery areas for offline use, or even fly in a fully offline mode.

![](https://i1.wp.com/inspire.eaa.org/wp-content/uploads/2019/09/Cessna-172-Skyhawk_a.png?w=740)

A Cessna 172 over the Cascade Mountains.

All of this data results in an environment that is often breathtakingly lifelike, and it means that the entire planet is effectively what we used to call a “high detail area,” only more realistic. For the tech-savvy, many of the scenery areas boast a resolution of 3 _centimeters_ per pixel, while the default in FSX was about 1 _meter_ per pixel. Throw in 1.5 trillion trees, individual blades of grass modeled in 3D, and a complete overhaul of lighting and shadows, and the result is an unprecedented level of detail for a flight simulator of any kind. True VFR flight, day or night, with real-world landmarks is now possible everywhere on the planet.

![](https://i1.wp.com/inspire.eaa.org/wp-content/uploads/2019/09/NY.jpeg?fit=740%2C416)

New York City.

**How’s the Weather?**
----------------------

Put simply, the weather just looks real. Clouds are fully volumetric, meaning they are truly modeled in three dimensions, and the way they form, move, dissipate, and interact with terrain is a huge leap forward in terms of realism. The sim supports as many as 60 cloud layers, including fronts, storms, precipitation, etc. Weather is modeled to a distance of 600 kilometers, meaning that systems will be visible even way out on the horizon, rather than fading or even popping in as you approach.

![](https://i2.wp.com/inspire.eaa.org/wp-content/uploads/2019/09/Clouds-to-the-horizon.jpeg?fit=740%2C398)

A high-altitude look at clouds visible all the way to the horizon.

Thanks to the new lighting engine, clouds cast shadows, and everything from entire cities to gauges in the cockpit looks dramatically different under an overcast sky as opposed to a bright and sunny day. You’ll even see rainbows when conditions are just right.

![](https://i1.wp.com/inspire.eaa.org/wp-content/uploads/2019/09/VolumetricCloudsThrough.jpeg?fit=740%2C398)

Note the variances in lighting and shadowing with multiple cloud layers.

In addition to clouds and precipitation, the system models temperature, pressure, humidity, dew point, and wind direction and speed, all of this in as many as 20 layers. Winds interact with the scenery with greatly improved fidelity, making things like up- and downdrafts, rotors, ridge lift, etc. much more dynamic and precise. The team even demonstrated a visualization tool that shows wind currents flowing up and over the side of a mountain, just to illustrate the complexity of the modeling.

![](https://i2.wp.com/inspire.eaa.org/wp-content/uploads/2019/09/WindSimMountain.jpeg?fit=740%2C398)

Visualization tools demonstrate how the simulation models wind interacting with terrain.

Weather is automatically downloaded from real-world sources, creating accurate conditions that change over time. In addition, the build we were shown included a set of simple weather themes that could be chosen from a drop-down menu, changing the conditions in the sim instantaneously as the user clicked through the options.

![](https://i2.wp.com/inspire.eaa.org/wp-content/uploads/2019/09/VideoRain.jpeg?fit=740%2C398)

It’s raining over there just south of Seattle.

**More Than Just the World**
----------------------------

The new Flight Simulator is more than just a Bing-driven virtual tour of the world with some cool-looking clouds. The underlying simulation itself now performs with considerably higher fidelity. In older versions, aerodynamic effects were generally modeled based on the aircraft’s single center point. It’s an oversimplification, but the idea of ground effect makes for an easy example. In FSX, if the center point of the airplane were at or below a given altitude, then you felt ground effect. In the new version, the simulation engine looks at every single surface — and there may be thousands — and models things appropriately. In a crosswind landing, for instance, if you’re flying a wing-low approach, that wing will encounter ground effect before the other one. That’s a microcosmic way of saying that the simulation engine is now generally sophisticated enough to model the interactions of every part of the airplane and the air around it. This also means that stall/spin modeling is dramatically better as well.

In addition, the new engine brings higher-fidelity collision detection, which makes things like bumpy runways, braking on slick surfaces, varying degrees of friction, etc. much more nuanced. Under the hood, the development team has done significant work with integration, using something called adaptive time steps. The upshot is that the simulation now always updates at the same frequency as the visual frame rate. This improves fidelity overall, and brings a more dynamic feel to virtual flying.

**What About All of My Third-Party Aircraft?**
----------------------------------------------

Microsoft is incorporating a legacy mode that it expects will provide near-complete backward compatibility, so those of us who have huge libraries of old favorites won’t be starting entirely from scratch. In addition, Microsoft is committed to providing a software development kit (SDK) with the product at launch that will give developers the tools they need to build add-ons, though they caution that it is something that will be polished and expanded through post-launch updates. In other news for add-on aircraft builders, every parameter is now exposed in plain text, with no more binaries. This means it’s going to be easier than ever to create high-quality add-on aircraft, or to tinker with the ones you already have. For those who like emulating glass cockpits, those displays are fully programmable based on straightforward coding instead of a library of animations, and support things like touch screens and synthetic vision.

While the team is currently evaluating something like an in-sim store for supplemental content, there will be no requirements to use it, and no restrictions of any kind on downloading freeware or payware add-ons from other sources.

**Firsthand Flying**
--------------------

Prior to the event, I was told I’d get “some” hands-on time with the sim, and I assumed that meant lining up at a shared computer for a few minutes of a restricted and supervised demo. Instead, I was shown to my own workstation that actually had my name on it, and turned loose for hours. It was equipped with a Logitech G Pro yoke and throttle quadrant, a set of Thrustmaster TPR rudder pedals, and a David Clark aviation headset, which was a nice touch. We weren’t allowed to capture images or video of our hands-on sessions, but Microsoft provided several screenshots and a lot of b-roll video that I’m sure we’ll see all over the web in a day or so.

The new user interface is clean and well organized, though a few things were disabled for our preview. It’s got a translucent glass look, tidy and minimal, with a nicely animated globe for selecting starting airports, flight planning, etc. Once you select an area, load times seemed about the same as FSX, but once you’re in the sim, anything you change seems to happen instantly.

![](https://i1.wp.com/inspire.eaa.org/wp-content/uploads/2019/09/Cessna-172-Skyhawk_g-1.png?fit=740%2C418)

The scenery, lighting, and weather all come together to make an exceptionally convincing experience.

We had three aircraft to choose from: a Cessna 172, a Daher TBM 930, and a Robin DR400. We’ve seen other aircraft in videos from Microsoft, but there’s no confirmation at this point what will be included. I flew all three, and one of the first things I noticed was that it still feels like Flight Sim, somehow. It’s almost impossible to quantify, much less articulate, but it didn’t feel like something foreign that I’d have to learn and get used to all over again; instead, it felt comfortable, and familiar. It’s a significant upgrade in every respect — with 13 years since the last major release, it had better be — but it was still Flight Sim to me, in the best possible sense.

Flight dynamics were convincing, and the numbers were spot on in the 172, and matched book specs in the TBM and the DR400. Stalls feel a lot more accurate now, with more variation in the buffeting and the break. The default 172 drops a wing a lot more aggressively than the real thing, but that was okay because it showed off how the new engine handles spins, which was remarkably realistic. I’m sure that behavior will be tuned well before launch, along with my minor grumble about not having enough rudder effectiveness to hold the airplane in a slip beyond more than just a few degrees of bank. (My old friend Khoi, who used to work with me as a high-school intern, is now on the test team and promised that he’d chase down those bugs. The torch is passed!)

![](https://i2.wp.com/inspire.eaa.org/wp-content/uploads/2019/09/Daher-Socata-TBM-930_c.png?w=740)

The Daher TBM 930 cruises between layers.

The performance was buttery-smooth throughout my testing. I didn’t find a frame-rate counter, but it was easily 30 fps (frames per second) or greater. In about five hours of flying, I saw a handful of stutters in the scenery, and made it crash to the desktop twice. I spotted one or two instances of odd scenery textures, one airport on a plateau thanks to some bad elevation data, a slight lag in how building reflections are drawn on lakes, and noted that some of the water textures were slightly repetitive. Once a software tester, always a software tester, of course, but hiccups like these are absolutely negligible when you’re talking about a pre-alpha build. The computers were described as upper-, but not top-, end machines with GeForce RTX video cards, and the internet connection feeding the scenery tested out at about 25 megabits.

Speaking of scenery, we were all stunned by the early videos and screenshots Microsoft released back in May, and I can say now that they didn’t come close to doing it justice. It is absolutely breathtaking. I chose sample airports all over the world (after flying over my house first — duh — and then heading to Chicago, declaring an emergency, and landing in the park that will always be Meigs Field to me ) and ran out of adjectives to describe just how good, how real it looks. Terrain, buildings, water, 3D grass, undulating runways — all of it looks simply amazing. There’s no LOD (level of detail) popping to distract you, just a big, beautiful, and almost impossibly real world to explore. The beauty, depth, and realism of the scenery, coupled with the lighting, shadows, and weather, create a virtual flight experience that is nothing short of sublime. I’ve never experienced a more convincing and immersive simulation, period.

![](https://i1.wp.com/inspire.eaa.org/wp-content/uploads/2019/09/Paris.jpeg?fit=740%2C416)

A hazy, commanding view of Paris.

**What I Didn’t See**
---------------------

Of course, this is supposed to be a preview, not a hagiography. Even though the build I got to try out was dramatically more stable and complete than what I would have expected, there were still things missing. For example, there wasn’t an advanced weather interface — I could choose themes, but couldn’t get in and set specific cloud layers at various heights to set up for an instrument approach, for example. Also missing from the build was ATC and AI traffic, and the team didn’t address those to any great degree in their presentations. They did say there will be some basic multiplayer functionality at launch that they plan to develop, but didn’t elaborate beyond that. There was also no public discussion of pricing, and no firm launch date other than 2020.

**Going Forward**
-----------------

There’s no way that attending an event like this wouldn’t be a bit surreal for me. After all, I used to host things like this — though they were never that fancy, which says good things about the new team’s marketing budget — and I was usually the one in front of the audience, giving the presentation. That said, I came away with nothing but enthusiasm and optimism.

As a former Microsoft employee, I’m proud to see the product make what promises to be a triumphant return, and my colleagues from that era should be, too.

As an EAA employee, I’m thrilled to see a product that has done so much to help millions of people indulge and explore their passion for aviation become available again. All of us are excited to continue talking to the team at Microsoft about ways we can work together to further EAA’s mission of growing participation in aviation.

As a customer, I just want them to hurry up and finish it so I can buy it.

### Post Comments

comments

  
  
from Hacker News https://ift.tt/2ojos5F