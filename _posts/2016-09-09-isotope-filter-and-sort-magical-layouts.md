---
title: 'Isotope · Filter and sort magical layouts'
date: 2020-01-23T03:35:00+01:00
draft: false
---

Install
-------

### Download

### CDN

Link directly to [unpkg](https://unpkg.com).

```
<script src="https://unpkg.com/isotope-layout@3/dist/isotope.pkgd.js">script>  <script src="https://unpkg.com/isotope-layout@3/dist/isotope.pkgd.min.js">script> 
```

### Package managers

[Install with npm](https://www.npmjs.com/package/isotope-layout): `npm install isotope-layout`

Install with Bower: `bower install isotope-layout --save`

License
-------

### Commercial license

If you want to use Isotope to develop commercial sites, themes, projects, and applications, the Commercial license is the appropriate license. With this option, your source code is kept proprietary. [Read more about Isotope commercial licensing](https://isotope.metafizzy.co/license.html).

Once purchased, you’ll receive a commercial license PDF and be all set to use Isotope in your commercial applications.

### Open source license

If you are creating an open source application under a license compatible with the [GNU GPL license v3](https://www.gnu.org/licenses/gpl-3.0.html), you may use Isotope under the terms of the GPLv3. [Read more about Isotope open source licensing](https://isotope.metafizzy.co/license.html).

Getting started
---------------

### HTML

Include the Isotope `.js` file in your site.

```
<script src="/path/to/isotope.pkgd.min.js">script> 
```

Isotope works on a container element with a group of similar child items.

```
<div class="grid"> <div class="grid-item">...div> <div class="grid-item grid-item--width2">...div> <div class="grid-item">...div> ... div> 
```

### CSS

All sizing of items is handled by your CSS.

```
.grid-item { width: 25%; } .grid-item--width2 { width: 50%; } 
```

### Initialize with jQuery

You can use Isotope as a jQuery plugin: `$('selector').isotope()`.

```
$('.grid').isotope({ // options itemSelector: '.grid-item', layoutMode: 'fitRows' }); 
```

### Initialize with Vanilla JavaScript

You can use Isotope with vanilla JS: `new Isotope( elem, options )`. The `Isotope()` constructor accepts two arguments: the container element and an options object.

```
var elem = document.querySelector('.grid'); var iso = new Isotope( elem, { // options itemSelector: '.grid-item', layoutMode: 'fitRows' }); // element argument can be a selector string // for an individual element var iso = new Isotope( '.grid', { // options }); 
```

### Initialize in HTML

You can initialize Isotope in HTML, without writing any JavaScript. Add `data-isotope` attribute to the container element. [Options](https://isotope.metafizzy.co/options.html) can be set in its value.

```
<div class="grid" data-isotope='{ "itemSelector": ".grid-item", "layoutMode": "fitRows" }'> 
```

Options set in HTML must be valid JSON. Keys need to be quoted, for example `"itemSelector":`. Note the HTML attribute `data-isotope` is set with single quotes `'`, but JSON entities use double-quotes `"`.

Next
----

Learn more about how to use Isotope:

Isotope in use
--------------

Justin Bieber, [Tyler Perry](http://www.tylerperry.com/entertainment/), [Colonel Sanders](http://colonelsanders.com): they all have used Isotope.

Are you using Isotope? Tweet [@metafizzyco](https://twitter.com/metafizzyco) or email [yo@metafizzy.co](mailto:yo@metafizzy.co) to share your work and possibly get it featured here.

People like Isotope
-------------------

[People like Isotope - Curated tweets by metafizzyco](https://twitter.com/metafizzyco/timelines/719923562660917248?ref_src=twsrc%5Etfw)

  
  
from Hacker News https://ift.tt/2plXF32