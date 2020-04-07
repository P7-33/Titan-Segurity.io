---
title: 'Standalone WebAssembly games using I/O devices'
date: 2020-01-19T11:32:00+01:00
draft: false
---

![](https://miro.medium.com/max/1000/1*DWGMetEf3HRzocVkrclVFw.png "Building Graphical Applications with Wasmer and WASI")  

Let’s take a step back and dive into how I/O devices can help the community today.

Finding what Features the Community can use, Today
==================================================

We did some research on what people in the open source community are trying to build with WebAssembly, and we found that it was a lot of games! [Sandspeil](https://maxbittker.com/making-sandspiel), [WasmBoy](https://github.com/torch2424/wasmboy), and [Continuation Lab’s port of DOOM 3](https://www.continuation-labs.com/projects/d3wasm/) are all amazing games built with WebAssembly. Games Engines like [Unity](https://blogs.unity3d.com/2018/08/15/webassembly-is-here/), [Gdevelop](https://www.infoq.com/articles/wasm-game-editor-port/), and [Construct 3](https://twitter.com/IainShorter/status/1158769551229816833) support outputting games for web browsers that use WebAssembly. 🎮

However, none of these games or engines support running the game standalone. For example, currently, you could not have a single Wasm Binary create and interface with Graphics and Input as you would still need additional code for the specific platform (like a web browser) in a different language.  
Wasmer’s I/O devices allows developers to have a single Wasm Binary open a Window, write to a Frame Buffer, and read input events from a user. 💪

Let’s take a look at how I/O devices work and enable this functionality.

Building WASI Applications with Wasmer I/O devices
==================================================

I/O devices work by creating **virtual device files in the runtime filesystem**, similar to a device file on a UNIX operating system. If a Wasm module uses the WASI bindings of reading/writing files, the runtime can react to the events and perform actions for the Wasm module. 😎

For example, I/O devices creates a`/_wasmer/dev/fb0/fb` file that contains a RGBA byte array of a buffer to be drawn. Which is similar to [writing directly to a linux framebuffer](http://seenaburns.com/2018/04/04/writing-to-the-framebuffer/)! 🖼️

Since the API is essentially an abstraction over a normal Filesystem, and the current WASI spec, Wasmer I/O devices can be tried today, with any language / toolchain that supports WASI!

In fact, we even got a working standalone version of WasmBoy that can be tried with the Wasmer runtime! This works by using the `io-devices-lib-assemblyscript` package that we built. The package, and also a Rust crate for interacting with I/O Devices, can be found on our [io-devices-lib](https://github.com/wasmerio/io-devices-lib) repository.

WasmBoy is now available on [WAPM](https://wapm.io/), as [WasmerBoy](https://wapm.io/package/torch2424/wasmerboy). You can install Wasmer and WAPM by following the [instructions here](https://docs.wasmer.io/wapm/wapm-installation). Then, Wasmerboy can be installed standalone by running: `wapm install -g torch2424/wasmerboy` . Then, by running `wasmerboy --dir=my-dir my-dir/my-rom-file.gb` . For example, we can run the MIT licensed [Tobu Tobu Girl](https://tangramgames.dk/tobutobugirl/) using WasmerBoy from WAPM:

> You can download the Tobu Tobug Girl rom [from this link](https://tangramgames.itch.io/tobu-tobu-girl-deluxe/purchase?popup=1)

Showing WasmerBoy running from WAPM / Wasmer CLI

WasmerBoy also works on Wasmer-JS / WebAssembly.sh (on Desktop Chrome)! You can drag and drop the ROM file to WebAssembly.sh, which will add it to the filesystem. Then, you can run the same command: `wasmerboy /tmp/my-rom-file.gb` . Which will open a popup running WasmerBoy!

Showing WasmerBoy running from Wasmer-JS / WebAssembly.sh

Thank you!
==========

We are SO excited to see the interest and projects that could come from this. We really hope this helps to grow the WebAssembly community, and help as a jumping board for spec authors when this eventually does get proposed for the WASI spec. 🙌

Again, we would like to re-iterate, this is an experimental feature, that is not standardized. I/O devices is meant for experimenting with building standalone WebAssembly modules as a sneak peek at the eventual future when there could be a standardized feature for this type of functionality in the WASI spec. As this idea is an important part of the web platform, as highlighted in [Paul Lewis’ “Custom Web Shadow Elements, or Whatever…” talk](https://vimeo.com/364370506).

To get started with I/O devices, the latest release of Wasmer has a new flag:  
`--enable-experimental-io-devices`.

I/O devices has its own Wasmer-JS package, `@wasmer/io-devices`. The I/O devices package is utilized in the `@wasmer/wasm-temrinal` package, and [WebAssembly.sh](https://webassembly.sh/) to support t I/O devices by default.

Then, you can try a Wasm Module that uses the I/O devices, such as WasmBoy on WAPM, or build a Wasm module in Rust or AssemblyScript using the experimental [I/O Devices Lib](https://github.com/wasmerio/io-devices-lib). 🦀🚀

Thank YOU for reading this article! Feel free to open issues, send us ideas, or send us your cool projects! We are happy to help the community in any way we can! Cheers! 🍻

  
  
from Hacker News https://ift.tt/2R3eVLt