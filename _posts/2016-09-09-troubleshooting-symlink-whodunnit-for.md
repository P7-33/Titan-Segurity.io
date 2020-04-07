---
title: 'Troubleshooting a Symlink — A Whodunnit for the Git Record books'
date: 2020-02-06T16:02:00+01:00
draft: false
---

While I normally sport the well-worn fedora of a hard-boiled sysadmin, Sunday mornings I swap that neo-noir accessory for the tech-noir: a pair of pro headphones. This is the tale of the collision of those two roles. An educational caper, dear reader. You see, my weekly gig is to run a Facebook Live Stream, and Facebook just recently began enforcing a new policy: all video streams are required to use encryption. We have Fedora installed on the media machine, and use Open Broadcaster Software (OBS) to stream. It should have been easy to update the stream settings. I made the necessary changes and tested it out — no luck. The error message was less than helpful: “Failed to connect to server”. With a sigh, I took off my headphones, put my sysadmin hat on, and walked out into the digital darkness. It was time to get back to work.

What the RTMPS?
---------------

Some terms, before we dive in. RTMP is the Real Time Messaging Protocol, originally developed by Macromedia. Thanks to Adobe, a version of RTMP is now an open specification, and many video streaming services now use it to transport live audio and video across the internet. RTMPS is simply the encrypted version, where RTMP is wrapped inside a TLS/SSL connection. TLS, Transport Layer Security, is the same protocol that powers HTTPS. TLS does depend on your machine having a good copy of the certificate bundle, a collection of public keys that are considered to be trustworthy.

How does one go about trying to fix this sort of problem? A good first step is to get a more useful error message. Running OBS from a command line lets us see all the extra output messages that are usually invisible. Below I’ve cut out all the extra messages, to highlight the failing connection attempt.

```
  
info: \[rtmp stream: 'simple\_stream'\] Connecting to RTMP URL rtmps://rtmp-api.facebook.com:443/rtmp/...  
info: RTMP\_Connect1, TLS\_Connect failed: -0x7680  
info: \[rtmp stream: 'simple\_stream'\] Connection to rtmps://rtmp-api.facebook.com:443/rtmp/ failed: -2  
info: ==== Streaming Stop ================================================  

```

Now we’re getting somewhere. The failure is specifically in the TLS connection, which we could have guessed. We also get an error code. Quick note on trying to search for that error: Google will interpret the leading dash as an indicator that you want results that don’t include that search term. Surrounding it in quotation marks, `"-0x7680"` is the way to get useful results.

How to Narrow Down the Cause of an Error
----------------------------------------

