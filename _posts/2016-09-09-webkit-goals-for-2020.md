---
title: 'WebKit Goals for 2020'
date: 2019-11-09T07:11:00+01:00
draft: false
---

*   Audiences
    *   Users
    *   Web Developers
    *   Native Developers
    *   WebKit
*   Users
    *   Performance
        *   Performance Defense
            *   PLT5, JetStream 2, Speedometer 2, MotionMark, RAMification
        *   New things to measure
            *   IndexedDB, Promises, back-forward, JSC API, Battery life
        *   Performance Ideas
            *   Media query change handling
            *   No sync IPC for cookies
            *   Fast for-of iteration
            *   Turbo DFG
            *   Async gestures
            *   Fast scrolling on macOS
            *   Global GC
            *   Service Worker declarative routing
    *   Privacy
        *   Address ITP bypasses, logged in API, in-app browser privacy, PCM with fraud prevention
    *   Security
        *   Authentication
            *   WebAuthN external authenticators (NFC/USB) on iOS
            *   Device-bound auth
        *   Network Security
            *   Disabling TLS 1.0 and 1.1
            *   Automatic HTTPS Upgrades
            *   No opener / Cross-Origin-Opener-Policy
        *   JavaScript Hardening
            *   JSC Fuzz-0
            *   Use IsoSubspaxes for all GC objects
            *   Software Verified JIT
        *   WebCore Hardening
            *   Achieve WebCore Fuzz-0
            *   IsoHeaps for everything in WebContent
            *   Automatic Smart Pointers
        *   Sandbox Hardening
            *   Stronger WebContent Sandbox
            *   CoreIPC Fuzz-0
            *   Get IOKit Out of WebContent
*   Web Developers
    *   Web Platform: Catchup
        *   Graphics & Animations
            *   CSS overscroll-behavior
            *   WebGL 2
            *   Web Animations
        *   Media
            *   Media Session Standard
            *   MediaStream Recording
            *   Picture-in-Picture API
            *   Remote Playback API (ask jer)
        *   DOM, JavaScript & Text
            *   Async Clipboard API
            *   BigInt best-possible performance with JIT layers
            *   DIalog element
            *   HTML enterkeyhint attribute
            *   Resize Observer
            *   requestIdleCallback
            *   Unicode 12
    *   Web Platform: Innovation
        *   CSS Shadow Parts
        *   CSS ui-\* font keywords (expose new system fonts, serif, monospace)
        *   GenericCue (Captions besides WebVTT)
        *   JS builtin modules
        *   Prototype and spec for streamable fonts
        *   Undo Web API
    *   Web Platform: Quality
        *   WPT
            *   CSS (writing modes, overflow, multicol…)
            *   Service Workers
            *   SVG
            *   XHR + Fetch
        *   Other
            *   tests262 100% pass rate
            *   WebAudio low hanging fruit
    *   Dev Tools
        *   Improvements in every STP
            *   Async stack traces for Promises
            *   Stepping through Async Await
            *   Network Throttling
            *   Network Tab Overview + time range selection
            *   User Timing
            *   Timeline Filmstrip
            *   Improve console UI
        *   Larger Changes
            *   Responsive Design Mode 2.0
            *   Feature usage telemetry
*   Native Developers
    *   Obsolete Legacy WebKit
        *   WKWebView API needed for migration
        *   Fix cookie flakiness due to multiple process pools
        *   WKWebView APIs for Media
*   WebKit Developers
    *   Architecture Health
        *   Define “intent to implement” style process
        *   Faster Builds (finish unified builds)
        *   Next-gen layout for line layout
        *   Regression Test Debt repayment
    *   Service & Tools Improvements
        *   IOSurface in Simulator
        *   EWS Improvements 2020
        *   Buildbot 2.0
        *   WebKit on GitHub as a project (year 1 of a multi-year project)

Q & A

*   What architecture changes are associated with Turbo DFG
    *   Open to different ideas: first will be removing the baseline, definitely a possibility of a 5th tier, first replacing baseline
*   Finishing unified builds: will there be a bot to verify non-unified will still operate?
    *   No specific plans, but a worthy idea
*   Native dev: WKWebView for Media Applications?
    *   Many apps that use WKWebView want to control how media playback works
    *   About control of video in a web view
*   How do you decide what’s important to do next?
    *   We look at a number of factors
    *   It used to be a judgement call, now we’re codifying
    *   We look at a number of signals
    *   How much dev interest?
    *   is there a harmful aspect?
    *   WPT areas are similar:
        *   Most tests failing in Safari, but not in FF or Chrome
    *   Sometimes we use high-value websites

### Download in other formats:

  
  
from Hacker News https://ift.tt/2WYIHSU