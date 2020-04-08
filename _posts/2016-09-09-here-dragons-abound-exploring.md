---
title: 'Here Dragons Abound: Exploring procedural generation and display of fantasy maps'
date: 2019-11-01T06:52:00+01:00
draft: false
---

In a

[previous posting](https://heredragonsabound.blogspot.com/2019/08/azgarrs-fantasy-map-generator.html)

I reviewed

[Azgaar's Fantasy Map Generator](https://azgaar.github.io/Fantasy-Map-Generator/)

 and as I noted, one of the things I really liked was his method for defining terrain generation by composing basic terrain generation actions in a template:

In 

**Dragons Abound**

, the equivalent terrain generation control is handled by turning actions on and off with parameters, and the sequence of actions is hard-coded into terrain generation code.  This is much less flexible and much more fragile than Azgaar's approach.  Well, never let it be said that I'm too proud to recognize a great idea and steal it!  So I did.

**Dragons Abound**

 has a bunch of different terrain generation primitives, so the basic notion of creating a template that could point to these primitives and execute them was pretty straightforward to implement.  In some sense, 

**Dragons Abound**

 has templates already; they're just not encoded in a declarative fashion.  And they are missing some features.  Two of Azgaar's nice features are (1) a repetition count, and (2) that any parameter to the primitive can be expressed as a range of numbers to be randomly generated when the primitive is executed.  I added both of these features.

I also added a percentage chance to each primitive; this is the chance the primitive will execute.  Azgaar has something like this.  If you express the number of repetitions for an action in Azgaar's templates as a fraction, it has a fractional chance of executing the last repetition.  So an action with “n: 3.5" would produce 3 repetitions half the time and 4 repetitions half the time.  But I actually wanted something a little different from this.  I want to be able to say “On 25% of the maps, add 3-6 little islands."  That requires separating the chance to execute from the number of repetitions. 

Converting 

**Dragons Abound**

's primitives to work well in a template was a little more difficult.  Most of 

**Dragons Abound**

's terrain generation primitives are written as standalone functions that pull their parameters from the global parameter structure.  So these needed to rewritten so that they received their parameters from the template.  And for ease of writing the templates, I wanted each parameter to fall back to a value in the global parameter structure if it wasn't in the template.  This provided a lot of flexibility; for the common cases the template specification is very succinct, but I can override anything by adding it to the template.

A different kind of challenge arose with regards to 

**Dragons Abound**

's “additional map features."  These are minor map features such as cluster islands (like Hawaii) or barrier islands, etc.  They don't really contribute to the overall land shapes, but provide some areas of additional interest.  In my original approach to generation, these all have some percentage chance of appearing on any map.  One drawback to this approach is that I can sometimes get all the options at once, which is problematic.  For instance, 

**Dragons Abound**

 has four different methods for generating small islands, so on some maps I would end up with a lot of small islands!  What I really want to do is decide whether I want to have islands, and then pick one of those methods.  To accomplish this, I added a “choice" action to templates that chooses one action from a list of alternatives.  Using this I can say something like “Add some small islands to 75% of the maps, and do that by randomly selecting one of these four alternative methods for creating small islands."

In the course of converting the primitives to templates, I found and cleaned up a number of bugs.

One bug had to do with rivers.  Occasionally 

**Dragons Abound**

 generates maps like this:

which have rivers that end abruptly in the middle of the land rather than continuing to the ocean.

For various reasons, I thought this happened because of a breakdown in 

**Dragons Abound**

's sink fill algorithm.  As a bit of background, if you draw rivers by following the contour of the land down to the ocean, spots in the interior of the land that are local minima (that is, all of the neighboring land is higher) create problems, because if a river flows into that spot it cannot flow out.  Which would create rivers ending in the middle of nowhere, as above.

(In “real life" a spot like that would fill up with water creating a lake, until it overflowed and the water could continue on downhill.  If you want to know why 

**Dragons Abound**

 doesn't do that, you'll have to find that discussion in the archives :-)

The sink filling algorithm 

**Dragons Abound**

 uses is called the Planchon-Darboux algorithm.  It's elegant and efficient (you can read the original paper

[here](http://horizon.documentation.ird.fr/exl-doc/pleins_textes/pleins_textes_7/sous_copyright/010031925.pdf)

) but for whatever reason I find it difficult to wrap my head around.  And that's made more complicated because 

**Dragons Abound**

 changes the resolution of the underlying map after drawing the coasts, and other factors.

At any rate, after many hours of debugging I finally figured out that the problem wasn't in the sink filling algorithm at all.  Instead, there was an invisible river on the map that the two orphaned rivers were flowing into.  Why the river was invisible became the next debugging mystery.

After some more painful pounding of head against wall, I traced the problem to the river drawing code.  In that code, there's a test that says to stop drawing the river once it reaches the ocean (actually a bit after it reaches the ocean).  (Rivers actually keep flowing under the ocean.  This is useful if, for example, the sea level changes.)  This makes the river broaden out properly at the coast, and prevents a situation where a river can come out of the ocean to cross land again.

This test was creating a problem in the infrequent case where a river starts on the edge of the map.  Technically the edge of the map is not part of the land and counts as being in the ocean.  (This lets rivers drain to the edge of the map.)  So if a river started on the edge of the map, the river drawing routine would immediately exit without drawing any river.

The solution was to make the ocean test a little smarter by looking backwards from the end of the river rather than forward from the start of the river.  With this fix in place the mystery rivers find an outlet:

They now flow into the Ox-Eye River and eventually to the sea.

That was rather a longer interruption than I would have liked, but that problem has been annoying me for a while, so I'm glad to have it fixed.

I encountered another problem while converting “Add Peninsulas."  This is a chunk of code that tries to

[add islands to the ends of peninsulas](https://heredragonsabound.blogspot.com/2016/11/islands-are-just-mountains-up-to-their.html)

.  After the conversion, I had difficulty finding a test case where an island range was successfully added to the map.  This isn't entirely unlikely; this routine looks for a specific coast configuration that isn't always present.  Still, I should have been able to find something.

Inspecting the code, I discovered that when I

[modified the coast creation to generate more detailed coasts](https://heredragonsabound.blogspot.com/2018/12/voronoi-revisited-part-1.html)

, I had broken some of the internal dependencies that Add Peninsulas used.  Fixing this required largely rewriting the code, but fortunately it is not long and is

[fairly easy to understand](https://gamedev.stackexchange.com/questions/169723/how-can-bays-and-straits-be-determined-in-a-procedurally-generated-map/169737#169737)

.  Ran into a few problems along the way, like this peninsula:

That's actually sort of interesting looking, but definitely not what it's supposed to be.  

**Dragons Abound**

 uses perturbation when painting the peninsula.  With that turned off here's what the peninsula looks like:

So this looks like a case where the perturbation is too wild.  I don't want this to (always) be perfectly straight but not quite such a wild curve!

That's a little better.  I spent a while tweaking the parameters of this code to get better looking peninsulas, but I'm still not entirely happy with the way it works.

Working on converting the previously mentioned island-creating routines to templates, I discovered that they failed if there wasn't any existing land.  (This is not normally a problem because 

**Dragons Abound**

 adds islands as late step in land generation, but came up when I tried to create a template for an all islands map.)  The reason island creation failed was that island placement needs to know how far away a potential island location is from existing land, and this was impossible to calculate if there was no land!

I fixed the routine that calculates the distance to land to work when there was no land, and while I was at it, I rewrote the entire routine for better efficiency.  Along the way I learned a lesson about accidentally using depth-first search when you mean to use bread-first search on a map with a few hundred thousand locations.  (Spoiler Alert:  It's a lot slower.)  At any rate, eventually I could create islands in an empty sea:

Another (funny) problem popped up as I started working on another template:

Square landmasses are probably not very realistic.  This was an odd problem that took a while to understand.

As mentioned above, 

**Dragons Abound**

 has a sink filling algorithm which makes sure that every location can flow downhill to the edge of the map.  When you run this on a completely flat map, it essentially turns the map into a pyramid, with the highest point in the center running down on four sides to the edges of the map.  If you then partially flood the map, the top of the pyramid sticks out of the water and forms the square landmass seen in the map above.  My solution was to add a little noise to the map before creating terrain, so that there aren't any large completely flat areas to form pyramids.

With the basic templating mechanism working, I started on some templates to recreate the different terrain generation types I had previously.  The first is the standard large island in the middle of the map.  The template for this puts a large island in the middle of the map, adds 3 smaller overlapping islands, and then adds smaller islands and other decorations.  That gives us landforms that look like this:

That was a pretty straightforward conversion.

A second map type is a peninsula shape, something like Florida in the United States.  To create this type of shape, I can create a long elliptical island, offset it into a corner, and then angle it to go across the map on the diagonal.

I like to add another ellipse at a cross-angle to the peninsula at the edge of the map to suggest a larger landmass “off-screen."

One problem with this template (and it was a problem with my corresponding formula pre-template) is that I have to specify the corner where I'm offsetting the peninsula, and the angle to the other corner.  If I want a peninsula coming from (say) the upper-right hand corner instead, I need a new template.  What I'd really like is a template that would just randomly select a corner and adjust accordingly.

One way to do this is to introduce a new operator for templates that can mirror (flip) the map along either the X or the Y dimension.  Using this operator in various combinations gives three more variants of the above map.  However, flipping the map isn't as easy as you might expect.  The map is based upon a Voronoi graph, not a 2D array of locations.  Each location knows its center, its edges, its neighbors and so on.  So I cannot simply swap indices in an array; I need to go through every location on the map, look up the corresponding flipped location and swap heights.  And this is slow, because finding a location by its coordinates is not fast.  (Even though I do use a quadtree to speed things up.)  That aside, it works well:

If I add a step to the template to flip on the X axis and a step to flip on the Y axis and give them both a 50% chance of executing, then I get all four possibilities.

(On a square map like the ones I normally use, it's also possible to do a 90 degree rotation, but I don't want to have an operation that only works on a square map.)

Another type of map I'd like to produce is a coastline: something like looking at a chunk of the east or west coasts of the United States.  

**Dragons Abound**

 has a routine for adding a slope across the map which can be used to create landmasses of this sort:

The terrain this produces is somewhat unsatisfactory, being essentially just a long ramp into the ocean.  This is can be somewhat addressed by other land creation routines that do things like add mountains in appropriate places, but it's still not very convincing.

Another way to create this sort of map is to create a very big island centered on one edge of the map, so that one long coast of the island shows up on the map -- somewhat like the peninsula, but running the other direction.  The angle can vary 180 degrees and then we can use the map flip trick from the peninsula template to effectively get all the possible angles.

Azgaar has a template called Atoll that produces a circular ring of islands like this:

I don't particularly want to generate island rings like this, but I do want to do something somewhat similar, which is to take a bite out of a landmass to create a large bay, as in this map:

The bay is created by dropping a smaller, negative island on top of the main landmass.  A negative island has a negative height, so it pushes down all the land where it is placed.  The challenge is placing the negative island.  If it is entirely inland it will create an interior sea; if it is too far out to sea it will not create an obvious bay.  My solution is to try random locations and then count the number of land and ocean locations within the rough circle of the bay. If there are at least 50% land locations and at least one ocean location, it gets used.  Here's an example of the placement of a large and a small bay:

This seems to work reasonably well.

The last (?) template from Azgaar I want to look at is “Mediterranean," which as the name suggests, is a land mass around a large central sea.  I don't totally understand Azgaar's template for this type of map but a reasonable approach would seem to be placing (overlapping) islands around the edge of the map.  That produces maps like this:

In this template the best number of islands along each side is enough to cover the edge but occasionally to leave gaps.  However, the appropriate number varies with the size of the islands and the length of the sides.  Luckily, most of my template actions already are sized as a percentage of the map size (e.g., “place an island that is 35% of the width of the map") so I can pick a number and size of islands that will work pretty well regardless of the size and proportions of the sides.

A nice option on this type of map is a chance for a small central island.

The last capability I want to add is to choose a template randomly, so that when I generate a random map, it might use any of the terrain templates.  I can use the same mechanism to randomly select a map style.  (This has a toggle so I can easily turn it off when I'm developing.)

My thanks again to Azgaar for all his good work and inspiration!

  
  
from Hacker News https://ift.tt/2dJGYv4