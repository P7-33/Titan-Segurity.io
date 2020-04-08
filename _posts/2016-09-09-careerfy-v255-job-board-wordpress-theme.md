---
title: 'Careerfy v2.5.5 – Job Board WordPress Theme'
date: 2019-10-15T08:09:00+01:00
draft: false
---

  
  
from Hacker News https://ift.tt/2VEtMNk

We started in .NET Core 1.0 with a very minimal API set that only included ~18K of the .NET Framework APIs. With [.NET Standard 2.0](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-0/), we tried to make it much more viable to share code between .NET Framework, .NET Core, and Xamarin which resulted in approximately 38K .NET Frameworks APIs being available in .NET Core 2.0. We also built the [Windows Compatibility Pack](https://devblogs.microsoft.com/dotnet/announcing-the-windows-compatibility-pack-for-net-core/) which made another 21K .NET Framework APIs available to .NET Core, resulting in almost 60K additional APIs. And in .NET Core 3.0 we added WPF and WinForms, which increased the number of .NET Framework APIs ported to .NET Core to over 120k, which is more than half of all .NET Framework APIs.

It’s also worth pointing out that we added about 62K APIs to .NET Core that don’t exist in .NET Framework. If we compare their total number of APIs, .NET Core has about 80% of the API surface of .NET Framework.

[![](https://user-images.githubusercontent.com/5169960/66777114-f8db7c80-ee7c-11e9-9161-acfe1c491586.png)](https://user-images.githubusercontent.com/5169960/66777114-f8db7c80-ee7c-11e9-9161-acfe1c491586.png)

We announced that the [future of .NET](https://devblogs.microsoft.com/dotnet/net-core-is-the-future-of-net/) will be based on .NET Core. And at Build 2019, [Scott Hunter stated](https://www.youtube.com/watch?v=ZlO1utbB2GQ&t=54m20s) that AppDomains, remoting, Web Forms, WCF server, and Windows Workflow won’t be ported to .NET Core.

With .NET Core 3.0, we’re at the point where we’ve ported all technologies that are required for modern workloads, be that desktop apps, mobile apps, console apps, web sites, or cloud services. That’s not to say that we don’t have any gaps or opportunities for new technologies, but we generally believe we won’t be finding them in the .NET Framework code base anymore. Moving forward, we’re focusing our resources on incorporating new technologies.

Simultaneously, we’re looking into releasing more of the [.NET Framework code base under the MIT license](https://github.com/microsoft/referencesource) on GitHub to allow the community to create OSS projects for technologies we’re not intending to bring to .NET Core. For example, there already are community projects for [CoreWF](https://github.com/UiPath/corewf) and [CoreWCF](https://github.com/CoreWCF/CoreWCF).

We’d like to thank everyone who filed issues with requests for APIs being ported. Those issues allowed us to prioritize and close the gaps that prevented people from porting to .NET Core.

But since we generally no longer plan to bring existing technologies from .NET Framework to .NET Core we’ll be closing all issues that are [labeled with port-to-core](https://github.com/dotnet/corefx/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+label%3Aport-to-core).

### Discussion

To discuss this issue, please comment on the corresponding issue at [dotnet/corefx#41769](https://github.com/dotnet/corefx/issues/41769).