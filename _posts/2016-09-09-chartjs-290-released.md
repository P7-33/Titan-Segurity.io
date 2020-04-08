---
title: 'Chart.js 2.9.0 Released'
date: 2019-10-26T04:17:00+01:00
draft: false
---

![](https://avatars3.githubusercontent.com/u/10342521?s=400&v=4 "Release v2.9.0 · chartjs/Chart.js · GitHub")  

Breaking changes
----------------

*   [#6131](https://github.com/chartjs/Chart.js/pull/6131) `helpers._decimalPlaces` is now private

Enhancements
------------

*   [#6527](https://github.com/chartjs/Chart.js/pull/6527) Hover styling for dataset in 'dataset' mode
*   [#6268](https://github.com/chartjs/Chart.js/pull/6268) Implement `dataset.order`
*   [#6509](https://github.com/chartjs/Chart.js/pull/6509) Make `autoSkip` aware of major ticks
*   [#6460](https://github.com/chartjs/Chart.js/pull/6460) Implemented RTL support for legends and tooltips
*   [#6490](https://github.com/chartjs/Chart.js/pull/6490) HTML DOM building
*   [#6326](https://github.com/chartjs/Chart.js/pull/6326) Draw the rightmost grid line when `offsetGridLines` is true
*   [#6343](https://github.com/chartjs/Chart.js/pull/6343) Handle reverse support in core.scale
*   [#6289](https://github.com/chartjs/Chart.js/pull/6289) Support `spanGaps` in radar charts
*   [#6323](https://github.com/chartjs/Chart.js/pull/6323) Support object values for bar charts
*   [#6287](https://github.com/chartjs/Chart.js/pull/6287) Support rotation for `pointStyle` image
*   [#6257](https://github.com/chartjs/Chart.js/pull/6257) Allow specifying labels in time scale options
*   [#6281](https://github.com/chartjs/Chart.js/pull/6281) Support boundary filling modes in radialLinear scale
*   [#6056](https://github.com/chartjs/Chart.js/pull/6056) Add support for floating bar chart (`[start, end]`)
*   [#6241](https://github.com/chartjs/Chart.js/pull/6241) Implement layers (z-index) for layout items
*   [#5621](https://github.com/chartjs/Chart.js/pull/5621) Make legend appearance consistent with chart elements
*   [#5999](https://github.com/chartjs/Chart.js/pull/5999) Implement per-dataset type (default and per-chart) options
*   [#6097](https://github.com/chartjs/Chart.js/pull/6097) Specify time scale `min` and `max` in standard manner
*   [#6141](https://github.com/chartjs/Chart.js/pull/6141) Legend align option. Thanks [@dkichler](https://github.com/dkichler)
*   [#6128](https://github.com/chartjs/Chart.js/pull/6128) Make line options scriptable. Thanks [@janelledement](https://github.com/janelledement)

Performance
-----------

*   [#6594](https://github.com/chartjs/Chart.js/pull/6594) Remove a couple calls to `helpers.each`
*   [#6247](https://github.com/chartjs/Chart.js/pull/6247) Remove duplicate scale building
*   [#6579](https://github.com/chartjs/Chart.js/pull/6579) Cache resolved data element options
*   [#6575](https://github.com/chartjs/Chart.js/pull/6575) Simplify line drawing
*   [#6508](https://github.com/chartjs/Chart.js/pull/6508) Add `ticks.sampleSize` option
*   [#6354](https://github.com/chartjs/Chart.js/pull/6354) Perf improvement for `ticks.source:'labels'`
*   [#6301](https://github.com/chartjs/Chart.js/pull/6301) Replace `helpers.each` with for-loops
*   [#6304](https://github.com/chartjs/Chart.js/pull/6304) Refactor `core.layout`
*   [#6307](https://github.com/chartjs/Chart.js/pull/6307) Faster major tick calculation
*   [#6250](https://github.com/chartjs/Chart.js/pull/6250) Cache `getScaleForId()` calls in the line controller
*   [#6148](https://github.com/chartjs/Chart.js/pull/6148) Replace `helpers.extend`

Bug Fixes
---------

*   [#6249](https://github.com/chartjs/Chart.js/pull/6249) Bar options should be defined on dataset instead of scale
*   [#6556](https://github.com/chartjs/Chart.js/pull/6556) Inject styles into Shadow DOM when inside Shadow DOM
*   [#6583](https://github.com/chartjs/Chart.js/pull/6583) Fix unit determination when `autoSkip` is enabled
*   [#6581](https://github.com/chartjs/Chart.js/pull/6581) Return correct index/value id in radar/polarArea
*   [#6580](https://github.com/chartjs/Chart.js/pull/6580) Fix logarithmic test to use correct scale
*   [#6528](https://github.com/chartjs/Chart.js/pull/6528) Make sure `zeroLineIndex` is defined
*   [#6523](https://github.com/chartjs/Chart.js/pull/6523) Fix right side scale ticks
*   [#6423](https://github.com/chartjs/Chart.js/pull/6423) Clamp argument of `toExponential` between 0 and 20. Thanks [@veggiesaurus](https://github.com/veggiesaurus)
*   [#6328](https://github.com/chartjs/Chart.js/pull/6328) Fix `getValueForPixel` in time scale
*   [#6292](https://github.com/chartjs/Chart.js/pull/6292) Adjust vertical alignment of tooltip items
*   [#6321](https://github.com/chartjs/Chart.js/pull/6321) Update dataset metadata when axisID changes
*   [#6291](https://github.com/chartjs/Chart.js/pull/6291) Assign unique scale IDs
*   [#6288](https://github.com/chartjs/Chart.js/pull/6288) Fix regression in `lineTension`
*   [#6282](https://github.com/chartjs/Chart.js/pull/6282) Treat null as NaN in radialLinear scale
*   [#6285](https://github.com/chartjs/Chart.js/pull/6285) Keep lines on the left and right edges from being cut
*   [#6269](https://github.com/chartjs/Chart.js/pull/6269) Apply lineJoin style at the first point in radar charts
*   [#6280](https://github.com/chartjs/Chart.js/pull/6280) Fix point label counting in radialLinear scale
*   [#6279](https://github.com/chartjs/Chart.js/pull/6279) Treat 0 as a valid point label
*   [#6265](https://github.com/chartjs/Chart.js/pull/6265) Utilize `tick.major` in `tickFormatFunction`
*   [#6264](https://github.com/chartjs/Chart.js/pull/6264) Apply offset regardless of min/max setting
*   [#6258](https://github.com/chartjs/Chart.js/pull/6258) Fix ticks generation for vertical time scale
*   [#6259](https://github.com/chartjs/Chart.js/pull/6259) Fix `determineUnitForFormatting` floating point error
*   [#6115](https://github.com/chartjs/Chart.js/pull/6115) Fix overlapping auto-generated ticks on time scale
*   [#6238](https://github.com/chartjs/Chart.js/pull/6238) Fix tooltip title in radar charts
*   [#6224](https://github.com/chartjs/Chart.js/pull/6224) Fix arc size calculation when circumference is under 2\*PI
*   [#6215](https://github.com/chartjs/Chart.js/pull/6215) Fix arc border with circumference over 2\*PI
*   [#5961](https://github.com/chartjs/Chart.js/pull/5961) Fix tick label rotation and layout issues
*   [#6182](https://github.com/chartjs/Chart.js/pull/6182) Use the appropriate time format for auto tick generation
*   [#6208](https://github.com/chartjs/Chart.js/pull/6208) Fill before drawing lines
*   [#6209](https://github.com/chartjs/Chart.js/pull/6209) Fix missing tooltip value in radar charts
*   [#6177](https://github.com/chartjs/Chart.js/pull/6177) Normalize angle for index in radialLinear scale
*   [#6102](https://github.com/chartjs/Chart.js/pull/6102) Fix `ticks.minor` and `ticks.major` issues
*   [#6129](https://github.com/chartjs/Chart.js/pull/6129) Fix hover animation
*   [#6120](https://github.com/chartjs/Chart.js/pull/6120) Improved `helpers.almostWhole`

Documentation
-------------

*   [#6585](https://github.com/chartjs/Chart.js/pull/6585) Add a note to the perf documentation about rotation
*   [#6554](https://github.com/chartjs/Chart.js/pull/6554) Add link to linear radial axis for radar chart doc
*   [#6491](https://github.com/chartjs/Chart.js/pull/6491) Add `elements.arc.angle` in documentation
*   [#6466](https://github.com/chartjs/Chart.js/pull/6466) Fixed incorrect spelling in pie dataset options. Thanks [@SeppPenner](https://github.com/SeppPenner)
*   [#6435](https://github.com/chartjs/Chart.js/pull/6435) Add link back to home page from docs
*   [#6393](https://github.com/chartjs/Chart.js/pull/6393) Add radar chart config options
*   [#6293](https://github.com/chartjs/Chart.js/pull/6293) Correct descriptions on `ticks.display` and add `pointLabels.display`
*   [#6263](https://github.com/chartjs/Chart.js/pull/6263) Add sample for radar scriptable options
*   [#6244](https://github.com/chartjs/Chart.js/pull/6244) Fix data in timeseries sample
*   [#6186](https://github.com/chartjs/Chart.js/pull/6186) Typo in doughnut documentation. Thanks [@joshuamcewen](https://github.com/joshuamcewen)
*   [#6132](https://github.com/chartjs/Chart.js/pull/6132) Make docs consistent for `cubicInterpolationMode` and `fill`. Thanks [@stockiNail](https://github.com/stockiNail)
*   [#6119](https://github.com/chartjs/Chart.js/pull/6119) Demonstrate multiple units on timeseries example
*   [#6139](https://github.com/chartjs/Chart.js/pull/6139) Documented tooltip alignment options
*   [#6134](https://github.com/chartjs/Chart.js/pull/6134) Documented date adapter

Development
-----------

*   [#6507](https://github.com/chartjs/Chart.js/pull/6507) Improved minimization when calling helpers
*   [#6497](https://github.com/chartjs/Chart.js/pull/6497) Reduce indentation
*   [#6355](https://github.com/chartjs/Chart.js/pull/6355) Do `autoSkip` in `update`
*   [#6493](https://github.com/chartjs/Chart.js/pull/6493) Upgrade rollup and plugins
*   [#6362](https://github.com/chartjs/Chart.js/pull/6362) Improved code minimization
*   [#6360](https://github.com/chartjs/Chart.js/pull/6360) Create `helpers.math._factorize`
*   [#6351](https://github.com/chartjs/Chart.js/pull/6351) Lazily compute label sizes
*   [#6347](https://github.com/chartjs/Chart.js/pull/6347) Render charts only once in time scale tests
*   [#6246](https://github.com/chartjs/Chart.js/pull/6246) Avoid time related deprecation warnings in tests

Thanks to the maintainers and collaborators for their help to improve and test Chart.js ([@nagix](https://github.com/nagix), [@kurkle](https://github.com/kurkle), [@benmccann](https://github.com/benmccann), [@etimberg](https://github.com/etimberg) and [@simonbrunel](https://github.com/simonbrunel)).

You can’t perform that action at this time.

You signed in with another tab or window. [Reload](https://github.com/chartjs/Chart.js/releases/tag/v2.9.0) to refresh your session. You signed out in another tab or window. [Reload](https://github.com/chartjs/Chart.js/releases/tag/v2.9.0) to refresh your session.

  
  
from Hacker News https://ift.tt/347ABtx