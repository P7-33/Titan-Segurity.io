---
title: 'Choropleth Map'
date: 2019-11-10T08:51:00+01:00
draft: false
---

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f7/Australian_Census_2011_demographic_map_-_Australia_by_SLA_-_BCP_field_2715_Christianity_Anglican_Persons.svg/280px-Australian_Census_2011_demographic_map_-_Australia_by_SLA_-_BCP_field_2715_Christianity_Anglican_Persons.svg.png)](https://en.wikipedia.org/wiki/File:Australian_Census_2011_demographic_map_-_Australia_by_SLA_-_BCP_field_2715_Christianity_Anglican_Persons.svg)

A choropleth map that visualizes the fraction of

[Australians](https://en.wikipedia.org/wiki/Australians "Australians")

that identified as

[Anglican](https://en.wikipedia.org/wiki/Anglican "Anglican")

at the 2011 census

A **choropleth map** (from [Greek](https://en.wikipedia.org/wiki/Greek_language "Greek language") χῶρος "area/region" and πλῆθος "multitude") is a [thematic map](https://en.wikipedia.org/wiki/Thematic_map "Thematic map") in which areas are shaded or patterned in proportion to the measurement of the statistical variable being displayed on the map, such as population density or [per-capita income](https://en.wikipedia.org/wiki/Per-capita_income "Per-capita income").

Choropleth maps provide an easy way to visualize how a measurement varies across a geographic area or show the level of variability within a region. A [heat map](https://en.wikipedia.org/wiki/Heat_map "Heat map") is similar but does not use geographic boundaries.

Overview
--------

The earliest known choropleth map was created in 1826 by [Baron Pierre Charles Dupin](https://en.wikipedia.org/wiki/Charles_Dupin "Charles Dupin").[\[1\]](https://en.wikipedia.org/wiki/Choropleth_map#cite_note-MF08-1) They were first called "_cartes teintées_" (_coloured map_ in French). The term "choroplethe map" was introduced in 1938 by the geographer [John Kirtland Wright](https://en.wikipedia.org/wiki/John_Kirtland_Wright "John Kirtland Wright") in "Problems in Population Mapping".[\[2\]](https://en.wikipedia.org/wiki/Choropleth_map#cite_note-JKW-2)

Choropleth maps are based on statistical data aggregated over previously defined regions (e.g., counties), in contrast to area-class and [isarithmic](https://en.wikipedia.org/wiki/Contour_line "Contour line") maps, in which region boundaries are defined by data patterns. Thus, where defined regions are important to a discussion, as in an election map divided by electoral regions, choropleths are preferred.

Where real-world patterns may not conform to the regions discussed, issues such as the [ecological fallacy](https://en.wikipedia.org/wiki/Ecological_fallacy "Ecological fallacy") and the [modifiable areal unit problem](https://en.wikipedia.org/wiki/Modifiable_areal_unit_problem "Modifiable areal unit problem") (MAUP) can lead to major misinterpretations, and other techniques are preferable.[\[3\]](https://en.wikipedia.org/wiki/Choropleth_map#cite_note-3) Similarly, the size and specificity of the displayed regions depend on the variable being represented. While the use of smaller and more specific regions can decrease the risk of ecological fallacy and MAUP, it can cause the map to appear to be more complicated. Although representing specific data in large regions can be misleading, it can make the map clearer and easier to interpret and remember.[\[4\]](https://en.wikipedia.org/wiki/Choropleth_map#cite_note-4) The choice of regions will ultimately depend on the map's intended audience and purpose.

The [dasymetric technique](https://en.wikipedia.org/wiki/Dasymetric_map "Dasymetric map") can be thought of as a compromise approach in many situations. Broadly speaking, choropleths represent two types of data: spatially extensive or spatially intensive.

*   Spatially extensive data are things like populations. The population of the UK might be 65 million, but it would not be accurate to arbitrarily cut the UK into two halves of equal area and say that the population of each half of the UK is 32.5 million.
*   Spatially intensive data are things like rates, densities and proportions, which can be thought of conceptually as field data that is averaged over an area. Though the UK's 60 million inhabitants occupy an area of about 240,000 km2, and the population density is therefore about 250/km2, arbitrary halves of equal area would not both have the same population density.

Normalization
-------------

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c8/Choropleth-density.png/220px-Choropleth-density.png)](https://en.wikipedia.org/wiki/File:Choropleth-density.png)

Normalization:the map on the left uses total population to determine color. This causes larger polygons to appear to be more urbanized than the smaller dense urban areas of

[Boston](https://en.wikipedia.org/wiki/Boston "Boston")

, Massachusetts. The map on the right uses population density. A properly normalized map will show variables independent of the size of the polygons.

Another common error in choropleths is the use of raw data values to represent magnitude rather than normalized values to produce a map of densities.[\[5\]](https://en.wikipedia.org/wiki/Choropleth_map#cite_note-5) This is problematic because the eye naturally integrates over areas of the same color, giving undue prominence to larger polygons of moderate magnitude and minimizing the significance of smaller polygons with high magnitudes. The problem with using data in total counts arises when the polygons are not all the same size (in area or total population), as in the figure at right. Because a single color, representing a single value, is spread over the entire area of the district, large areas will be more dominant in the visual hierarchy than they should be, and are commonly misinterpreted as having larger values than smaller districts with the same color. To solve this issue, one can _normalize_ the variable by dividing it by the total area, thus deriving _density_, which is a field. Another solution is to represent total amounts using a [proportional symbol map](https://en.wikipedia.org/wiki/Thematic_map#Proportional_symbol "Thematic map").

Other valid forms of normalization for choropleth maps can be derived by computing ratios between two total amounts, such as rates of change (population growth = 2010 population / 2000 population) and mean allocations (mean family income = total income / total families), or other descriptive statistics such as the median or standard deviation.[\[6\]](https://en.wikipedia.org/wiki/Choropleth_map#cite_note-6)

Classification
--------------

Color progression
-----------------

When mapping quantitative data, a specific color progression should be used to depict the data properly. There are several different types of color progressions used by cartographers. The following are described in detail in Robinson et al. (1995)[\[7\]](https://en.wikipedia.org/wiki/Choropleth_map#cite_note-7)

Single-hue progressions fade from a dark shade of the chosen color to a very light or white shade of relatively the same hue. This is a common method used to map magnitude. The darkest hue represents the greatest number in the data set and the lightest shade representing the least number.

Two variables may be shown through the use of two overprinted single color scales. The hues typically used are from red to white for the first data set and blue to white for the second, they are then overprinted to produce varying hues. These type of maps show the magnitude of the values in relation to each other.

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/1/15/Color_progression_examples_bi-polar.svg/220px-Color_progression_examples_bi-polar.svg.png)](https://en.wikipedia.org/wiki/File:Color_progression_examples_bi-polar.svg)

Bi-polar color progression

Bi-polar progressions are normally used with two opposite hues to show a change in value from negative to positive or on either side of some either central tendency, such as the mean of the variable being mapped or other significant value like [room temperature](https://en.wikipedia.org/wiki/Room_temperature "Room temperature"). For example, a typical progression when mapping temperatures is from dark blue (for cold) to dark red (for hot) with white in the middle. When one extreme can be considered better than the other (as in this map of life expectancy[\[8\]](https://en.wikipedia.org/wiki/Choropleth_map#cite_note-8)) then it is common to denote the poor alternative with shades of red, and the good alternative with green.

Complementary hue progressions are a type of bi-polar progression. This can be done with any of the complementary colors and will fade from each of the darker end point hues into a gray shade representing the middle. An example would be using blue and yellow as the two end points.

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/3/33/Color_progression_examples_blended_hue.svg/220px-Color_progression_examples_blended_hue.svg.png)](https://en.wikipedia.org/wiki/File:Color_progression_examples_blended_hue.svg)

Blended hue color progression

Blended hue progressions use related hues to blend together the two end point hues. This type of color progression is typically used to show elevation changes. For example, from yellow through orange to brown.

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0a/Color_progression_examples_partial_spectral.svg/220px-Color_progression_examples_partial_spectral.svg.png)](https://en.wikipedia.org/wiki/File:Color_progression_examples_partial_spectral.svg)

Partial spectral color progression

Partial spectral hue progressions are used to map mixtures of two distinct sets of data. This type of hue progression will blend two adjacent opponent hues and show the magnitude of the mixing data classes.

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4c/Color_progression_examples_full-spectral.svg/220px-Color_progression_examples_full-spectral.svg.png)](https://en.wikipedia.org/wiki/File:Color_progression_examples_full-spectral.svg)

Full-spectral color progression

Full spectral progression contains hues from blue through red. This is common on relief maps and modern weather maps. This type of progression is not recommended under other circumstances because certain color connotations can confuse the map user.

Value progression maps are monochromatic. Although any color may be used, the archetype is from black to white with intervening shades of gray that represent magnitude. According to Robinson _et al._ (1995).[\[9\]](https://en.wikipedia.org/wiki/Choropleth_map#cite_note-9) this is the best way to portray a magnitude message to the map audience. It is clearly understood by the user and easy to produce in print.

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/4/46/Color_progression_examples_qualitative.svg/220px-Color_progression_examples_qualitative.svg.png)](https://en.wikipedia.org/wiki/File:Color_progression_examples_qualitative.svg)

Qualitative color progression

A Qualitative progression is often used when working with nominal or qualitative data. The colors shown on the map seem unrelated to one another or are arbitrarily chosen. For example, a choropleth map of "most prevalent religion" would be best shown with this type of scheme.

### Usability

When using any of these methods, there are two important principles: first is that darker colors are perceived as being higher in magnitude; second is that, while there are millions of color variations, the human eye is limited as to how many colors it can easily distinguish. Generally, five to seven color categories are recommended. The map user should be able to easily identify the implied magnitude of the hue and to match it with the legend.

Additional considerations include [color blindness](https://en.wikipedia.org/wiki/Color_blindness "Color blindness") and various reproduction techniques. For example, the red–green bi-polar progression described in the section above is likely to cause problems for [dichromats](https://en.wikipedia.org/wiki/Dichromacy "Dichromacy"). A related issue is that color scales which rely primarily on [hue](https://en.wikipedia.org/wiki/Hue "Hue") with insufficient variation in [saturation or intensity](https://en.wikipedia.org/wiki/HSL_and_HSV "HSL and HSV") may be compromised if reproduced in black and white. Conversely, if a map is legible in black and white ([lightness](https://en.wikipedia.org/wiki/Lightness "Lightness")\-based), then a prospective user's perception of color is irrelevant.

Color can greatly enhance the communication between the cartographer and their audience, but poor color choice can result in a map that is neither effective nor appealing to the map user. A simpler correlation between color-properties and underlying values is better.[\[11\]](https://en.wikipedia.org/wiki/Choropleth_map#cite_note-11) With considerations for black-and-white rendering, the color mapping function should be chosen to make sure the [lightness](https://en.wikipedia.org/wiki/Lightness "Lightness") of the color is still monotonic, or the uneven change would make it hard to interpret levels, for both normal and colorblind viewers. One commonly-mentioned offender is the "rainbow" palette, the default palette in many statistical applications that has a back-and-forth change in lightness.[\[12\]](https://en.wikipedia.org/wiki/Choropleth_map#cite_note-12)

See also
--------

1.  **[^](https://en.wikipedia.org/wiki/Choropleth_map#cite_ref-MF08_1-0)** [Michael Friendly](https://en.wikipedia.org/wiki/Michael_Friendly "Michael Friendly") (2008). ["Milestones in the history of thematic cartography, statistical graphics, and data visualization"](http://www.math.yorku.ca/SCS/Gallery/milestone/milestone.pdf).
2.  **[^](https://en.wikipedia.org/wiki/Choropleth_map#cite_ref-JKW_2-0)** [John Kirtland Wright](https://en.wikipedia.org/wiki/John_Kirtland_Wright "John Kirtland Wright") (1938). ["Problems in Population Mapping" in "Notes on statistical mapping, with special reference to the mapping of population phenomena"](https://www.worldcat.org/oclc/5160537/).
3.  **[^](https://en.wikipedia.org/wiki/Choropleth_map#cite_ref-3)** T. Slocum, R. McMaster, F. Kessler, H. Howard (2009). _Thematic Cartography and Geovisualization_, Third Edn, pages 85–86. Pearson Prentice Hall: Upper Saddle River, NJ.
4.  **[^](https://en.wikipedia.org/wiki/Choropleth_map#cite_ref-4)** Rittschof, Kent (1998). "Learning and Remembering from Thematic Maps of Familiar Regions". _Educational Technology Research and Development_. **46**: 19–38.
5.  **[^](https://en.wikipedia.org/wiki/Choropleth_map#cite_ref-5)** [Mark Monmonier](https://en.wikipedia.org/wiki/Mark_Monmonier "Mark Monmonier") (1991). _How to Lie with Maps_. pp. 22–23. University of Chicago Press
6.  **[^](https://en.wikipedia.org/wiki/Choropleth_map#cite_ref-6)** T. Slocum, R. McMaster, F. Kessler, H. Howard (2009). Thematic Cartography and Geovisualization, Third Edn, page 252. Pearson Prentice Hall: Upper Saddle River, NJ.
7.  **[^](https://en.wikipedia.org/wiki/Choropleth_map#cite_ref-7)** Robinson, A.H., Morrison, J.L., Muehrke, P.C., Kimmerling, A.J. & Guptill, S.C. (1995) _Elements of Cartography._ (6th Edition), New York: Wiley.
8.  **[^](https://en.wikipedia.org/wiki/Choropleth_map#cite_ref-8)** Patricia Cohen (9 August 2011). ["What Digital Maps Can Tell Us About the American Way"](http://artsbeat.blogs.nytimes.com/2011/08/09/what-digital-maps-can-tell-us-about-the-american-way). New York Times.
9.  **[^](https://en.wikipedia.org/wiki/Choropleth_map#cite_ref-9)** Robinson et al. (1995), op. cit.
10.  **[^](https://en.wikipedia.org/wiki/Choropleth_map#cite_ref-10)** ["Western Geographic Science Center"](http://geography.wr.usgs.gov/science/dasymetric/). Retrieved 13 November 2015.
11.  **[^](https://en.wikipedia.org/wiki/Choropleth_map#cite_ref-11)** Light; et al. (2004). ["The End of the Rainbow? Color Schemes for Improved Data Graphics"](http://geog.uoregon.edu/datagraphics/EOS/Light-and-Bartlein.pdf) (PDF). _Eos_. **85** (40): 385–91. [doi](https://en.wikipedia.org/wiki/Digital_object_identifier "Digital object identifier"):[10.1029/2004EO400002](https://doi.org/10.1029%2F2004EO400002).
12.  **[^](https://en.wikipedia.org/wiki/Choropleth_map#cite_ref-12)** Stauffer, Reto. ["Somewhere over the Rainbow"](http://hclwizard.org/#somewhere-over-the-rainbow). _HCL Wizard_. Retrieved 14 August 2019.

References
----------

*   Dent, Borden; Torguson, Jeffrey; Hodler, Thomas. _Cartography Thematic Map Design_. McGraw-Hill. [ISBN](https://en.wikipedia.org/wiki/International_Standard_Book_Number "International Standard Book Number") [978-0-072-94382-5](https://en.wikipedia.org/wiki/Special:BookSources/978-0-072-94382-5 "Special:BookSources/978-0-072-94382-5").

External links
--------------

{Alatalis}

  
  
from Hacker News https://ift.tt/1vzdl2Q