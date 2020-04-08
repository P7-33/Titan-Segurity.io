---
title: 'Standard Go Project Layout'
date: 2019-09-26T01:52:00+01:00
draft: false
---

[](https://github.com/golang-standards/project-layout#standard-go-project-layout)Standard Go Project Layout
===========================================================================================================

This is a basic layout for Go application projects. It's not an official standard defined by the core Go dev team; however, it is a set of common historical and emerging project layout patterns in the Go ecosystem. Some of these patterns are more popular than others. It also has a number of small enhancements along with several supporting directories common to any large enough real world application.

If you are trying to learn Go or if you are building a PoC or a toy project for yourself this project layout is an overkill. Start with something really simple (a single `main.go` file is more than enough). As your project grows keep in mind that it'll be important to make sure your code is well structured otherwise you'll end up with a messy code with lots of hidden dependencies and global state. When you have more people working on the project you'll need even more structure. That's when it's important to introduce a common way to manage packages/libraries. When you have an open source project or when you know other projects import the code from your project repository that's when it's important to have private (aka `internal`) packages and code. Clone the repository, keep what you need and delete everything else! Just because it's there it doesn't mean you have to use it all. None of these patterns are used in every single project. Even the `vendor` pattern is not universal.

This project layout is intentionally generic and it doesn't try to impose a specific Go package structure.

This is a community effort. Open an issue if you see a new pattern or if you think one of the existing patterns needs to be updated.

If you need help with naming, formatting and style start by running [`gofmt`](https://golang.org/cmd/gofmt/) and [`golint`](https://github.com/golang/lint). Also make sure to read these Go code style guidelines and recommendations:

See [`Go Project Layout`](https://medium.com/golang-learn/go-project-layout-e5213cdcfaa2) for additional background information.

More about naming and organizing packages as well as other code structure recommendations:

[](https://github.com/golang-standards/project-layout#go-directories)Go Directories
-----------------------------------------------------------------------------------

### [](https://github.com/golang-standards/project-layout#cmd)`/cmd`

Main applications for this project.

The directory name for each application should match the name of the executable you want to have (e.g., `/cmd/myapp`).

Don't put a lot of code in the application directory. If you think the code can be imported and used in other projects, then it should live in the `/pkg` directory. If the code is not reusable or if you don't want others to reuse it, put that code in the `/internal` directory. You'll be surprised what others will do, so be explicit about your intentions!

It's common to have a small `main` function that imports and invokes the code from the `/internal` and `/pkg` directories and nothing else.

See the [`/cmd`](https://github.com/golang-standards/project-layout/blob/master/cmd/README.md) directory for examples.

### [](https://github.com/golang-standards/project-layout#internal)`/internal`

Private application and library code. This is the code you don't want others importing in their applications or libraries.

Put your actual application code in the `/internal/app` directory (e.g., `/internal/app/myapp`) and the code shared by those apps in the `/internal/pkg` directory (e.g., `/internal/pkg/myprivlib`).

### [](https://github.com/golang-standards/project-layout#pkg)`/pkg`

Library code that's ok to use by external applications (e.g., `/pkg/mypubliclib`). Other projects will import these libraries expecting them to work, so think twice before you put something here :-)

It's also a way to group Go code in one place when your root directory contains lots of non-Go components and directories making it easier to run various Go tools (as mentioned in the [`Best Practices for Industrial Programming`](https://www.youtube.com/watch?v=PTE4VJIdHPg) from GopherCon EU 2018).

See the [`/pkg`](https://github.com/golang-standards/project-layout/blob/master/pkg/README.md) directory if you want to see which popular Go repos use this project layout pattern. This is a common layout pattern, but it's not universally accepted and some in the Go community don't recommend it.

### [](https://github.com/golang-standards/project-layout#vendor)`/vendor`

Application dependencies (managed manually or by your favorite dependency management tool like [`dep`](https://github.com/golang/dep)).

Don't commit your application dependencies if you are building a library.

[](https://github.com/golang-standards/project-layout#service-application-directories)Service Application Directories
---------------------------------------------------------------------------------------------------------------------

### [](https://github.com/golang-standards/project-layout#api)`/api`

OpenAPI/Swagger specs, JSON schema files, protocol definition files.

See the [`/api`](https://github.com/golang-standards/project-layout/blob/master/api/README.md) directory for examples.

[](https://github.com/golang-standards/project-layout#web-application-directories)Web Application Directories
-------------------------------------------------------------------------------------------------------------

### [](https://github.com/golang-standards/project-layout#web)`/web`

Web application specific components: static web assets, server side templates and SPAs.

[](https://github.com/golang-standards/project-layout#common-application-directories)Common Application Directories
-------------------------------------------------------------------------------------------------------------------

### [](https://github.com/golang-standards/project-layout#configs)`/configs`

Configuration file templates or default configs.

Put your `confd` or `consul-template` template files here.

### [](https://github.com/golang-standards/project-layout#init)`/init`

System init (systemd, upstart, sysv) and process manager/supervisor (runit, supervisord) configs.

### [](https://github.com/golang-standards/project-layout#scripts)`/scripts`

Scripts to perform various build, install, analysis, etc operations.

These scripts keep the root level Makefile small and simple (e.g., `https://github.com/hashicorp/terraform/blob/master/Makefile`).

See the [`/scripts`](https://github.com/golang-standards/project-layout/blob/master/scripts/README.md) directory for examples.

### [](https://github.com/golang-standards/project-layout#build)`/build`

Packaging and Continuous Integration.

Put your cloud (AMI), container (Docker), OS (deb, rpm, pkg) package configurations and scripts in the `/build/package` directory.

Put your CI (travis, circle, drone) configurations and scripts in the `/build/ci` directory. Note that some of the CI tools (e.g., Travis CI) are very picky about the location of their config files. Try putting the config files in the `/build/ci` directory linking them to the location where the CI tools expect them (when possible).

### [](https://github.com/golang-standards/project-layout#deployments)`/deployments`

IaaS, PaaS, system and container orchestration deployment configurations and templates (docker-compose, kubernetes/helm, mesos, terraform, bosh).

### [](https://github.com/golang-standards/project-layout#test)`/test`

Additional external test apps and test data. Feel free to structure the `/test` directory anyway you want. For bigger projects it makes sense to have a data subdirectory. For example, you can have `/test/data` or `/test/testdata` if you need Go to ignore what's in that directory. Note that Go will also ignore directories or files that begin with "." or "\_", so you have more flexibility in terms of how you name your test data directory.

See the [`/test`](https://github.com/golang-standards/project-layout/blob/master/test/README.md) directory for examples.

[](https://github.com/golang-standards/project-layout#other-directories)Other Directories
-----------------------------------------------------------------------------------------

### [](https://github.com/golang-standards/project-layout#docs)`/docs`

Design and user documents (in addition to your godoc generated documentation).

See the [`/docs`](https://github.com/golang-standards/project-layout/blob/master/docs/README.md) directory for examples.

### [](https://github.com/golang-standards/project-layout#tools)`/tools`

Supporting tools for this project. Note that these tools can import code from the `/pkg` and `/internal` directories.

See the [`/tools`](https://github.com/golang-standards/project-layout/blob/master/tools/README.md) directory for examples.

### [](https://github.com/golang-standards/project-layout#examples)`/examples`

Examples for your applications and/or public libraries.

See the [`/examples`](https://github.com/golang-standards/project-layout/blob/master/examples/README.md) directory for examples.

### [](https://github.com/golang-standards/project-layout#third_party)`/third_party`

External helper tools, forked code and other 3rd party utilities (e.g., Swagger UI).

### [](https://github.com/golang-standards/project-layout#githooks)`/githooks`

Git hooks.

### [](https://github.com/golang-standards/project-layout#assets)`/assets`

Other assets to go along with your repository (images, logos, etc).

### [](https://github.com/golang-standards/project-layout#website)`/website`

This is the place to put your project's website data if you are not using Github pages.

See the [`/website`](https://github.com/golang-standards/project-layout/blob/master/website/README.md) directory for examples.

[](https://github.com/golang-standards/project-layout#directories-you-shouldnt-have)Directories You Shouldn't Have
------------------------------------------------------------------------------------------------------------------

### [](https://github.com/golang-standards/project-layout#src)`/src`

Some Go projects do have a `src` folder, but it usually happens when the devs came from the Java world where it's a common pattern. If you can help yourself try not to adopt this Java pattern. You really don't want your Go code or Go projects to look like Java :-)

Don't confuse the project level `/src` directory with the `/src` directory Go uses for its workspaces as described in [`How to Write Go Code`](https://golang.org/doc/code.html). The `$GOPATH` environment variable points to your (current) workspace (by default it points to `$HOME/go` on non-windows systems). This workspace includes the top level `/pkg`, `/bin` and `/src` directories. Your actual project ends up being a sub-directory under `/src`, so if you have the `/src` directory in your project the project path will look like this: `/some/path/to/workspace/src/your_project/src/your_code.go`. Note that with Go 1.11 it's possible to have your project outside of your `GOPATH`, but it still doesn't mean it's a good idea to use this layout pattern.

[](https://github.com/golang-standards/project-layout#badges)Badges
-------------------------------------------------------------------

*   [Go Report Card](https://goreportcard.com/) - It will scan your code with `gofmt`, `go vet`, `gocyclo`, `golint`, `ineffassign`, `license` and `misspell`. Replace `github.com/golang-standards/project-layout` with your project reference.
    
*   [GoDoc](http://godoc.org) - It will provide online version of your GoDoc generated documentation. Change the link to point to your project.
    
*   Release - It will show the latest release number for your project. Change the github link to point to your project.
    

[![Go Report Card](https://camo.githubusercontent.com/76ae5cf1f35c33600184fc07370a007efab09b13/68747470733a2f2f676f7265706f7274636172642e636f6d2f62616467652f6769746875622e636f6d2f676f6c616e672d7374616e64617264732f70726f6a6563742d6c61796f75743f7374796c653d666c61742d737175617265)](https://goreportcard.com/report/github.com/golang-standards/project-layout) [![Go Doc](https://camo.githubusercontent.com/ac30242392a5470effdd2b008d7be055b6f6f8d6/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f676f646f632d7265666572656e63652d626c75652e7376673f7374796c653d666c61742d737175617265)](http://godoc.org/github.com/golang-standards/project-layout) [![Release](https://camo.githubusercontent.com/21ec77f51096b4c302f8666ee16e81a58a264cc9/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f72656c656173652f676f6c616e672d7374616e64617264732f70726f6a6563742d6c61796f75742e7376673f7374796c653d666c61742d737175617265)](https://github.com/golang-standards/project-layout/releases/latest)

[](https://github.com/golang-standards/project-layout#notes)Notes
-----------------------------------------------------------------

A more opinionated project template with sample/reusable configs, scripts and code is a WIP.

  
  
from Hacker News https://github.com/golang-standards/project-layout