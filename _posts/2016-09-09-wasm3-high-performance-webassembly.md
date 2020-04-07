---
title: 'Wasm3 – A high performance WebAssembly interpreter in C'
date: 2020-01-13T04:47:00+01:00
draft: false
---

[![](https://github.com/wasm3/wasm3/raw/master/extra/screenshot.png)](https://github.com/wasm3/wasm3/blob/master/extra/screenshot.png)

[](https://github.com/wasm3/wasm3#-wasm3)[![](https://github.com/wasm3/wasm3/raw/master/extra/wasm-symbol.svg?sanitize=true)](https://github.com/wasm3/wasm3/blob/master/extra/wasm-symbol.svg) Wasm3
=====================================================================================================================================================================================================

[![WAPM](https://camo.githubusercontent.com/b19b9fd0865233b2fdd974590e20d115ef02b4c8/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f7761706d2d76302e342e322d3635346666302e737667)](https://wapm.io/package/vshymanskyy/wasm3) [![GitHub issues](https://camo.githubusercontent.com/9755bf30805624e3a243345068d61350b93ee92f/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f6973737565732d7261772f7761736d332f7761736d332e7376673f6c6162656c3d69737375657326636f6c6f723d73756363657373)](https://github.com/wasm3/wasm3/issues) [![GitHub license](https://camo.githubusercontent.com/890acbdcb87868b382af9a4b1fac507b9659d9bf/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f6c6963656e73652d4d49542d626c75652e737667)](https://github.com/wasm3/wasm3) [![Tests status](https://camo.githubusercontent.com/25dc39b1847274536895d766fab7a7d5faa858c4/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f776f726b666c6f772f7374617475732f7761736d332f7761736d332f74657374732e7376673f6c6162656c3d7465737473)](https://github.com/wasm3/wasm3/actions)

A high performance WebAssembly interpreter written in C.

**∼ 15.8x faster** than other wasm interpreters (`wac`, `life`, `wasm-micro-runtime`)  
**∼ 4..5x slower** than state of the art wasm `JIT` engines (`liftoff`, `cranelift`)  
**∼ 11.5x slower** than native execution  
\* Based on [**CoreMark 1.0** benchmark](https://github.com/wasm3/wasm3/blob/master/test/benchmark/coremark/README.md). Your mileage may vary.

[](https://github.com/wasm3/wasm3#getting-started)Getting Started
-----------------------------------------------------------------

Here's an online demo and a small [getting started](https://wapm.io/package/vshymanskyy/wasm3) guide:

[![LIVE DEMO](https://github.com/wasm3/wasm3/raw/master/extra/button.png)](https://webassembly.sh/?run-command=wapm%20install%20vshymanskyy/wasm3)

[](https://github.com/wasm3/wasm3#status)Status
-----------------------------------------------

`wasm3` passes the [WebAssembly spec testsuite](https://github.com/WebAssembly/spec/tree/master/test/core) and is able to run many `WASI` apps.

Minimum useful system requirements: **~64Kb** for code and **~10Kb** RAM

`wasm3` runs on a wide range of [platforms](https://github.com/wasm3/wasm3/blob/master/platforms):

*   [![](https://camo.githubusercontent.com/7f5bed56b38bd4a117d7a5b656abe311a3662a69/68747470733a2f2f63646e2e7261776769742e636f6d2f73696d706c652d69636f6e732f73696d706c652d69636f6e732f646576656c6f702f69636f6e732f6c696e75782e737667)](https://camo.githubusercontent.com/7f5bed56b38bd4a117d7a5b656abe311a3662a69/68747470733a2f2f63646e2e7261776769742e636f6d2f73696d706c652d69636f6e732f73696d706c652d69636f6e732f646576656c6f702f69636f6e732f6c696e75782e737667) Linux, [![](https://camo.githubusercontent.com/ccb4a2937d0f8566bbf00231b4a3f70c2e7f4207/68747470733a2f2f63646e2e7261776769742e636f6d2f73696d706c652d69636f6e732f73696d706c652d69636f6e732f646576656c6f702f69636f6e732f77696e646f77732e737667)](https://camo.githubusercontent.com/ccb4a2937d0f8566bbf00231b4a3f70c2e7f4207/68747470733a2f2f63646e2e7261776769742e636f6d2f73696d706c652d69636f6e732f73696d706c652d69636f6e732f646576656c6f702f69636f6e732f77696e646f77732e737667) Windows, [![](https://camo.githubusercontent.com/faad054fb2610ff55ac4f472d461e791e39e42be/68747470733a2f2f63646e2e7261776769742e636f6d2f73696d706c652d69636f6e732f73696d706c652d69636f6e732f646576656c6f702f69636f6e732f6170706c652e737667)](https://camo.githubusercontent.com/faad054fb2610ff55ac4f472d461e791e39e42be/68747470733a2f2f63646e2e7261776769742e636f6d2f73696d706c652d69636f6e732f73696d706c652d69636f6e732f646576656c6f702f69636f6e732f6170706c652e737667) OS X
*   [![](https://camo.githubusercontent.com/68a9159b1c337ad66fa4523732be2e23dcd896eb/68747470733a2f2f63646e2e7261776769742e636f6d2f73696d706c652d69636f6e732f73696d706c652d69636f6e732f646576656c6f702f69636f6e732f616e64726f69642e737667)](https://camo.githubusercontent.com/68a9159b1c337ad66fa4523732be2e23dcd896eb/68747470733a2f2f63646e2e7261776769742e636f6d2f73696d706c652d69636f6e732f73696d706c652d69636f6e732f646576656c6f702f69636f6e732f616e64726f69642e737667) Android, [![](https://camo.githubusercontent.com/faad054fb2610ff55ac4f472d461e791e39e42be/68747470733a2f2f63646e2e7261776769742e636f6d2f73696d706c652d69636f6e732f73696d706c652d69636f6e732f646576656c6f702f69636f6e732f6170706c652e737667)](https://camo.githubusercontent.com/faad054fb2610ff55ac4f472d461e791e39e42be/68747470733a2f2f63646e2e7261776769742e636f6d2f73696d706c652d69636f6e732f73696d706c652d69636f6e732f646576656c6f702f69636f6e732f6170706c652e737667) iOS
*   [![](https://camo.githubusercontent.com/1d6c44ef9b755131a58aaf65f102350cec3d3ac5/68747470733a2f2f63646e2e7261776769742e636f6d2f73696d706c652d69636f6e732f73696d706c652d69636f6e732f646576656c6f702f69636f6e732f72617370626572727970692e737667)](https://camo.githubusercontent.com/1d6c44ef9b755131a58aaf65f102350cec3d3ac5/68747470733a2f2f63646e2e7261776769742e636f6d2f73696d706c652d69636f6e732f73696d706c652d69636f6e732f646576656c6f702f69636f6e732f72617370626572727970692e737667) Raspberry Pi, Orange Pi and other **SBC**s
*   [![](https://camo.githubusercontent.com/5eb27cf1d6d49e2536d441cdbfcda87253e23ffc/68747470733a2f2f63646e2e7261776769742e636f6d2f6665617468657269636f6e732f666561746865722f6d61737465722f69636f6e732f6370752e737667)](https://camo.githubusercontent.com/5eb27cf1d6d49e2536d441cdbfcda87253e23ffc/68747470733a2f2f63646e2e7261776769742e636f6d2f6665617468657269636f6e732f666561746865722f6d61737465722f69636f6e732f6370752e737667) **MCU**s:  
    Arduino MKR\*, Arduino Due, Particle Photon,  
    ESP8266, ESP32, Air602 (W600), nRF52, nRF51,  
    Blue Pill (STM32F103C8T6), MXChip AZ3166 (EMW3166),  
    Maix (K210), HiFive1 (E310), Fomu (ICE40UP5K), ATmega1284 etc.
*   [![](https://camo.githubusercontent.com/ecb25d1195d7491b55ca4507dab1d11e7b99c61f/68747470733a2f2f63646e2e7261776769742e636f6d2f6665617468657269636f6e732f666561746865722f6d61737465722f69636f6e732f776966692e737667)](https://camo.githubusercontent.com/ecb25d1195d7491b55ca4507dab1d11e7b99c61f/68747470733a2f2f63646e2e7261776769742e636f6d2f6665617468657269636f6e732f666561746865722f6d61737465722f69636f6e732f776966692e737667) **OpenWRT**\-enabled routers
*   [![](https://camo.githubusercontent.com/d5669eb588d0e0bbaae8f99b8f764ccc0a30ad5e/68747470733a2f2f63646e2e7261776769742e636f6d2f73696d706c652d69636f6e732f73696d706c652d69636f6e732f646576656c6f702f69636f6e732f6d6f7a696c6c6166697265666f782e737667)](https://camo.githubusercontent.com/d5669eb588d0e0bbaae8f99b8f764ccc0a30ad5e/68747470733a2f2f63646e2e7261776769742e636f6d2f73696d706c652d69636f6e732f73696d706c652d69636f6e732f646576656c6f702f69636f6e732f6d6f7a696c6c6166697265666f782e737667) [![](https://camo.githubusercontent.com/7c4f7c988d8c1ba719de21251c974ce0c7fa9de9/68747470733a2f2f63646e2e7261776769742e636f6d2f73696d706c652d69636f6e732f73696d706c652d69636f6e732f646576656c6f702f69636f6e732f676f6f676c656368726f6d652e737667)](https://camo.githubusercontent.com/7c4f7c988d8c1ba719de21251c974ce0c7fa9de9/68747470733a2f2f63646e2e7261776769742e636f6d2f73696d706c652d69636f6e732f73696d706c652d69636f6e732f646576656c6f702f69636f6e732f676f6f676c656368726f6d652e737667) [![](https://camo.githubusercontent.com/bb3acc29f50d9de82f3804d5b0dfc978d38e9cc8/68747470733a2f2f63646e2e7261776769742e636f6d2f73696d706c652d69636f6e732f73696d706c652d69636f6e732f646576656c6f702f69636f6e732f7361666172692e737667)](https://camo.githubusercontent.com/bb3acc29f50d9de82f3804d5b0dfc978d38e9cc8/68747470733a2f2f63646e2e7261776769742e636f6d2f73696d706c652d69636f6e732f73696d706c652d69636f6e732f646576656c6f702f69636f6e732f7361666172692e737667) [![](https://camo.githubusercontent.com/72745eeef4a16ce81f29c9d92a5174ec0b4917bf/68747470733a2f2f63646e2e7261776769742e636f6d2f73696d706c652d69636f6e732f73696d706c652d69636f6e732f646576656c6f702f69636f6e732f6d6963726f736f6674656467652e737667)](https://camo.githubusercontent.com/72745eeef4a16ce81f29c9d92a5174ec0b4917bf/68747470733a2f2f63646e2e7261776769742e636f6d2f73696d706c652d69636f6e732f73696d706c652d69636f6e732f646576656c6f702f69636f6e732f6d6963726f736f6674656467652e737667) Browsers... yes, using WebAssembly itself!
*   [![](https://github.com/wasm3/wasm3/raw/master/extra/wasm-symbol.svg?sanitize=true)](https://github.com/wasm3/wasm3/blob/master/extra/wasm-symbol.svg) `wasm3` can execute `wasm3` (self-hosting)

`wasm3` is built on top of [Steven Massey](https://github.com/soundandform)'s novel [interpreter topology](https://github.com/wasm3/wasm3/blob/master/source/README.md), with:

*   Wasm 1.0 spec conformance
*   `WASI` support
*   Support of `x86`, `x64`, `ARM`, `MIPS`, `RISC-V`, `Xtensa` architectures

[](https://github.com/wasm3/wasm3#building)Building
---------------------------------------------------

See [DEV.md](https://github.com/wasm3/wasm3/blob/master/DEV.md)

[](https://github.com/wasm3/wasm3#testing--fuzzing)Testing & Fuzzing
--------------------------------------------------------------------

See [test/README.md](https://github.com/wasm3/wasm3/blob/master/test/README.md)

### [](https://github.com/wasm3/wasm3#license)License

This project is released under The MIT License (MIT)

  
  
from Hacker News https://github.com/wasm3/wasm3