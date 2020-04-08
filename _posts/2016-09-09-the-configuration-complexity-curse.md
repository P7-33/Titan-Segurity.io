---
title: 'The Configuration Complexity Curse'
date: 2019-11-16T11:40:00+01:00
draft: false
---

> Don’t be a YAML Engineer

Spare a thought for a software engineer entering the industry nowadays. You thought you were ready after studying your theory and the weekend side projects. Now, you get hit with a wave of new tools and concepts out of nowhere. Microservices? REST? Cloud Computing? RPC (What’s an IDL)? Docker (What’s a container)? Kubernetes? Continuous Integration? Continuous Deployment? Even for veterans, like a frog in slowly boiling water, you look up one day and realize things have become **complicated**.

How did this happen? Each of these things looks useful in isolation, but now you have to figure out how to use it best for yourself as well as with these other tools in concert. First a tool must be configured, usually in YAML (so much YAML). Now this tool needs to be integrated to work with everything else. If you are lucky, you may have an internal platform team to package and abstract the complexity for you. Otherwise, you are going end up with a rube goldbergian system that wraps all these tools so you can coordinate configuration between everything just to maintain sanity.

I think there is light at the tunnel here, but Kubernetes itself is a prime example of this industry wide pathology we experience building software platforms.

Kubernetes: It’s Turtles All The Way Down
-----------------------------------------

You start by hand writing YAML files and pushing them to a cluster with `kubectl`. Before resting on your laurels as a newly minted distributed systems engineer, you realize that you need a way to pass dynamic values to your YAML file. Enter the tool explosion; Nod along if you have ever done or considered using one of these techniques:

