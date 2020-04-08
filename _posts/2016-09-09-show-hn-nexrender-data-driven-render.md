---
title: 'Show HN: Nexrender – Data-Driven Render Automation for After Effects'
date: 2019-10-13T10:04:00+01:00
draft: false
---

[![](https://user-images.githubusercontent.com/2182108/60247318-22ba6480-98c9-11e9-8447-1cbb01db15fe.png)](https://user-images.githubusercontent.com/2182108/60247318-22ba6480-98c9-11e9-8447-1cbb01db15fe.png)

  

Automate your Adobe After Effects rendering workflows. Create data-driven and template based videos.

[](https://github.com/inlife/nexrender#table-of-contents)Table of contents
==========================================================================

[](https://github.com/inlife/nexrender#introduction)Introduction
================================================================

> Note: this is a newly released major version of the software. For older, more "stable" version please refer to ["stable"](https://github.com/inlife/nexrender/tree/stable) branch.

`nexrender` is a simple, small, carefully designed application with the main goal of rendering automation for Adobe After Effects based rendering workflows.

At this point in time, the project is mainly targeted at people at least somewhat comfortable with scripting or development, and that have basic knowledge of `javascript` language and `json` formats.

### [](https://github.com/inlife/nexrender#features)Features

*   data-driven, dynamic, personalized video rendering
*   automated video management, processing, and delivery
*   network oriented project structure, render farm
*   highly modular nature, extensive plugin support
*   works only in cli mode, never launches After Effects GUI application
*   does not require licenses for Adobe After Effects on any worker machine
*   free to use and open source

### [](https://github.com/inlife/nexrender#how-it-works)How it works

*   rendering: It uses Adobe After Effects' aerender command-line interface application.
*   compositing: It creates a temporary folder, copies project and replaces assets with provided ones.
*   personalization: It uses AE's expressions, scripting, and compositing (noted above).
*   scheduling: It stores projects in a local database, managed from anywhere using http api.
*   network: It renders project per machine, and can be used to render several projects simultaneously.
*   farm: Can be used to render a single project on several machines via Multi-Machine Sequence.

### [](https://github.com/inlife/nexrender#alternatives)Alternatives

Probably the closest (feature-wise) alternative that exists at the moment is the Dataclay's [Templater](http://dataclay.com/) bot edition. Compared to nexrender it has a rich GUI support and a number of enterprise-scale features, however, it is not free.

[](https://github.com/inlife/nexrender#installation)Installation
================================================================

You can download binaries directly from the [releases](https://github.com/inlife/nexrender/releases) section, or install them using npm, whichever option works better for you.

However, please note: the npm version of the binaries doesn't include all optional `plugin` packages that are covered in the usage section. If you wish to install them as well, please do so by providing each one individually:

```
npm i -g @nexrender/cli @nexrender/action-copy @nexrender/action-encode ... 
```

[](https://github.com/inlife/nexrender#usage)Usage
==================================================

We will be using `nexrender-cli` binary for this example. It's recommended to download/install it if you haven't already.

Also, check out these example/tutorial videos made by our community:

[](https://github.com/inlife/nexrender#job)Job
----------------------------------------------

A job is a single working unit in the nexrender ecosystem. It is a json document, that describes what should be done, and how it should be done. Minimal job description always should contain a pointer onto Adobe After Effects project, which is needed to be rendered, and a composition that will be used to render.

The pointer is `src` (string) field containing a URI pointing towards specified file, followed by `composition` (string) field, containing the name of the composition that needs to be rendered.

> Note: check out [supported protocols](https://github.com/inlife/nexrender#protocols) for `src` field.

```
// myjob.json { "template": { "src": "file:///users/myuser/documents/myproject.aep", "composition": "main" } }
```

or for remote file accessible via http

```
// myjob.json { "template": { "src": "http://example.com/myproject.aep", "composition": "main" } }
```

Submitting this data to the binary will result in start of the rendering process:

```
$ nexrender-cli '{"template":{"src":"file:///home/documents/myproject.aep","composition":"main"}}'
```

or more conveniently using the `--file` option

```
$ nexrender-cli --file myjob.json
```

> Note: its recommended to run `nexrender-cli -h` at least once, to read all useful information about available options.

More info: [@nexrender/cli](https://github.com/inlife/nexrender/blob/master/packages/nexrender-cli)

### [](https://github.com/inlife/nexrender#assets)Assets

We've successfully rendered a static project file using nexrender, however, there is no much point doing that unless we are going to add some dynamic data into the mix.

A way to implement something like that is to add an `asset` to our job definition:

```
// myjob.json { "template": { "src": "file:///d:/documents/myproject.aep", "composition": "main" }, "assets": \[ { "src": "file:///d:/images/myimage.png", "type": "image", "layerName": "background.png" } \] }
```

What we've done there is we told nexrender to use a particular asset as a replacement for something that we had defined in our `aep` project. More specifically, when rendering is gonna happen, nexrender will copy/download this asset file, and attempt to find and replace `footage` entry by specified layer name.

Check out: [detailed information about footage items](https://github.com/inlife/nexrender#footage-items).

### [](https://github.com/inlife/nexrender#actions)Actions

You might've noticed that unless you added `--skip-cleanup` flag to our command, all rendered results will be deleted, and a big warning message will be shown every time you attempt to run the `nexrender-cli` with our job.

The reason is that we haven't defined any actions that we need to do after we finished actual rendering. Let's fix that and add a simple one, copy.

```
// myjob.json { "template": { "src": "http://example.com/assets/myproject.aep", "composition": "main" }, "assets": \[ { "src": "http://example.com/assets/myimage.png", "type": "image", "layerName": "background.png" } \], "actions":{ "postrender": \[ { "module": "@nexrender/action-encode", "preset": "mp4", "output": "encoded.mp4" }, { "module": "@nexrender/action-copy", "input": "encoded.mp4", "output": "d:/mydocuments/results/myresult.mp4" } \] } }
```

We've just added a `postrender` action, that will occur right after we finished rendering. A module that we described in this case, is responsible for copying result file from a temp folder to the `output` folder.

There are multiple built-in modules within nexrender ecosystem:

Every module might have his own set of fields, however, `module` field is always there.

Also, you might've noticed that `actions` is an object, however, we described only one (`postrender`) field in it. And there is one more, its called `prerender`. The latter can be used to process data/assets just before the actual render will start.

Also, if you are planning on having more than one action, please note: **actions are order-sensitive**, that means if you put let's say some encoding action after upload, the latter one might not be able to find a file that needs to be generated by former one, since the ordering was wrong.

If you have at least some experience with `Node.js`, you might've noticed that the `module` definition looks exactly like a package name. And well, yes it is. When nexrender stumbles upon a `module` entry, it will try to require this package from internal storage, and then if no module has been found, it will attempt to look for globally installed Node.js modules with that name.

That means if you are comfortable with writing `Node.js` code, you can easily create your own module, and use it by providing either absolute/relative path (on a local machine), or publishing the module and installing it globally on your target machine.

```
npm i -g my-awesome-nexrender-action
```

And then using it:

```
{ "actions":{ "postrender": \[ { "module": "my-awesome-nexrender-action", "param1": "something big", "param2": 15 } \] } }
```

Also, you can [checkout packages](https://github.com/inlife/nexrender#external-packages) made by other contributors across the network:

### [](https://github.com/inlife/nexrender#details)Details

Job structure has more fields, that we haven't checked out yet. The detailed version of the structure looks like this:

```
{ "template": { "src": String, "composition": String, "frameStart": Number, "frameEnd": Number, "frameIncrement": Number, "continueOnMissing": Boolean, "settingsTemplate": String, "outputModule": String, "outputExt": String, }, "assets": \[\], "actions": { "prerender": \[\], "postrender": \[\], }, "onChange": Function, "onRenderProgress": Function }
```

Majority of the fields are just proxied to the `aerender` binary, and their descriptions and default values can be checked [here](https://helpx.adobe.com/after-effects/using/automated-rendering-network-rendering.html).

*   `onChange` is a [callback](https://github.com/inlife/nexrender/blob/master/packages/nexrender-core/src/helpers/state.js) which will be triggered every time the job state is changed (happens on every task change).
    
*   `onRenderProgress` is a [callback](https://github.com/inlife/nexrender/blob/master/packages/nexrender-core/src/tasks/render.js) which will be triggered every time the rendering progress has changed.
    

Note: Callback functions are only available via programmatic use. For more information, please refer to the source code.

[](https://github.com/inlife/nexrender#programmatic)Programmatic
----------------------------------------------------------------

In case you are building your own application and just need to use a rendering part, or you wanna manually trigger jobs from your code, there is a way to use nexrender programmatically:

Install the [@nexrender/core](https://github.com/inlife/nexrender/tree/master/packages/nexrender-core)

```
$ npm install @nexrender/core --save
```

And then load it, and run it

```
const { init, render } \= require('@nexrender/core') const settings \= init({ logger: console, }) const main \= async () \=> { const result \= await render(/\*myJobJson\*/, settings) } main().catch(console.error);
```

More info: [@nexrender/core](https://github.com/inlife/nexrender/blob/master/packages/nexrender-core)

[](https://github.com/inlife/nexrender#template-rendering)Template rendering
============================================================================

One of the main benefits of using nexrender is an ability to render projects using data other than what has been used while the project has been created. Data means any sort of source/footage material, it can be images, audio tracks, video clips, text strings, values for colors/positions, even dynamic animations using expressions. All of those things can be replaced for every job without even opening a project file or starting After Effects.

> Note: Also this process can be called in other ways: **templated**, **data-driven** or **dynamic** video generation.

This approach allows you to create a .aep file once, and then reuse it for as many target results as you need to. However, what is needed to get started?

[](https://github.com/inlife/nexrender#footage-items)Footage items
------------------------------------------------------------------

Footage item replacement is what briefly has been covered in the `Job` section of this document. The idea is quite simple, you describe which asset will replace existing described footage item in a specific layer, by specifying `src`, and one of the `layerName` or `layerIndex` options.

### [](https://github.com/inlife/nexrender#fields)Fields

*   `src`: string, a URI pointer to the specific resource, check out [supported protocols](https://github.com/inlife/nexrender#protocols)
*   `type`: string, for footage items, is one of (`image`, `audio`, `video`)
*   `layerName`: string, target layer name in the After Effects project
*   `layerIndex`: integer, can be used instead of `layerName` to select a layer by providing an index, starting from 1 (default behavior of AE jsx scripting env)
*   `composition`: string, composition where the layer is, useful for searching layer in pre-compositions. If none is provided, it uses the default composition set in the template. Providing `"*"` will result in a wildcard compostion matching, and will apply this data to every matching layer in every matching composition.

Specified asset from `src` field will be downloaded/copied to the working directory, and just before rendering will happen, a fotage item with specified `layerName` or `layerIndex` in the original project will be replaced with the freshly downloaded asset.

This way you (if you are using network rendering) you can not only deliver assets to the target platform but also dynamically replace them.

> Note: if `layerName` is used for footage file asset, it should always contain the extension in the name as well.

### [](https://github.com/inlife/nexrender#example)Example

```
{ "assets": \[ { "src": "https://example.com/assets/image.jpg", "type": "image", "layerName": "MyNicePicture.jpg" }, { "src": "file:///home/assets/audio.mp3", "type": "audio", "layerIndex": 15 } \] }
```

[](https://github.com/inlife/nexrender#data-items)Data items
------------------------------------------------------------

The second important point for the dynamic data-driven video generation is the ability to replace/change/modify non-footage data in the project. To do that a special asset of type `data` can be used.

### [](https://github.com/inlife/nexrender#fields-1)Fields

*   `type`: string, for data items, is always `data`
*   `layerName`: string, target layer name in the After Effects project
*   `layerIndex`: integer, can be used instead of `layerName` to select a layer by providing an index, starting from 1 (default behavior of AE jsx scripting env)
*   `property`: string, indicates which layer property you want to change
*   `value`: mixed, optional, indicates which value you want to be set to a specified property
*   `expression`: string, optional, allows you to specify an expression that can be executed every frame to calculate the value
*   `composition`: string, composition where the layer is, useful for searching layer in pre-compositions. If none is provided, it uses the default composition set in the template.

Since both `value` and `expression` are optional you can provide them in any combination, depending on the effect you want to achieve. Providing value will set the exact value for the property right after execution, and providing an expression will make sure it will be evaluated every frame.

> Note: If you are not sure what expressions are, and how to use them, please refer [to this page](https://helpx.adobe.com/after-effects/using/expression-basics.html)

And if you are not sure what is a `property` and where to get it you can refer to this image:

**Property Example**

> As you can see there are a few `Property Groups` like Text, Masks, Transform that include actual properties. Those properties are what can be used as a target.

[![](https://user-images.githubusercontent.com/2182108/52443468-7270dd00-2b2e-11e9-8336-255349279c43.png)](https://user-images.githubusercontent.com/2182108/52443468-7270dd00-2b2e-11e9-8336-255349279c43.png)

In case you need to change some **deep properties**, like show on this image:

[![](https://user-images.githubusercontent.com/7440211/59557356-6fa45e00-8fe0-11e9-84d4-f4e8152f2913.png)](https://user-images.githubusercontent.com/7440211/59557356-6fa45e00-8fe0-11e9-84d4-f4e8152f2913.png)

You can do that by providing the property name using a dot `.` separator. (Example: "Effects.Skin\_Color.Color") In case your property already has `.` in the name, and you are sure it will lead to a collision, while parsing, you can also use arrow symbol `->` instead.

You can also change the deeper attributes of properties, for example the font of a text layer using "Source Text.font" or the font size by "Source Text.fontSize".

### [](https://github.com/inlife/nexrender#example-1)Example

```
{ "assets": \[ { "type": "data", "layerName": "MyNicePicture.jpg", "property": "Position", "value": \[500, 100\] }, { "type": "data", "layerName": "my text field", "property": "Source Text", "expression": "time > 100 ? 'Bye bye' : 'Hello world'" }, { "type": "data", "layerName": "my text field", "property": "Source Text.font", "value": "Arial-BoldItalicMT" }, { "type": "data", "layerName": "background", "property": "Effects.Skin\_Color.Color", "value": \[1, 0, 0\] }, { "type": "data", "layerIndex": 15, "property": "Scale", "expression": "\[time \* 0.1, time \* 0.1\]" }, \] }
```

> Note: any error in expression will prevent the project from rendering. Make sure to read error messages reported by After Effects binary carefully.

[](https://github.com/inlife/nexrender#script-items)Script items
----------------------------------------------------------------

The last and the most complex and yet the most powerful is an ability to execute custom `jsx` scripts just before the rendering will start. This approach allows you to do pretty much anything that is allowed for scripting, like creating/removing layers, adding new elements, restructuring the whole composition, and probably much more.

Now, actual complexity happens only from the side of actual scripting, you need to have some basic knowledge of `ExtendScript Toolkit`, and from the nexrender side everything is quite simple. You only need to provide an `src` pointing towards script resource and set up proper type.

### [](https://github.com/inlife/nexrender#fields-2)Fields

*   `src`: string, a URI pointer to the specific resource, check out [supported protocols](https://github.com/inlife/nexrender#protocols)
*   `type`: string, for script items, is always `script`

### [](https://github.com/inlife/nexrender#example-2)Example

```
{ "assets": \[ { "src": "http://example.com/scripts/myscript.jsx", "type": "script" } \] }
```

That pretty much covers basics of templated rendering.

[](https://github.com/inlife/nexrender#network-rendering)Network rendering
==========================================================================

We've covered basics on how to set up a minimal rendering flow using local cli machine rendering. Now, what if you want to start rendering on a remote machine, to reduce load while you are working on your local machine. Or maybe you need to render so many videos at once, that you will require a whole fleet of nodes running on some cloud cluster.

With nexrender, you can quite quickly and easily spin up your own rendering cluster.

[](https://github.com/inlife/nexrender#using-binaries)Using binaries
--------------------------------------------------------------------

You can download compiled versions of binaries directly from the [releases](https://github.com/inlife/nexrender/releases) section, or install them using npm, whichever option works better for you.

### [](https://github.com/inlife/nexrender#nexrender-server)`nexrender-server`

#### [](https://github.com/inlife/nexrender#description)Description:

A CLI application which is responsible for job management, worker node cooperation, communications with the `nexrender-worker` instances, and serves mainly as a producer in the nexrender network model.

Technically speaking its a very tiny HTTP server running with a minimal version of REST API.

#### [](https://github.com/inlife/nexrender#supported-platforms)Supported platforms:

Windows, macOS, Linux

#### [](https://github.com/inlife/nexrender#requirements)Requirements:

None

#### [](https://github.com/inlife/nexrender#example-3)Example

```
$ nexrender-server \\ --port=3050 \\ --secret=myapisecret
```

More info: [@nexrender/server](https://github.com/inlife/nexrender/blob/master/packages/nexrender-server)

### [](https://github.com/inlife/nexrender#nexrender-worker)`nexrender-worker`

#### [](https://github.com/inlife/nexrender#description-1)Description:

A CLI application which is responsible mainly for actual job processing and rendering, communication with the `nexrender-server`, and serves mainly as a consumer in the nexrender network model.

#### [](https://github.com/inlife/nexrender#supported-platforms-1)Supported platforms:

Windows, macOS

#### [](https://github.com/inlife/nexrender#requirements-1)Requirements:

Installed licensed/trial version of Adobe After Effects

#### [](https://github.com/inlife/nexrender#example-4)Example

```
$ nexrender-worker \\ --host=https://my.server.com:3050 \\ --secret=myapisecret
```

> Note: its recommended to run `nexrender-worker -h` at least once, to read all useful information about available options.

More info: [@nexrender/worker](https://github.com/inlife/nexrender/blob/master/packages/nexrender-worker)

[](https://github.com/inlife/nexrender#using-api)Using API
----------------------------------------------------------

Now, after you've loaded up your worker and server nodes, they will need some jobs to be submitted to the server to start actual rendering. There are 2 main ways to do that, first one - just send a direct POST request to add a job to the server.

```
curl \\ --request POST \\ --header "nexrender-secret: myapisecret" \\ --header "content-type: application/json" \\ --data '{"template":{"src":"http://my.server.com/assets/project.aep","composition":"main"}}' \\ http://my.server.com:3050/api/v1/jobs
```

Another option is to use already created API module for js:

```
npm install @nexrender/api --save
```

```
const { createClient } \= require('@nexrender/api') const client \= createClient({ host: 'http://my.server.com:3050', secret: 'myapisecret', }) const main \= async () \=> { const result \= await client.addJob({ template: { src: 'http://my.server.com/assets/project.aep', composition: 'main', } }) result.on('created', job \=> console.log('project has been created')) result.on('started', job \=> console.log('project rendering started')) result.on('finished', job \=> console.log('project rendering finished')) result.on('error', err \=> console.log('project rendering error', err)) } main().catch(console.error);
```

More info: [@nexrender/api](https://github.com/inlife/nexrender/blob/master/packages/nexrender-api)

[](https://github.com/inlife/nexrender#tested-with)Tested with
==============================================================

Current software was successfully tested on:

*   Adobe After Effects CS 5.5 \[OS X 10.14.2\]
*   Adobe After Effects CC (version 12.1.168) \[OS X 10.11.2, Windows 10 64bit\]
*   Adobe After Effects CC 2015 (version 13.6.0) \[OS X 10.11.2\]
*   Adobe After Effects CC 2018.3 \[Windows 2012 Server R2 Datacenter\]
*   Adobe After Effects CC 2019 \[OS X 10.14.2, Windows Server 2019 (AWS)\]

[](https://github.com/inlife/nexrender#additional-information)Additional Information
====================================================================================

[](https://github.com/inlife/nexrender#protocols)Protocols
----------------------------------------------------------

`src` field is a URI string, that describes path pointing to the specific resource. It supports a few different protocols:

*   Built-in:
    
    *   `file://` - file on a local file system, may include environment variables identified by a preceding $ sign (possibly a pipe? need testing)
    *   `http://` - file on remote http server
    *   `https://` - file on remote http server served via https
    *   `data://` - URI encoded data, can be a [base64 or plain text](https://en.wikipedia.org/wiki/Data_URI_scheme)
*   External:
    

### [](https://github.com/inlife/nexrender#examples)Examples

Here are some examples of src paths:

```
file:///home/assets/image.jpg file:///d:/projects/project.aep file://$ENVIRONMENT_VARIABLE/image.jpg http://somehost.com:8080/assets/image.jpg?key=foobar https://123.123.123.123/video.mp4 data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAUAAAAFCAYAAACNbyblAAAAHElEQVQI12P4//8/w38GIAXDIBKE0DHxgljNBAAO9TXL0Y4OHwAAAABJRU5ErkJggg== data:text/plain;charset=UTF-8,some%20data:1234,5678 
```

[](https://github.com/inlife/nexrender#development)Development
--------------------------------------------------------------

If you wish to contribute by taking an active part in development, you might need this basic tutorial on how to get started:

1.  clone the repo
2.  run `npm install`
3.  run `npm start`

The last command will run [lerna](https://lernajs.io/) bootstrap action to setup dependencies for all packages listed in the `packages/` folder, and link them together accordingly to their dependency relations.

After that, you can start the usual development flow of writing code and testing it with `npm start` in a specific package.

Why this multi-package structure has been chosen? It seemed like a much smarter and easier way to achieve a few things:

1.  separation of concerns, every module is responsible for a limited set of things
2.  modularity and plugin-friendly nature, which allows external packages to be used instead, or alongside built-in ones
3.  minimal dependency, as you might've noticed, packages in nexrender try to have as little dependencies as possible making it much easier to maintain and develop

The recommended approach is to add only needed things as dependencies, it's better to take some time to research module that is being added to the project, to see how many its own dependencies it will introduce, and possibly find a better and smaller one, or even extract some specific feature into a new micro module.

And of course, the main thing about development is that it should be fun. :)

[](https://github.com/inlife/nexrender#project-values)Project Values
--------------------------------------------------------------------

This project has a few principle-based goals that guide its development:

*   **Do our thing really well.** Our thing is data-based automating of the rendering, and hanlding other interactive related components of that task set. It is not meant to be a replacement for specific corporate tools templater bot, rendergarden, etc. that have lots of features and customizability. (Some customizability is OK, but not to the extent that it becomes overly complicated or error-prone.)
    
*   **Limit dependencies.** Keep the packages lightweight.
    
*   **Pure nodejs.** This means no native module or other external/system dependencies. This package should be able to stand on its own and cross-compile easily to any platform -- and that includes its library dependencies.
    
*   **Idiomatic nodejs.** Keep modules small, minimal exported names, promise based async handling.
    
*   **Be elegant.** This package should be elegant to use and its code should be elegant when reading and testing. If it doesn't feel good, fix it up.
    
*   **Well-documented.** Use comments prudently; explain why non-obvious code is necessary (and use tests to enforce it). Keep the docs updated, and have examples where helpful.
    
*   **Keep it efficient.** This often means keep it simple. Fast code is valuable.
    
*   **Consensus.** Contributions should ideally be approved by multiple reviewers before being merged. Generally, avoid merging multi-chunk changes that do not go through at least one or two iterations/reviews. Except for trivial changes, PRs are seldom ready to merge right away.
    
*   **Have fun contributing.** Coding is awesome!
    

[](https://github.com/inlife/nexrender#external-packages)External Packages
--------------------------------------------------------------------------

Here you can find a list of packages published by other contributors:

Since nexrender allows to use external packages installed globally from npm, its quite easy to add your own modules

### [](https://github.com/inlife/nexrender#custom-actions)Custom Actions

To add a custom pre- or post-render action, all you need to do is to create a at least single file, that is going to return a function with promise.

```
// mymodule.js module.exports \= (job, settings, action, type) \=> { console.log('hello from my module: ' + action.module); return Promise.resolve(); }
```

To use that action locally you can then require it by either using relative or global path. Additionally you can create a private npm module and link it, so it would become visible globally or even publish it to npm/your own private repo and use it.

```
// example 1 { "module": "d:/myprojects/mymodule/index.js", "somearg1": "hello world", "somearg2": 123456 }
```

```
// example 2 { "module": "my-super-cool-module", "somearg1": "hello world", "somearg2": 123456 }
```

```
// example 3 { "module": "@myorg/mymodule", "somearg1": "hello world", "somearg2": 123456 }
```

From there you can build pretty much any module that could process downloaded data before starting rendering, or doing tranformations on data after, or just simply sending an email when rendering is finished.

> Note: both `job` and `settings` are mutable structures, any modifications made to them will reflect onto the flow of the next calls. Hence they can be used to store state between actions.

[](https://github.com/inlife/nexrender#migrating-from-v0x)Migrating from v0.x
-----------------------------------------------------------------------------

First version of nexrender was published in 2016, and it has been used by many people for quite some time since then. Even though verion v1.x is based on the same concepts, it introduces major breaking changes that are incompatible with older version.

However, majority of those changes were made to allow new, previously unimaginable things.

### [](https://github.com/inlife/nexrender#naming)Naming

1.  Nexrender Project -> Nexrender Job
2.  Nexrender Rendernode -> Nexrender Worker
3.  Nexrender API Server -> Nexrender Server

Referring to project was confusing since it could be applied for both aep project and nexrender project. And rendernode name was quite too long, and unconvinient to use.

### [](https://github.com/inlife/nexrender#structure)Structure

The structure of the job has changed, majority of the fields were moved from the root namespace, into "template" namespace, merging it with old "project.settings" namespace. Assets structure remained pretty much similar. A new object actions has been introduced.

### [](https://github.com/inlife/nexrender#assets-1)Assets

Replaced http and file only assets to a URI based links, theoretically extendable without any limits. Many new other protocols and implementations can be added in a decentrilized manner.

Strict division between asset types:

*   \[image, audio, video\] - footage items, behave like files
*   \[data\] - dynamic data assets, for direct value setting and expressions
*   \[script\] - files allowing full scripting limitless scripting support

### [](https://github.com/inlife/nexrender#rendering)Rendering

The biggest change that happened, is removal of old hacky way of replacing assets and patching aepx file to write custom expressions.

Instead it has been replaced with brand new, recently discovered ExtendScript based injection. It allows to do a few quite important things:

1.  Import and replace footage items via scripting, making it very reliable. (No more bugs related to same-system existing path override for aep project)
2.  Set/Replace text, expressins and other types of data via scripting. (No more bugs related to changes in aepx structure, and no need to use aepx format at all)
3.  Ability to run custom ExtendScript jsx scripts, which is limitless and revolutionary compared to previous version.

### [](https://github.com/inlife/nexrender#cli)CLI

Project has been devided onto multiple subprojects, and mutiple cli applications as a result. Every cli application is auto-compiled to a platform specific executable on publish and auto-uploaded to the releases section.

This allows anyone to use nexrender cli without installing a nodejs runtime onto target system.

New CLI tool allows to run render directly from console for a local job, without need to start whole cluster.

Worker, and CLI apps include minor QoL improvments, such as auto creation of the ae\_render\_only\_node.txt file that allows free licensing, and After Effects folder auto detection.

All tools include better help screen, and a lot of customization from command line arguments.

[](https://github.com/inlife/nexrender#customers)Customers
----------------------------------------------------------

Techinically, since the tool is free, custormers should be called users. In any case this section describes a list of users or companies that are proud users of nexrender. If you've used nexrender, and you like it, please feel free to add yourself into the list.

[](https://github.com/inlife/nexrender#plans)Plans
--------------------------------------------------

1.  Adding more upload/download providers
2.  Add an algo of splitting the main job onto sub jobs, rendering them on multiple machines and then combining back into a single job. `@nexrender/action-merge-parent, @nexrender/action-merge-child`

  
  
from Hacker News https://github.com/inlife/nexrender