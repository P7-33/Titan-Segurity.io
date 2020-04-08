---
title: 'The Tech of Pixar: Piper (2017)'
date: 2019-11-08T06:47:00+01:00
draft: false
---

##### _Story written by guest writer Leif Pedersen, edited by fxguide._

_Piper_ is the kind of film that elicits disbelief, a film that allows you to admire the beauty of the imagery and yet also marvel at its technical prowess. As with any Pixar film, the focus is on the story, and this is where RenderMan was able to help the artists and the tools development team with the creative edge that the Director needed to tell this remarkable story.

[![piper-08](https://www.fxguide.com/wp-content/uploads/2017/01/piper-08-830x467.jpg)](https://www.fxguide.com/wp-content/uploads/2017/01/piper-08.jpg)

_Piper_ tells the story of a daring bird who is confronted with a tough problem as it tries to approach it creatively and collaboratively, a fitting parallel for the challenges and solutions the development team faced as they approached the beautiful golden sun-drenched beach of _Piper_.

[![piper-02a](https://www.fxguide.com/wp-content/uploads/2017/01/piper-02a-830x467.jpg)](https://www.fxguide.com/wp-content/uploads/2017/01/piper-02a.jpg)

For the first time, this project came from Pixar’s tools department, which is in charge of creating the cutting edge technology responsible for the wonderful imagery present in all Pixar films. _Piper_ was also the only short at Pixar which was started in REYES and transitioned into RIS. Development was done very early on with REYES’ plausible hybrid-raytracer.

“…the approach to many of the usual technical challenges had to be completely different.”

 Erik Smitt

At the time, the team was getting interesting results and traditional shading and lighting methods were beginning to be deployed, such as reliance on displacement maps, shadow maps and point clouds for global illumination and subsurface scattering, but when the team got their hands on RIS they were sold.

“Our initial images with RIS were very promising, the characters and their environments looked integrated, like they belonged in the same world,” said Erik Smitt, Director of Photography on _Piper_, “We no longer had to approach our shots with per-character lighting rigs in order to create cohesion in the shot, this was very creatively liberating, because we could get close to a finished shot much quicker.”

[![piper-sand-01-viewport](https://www.fxguide.com/wp-content/uploads/2017/01/piper-sand-01-viewport.jpg)](https://www.fxguide.com/wp-content/uploads/2017/01/piper-sand-01-viewport.jpg)

Houdini Viewport

[![piper-sand-01-render](https://www.fxguide.com/wp-content/uploads/2017/01/piper-sand-01-render.jpg)](https://www.fxguide.com/wp-content/uploads/2017/01/piper-sand-01-render.jpg)

Final image

The team was able to light shots and approach shading in a completely physical manner, so much so, “that the approach to many of the usual technical challenges had to be completely different” he adds. One example was the beach sand. “Traditionally, we would have used displacement maps and shading tricks to accomplish such an intimate and finely detailed beach,” said Brett Levin, Technical Supervisor on Piper, “but we decided to see what RIS could do.” And they did…the team decided to fill the beach with real grains of sand, all of it…

[![piper-06](https://www.fxguide.com/wp-content/uploads/2017/01/piper-06-830x467.jpg)](https://www.fxguide.com/wp-content/uploads/2017/01/piper-06.jpg)

Every shot in _Piper_ is composed of millions of grains of sand, each one of them around 5000 polygons. No bumps or displacements were used in the grains, just procedurally generated Houdini models. Displacements were the first option for creating the sand, but after many tests, the required displacement detail needed to convey the sand closeups were approximately 36 times the normal displacement map resolution used in production, which made displacements inefficient and started to make sand instancing a viable solution.

[![Each sand grain was modeled like the real thing](https://www.fxguide.com/wp-content/uploads/2017/01/piper-sand-grains-830x323.jpg)](https://www.fxguide.com/wp-content/uploads/2017/01/piper-sand-grains.jpg)

Each sand grain was modeled like the real thing

The sand dunes were sculpted in Mudbox and the resulting displaced mesh drove the sand generation in Houdini using a Poisson Distribution model. The resulting sand grains were simulated in Houdini’s grain solver which created a fine layer of sand on top of the mesh, this result was driven by a combination of culling techniques including camera frustum, facing angles and distance, creating a variance of dense to coarse patches of sand for optimum efficiency.

[![Poisson Distribution](https://www.fxguide.com/wp-content/uploads/2017/01/piper-poisson-830x428.jpg)](https://www.fxguide.com/wp-content/uploads/2017/01/piper-poisson.jpg)

Poisson Distribution

The variety of sand was driven by RenderMan Primvars in order to drive shading variance and dry-to-wet shading parameters, this gave the shading team great control with only 12 grains of sand. The grains were populated using geo instancing and point clouds, both data types handled via Pixar’s USD (Universal Scene Description), now an open source format, which allowed for the efficient description of very complex scenes.

[![piper-sand-zones](https://www.fxguide.com/wp-content/uploads/2017/01/piper-sand-zones-830x531.jpg)](https://www.fxguide.com/wp-content/uploads/2017/01/piper-sand-zones.jpg)

“Rendering such large data sets was going to be a challenge, but we were able to leverage instancing very successfully, with some scenes using a ray depth of 128, which would have been impossible with previous technology,” said Brett Levin. This makes the renders incredibly lifelike, but traditionally very resource intensive, yet RIS was able to handle the enormous computational needs out-of-the-box. “We were able to try new and inventive ways to problem solve a shot in a physical way, trusting in RenderMan’s pathtracing technology, which we would have never attempted before RIS.”

[![The sand's natural luminance was simulated by Light Transport](https://www.fxguide.com/wp-content/uploads/2017/01/piper-sand-grains-02-830x607.jpg)](https://www.fxguide.com/wp-content/uploads/2017/01/piper-sand-grains-02.jpg)

The sand’s natural luminance was simulated by Light Transport

The color of the sand was taken from an albedo palette generated from the beach on an overcast day, from which they made many types of shaders, varying from shell, stone, and refractive glass. These also had to be wet, dry and have varying degrees of tints and shades in order to simulate the billions of grains of sand convincingly.

[![Early Sand Look Dev CGI vs Photographic reference](https://www.fxguide.com/wp-content/uploads/2017/01/piper-sand-synth.jpg)](https://www.fxguide.com/wp-content/uploads/2017/01/piper-sand-synth.jpg)

Early Sand Look Dev CGI vs Photographic reference

Another challenge were Mach bands, which is an optical illusion that exaggerates subtle changes in contrast when the values come into contact with one another, thus creating unpleasing sand images. The team created a custom dithering solution for this, making the final images feel much more natural.

“We were able to rely purely on light transport”

 Erik Smitt

Director of Photography on Piper

Depending on the shoreline, sand can behave in many different ways. Creating these differing sand types was a nice challenge. The team ultimately categorized three distinct types: Wet, Moist, and Dry.

[![Sand wetness types](https://www.fxguide.com/wp-content/uploads/2017/01/piper-sand-wetness-types-830x486.jpg)](https://www.fxguide.com/wp-content/uploads/2017/01/piper-sand-wetness-types.jpg)

Sand wetness types

Explicit constraint networks were created to give the sand grains a level of stickiness, yet with the necessary breakable constraints to allow for a crumbling effect. After manipulating the grain solver in Houdini, the team was able to separate these subtle differences in moisture into art-directable states which could be simulated and animated with predictable results.

[![piper-sand-tension-dry](https://www.fxguide.com/wp-content/uploads/2017/01/piper-sand-tension-dry.jpg)](https://www.fxguide.com/wp-content/uploads/2017/01/piper-sand-tension-dry.jpg)

[![Sand tension and clumping](https://www.fxguide.com/wp-content/uploads/2017/01/piper-sand-tension-wet.jpg)](https://www.fxguide.com/wp-content/uploads/2017/01/piper-sand-tension-wet.jpg)

Sand tension and clumping

The water and foam used Houdini’s FLIP solver. For timing, the team animated simple wave shapes, from which they extracted the leading edge curve and encoded direction. They then built the FX wave shapes and adjusted the thickness based on flow. From there, they sourced the points and ran a low-res FLIP simulations. Lastly, a frustum-padded area is used to run high-res FLIP simulations using velocities from low-res pass. Sometimes retiming of waves was needed for artistic control.

[![Water Sim breakdown](https://www.fxguide.com/wp-content/uploads/2017/01/piper-water-breakdown-830x424.jpg)](https://www.fxguide.com/wp-content/uploads/2017/01/piper-water-breakdown.jpg)

Water Sim breakdown

The foam shading was done with a hybrid volume/thin surface shader, which was rendered with over 100 ray depth bounces. This gave the foam particles the required refractive luminance to realistically convey water bubbles. “RenderMan loved these challenges. We were able to rely purely on light transport to convey such realism in the foam and sand. RIS was doing really well with the incredibly demanding tasks,” said Erik Smitt.

[![piper-foam-breakdown](https://www.fxguide.com/wp-content/uploads/2017/01/piper-foam-breakdown-830x1511.jpg)](https://www.fxguide.com/wp-content/uploads/2017/01/piper-foam-breakdown.jpg)

Several in-house solutions for bubble interaction and popping were used, such as GIN, Pixar’s system for creating fields in 3D, as well as procedural foam patterns. These tiny bubbles were then carried with the water surface velocity and used a power-law distribution function for creation. Density was based on particle proximity and in turn, it was used to drive foam popping and stacking.

[![GIN Bubble Breakdown](https://www.fxguide.com/wp-content/uploads/2017/01/piper-bubble-generation-830x311.jpg)](https://www.fxguide.com/wp-content/uploads/2017/01/piper-bubble-generation.jpg)

GIN Bubble Breakdown

Another great shading trick was used to work around the inherent issues with liquid simulations and water tension, causing an effect called Meniscus, where an unwanted “lip” is formed where the water meets the beach. To work around this, the team duplicated the entire beach geometry and used a dynamic IOR blend to transition between the wet and moist sand. This got rid of the imprecision and created natural lapping water.

[![Water tension and meniscus effect](https://www.fxguide.com/wp-content/uploads/2017/01/piper-meniscus-830x362.jpg)](https://www.fxguide.com/wp-content/uploads/2017/01/piper-meniscus.jpg)

Water tension and meniscus effect

Combined with procedurally generated water runoff in Houdini, the team was able to use the resulting ripple patterns as image based displacements in Katana, giving subtle touches to a beautiful looking beach shore.

[![Houdini to Katana: Water ripples](https://www.fxguide.com/wp-content/uploads/2017/01/piper-water-ripples-830x380.jpg)](https://www.fxguide.com/wp-content/uploads/2017/01/piper-water-ripples.jpg)

Houdini to Katana: Water ripples

_Piper_ was heavily influenced by macro photography and originally the team was going to use Depth of Field in Nuke with a Deep Compositing workflow but realized that RenderMan was handling in-render DOF incredibly well and with an accuracy that was hard to match in post. For some exaggerated DOF shots, a combination technique was used, where they re-projected the renders onto USD geometry and added extra blur with Deep Image Data, creating a more stylized look.

[![piper-07](https://www.fxguide.com/wp-content/uploads/2017/01/piper-07-830x467.jpg)](https://www.fxguide.com/wp-content/uploads/2017/01/piper-07.jpg)

Piper Was Heavily Influenced by Macro Photography

Finally, to get rid of pathtracing noise, the development team was happy to use the new RenderMan Denoise. Traditionally, refractive surfaces and heavy DOF requires a lot of additional sampling to clean up entirely, but the Denoiser allowed the team to really push these techniques without having to be afraid of unwanted noise or impossibly long render times. They also leveraged integrator clamps and LPE filtering on caustic paths to kill ‘fireflies’.

[![AOVs as Used in Piper ](https://www.fxguide.com/wp-content/uploads/2017/01/piper-aovcheck-830x509.jpg)](https://www.fxguide.com/wp-content/uploads/2017/01/piper-aovcheck.jpg)

AOVs as Used in Piper

In the end, _Piper_ was able to push RenderMan to new physical shading and lighting standards, which helped carry its new RIS technology to unprecedented heights, paving the way for new and exciting times for physical workflows at Pixar.

Part 2 of our Tech of Pixar Oscar series focuses on the Feature film: _Finding Dory._

Note: _All images Copyright Disney/Pixar. Do not reproduce without permission._

  
  
from Hacker News https://ift.tt/2JXEzgH