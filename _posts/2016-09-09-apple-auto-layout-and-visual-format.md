---
title: 'Apple''s auto layout and visual format language for JavaScript (2016)'
date: 2020-01-09T04:47:00+01:00
draft: false
---

### [](http://ijzerenhein.github.io/autolayout.js/#auto-whut-layout)Auto-whut-layout?

AutoLayout.js implements [Apple's Auto Layout](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/AutolayoutPG/index.html) constraint system and [Visual Format Language](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/AutolayoutPG/VisualFormatLanguage.html) in Javascript. Auto layout is a system which lets you perform lay out using mathematical relationships. It is based on the [incremental cassowary constraint solving toolkit](https://en.wikipedia.org/wiki/Cassowary_(software)) and uses the awesome [Cassowary.js](https://github.com/slightlyoff/cassowary.js) library. AutoLayout.js provides a simple API and programming model for integrating auto layout and VFL into other Javascript technologies, as well as an [editor](https://github.com/IjzerenHein/visualformat-editor) for creating layouts using (E)VFL.

[Click here to open the editor full-screen.](https://rawgit.com/IjzerenHein/visualformat-editor/master/dist/index.html?vfl=example)

### [](http://ijzerenhein.github.io/autolayout.js/#getting-started)Show us the code!

```
var constraints = AutoLayout.VisualFormat.parse([ 'H:|[view1(==view2)]-10-[view2]|' 'V:|[view1,view2]|' ], {extended: true}); var view = new AutoLayout.View({constraints: constraints}); view.setSize(400, 500); console.log(view.subViews.view1); // {left: 0, top: 0, width: 195, height: 500} console.log(view.subViews.view2); // {left: 205, top: 0, width: 195, height: 500} 
```The example above creates an auto layout View and populates it with constraints from the VFL parser. The View automatically creates sub-views based on the names used in the constraints/vfl. Next, the size of the view is set, which causes the sub-views to resize and re-position. The position and size of the sub-views can then be accessed through the `.subViews` property.

### [](http://ijzerenhein.github.io/autolayout.js/#getting-started)Getting started

If you want to get started with AutoLayout.js, please visit the [github page](https://github.com/IjzerenHein/autolayout.js#getting-started). You can find an example there to get started with [DOM layouting](https://github.com/IjzerenHein/autolayout.js/tree/master/examples/DOM) as well as other [useful resources](https://github.com/IjzerenHein/autolayout.js#additional-resources). There is also a [slack channel](https://overconstrained.slack.com/messages/autolayout-js/) hosted by [overconstrained.io](http://overconstrained.io/).

### [](http://ijzerenhein.github.io/autolayout.js/#extended-vfl)Extended Visual Format Language (EVFL)

Apple's Visual Format Language prefers good notation over completeness of expressibility. Because of this some useful constraints cannot be expressed by "Standard" VFL. AutoLayout.js defines an extended syntax (superset of VFL) which you can opt-in to use:

```
AutoLayout.VisualFormat.parse(vfl, {extended: true});
```

#### Proportional size: `%`

To make the size proportional to the size of the parent, you can use the following % syntax:

```
|-[view1(==50%)] // view1 is 50% the width of the parent (regardless of any spacing) [view1(>=50%)] // view1 should always be more than 50% the width of the parent
```

#### Operators: `* / + -`

Operators can be used to create linear equations of the form: `view1.attr1 == view2.attr2 * multiplier + constant`. To for instance, make the width or height proportional to another view, use:

```
|-[view1(==view2/2)]-[view2]-| // view1 is half the width of view2 |-[view1(==view2*4-100)]-[view2]-| // view1 is four times the width minus 100, of view2
```

#### Attributes: `.{attribute}`

In some cases it is useful to for instance make the width equal to the height:

```
|-[view1]-| V:|-[view1(view1.width)]
```

You can also combine with operators to enforce an aspect ratio:

```
V:|-[view1(view1.width/3)]
```

Supported attributes:

```
.width .height .left .top .right .bottom .centerX .centerY
```

#### Z-ordering: `Z:`

When sub-views overlap it can be useful to specify the z-ordering for the sub-views:

```
Z:|[child1][child2] // child2 is placed in front of child1 Z:|[background]-10-[child1..2] // child1 and child2 are placed 10 units in-front of background
```

#### Equal size spacers / centering: `~`

Sometimes you just want to center a view. To do this use the \`~\` connector:

```
|~[view1(100)]~| // view1 has width of 100 and is centered V:|~(10%)~[view2]~| // top & bottom spacers have height of 10%
```

All \`~\` connectors inside a single line of EVFL are constrained to have the same size. You can also use more than 2 connectors to proportionally align views:

```
|~[child1(10)]~[child2(20)]~[child3(30)]~|
```

#### View stacks: `[col:[header][content[footer]]`

View stacks make it possible to group views into a column or a row. The following example creates a view stack named \`column\` which contains three sub-views. The benefit of this is is revealed in the second line, in which the stack as whole is horizontally positioned.

```
V:|[column:[top(50)][content][bottom(50)]]| H:|[column]|
```

#### View ranges: `[circle1..5]`

View ranges make it possible to select multiple views at once and apply rules for them:

```
//shapes circle1..5:circle H:[circle1(circle1.height)] // set aspect-ratio for circle1 HV:[circle2..5(circle1)] // use same width/height for other circles H:|[circle1]-[circle2]-[circle3]-[circle4]-[circle5]| V:|~[circle1..5]~| // center all circles vertically
```

#### Multiple views: `[view1,view2,..]`

Similar to 'View ranges', multiple views can be separated using the `,` character:

```
H:|[left(top,right)]-[top,bottom]-[right]| V:|[left,right]| V:|[top(bottom)]-[bottom]|
```

#### Multiple orientations: `HV:`

Sometimes you just want to fill a view to its container. With standard VFL you have to write two lines, one for the horizontal orientation and one for vertical:

```
H:|[background]| V:|[background]|
```

With Extended VFL, these can be combined into one line:

```
HV:|[background]|
```

When using spacers, you can even use different spacings for horizontal & vertical orientations:

```
//spacing: [10, 20] HV:|-[background]-|
```

#### Disconnections (right/bottom alignment): `->`

By default, views are interconnected when defined after each other (e.g. `[view1][view2][view3]`). In some cases it is useful to not interconnect the views, in order to align content to the right or bottom. The following example shows a disconnection causing the content after the disconnect to align to the right-edge:

```
 // left1..2 are left-aligned, right1..2 are right aligned |[left1(100)][left2(300)]->[right1(100)][right2(100)]| ^^ ^^ ^^ left1 is left2 and right2 is connected to right1 are connected to super-view not connected super-view
```

#### Negative values (overlapping views):

Numbers and percentages can also be negative, which can be useful for overlapping views:

```
H:|[top,middle,bottom]| V:|[top(100)]-(-10)-[middle(top)]-(middle/-2)-[bottom]| Z:|[top][middle][bottom]
```

#### Explicit constraint syntax:

Constraints can also be expressed explicitly. This can be particular useful when it is otherwise not possible to express a layout or rule:

```
C:view1.centerX(view2.centerX) // view1 is horizontally centered to view2 C:view1.centerX(view2) // attribute is inferred when omitted (centerX) C:view1.centerX(view2).bottom(view2.bottom) // chaining syntax C:view1.height(view2.width*2+10) // expressions
```

#### Comments: `// comments here`

Single line comments can be used to explain the VFL or to prevent its execution:

```
// Enfore aspect ratios [view1(view1.height/3)] // enfore aspect ratio 1/3 // [view2(view2.height/3)] 
```

#### Documentation

The full EVFL syntax documentation is hosted [here on github](https://github.com/IjzerenHein/autolayout.js#extended-visual-format-language-evfl).

  
  
from Hacker News https://ift.tt/2egUtFY