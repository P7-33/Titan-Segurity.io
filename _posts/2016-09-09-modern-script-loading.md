---
title: 'Modern Script Loading'
date: 2019-09-28T02:47:00+01:00
draft: false
---

> Serving the right code to the right browsers can be tricky. Here are some options.

![](https://res.cloudinary.com/wedding-website/image/upload/v1562702391/modern-script-loading_ku0eml.jpg)

Serving modern code to modern browsers can be great for performance. Your JavaScript bundles can contain more compact or optimized modern syntax, while still supporting older browsers.

The tooling ecosystem has consolidated on using the [module/nomodule pattern](https://philipwalton.com/articles/deploying-es2015-code-in-production-today/) for declaratively loading modern VS legacy code, which provides browsers with both sources and lets them decide which to use:

Unfortunately, it's not quite that straightforward. The HTML-based approach shown above triggers [over-fetching of scripts in Edge and Safari](https://gist.github.com/jakub-g/5fc11af85a061ca29cc84892f1059fec).

### What can we do?

What can we do? We want to deliver two compile targets depending on the browser, but a couple older browsers don't quite support the nice clean syntax for doing so.

First, there's the [Safari Fix](https://gist.github.com/samthor/64b114e4a4f539915a95b91ffd340acc). Safari 10.1 supports JS Modules not the `nomodule` attribute on scripts, which causes it to execute both the modern and legacy code _(yikes!)_. Thankfully, Sam found a way to use a non-standard `beforeload` event supported in Safari 10 & 11 to polyfill `nomodule`.

#### Option 1: Load Dynamically

We can circumvent these issues by implementing a tiny script loader, similar to how [LoadCSS](https://github.com/filamentgroup/loadCSS) works. Instead of relying on browsers to implement both ES Modules and the `nomodule` attribute, we can attempt to execute a Module script as a "litmus test", then use the result of that test to choose whether to load modern or legacy code.

```
 self.modern = true    addEventListener('load', function() { var s = document.createElement('script') if (self.modern) { s.src = '/modern.js' s.type = 'module' } else { s.src = '/legacy.js' } document.head.appendChild(s) }) 
```

However, this solution requires waiting until our first "litmus test" module script has run before it can inject the correct script. This is because `</code> is always asynchronous. There is a better way!</p><p>A standalone variant of this can be implemented by checking if the browser supports <code>nomodule</code>. This would mean browsers like Safari 10.1 are treated as legacy even though they support Modules, but that <a href="https://github.com/web-padawan/polymer3-webpack-starter/issues/33#issuecomment-474993984">might be</a> a <a href="https://github.com/babel/babel/pull/9584">good thing</a>. Here's the code for that:</p><pre><code>var s = document.createElement('script') if ('noModule' in s) { // notice the casing s.type = 'module' s.src = '/modern.js' } else s.src = '/legacy.js' } document.head.appendChild(s) </code></pre><p>This can be quickly rolled into a function that loads modern or legacy code, and also ensures both are loaded asynchronously:</p><pre><code><script> $loadjs("/modern.js","/legacy.js") function $loadjs(src,fallback,s) { s = document.createElement('script') if ('noModule' in s) s.type = 'module', s.src = src else s.async = true, s.src = fallback document.head.appendChild(s) }`

_What's the trade-off?_ **preloading**.

The trouble with this solution is that, because it's completely dynamic, the browser won't be able to discover our JavaScript resources until it runs the bootstrapping code we wrote to inject modern vs legacy scripts. Normally, browsers scan HTML as it is being streamed to look for resources they can preload. There's a solution, though it's not perfect: we can use  to preload the modern version of a bundle in modern browsers. Unfortunately, [only Chrome supports `modulepreload`](https://developers.google.com/web/updates/2017/12/modulepreload) so far.

```
 self.modern=1 
```

Whether this technique works for you can come down to the size of the HTML document you're embedding those scripts into. If your HTML payload is as small as a splash screen or just enough to bootstrap a client-side application, giving up the preload scanner is less likely to impact performance. If you are server-rendering a lot of meaningful HTML for the browser to stream, the preload scanner is your friend and this might not be the best approach for you.

Here's what this solution might look like in prod:

```
 self.modern=1  $loadjs("/modern.js","/legacy.js") function $loadjs(e,d,c){c=document.createElement("script"),self.modern?(c.src=e,c.type="module"):c.src=d,document.head.appendChild(c)} 
```

It's also be pointed out that the set of [browsers supporting JS Modules](https://caniuse.com/#feat=es6-module) is quite similar to [those that support](https://caniuse.com/#feat=link-rel-preload) . For some websites, it might make sense to use  rather than relying on modulepreload. This may have performance drawbacks, since classic script preloading doesn't spread parsing work out over time as well as modulepreload.

#### Option 2: User Agent Sniffing

I don't have a concise code sample for this since User Agent detection is nontrivial, but there's a great [Smashing Magazine article](https://www.smashingmagazine.com/2018/10/smart-bundling-legacy-code-browsers/) about it.

Essentially, this technique starts with the same ``</code> in the HTML for all browsers. When <code>bundle.js</code> is requested, the server parses the requesting browser's User Agent string and chooses whether to return modern or legacy JavaScript, depending on whether that browser is recognized as modern or not.</p><p>While this approach is versatile, it comes with some severe implications:</p><ul><li>since server smarts are required, this doesn't work for static deployment (static site generators, Netlify, etc)</li><li>caching for those JavaScript URLs now varies based on User Agent, which is highly volatile</li><li>UA detection is difficult and can be prone to false classification</li><li>the User Agent string is easily spoofable and new UA's arrive daily</li></ul><p>One way to address these limitations is to combine the module/nomodule pattern with User Agent differentiation in order to avoid sending multiple bundle versions in the first place. This approach still reduces cacheability of the page, but allows for effective preloading, since the server generating our HTML knows whether to use <code>modulepreload</code> or <code>preload</code>.</p><pre><code>function renderPage(request, response) { let html = `<html><head>...`; const agent = request.headers.userAgent; const isModern = userAgent.isModern(agent); if (isModern) { html += ` <link rel=modulepreload href=modern.mjs> <script type=module src=modern.mjs> `; } else { html += `   `; } response.end(html); }``

For websites already generating HTML on the server in response to each request, this can be an effective solution for modern script loading.

#### Option 3: Penalize older browsers

The ill-effects of the module/nomodule pattern are seen in old versions of Chrome, Firefox and Safari - browser versions with very limited usage, since users are automatically updated to the latest version. This doesn't hold true for Edge 16-18, but there is hope: new versions of Edge will use a Chromium-based renderer that doesn't suffer from this issue.

It might be perfectly reasonable for some applications to accept this as a trade-off: you get to deliver modern code to 90% of browsers, at the expense of some extra bandwidth on older browsers. Notably, none of the User Agents suffering from this over-fetching issue have significant mobile market share - so those bytes are less likely to be coming from an expensive mobile plan or through a device with a slow processor.

If you're building a site where your users are primarily on mobile or recent browsers, the simplest form of the module/nomodule pattern will work for the vast majority of your users. Just be sure to include the [Safari 10.1 fix](https://gist.github.com/samthor/64b114e4a4f539915a95b91ffd340acc) if you have usage from slightly older iOS devices.

```
 !function(e,t,n){!("noModule"in(t=e.createElement("script")))&&"onbeforeload"in t&&(n=!1,e.addEventListener("beforeload",function(e){if(e.target===t)n=!0;else if(!e.target.hasAttribute("nomodule")||!n)return;e.preventDefault()},!0),t.type="module",t.src=".",e.head.appendChild(t),t.remove())}(document) 
```

#### Option 4: Use conditional bundles

One clever approach here is to use `nomodule` to conditionally load bundles containing code that isn't needed in modern browsers, such as polyfills. With this approach, the worst-case is that the polyfills are loaded or possibly even executed (in Safari 10.1), but the effect is limited to "over-polyfilling". Given that the current prevailing approach is to load and execute polyfills in all browsers, this can be a net improvement.

Angular CLI can be configured to use this approach for polyfills, as [demonstrated by Minko Gechev](https://blog.mgechev.com/2019/02/06/5-angular-cli-features/#conditional-polyfill-serving). After reading about this approach, I realized we could switch the automatic polyfill injection in preact-cli to use it - [this PR](https://github.com/preactjs/preact-cli/pull/833/files) shows how easy it can be to adopt the technique.

For those using Webpack, there's a [handy plugin](https://github.com/swimmadude66/webpack-nomodule-plugin) for `html-webpack-plugin` that makes it easy to add nomodule to polyfill bundles.

* * *

### What should you do?

The answer depends on your use-case. If you're building a client-side application and your app's HTML payload is little more than a `</code>, you might find <em>Option 1</em> to be compelling. If you're building a server-rendered website and can afford the caching impact, <em>Option 2</em> could be for you. If you're using <a href="https://developers.google.com/web/updates/2019/02/rendering-on-the-web#rehydration">universal rendering</a>, the performance benefits offered by preload scanning might be very important, and you look to <em>Option 3</em> or <em>Option 4</em>. Choose what fits your architecture.</p><p>Personally, I tend to make the decision to optimize for faster parse times on mobile rather than the download cost on some desktop browsers. Mobile users experience parsing and data costs as actual expenses - battery drain and data fees - whereas desktop users don't tend to have these constraints. Plus, it's optimizing for the 90% - for the stuff I work on, most users are on modern and/or mobile browsers.</p><h3 id="furtherreading">Further Reading</h3><p>Interested in diving deeper into this space? Here's some places to start digging:</p><p>Thanks to <a href="https://twitter.com/philwalton">Phil</a>, <a href="https://twitter.com/shubhie">Shubhie</a>, <a href="https://twitter.com/atcastle">Alex</a>, <a href="https://twitter.com/hdjirdeh">Houssein</a>, <a href="https://twitter.com/Janicklas">Ralph</a> and <a href="https://twitter.com/addyosmani">Addy</a> for the feedback.</p><p><strong>2019-07-16:</strong> fixed code sample in Option 1, which was broken due to the asynchronous <code>self.modern</code> initialization.<br /></p></section></div><br /><br />from Hacker News https://ift.tt/30pKzVt </x-turndown>`