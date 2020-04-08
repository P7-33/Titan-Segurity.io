---
title: 'Jekyll vs. GatsbyJS: Which Static Site Builder Builds the Best Website?'
date: 2019-10-30T10:53:00+01:00
draft: false
---

![static-site-builders](https://static.makeuseof.com/wp-content/uploads/2019/10/static-site-builders.jpg)

Static site builders are tools designed to make building a website easier by setting up a lot of the code you would normally have to write from scratch. Whether you need a website for a business or starting a blog, choosing a static website is typically a great choice.

Jekyll and GatsbyJS are two builders that have become particularly popular thanks to their ease of use. Which builder is best? Let’s break these two options down.

Jekyll vs. GatsbyJS: Under the Hood
-----------------------------------

It’s important to know what code is used to create each of these builders. If you already have a background in a certain programming language you may find one these builders a little easier to use.

### Jekyll (Ruby)

Jekyll is built with the [Ruby programming language](https://www.ruby-lang.org/en/downloads/). Ruby is an all-purpose language that is reliable for many different applications. Jekyll is a Ruby Gem, a package of code built inside of Ruby that makes installation simpler at the terminal.

### GatsbyJS (Javascript + React)

GatsbyJS is built using [React, a JavaScript library](https://reactjs.org/) that has become very popular for building websites. In order to use GatsbyJS, you will also need Node.js and the Node Package Manager (NPM).

Using GatsbyJS requires a pretty comfortable grasp of JavaScript. Fortunately, JavaScript is the most popular language for working on web code. If you have a good grasp of JavaScript you might find yourself more comfortable right from the start with GatsbyJS.

Jekyll vs. GatsbyJS: Installation
---------------------------------

Installation of both static website builders is pretty simple using the command line.

### Jekyll

To get started with Jekyll, once you have Ruby installed, you only need to run a few instructions at the command line. Jekyll’s **Quickstart Guide** is a great resource.

1.  Install Ruby
2.  Install Jekyll and Bundler Gems
3.  Create your website
4.  View in your browser on http://localhost:4000

It’s a pretty simple process once you get the hang of Ruby.

### GatsbyJS

GatsbyJS will require a few things to be installed to make launching a website simple. The three things you will need are:

*   Node.js
*   Git
*   Gatsby Command Line Interface (CLI)

Node.js is essential to run Gatsby.js, so you will need to make sure this is installed first. You can download Node.js for Windows. If you’re on macOS, GatsbyJS recommends using Homebrew to install Node.js through the terminal.

Git is required for GatsbyJS on all systems, but chances are you’re using this already if you’re working with code.

The Gatsby CLI is a tool built by GatsbyJS that lets you develop websites easier. It is a package in the Node Package Manager (NPM) for Node.js.

To install the Gatsby CLI all you have to do is run an NPM command at the terminal.

```
npm install -g gatsby-cli
```

Note for Windows users: GatsbyJS leans a little towards macOS in its installation. For Windows installation, [GatsbyJS recommends using Windows Subsystem for Linux](https://www.gatsbyjs.org/docs/gatsby-on-windows/) if you’re using Windows 10.

GatsbyJS provide a Quickstart Guide as well. The Gatsby CLI runs commands at the terminal using the `gatsby` command. Here is an example using a Gatsby starter, which is just a code template provided by GatsbyJS:

Once you run this sequence you can open **http://localhost:8000** to view your website.

Jekyll vs. GatsbyJS: Ecosystem and Features
-------------------------------------------

When choosing a site builder you should look at not only the builder but all other tools and support it can use.

### Jekyll

Jekyll uses a combination of Liquid, Markdown, HTML, and CSS to process websites. Liquid does a great job performing logic inside of HTML. Markdown is a neat little tool to speed up coding by letting you write plain text words; Markdown will convert your text to clean HTML. [Markdown has a long list of features that make your development easier](//www.makeuseof.com/tag/printable-markdown-cheat-sheet/).

Jekyll does have a plugin system that can create some additional functionality, using Ruby Gems. There is a host of plugins built into Ruby for Jekyll, and you can create your own.

Jekyll also features a pretty unique feature that can import code from existing websites, and convert them to Jekyll. The idea is to take an older, maybe more cluttered, website and improve performance with Jekyll. You can import code from WordPress, Tumblr, Drupal and more.

### GatsbyJS

GatsbyJS uses React.js by JavaScript which is widely used, thanks to its speed and modern design. Webpack, CSS, and JavaScript all combine to deliver an impressive stack.

GatsbyJS also has a rich plugin system supported by Node.js and delivered as packages. The popularity of Node.js gives GatsbyJS a little bit of an edge. NPM packages are extremely popular in web development thanks to their stability and the use of JavaScript.

GatsbyJS has a selection of starters and themes, which are just templates you can start a website with. They’re nice to have, but not something that really will make or break choosing GatsbyJS. The real advantage is going to be the use of Node.js

Jekyll vs. GatsbyJS: Final Impressions
--------------------------------------

Before wrapping up, it’s pretty clear that the programming language first and foremost is the most important thing to consider when deciding between these two builders. All of their real features are based around their code, so if you’re comfortable with Ruby (Jeykll) or JavaScrip t(GatsbyJS) the decision will be pretty clear.

We like Jekyll for its stability, it has great support from GitHub. The use of Liquid and Markdown are nice to have, and the feature to import old code is pretty useful.

GatsbyJS is packed with a lot of features, centered around Node.js. GatsbyJS touts a modern stack that can develop websites for both the web and mobile. React, Webpack, GraphQL, CSS, and HTML are built-in, and good to have. [JavaScript is one of the easiest languages to learn](//www.makeuseof.com/tag/easiest-programming-languages-beginners/), so even if you don’t know it, you can learn quickly.

The starter library for both builders is nice, but if you’re building a serious website you won’t have much of a use for them at all.

Both builders are powerful and evenly matched. With that being said the builder we like more is GatsbyJS. It uses [JavaScript which will work well into the future](//www.makeuseof.com/tag/top-programming-language-learn-future/), boasts great performance, and has the support of the NPM library which continues to grow.

Read the full article: [Jekyll vs. GatsbyJS: Which Static Site Builder Builds the Best Website?](https://www.makeuseof.com/tag/jekyll-vs-gatsbyjs-static-site-builder/)

  
  
from MakeUseOf https://ift.tt/36dQzEF  
via [IFTTT](https://ifttt.com/?ref=da&site=blogger)