**Text Templating:** Many are tempted to reach for text templating libraries like Jinja, etc. Most have experience using for templating HTML, why not use it here? At this point you can get by with just simple scripts to template values then push to the cluster, or just go with something [off the shelf](https://github.com/deepmind/kapitan). Trying to write a configuration file (basically a data structure described in text) with a text templating library is the road to tragedy. As anyone who tried to write [helm chart template](https://helm.sh/docs/chart_template_guide/#the-chart-template-developer-s-guide) knows, templates quickly become hairy and incredibly fragile. Because you are working with the template at the textual level, a template writer lacks the tools to build abstractions around the data itself and small things like indentation can break your template. I think I need to repeat this: **Do not use text templating for data configuration.**

**Data Layering:** This is when you build an overlay inheritance mechanism on top of YAML, keeping the raw YAML but wrapping it in a tool that can merge these separate documents according to its own rules. [`kustomize`](https://github.com/kubernetes-sigs/kustomize) would be the most well known tool now it that is it integrated into `kubectl`. This seems to work well enough and could be feasible for simple use cases. In comparison to data configuration languages though, this strategy breaks down when configurations grow in complexity and scale. Template writers lack abstraction and type validation that matters when things get complicated, as the semantics are locked into an opaque tool and not exposed as language features.

**Data Configuration Language (DCL):** This is the most advanced form of data configuration we have today, if you absolutely need to manage configuration for a system now I would recommend one of these tools. If the previous techniques are what I call ‘YAML Engineering’, DCLs would be actual languages designed for defining data and working with data at a semantic level. Examples of DCLs are [`jsonnet`](https://jsonnet.org) (used in [`kubecfg`](https://github.com/bitnami/kubecfg)/[`ksonnet`](https://github.com/ksonnet/ksonnet)), [`dhall`](https://github.com/dhall-lang/dhall-lang) (used in [`dhall-kubernetes`](https://github.com/dhall-lang/dhall-kubernetes)), and [`starlark`](https://github.com/bazelbuild/starlark) (used in [`isopod`](https://github.com/cruise-automation/isopod)). Google internally uses a tool called `borgcfg` (which inspired `kubecfg`) which evaluates configurations in a `jsonnet`\-like internal language to configure Borg (which inspired Kubernetes) deployments. As systems scale in complexity and size, DCLs have abstractions like types, functions, comprehensions, and conditionals to manage and create reusable configurations.

So, if you want to anything more advanced than straight YAML you will need to adopt one these approaches and integrate it with your development and release process. That will help as long as you are working directly with Kubernetes, but what about configuring your underlying infrastructure? If you are on a cloud platform like AWS or Azure, even a managed Kubernetes deployment requires a tool like CloudFormation or Terraform, which has or needs its own distinct abstractions to manage resources at that level of the stack. You cannot reuse the tooling invested in configuring Kubernetes and must yet again integrate another system for configuring the cloud provider at lower level. The sound you hear is a [turtle being stacked on another turtle](https://xkcd.com/244/).

Complex Systems == Complex Configuration
----------------------------------------

We went through an example with Kubernetes about how difficult it is to manage configuration, but Kubernetes is just one of many declarative systems that show this problem. Any declarative systems and tools that grow sufficiently in size and complexity need to be abstracted but we lack common tools to do so. You may not think a Terraform configuration needs to be abstracted, but when dealing with many teams that need to deploy infrastructure in a consistent way having reusable abstractions is incredibly valuable. Same for Continuous Integration. Maintaining a YAML file may be fine for a single project, but when your organization has hundreds of services generating a consistent set of automation and checks for every project is worth the effort.

This issue hits upon the main argument of this essay:

> **As scale forces us to build and use multiple complex systems, our configuration also grows in size and complexity. Our industry builds systems and integrations without investing in tooling to manage the growing configuration complexity.**

Innovation in platforms like the cloud and Kubernetes makes things that used to be difficult and complex for a small team to do an API call away. But the loop needs to be closed on how we can build libraries that any organization can use to have a base of best practices for any platform. Even current DCLs, which I consider closer to the model we should use, lack key pieces to manage configuration at scale.

CUE: Configure, Unify, Execute
------------------------------

We need a way to manage configuration that grows in size and needs to used in many different systems. I think a tool to solve this would need two key properties:

1.  The tool is a language that has the primitives needed to create and maintain reusable, large scale configuration.
2.  The tool can orchestrate and push configuration to many different systems without having to create a new, custom tool just for that combination.

There are many languages and configuration languages that we can and do use that attempt to solve this problem. [`CUE`](https://cuelang.org/docs/about/) is a (new) data configuration language that uses a novel approach to solving the issue with a vision to tackle both what is needed to do configuration at large scale with a way to finally avoid the all too common tool wrapping that we see today. The creator of `cuelang` ([this guy](https://twitter.com/mpvl_)) worked on `borgcfg` at Google, where the learnings of managing configuration across a large company drives much of what makes `cuelang` a solution for our configuration problems today.

Why CUE?
--------

### Configuration Needs A Different Programming Model

In the Kubernetes example before, I left out the option of using a a general purpose programming language. CUE is not even the first configuration language out there. Why should we pick a completely new tool instead of reusing something that already exists?

**CUE is based on a different model of logic programming that makes it well suited for configuration.** The language’s foundations make tasks like validation, templating, querying, and code generation first class features. CUE is designed around [graph unification](https://en.wikipedia.org/wiki/Graph_theory#Subsumption_and_unification) where sets of types and values can be modeled as directed graphs and then **unified** to the most specific representation of all graphs. In CUE, the graphs are the config structures and values of the same key will simplify to the most specific value. The graph unification model is used successfully in computational linguistics, where a grammar definition of a human language can be thought of as `100K` line configuration.

This idea is much more intuitive to see with an example. Let’s look at an example CUE definition:

```
// Schema municipality: { name: string pop: int capital: bool } // Schema & Data largeCapital: municipality & { name: string pop: >5M capital: true } // Data moscow: largeCapital & { name: "Moscow" pop: 11.92M capital: true } 
```

We can see three separate structs defined here with varying mixtures of types and values defined for each and the `&` operator to force unification between them. The combination of types and values in a single struct is significant here. In CUE, **types are values**. This means that types can be assigned to fields and can be immediately used to constrain values in the configuration. You can also see that fields become more constrained towards concrete values with each struct. `largeCapital` is `municipiality` with a new constraint on the population size. `moscow` is a `largeCity` with a concrete values (the most specific type) for all fields. Between structs `largeCity` and `moscow`, `largecity` _subsumes_ `moscow` and `moscow` is an _instance of_ `largeCity`.

If you want to go deeper I recommend reading [The Logic of CUE](https://cuelang.org/docs/concepts/logic/) to understand the theoretical foundation and what makes CUE different from other configuration languages. You can also watch [this video](https://youtu.be/b3fhA12KS48) from the creator if you prefer that. I think trying to go deeper into the theory would be me poorly rewording the original article. I would rather go into how the foundation of CUE enables features that are useful for configuration.

Type Checking And Boilerplate Removal
-------------------------------------

Going back to what we need a new configuration tool, types and abstractions are the largest factors in managing large scale configuration. With types, we express constraints on data and declare intent across potentially many users. Types protect users from errors when defining configuration and serves as automatic documentation. Taking an example from the website:

```
Spec :: { kind: string name: { first: !="" // must be specified and non-empty middle?: !="" // optional, but must be non-empty when specified last: !="" } // The minimum must be strictly smaller than the maximum and vice versa. minimum?: int & minimum } // A spec is of type Spec spec: Spec spec: { knid: "Homo Sapiens" // error, misspelled field name: first: "Jane" name: last: "Doe" } 
```

In CUE, we can see what fields are needed for a `Spec` type as well the constraints on each. CUE’s type system is expressive, where fields can be marked simply by its type, to specifying optionality and constraints from other fields as well. This mixing of types and values is underrated. In constrast with JSON, one needs to generate a separate specification format (like OpenAPI) with significant effort to document and validate the JSON being consumed. With CUE, configuration can be checked and validated during evaluation without extra effort or tooling.

Most of the current configuration tooling, both general purpose and data languages, focus on removing boilerplate/duplicate code to reduce verbosity. Many choose to use an override model like inheritance (defining base types and modifying) due to developer familarity with the paradigm. This is a key factor to why I think DCLs have not seen widespread use in the industry. Although it would seem to be a obvious model, inheritance has problems in both small and large scale configuration. For small projects, defining abstractions early can be a large upfront ask with small payoff. After all, to benefit from deduplication there needs to be duplicate configuration in the first place (For the sake of clarity abstraction too early can be counterproductive). With CUE, defining the config grants automatic validation and documentation right out the gate; Paired with default values you can immediately cut down the effort to reuse common data.

For large scale projects, inheritance creates deep layers of abstractions; It becomes difficult to tell where values are coming from in a config, much more so if the language has multiple mechanisms for abstraction (inheritance, mixins). At a practical level, deep hierarchies are common in configuration and subtrees near the leaves can be challenging to modify. CUE takes a different approach with graph unification and disallows overrides. This improves readability as deep layering is prevented from the beginning; One does not need to trace through multiple files to see where a value came from. Although CUE does not have inheritance, it does have the concept of a value being an instance of another (the value lattice). This model is less flexible, but in return we get great clarity. To take a simple example, imagine we have a `Animal` class and we want to define both a `Dog` and `Cat` class. With inheritance, we could define `Animal` as the base type then selectively override and add fields to represent each respective subclass. Although workable, if we wanted to go further and represent each breed of `Cat` and `Dog` we could quickly run into issues as each layer of the hierarchy can choose to modify data as it chooses. In CUE’s approach, instead of trying override data at each layer, we choose to model `Cat` and `Dog` as instances of `Animal`. For both types, we take `Animal`’s definition but instead **add constraints** to bound what defines each animal. Even though we have the same hierarchy of types, at each layer the data can only become **more specific** for that subtype. Thanks to that for breeds we only need to further constrain what makes a `Dog` a `Corgi` and at each level we can see how the data was constrained to allow the final value.

Scripting: Inversion of Control
-------------------------------

Configuration is never created for its own sake. The purpose of all configuration is to be fed to another system to do useful work with it. Especially today, we need to manage configuration between a dizzying amount of tools and services: Software as a Service (SaaS) offerings, Cloud vendors, Continous Integration, build tools, package managers…the list goes on. In the beginning, piping config files to various tools such as `kubectl` may be enough to get the job done. Eventually though, these tasks end up as part of a greater workflow that needs to be automated. Marcel describes a problem he has seen many times:

> At first using a general config lang is cute, piping results to kubectl and what have you. But this gets cumbersome, so one writes scripts. Then, as scripts are often inconvenient to distribute and use, so one turns this into a command line tool. These tools are typically domain specific. So sooner or later, this tool needs to be part of a larger control flow, and the whole process starts again. I’ve been guilty of writing a bunch of such tools.

The resultant tools tend to consist of undifferentied glue code that is duplicated at each level of control. Even worse, the solution is hyper-specific to the combination of tools that needs to be integrated. The problem is almost asking for a more general, flexible approach.

CUE’s solution is an open, declarative [scripting layer](https://cuelang.org/docs/usecases/scripting/) built on top of the configuration language. While configuration evaluation can remain hermetic (important for enabling CUE semantics), the scriping layer can freely combine injected data as well as functions to run various tasks in a dataflow pipeline. Data injection opens up many possibilities that can close the gap that other configuration languages miss. We can inject command line flags, data from the enviroment (environment variables, data fetched over the network), and computed data from the defined config that we need for complete automation pipelines.

Today, we have incredible tool churn because we cannot easily use the same configuration between multiple systems (compatibility and accessibility). The script layer instead proposes to **invert control**. Instead of pulling configuration data into inaccessible scripts and tools, why not push the code closer to the data? The flow of data drives the need to endlessly wrap tools to work with multiple systems. Instead, we can define the automation where data and dataflow are first class citizens.

It’s hard to visualize what this means without an example. The scripting layer is still being worked on, but here is an example from running `cue help cmd`:

```
package foo import "tool/exec" city: "Amsterdam" // Say hello! command hello: { var file: "out.txt" | string // save transcript to this file task ask: cli.Ask & { prompt: "What is your name?" response: string } // starts after ask task echo: exec.Run & { cmd: ["echo", "Hello", task.ask.response + "!"] stdout: string // capture stdout } // starts after echo task write: file.Append & { filename: var.file contents: task.echo.stdout } // also starts after echo task print: cli.Print & { contents: task.echo.stdout } } 
```

For CUE, files ending in `_tool.cue` are evaluated as script files with access to injected data as well as the `command` and `task` templates. Each `command` is given a name which can called as the entrypoint; the hello `command` would be executed with `cue cmd hello`. This command asks for a name then writes a greeting to both `stdout` and a file. This workflow is implemented as a pipeline of tasks with structs used to define arguments. Since CUE can see which tasks’ input use another task’s output, we automatically get parallel pipelines through dataflow analysis. Tasks can be cover all kinds of operations, one can see the current available ones [here](https://godoc.org/cuelang.org/go/pkg/tool)

Integration And Packages
------------------------

CUE is a superset of JSON. By design, CUE aims to be useful when working with other formats; CUE supports automation to import and export to/from other data formats. Importing data and schemas into CUE (like JSON, YAML, Protocol Buffers, OpenAPI definitions) allows for managing configurations in an expressive and scalable way. Exporting to other formats enables compatibility when pushing evaluated CUE with other systems. After all, a configuration is not written for its own sake, but to be used somewhere else.

The true implications of CUE code generation are realized in combination with the package system. CUE borrows Golang’s package system, and plans on implementing [minimal version selection with URI imports](https://cuelang.slack.com/archives/CLT3ULF6C/p1571240279098400). With this, we can create reusuable abstractions _for configuration_ that has previously only in the realm of general programming.

Take the [Kubernetes example](https://cue.googlesource.com/cue/+/refs/heads/master/doc/tutorial/kubernetes/README.md/). Kubernetes is a declarative infrastructure state converger. Like a cloud provider, Kubernetes has a massive API surface spread over multiple resources. On top of that, Kubernetes allows for defining [custom resources](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/) from external sources. To manually write a DCL library to cover all of the API surface would be a massive undertaking and would quickly become out of date. With CUE, we can generate CUE code from the OpenAPI specification. With the full resource API covered, we can layer our own opinionated libraries on top. Maybe you are a platform engineer at a company that wants to ensure everyone defines deployments with the required annotations, labels, and uses the company container repository. The community can also create libraries that encourage best practices and the package system makes it simple to distribute and integrate in any workflow. If the underlying resources were to change, it is straightforward to autogenerate the CUE code and check if the libraries are still compatible.

The Automation Dream
--------------------

Putting all these ideas together, we end up with a vision for future configuration. We can have libraries for not only configuring applications but also libraries of automation that run end-to-end workflows for pushing that data to systems. CUE’s design enables configuration at scale: organizations can define constraints and templates at a high level, users layer specific values to make concrete definitions. Organizations find it easier to enforce best practices and policy, front line engineers get templates and automation out of the box to become productive that much quicker. With distributed packaging, we are not limited to what only our teams can create but can leverage best practices and knowledge from the wider industry.

CUE And You
-----------

As of this writing, CUE is a pretty new (alpha) language. There is still much work to be done to reach the complete vision, especially in the integrations with other languages, platforms, and data formats. Fortunately, any improvements to the ecosystem can be easily shared for everyone to use.

If I were to summarize the main reason to choose CUE, it is because it chooses to build from a theoretical foundation that makes it a true contender for configuration needs. So many of the useful features CUE provides fall out from its properties (commutative, associative, and idempotent). In a industry where the way we work is becoming more complicated, CUE has come along to make things much more manageable.

If any of these people apply to you:

*   A developer who wants to use Kubernetes/Cloud in an effective way
*   An application developer who wants to create easy to share automation for a project
*   A platform developer who wants to create useful templates for every team to use
*   An architect who wants a simple way to enforce consistent policy across an organization
*   Tired of writing so much YAML

you should look into CUE.

  
  
from Hacker News https://ift.tt/2OjK2Qo