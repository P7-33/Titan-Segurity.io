---
title: 'Nvim-colorizer.lua: The fastest colorizer for neovim (and no dependencies too)'
date: 2019-10-18T05:23:00+01:00
draft: false
---

[](https://github.com/norcalli/nvim-colorizer.lua#colorizerlua)colorizer.lua
============================================================================

[![luadoc](https://camo.githubusercontent.com/60fb5c444d142958b0261a908b886d2d8ff2ff92/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f6c7561646f632d302e312d626c7565)](https://norcalli.github.io/luadoc/nvim-colorizer.lua/modules/colorizer.html)

A high-performance color highlighter for Neovim which has **no external dependencies**! Written in performant Luajit.

[![Demo.gif](https://raw.githubusercontent.com/norcalli/github-assets/master/nvim-colorizer.lua-demo-short.gif)](https://raw.githubusercontent.com/norcalli/github-assets/master/nvim-colorizer.lua-demo-short.gif)

[![Demo.mp4](https://raw.githubusercontent.com/norcalli/github-assets/master/nvim-colorizer.lua-demo-short.mp4)](https://raw.githubusercontent.com/norcalli/github-assets/master/nvim-colorizer.lua-demo-short.mp4)

[](https://github.com/norcalli/nvim-colorizer.lua#installation-and-usage)Installation and Usage
-----------------------------------------------------------------------------------------------

Use your plugin manager or clone directly into your `runtimepath`.

```
Plug 'norcalli/nvim-colorizer.lua'
```

As long as you have `malloc()` and `free()` on your system, this will work. Which includes Linux, OSX, and Windows.

One line setup. This will create an `autocmd` for `FileType *` to highlight every filetype.

```
lua require'colorizer'.setup()
```

### [](https://github.com/norcalli/nvim-colorizer.lua#why-another-highlighter)Why another highlighter?

Mostly, **RAW SPEED**.

This has no external dependencies, which means you install it and **it just works**. Other colorizers typically were synchronous and slow, as well. Being written with performance in mind and leveraging the excellent LuaJIT and a handwritten parser, updates can be done in real time. There are plugins such as [hexokinase](https://github.com/RRethy/vim-hexokinase) which have good performance, but it has some difficulty with becoming out of sync. The downside is that _this only works for Neovim_, and that will never change.

Additionally, having a Lua API that's available means users can use this as a library to do custom highlighting themselves.

### [](https://github.com/norcalli/nvim-colorizer.lua#customization)Customization

The available highlight modes are `foreground`, `background`. The default is `background`.

Full options list:

*   `no_names`: Disable parsing names like "Blue"
*   `rgb_fn`: Enable parsing `rgb(...)` functions.
*   `mode`: Highlight mode. Valid options: `foreground`,`background`

For basic setup, you can use a command like the following.

```
\-- Attaches to every FileType mode require 'colorizer'.setup() \-- Attach to certain Filetypes, add special configuration for \`html\` \-- Use \`background\` for everything else. require 'colorizer'.setup { 'css'; 'javascript'; html \= { mode \= 'foreground'; } } \-- Use the \`default\_options\` as the second parameter, which uses \-- \`foreground\` for every mode. This is the inverse of the previous \-- setup configuration. require 'colorizer'.setup({ 'css'; 'javascript'; html \= { mode \= 'background' }; }, { mode \= 'foreground' }) \-- Use the \`default\_options\` as the second parameter, which uses \-- \`foreground\` for every mode. This is the inverse of the previous \-- setup configuration. require 'colorizer'.setup { '\*'; \-- Highlight all files, but customize some others. css \= { rgb\_fn \= true; }; \-- Enable parsing rgb(...) functions in css. html \= { no\_names \= true; } \-- Disable parsing "names" like Blue or Gray }
```

For lower level interface, see the [LuaDocs for API details](https://norcalli.github.io/luadoc/nvim-colorizer.lua/modules/colorizer.html) or use `:h colorizer.lua` once installed.

[](https://github.com/norcalli/nvim-colorizer.lua#todo)TODO
-----------------------------------------------------------

  
  
from Hacker News https://github.com/norcalli/nvim-colorizer.lua