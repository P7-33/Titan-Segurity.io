---
title: 'Chronologic Versioning: No more arbitrary version updates and regressions'
date: 2020-01-02T05:06:00+01:00
draft: false
---

Summary
-------

Given a version number YEAR.MONTH.DAY.CHANGESET\_IDENTIFIER, increment the:

1.  YEAR version when the year changes,
2.  MONTH version when the month changes,
3.  DAY version when the day changes, and the
4.  CHANGESET\_IDENTIFIER everytime you commit a change to your package/project.

Introduction
------------

In the world of software management there exists a dreaded place called "dependency hell." The bigger your system grows and the more packages you integrate into your software, the more likely you are to find yourself, one day, in this pit of despair.

In systems with many dependencies, releasing new package versions can quickly become a nightmare. If the dependency specifications are too tight, you are in danger of version lock (the inability to upgrade a package without having to release new versions of every dependent package). If dependencies are specified too loosely, you will inevitably be bitten by version promiscuity (assuming compatibility with more future versions than is reasonable). Dependency hell is where you are when version lock and/or version promiscuity prevent you from easily and safely moving your project forward.

As a solution to this problem, I propose a simple set of rules and requirements that dictate how version numbers are assigned and incremented. Quite simply, these rules are temporal-based. You communicate changes to your project with specific increments to the version number. Consider a version format of `A.B.C.D` (Year.Month.Day.Change). `D` is not necessary to include if there has not been a new change. For instance:

You start work on a new project one day and the version number is `2006.04.01`. Later on that day, you commit a new change to the project. The version number would be `2006.04.01.1`. The following day, your first commit would result in version `2006.04.02`.

I call this system "Chronologic Versioning." Under this scheme, version numbers and the way they change are not only easier to understand but more likely to "stick" than other versioning schemes. No more arbitrary version updates and regressions to correct versioning mistakes.

Chronologic Versioning Specification (ChronVer)
-----------------------------------------------

The key words "MAY", "MUST", "MUST NOT", "OPTIONAL", "RECOMMENDED", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", and "SHOULD NOT" in this document are to be interpreted as described in [RFC 2119](https://tools.ietf.org/html/rfc2119 "Key words for use in RFCs to Indicate Requirement Levels").

1.  A version number MUST take the form `A.B.C.D` where `A`, `B`, `C`, and `D` are non-negative integers. `A` and `D` MUST NOT contain leading zeroes. `B` and `C` MUST contain a leading zero when they are a single digit. `A` is the annual version, `B` is the monthly version, `C` is the daily version, and `D` is the changeset version. Each element MUST increase numerically. For instance: `2006.04.01` > `2006.04.02` > `2006.04.03`.
    
2.  In the aforementioned example of a version number in the form `A.B.C.D`, `D` is an OPTIONAL include if it is otherwise zero. For instance: `2006.04.01` is equal to `2006.04.01.0`.
    
3.  If backwards incompatible changes are introduced you MUST append a hyphen and the reserved label "break". For instance: `2006.04.03.12` > `2006.04.03.12-break`.
    
4.  Once a versioned package has been released, the contents of that version MUST NOT be modified. Any modifications MUST be released as a new version.
    

Why Use Chronologic Versioning?
-------------------------------

With other versioning schemes, adherence is inconsistent and loose at best. Compliance? _Please_. To use semantic versioning as an example, it made sense when applications were released a few times a year or less. We are now in the age of continuous delivery/integration and the concept of a `v3.5.27` is lost on a web app or anything that sees rapid development and releases. Your users _almost certainly_ have no interest in nor are able to comprehend what you append to your version numbers either. Some people could decipher `10.14.5 (18F127a)` but it is **much** more pleasant to read `2019.04.29.5`.

While engineers like structure and order, they also benefit from ease of use. With Chronologic Versioning, it requires almost no thought to adhere to. While other versioning schemes almost certainly have their uses still, times have changed and so has their usefulness.

A pleasant side effect of using Chronologic Versioning is the ability to see _at a glance_ which of your dependencies in a project have not been updated in a while (if these dependencies are using Chronologic Versioning).

Chronologic Versioning provides you with a sane way of thinking about dependency management, saving you time **and** hassle.

If all of this sounds desirable, all you need to do to start using Chronologic Versioning is to declare that you are doing so and then follow the rules. Link to this website from your README so others know the rules and can benefit from them.

FAQ
---

### Doesn't this ecourage rapid development and fast iteration?

Absolutely! ChronVer is all about rapid development.

### This sounds neat for personal projects but how can I use this for work?

Tagging feature releases is a common workflow for many teams. What follows is an example of how ChronVer could work in a multi-contributor environment.

Imagine you have teams working on a feature and they split the task into UI and implementation branches.

```
2019.05.08.14 (base release) ├─ 2019.05.08.14-super-ui-enhance (UI fork) │ └─ 2019.05.08.14-super-ui-enhance.13 (UI fork, later in the day) └─ 2019.05.08.14-super-ui-please-work (implementation fork) └─ 2019.05.08.14-super-ui-please-work.57 (implementation fork, later in the day)
```

As you can see, `super-ui-enhance` and `super-ui-please-work` are feature releases forked from the fourteenth update of a release created on `2019.05.08`.

Sometime the following day, those branches might look like this:

*   `2019.05.09-super-ui-enhance`
*   `2019.05.09-super-ui-please-work.9`

When your work is merged into the main branch you can safely omit `-FEATURE_NAME.CHANGESET_IDENTIFIER` from the version number.

### How should I handle deprecating functionality?

Deprecating existing functionality is a normal part of software development and is often required to make forward progress. When you deprecate part of your public API (if it exists), you should do two things: (1) update your documentation to let users know about the change and (2) issue a breaking release with the deprecation in place.

### Is "v1.2.3" a chronologic version?

No, "v1.2.3" is not a chronologic version. However, prefixing a chronologic version with a "v" is a common way (in English) to indicate it is a version number. Abbreviating "version" as "v" is often seen with version control. Example: `git tag v2006.04.03.13 -m "Release version 2006.04.03.13"`, in which case "v2006.04.03.13" is a tag name and the chronologic version is "2006.04.03.13".

About
-----

The Chronologic Versioning specification is authored by [Paul Anthony Webb](https://webb.page "Homepage of Paul Anthony Webb"), digital architect of fine experiences.

This specification borrows heavily from [SemVer](https://semver.org "Semantic Versioning specification") and you should use it if you would like order but not ChronVer. If you would like to leave feedback, feel free to [send me an email](mailto:paul@chronver.org "Send Paul Anthony Webb an email about ChronVer")!

License
-------

Creative Commons — CC BY 3.0  
[https://creativecommons.org/licenses/by/3.0](https://creativecommons.org/licenses/by/3.0 "Attribution 3.0 Unported details")

  
  
from Hacker News https://chronver.org