Searching for that error number will bring up two interesting hits. One is [the thread in the OBS forum](https://obsproject.com/forum/threads/unable-to-live-stream-to-facebook-live-over-rtmps.102849/) where those of us facing this problem have been discussing it. The other hit is [the mbedtls documentation](https://tls.mbed.org/api/ssl_8h.html#a31bcc2bfd103177e3e76e04219e0497f), where an error with this code is defined. It’s possible that it’s a false positive, but since we’re troubleshooting a TLS issue, it’s likely related. That error is `MBEDTLS_ERR_SSL_CA_CHAIN_REQUIRED`, and is described as “No CA Chain is set, but required to operate.”

So what’s next? We’ve learned a bit, but still don’t have any answers, so let’s dive into code. My standby quick-and-dirty debugging technique is to add `printf()` calls to help follow code execution, but where to start? We have a breadcrumb in the program output, “RTMP\_Connect1”. Searching the OBS codebase on Github lands us at [a function with that name](https://github.com/obsproject/obs-studio/blob/fbc2d9c87e2be8f70216a7bebf936e187bbb711a/plugins/obs-outputs/librtmp/rtmp.c#L1042). Partway through the function, we can see [the command to print the log message that brought us here](https://github.com/obsproject/obs-studio/blob/fbc2d9c87e2be8f70216a7bebf936e187bbb711a/plugins/obs-outputs/librtmp/rtmp.c#L1100).

The error message indicates that a CA chain isn’t loaded. That sounds like an initialization problem. Perhaps that term “chain” is used in the OBS source. Searching our suspect file returns 18 hits, 17 of which are in a function named `RTMP_TLS_LoadCerts()`. I spent some time chasing down the execution flow of the RTMP connection, even making a sketch of when each function gets called. The code led me back to `RTMP_TLS_LoadCerts()`. That function has quite a bit of code in it, but we can safely ignore the parts that are specific to Windows or MacOS. There is an obvious line that should load system certs.

```
if (mbedtls\_x509\_crt\_parse\_path(chain, "/etc/ssl/certs/") &< 0) {  
        goto error;  
    }
```

So OBS makes a function call to the mbedtls library, requesting that the certificates in `/etc/ssl/certs/` are loaded. Let’s make sure a proper certificate file is actually there where OBS expects it to be:

![ca-bundle.crt is where it's supposed to be, but why is that file a different color?](https://hackaday.com/wp-content/uploads/2020/01/Screenshot_20200123_224031-e1579844109880.png)

Ca-bundle.crt is the file we’re looking for. Notice the teal color? Those three files are actually symlinks to another location. Files on Linux filesystems are symbolically linked all the time, so likely not a problem. I spent some time checking things like file permissions, and tried disabling selinux, but came up with nothing. It didn’t seem to be an overzealous security setting. All I was left with was the knowledge that I had an mbedtls function that should be loading the certificate bundle, but when the program actually tried to verify a TLS certificate, it complained that the chain, `ca-bundle.crt`, was missing. If the mbedtls function was failing, shouldn’t it error out there? The next logical step is to look at [the documentation for that function](https://tls.mbed.org/api/group__x509__module.html#ga571fc89b9f3217ab3dd67bd7af905066).

Now we find the first real hint about what could be happening. `mbedtls_x509_crt_parse_path()` can partially fail, and still give us a return code that doesn’t trigger an error. So, time to use `printf()` to see what that return code is on my machine. I added the code, compiled, ran the output binary… and got no such log output.

It took longer than I care to admit for me to figure out why my code changes didn’t seem to make a difference when running the program. This is a potential gotcha to watch out for. OBS uses a modular structure, consisting of the OBS binary, as well as various loadable modules. The code changes I was making were a part of `obs-outputs.so`, and even when running the compiled binary, those modules were being loaded from their default locations. To test my changes, I had to explicitly tell OBS to use the newly compiled module.

System Calls That Hate Symlinks
-------------------------------

Something was obviously amiss with `mbedtls_x509_crt_parse_path()`. I wasn’t seeing anything obvious in the documentation, but I did see a similar function, `mbedtls_x509_crt_parse_file()`. What would happen if we forced mbedtls to only try loading the one crt file that we care about? I made the change, compiled, and to my surprise OBS finally connected to Facebook Live. I had a real fix, but I still didn’t understand why it was broken. It’s time to look at the mbedtls sourcecode.

The [`parse_path()` function](https://github.com/ARMmbed/mbedtls/blob/development/library/x509_crt.c#L1518) is easily found in the mbedtls source tree. Make sure to watch the `#if defined()` blocks — We’re not interested in the code for Windows. Once we find [the loop that runs for each file](https://github.com/ARMmbed/mbedtls/blob/development/library/x509_crt.c#L1600) in the given path, the problem code might jump out at you.

```
  
        else if( stat( entry\_name, &sb ) == -1 )  
        {  
            ret = MBEDTLS\_ERR\_X509\_FILE\_IO\_ERROR;  
            goto cleanup;  
        }  
  
        if( !S\_ISREG( sb.st\_mode ) )  
            continue;  

```

`Stat()` is a system call that gets the status of a filesystem path, and then S\_ISREG is a macro that checks whether that path is pointing at a regular file. Notably, the parse\_file function does not do that check, and will happily load a symlink.

Report the Bug, But to Whom?
----------------------------

That, of course, is the core problem. Fedora uses a symlinked `ca-bundle.crt`, and mbedtls refuses to load `ca-bundle.crt` when it’s a symlink. We understand the problem, but what’s the proper fix? Which project actually has the bug here? OBS used the mbedtls function properly according to its documentation, and mbedtls may have a good security reason for refusing to load a bundle that’s actually a symlink. Is it on RPMFusion, and the package maintainer to fix the incompatibility? Personally, I think it’s really an mbedtls problem, particularly because this quirk isn’t mentioned in any documentation that I came across. Ultimately, it’s not my call which project needs to own this problem.

Our last task, then, is to report the bug we discovered. It’s a good idea to stop at this point, and ask yourself, is this bug a potential security issue? It’s best to try to report security issues privately, and most projects have contact instructions for disclosing those sorts of issues. Depending on where you found the problem, you may even be eligible for a bug bounty reward for finding the problem.

Assuming there is no security angle to consider, you’ll want to make a bug report. Does the project have a public bug tracker? That’s probably where it should go. If not, there is likely a mailing list where bugs are reported. Include enough information to reproduce the bug, and details on what you think is happening, but don’t include a bunch of log output in the bug or the mailing list. If it’s relevant, use pastebin or one of the other text hosting sites, to avoid including a wall of text in the bug report. If you have an idea of how to fix the problem, mention it. On a mailing list, patches are usually accepted. If the project is using Github or Gitlab, you can report the bug, and turn around and submit a pull request to fix it.

Particularly for trivial changes, I tend to ask what the project prefers, should I send a pull request, or is this trivial enough to fix without one. If you’re looking to do future work on the project, doing a PR is a handy way to get your name into the git record. Projects are more likely to look kindly on your future work, if there’s record of you already fixing bugs.

The End of Another Tale
-----------------------

This one turned out well enough. OBS is adding some workaround code to make sure the ca-bundle is properly loaded on systems where it’s a symlink. The mbedtls project sees this behavior as a bug, and I’ve submitted a patch to fix it. I noticed a related logic bug in the certificate loading code, and it’s been acknowledged as well. I’ve patched my copy of OBS so live-streams work again. It’s all in a days’ work for for the sysadmin. No rest for the weary, though. I have a pair of 10Gb Ethernet cards that die whenever they transfer VLAN tagged traffic. Just another case.

### Errata

I know the more experienced programmers will point it out in the comments, `stat()` doesn’t ever set st\_mode to S\_IFLNK. `Stat()` follows the symlink to report on the target, while `lstat()` tells you about the symlink itself. My fix worked, but the problem was slightly different than I thought it was. `Mbedtls_x509_crt_parse_path()` can return a positive value if only some of the files in the specified directory successfully loaded. OBS was treating that positive value as a failure, and immediately dumping the certificates that had been loaded. Chasing false leads like this is totally par for the course when it comes to finding and fixing bugs. In the end, the bug is fixed, and that’s what really matters. Now if you’ll excuse me, I need to find something to wash the taste of crow out of my mouth.

  
  
from Hackaday https://ift.tt/39eJYug  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)