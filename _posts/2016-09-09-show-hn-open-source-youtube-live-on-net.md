---
title: 'Show HN: Open-source YouTube, live on the net now and Powered by Node.js'
date: 2020-01-01T10:55:00+01:00
draft: false
---

[![](https://user-images.githubusercontent.com/7200471/71605820-40db7880-2b29-11ea-8fa0-b8628cfd55ad.png)](https://user-images.githubusercontent.com/7200471/71605820-40db7880-2b29-11ea-8fa0-b8628cfd55ad.png)

_**Deployment Options**_

One-Click Install For Heroku

[![Deploy](https://camo.githubusercontent.com/c0824806f5221ebb7d25e559568582dd39dd1170/68747470733a2f2f7777772e6865726f6b7563646e2e636f6d2f6465706c6f792f627574746f6e2e706e67)](https://heroku.com/deploy?template=https://github.com/mayeaux/nodetube)

Join us for collaboration here on [Discord](https://discord.gg/ejGah8H)

[](https://github.com/mayeaux/nodetube#prerequisites)Prerequisites
------------------------------------------------------------------

Please also check the [Wiki](https://github.com/mayeaux/nodetube/wiki) for additional information on getting site functionality running

*   Command Line Tools
*   [![](https://camo.githubusercontent.com/d484918c92c1847c2c59d98f1c32335eec73f3a8/687474703a2f2f64656c7567652d746f7272656e742e6f72672f696d616765732f6170706c652d6c6f676f2e676966)](https://camo.githubusercontent.com/d484918c92c1847c2c59d98f1c32335eec73f3a8/687474703a2f2f64656c7567652d746f7272656e742e6f72672f696d616765732f6170706c652d6c6f676f2e676966) **Mac OS X:** [Xcode](https://itunes.apple.com/us/app/xcode/id497799835?mt=12) (or **OS X 10.9+**: `xcode-select --install`)
*   [![](https://camo.githubusercontent.com/224d85f99b5e58b0e8b534636f2cb381fe575b62/687474703a2f2f64633934326434313938343361663035353233622d66663734616531333533376130316265366366656335393237383337646366652e7231342e6366312e7261636b63646e2e636f6d2f77702d636f6e74656e742f75706c6f6164732f77696e646f77732d382d35307835302e6a7067)](https://camo.githubusercontent.com/224d85f99b5e58b0e8b534636f2cb381fe575b62/687474703a2f2f64633934326434313938343361663035353233622d66663734616531333533376130316265366366656335393237383337646366652e7231342e6366312e7261636b63646e2e636f6d2f77702d636f6e74656e742f75706c6f6164732f77696e646f77732d382d35307835302e6a7067) **Windows:** [Visual Studio](https://www.visualstudio.com/products/visual-studio-community-vs)
*   [![](https://camo.githubusercontent.com/24ffd70fd53bced9e23cd0e8957e9bb6da67732f/68747470733a2f2f6c68352e676f6f676c6575736572636f6e74656e742e636f6d2f2d32595331636548577979732f41414141414141414141492f41414141414141414141632f304c43625f747354766d552f7334362d632d6b2f70686f746f2e6a7067)](https://camo.githubusercontent.com/24ffd70fd53bced9e23cd0e8957e9bb6da67732f/68747470733a2f2f6c68352e676f6f676c6575736572636f6e74656e742e636f6d2f2d32595331636548577979732f41414141414141414141492f41414141414141414141632f304c43625f747354766d552f7334362d632d6b2f70686f746f2e6a7067) **Ubuntu** / [![](https://camo.githubusercontent.com/e000936fc7105a861c76273c6cd87cb816a66dc0/68747470733a2f2f75706c6f61642e77696b696d656469612e6f72672f77696b6970656469612f636f6d6d6f6e732f332f33662f4c6f676f5f4c696e75785f4d696e742e706e67)](https://camo.githubusercontent.com/e000936fc7105a861c76273c6cd87cb816a66dc0/68747470733a2f2f75706c6f61642e77696b696d656469612e6f72672f77696b6970656469612f636f6d6d6f6e732f332f33662f4c6f676f5f4c696e75785f4d696e742e706e67) **Linux Mint:** `sudo apt-get install build-essential`
*   [![](https://camo.githubusercontent.com/4be6317f336cc3075468826802bd04fbbfe11f3a/687474703a2f2f69312d6e6577732e736f667470656469612d7374617469632e636f6d2f696d616765732f65787472612f4c494e55582f736d616c6c2f736c773231386e657773312e706e67)](https://camo.githubusercontent.com/4be6317f336cc3075468826802bd04fbbfe11f3a/687474703a2f2f69312d6e6577732e736f667470656469612d7374617469632e636f6d2f696d616765732f65787472612f4c494e55582f736d616c6c2f736c773231386e657773312e706e67) **Fedora**: `sudo dnf groupinstall "Development Tools"`
*   [![](https://camo.githubusercontent.com/a124c47491aa02d39bfb32105181962ba66b24c7/68747470733a2f2f656e2e6f70656e737573652e6f72672f696d616765732f622f62652f4c6f676f2d6765656b6f5f686561642e706e67)](https://camo.githubusercontent.com/a124c47491aa02d39bfb32105181962ba66b24c7/68747470733a2f2f656e2e6f70656e737573652e6f72672f696d616765732f622f62652f4c6f676f2d6765656b6f5f686561642e706e67) **OpenSUSE:** `sudo zypper install --type pattern devel_basis`

**Note:** If you are new to Node or Express, I recommend to watch [Node.js and Express 101](https://www.youtube.com/watch?v=BN0JlMZCtNU) screencast by Alex Ford that teaches Node and Express from scratch. Alternatively, here is another great tutorial for complete beginners - [Getting Started With Node.js, Express, MongoDB](http://cwbuecheler.com/web/tutorials/2013/node-express-mongo/).

[](https://github.com/mayeaux/nodetube#getting-started)Getting Started
----------------------------------------------------------------------

The easiest way to get started is to clone the repository:

```
# Get the latest snapshot git clone https://github.com/mayeaux/nodetube # Change directory cd nodetube # Install backend and frontend dependencies npm run installDeps # Then simply start your app npm start #If you're developing locally, you can boot the app with nodemon with: npm run dev
```

**Note:** I highly recommend installing [Nodemon](https://github.com/remy/nodemon). It watches for any changes in your node.js app and automatically restarts the server. Once installed, instead of `node app.js` use `nodemon app.js`. It will save you a lot of time in the long run, because you won't need to manually restart the server each time you make a small change in code. To install, run `sudo npm install -g nodemon`.

[](https://github.com/mayeaux/nodetube#yarn-vs-npm)Yarn vs NPM
--------------------------------------------------------------

Yarn is a new JavaScript package manager built by Facebook, Google, Exponent and Tilde. Yarn is not an attempt to replace `npm`, it's simply an alternative CLI client for fetching modules from the npm registry but it does have some unique benefits over using `npm`, most noticeably speed and consistency (via a lock file which ensures that only specific versions of dependencies are installed). Hackathon Starter includes a `yarn.lock` file by default and as project dependencies are updated, this file will be updated to reflect those changes.

To upgrade your local dependencies using Yarn, simply run `yarn upgrade`. This will update all dependencies to their latest version based on the [version range](https://docs.npmjs.com/getting-started/semantic-versioning#semver-for-consumers) specified in the `package.json` file. The yarn.lock file will be recreated as well. For further information, please see the official documention for [managing dependencies](https://yarnpkg.com/en/docs/managing-dependencies) and [upgrading dependencies](https://yarnpkg.com/en/docs/cli/upgrade). This [Yarn vs NPM](https://www.sitepoint.com/yarn-vs-npm/) article by SitePoint also has some very useful information.

[](https://github.com/mayeaux/nodetube#docker)Docker
----------------------------------------------------

The project has an experimental [Docker](https://www.docker.com/what-docker) setup, using [Docker Compose](https://docs.docker.com/compose/overview/). It is entirely optional, so if you don't want to use Docker, feel free to ignore it.

If you have Docker installed, there's a non-zero chance that running `docker-compose up` is all you need to do to build and start 3 docker containers (one each for the app itself, Redis, and MongoDB). From there, you should be able to connect to [http://localhost:49160](http://localhost:49160) and see the app running.

[](https://github.com/mayeaux/nodetube#project-structure)Project Structure
--------------------------------------------------------------------------

Name

Description

**config**/passport.js

Passport Local and OAuth strategies, plus login middleware.

**controllers**/api.js

Controller for /api route and all api examples.

**controllers**/contact.js

Controller for contact form.

**controllers**/home.js

Controller for home page (index).

**controllers**/user.js

Controller for user account management.

**models**/User.js

Mongoose schema and model for User.

**public**/

Static assets (fonts, css, js, img).

**public**/**js**/application.js

Specify client-side JavaScript dependencies.

**public**/**js**/main.js

Place your client-side JavaScript here.

**public**/**css**/main.scss

Main stylesheet for your app.

**public/css/themes**/default.scss

Some Bootstrap overrides to make it look prettier.

**views/account**/

Templates for _login, password reset, signup, profile_.

**views/api**/

Templates for API Examples.

**views/partials**/flash.pug

Error, info and success flash notifications.

**views/partials**/header.pug

Navbar partial template.

**views/partials**/footer.pug

Footer partial template.

**views**/layout.pug

Base template.

**views**/home.pug

Home page template.

.env.example

Your API keys, tokens, passwords and database URI.

app.js

The main application file.

package.json

NPM dependencies.

yarn.lock

Contains exact versions of NPM dependencies in package.json.

**Note:** There is no preference how you name or structure your views. You could place all your templates in a top-level `views` directory without having a nested folder structure, if that makes things easier for you. Just don't forget to update `extends ../layout` and corresponding `res.render()` paths in controllers.

[](https://github.com/mayeaux/nodetube#list-of-packages)List of Packages
------------------------------------------------------------------------

Package

Description

async

Utility library that provides asynchronous control flow.

bcrypt-nodejs

Library for hashing and salting user passwords.

cheerio

Scrape web pages using jQuery-style syntax.

clockwork

Clockwork SMS API library.

connect-mongo

MongoDB session store for Express.

dotenv

Loads environment variables from .env file.

express

Node.js web framework.

body-parser

Express 4 middleware.

express-session

Express 4 middleware.

morgan

Express 4 middleware.

compression

Express 4 middleware.

errorhandler

Express 4 middleware.

serve-favicon

Express 4 middleware offering favicon serving and caching.

express-flash

Provides flash messages for Express.

express-status-monitor

Reports real-time server metrics for Express.

express-validator

Easy form validation for Express.

fbgraph

Facebook Graph API library.

github

GitHub API library.

pug (jade)

Template engine for Express.

lastfm

Last.fm API library.

instagram-node

Instagram API library.

lob

Lob API library

lusca

CSRF middleware.

mongoose

MongoDB ODM.

node-foursquare

Foursquare API library.

node-linkedin

LinkedIn API library.

node-sass-middleware

Sass middleware compiler.

nodemailer

Node.js library for sending emails.

passport

Simple and elegant authentication library for node.js

passport-facebook

Sign-in with Facebook plugin.

passport-github

Sign-in with GitHub plugin.

passport-google-oauth

Sign-in with Google plugin.

passport-twitter

Sign-in with Twitter plugin.

passport-instagram

Sign-in with Instagram plugin.

passport-local

Sign-in with Username and Password plugin.

passport-linkedin-oauth2

Sign-in with LinkedIn plugin.

passport-oauth

Allows you to set up your own OAuth 1.0a and OAuth 2.0 strategies.

paypal-rest-sdk

PayPal APIs library.

request

Simplified HTTP request library.

stripe

Offical Stripe API library.

tumblr.js

Tumblr API library.

twilio

Twilio API library.

twit

Twitter API library.

lodash

Handy JavaScript utlities library.

validator

Used in conjunction with express-validator in **controllers/api.js**.

mocha

Test framework.

chai

BDD/TDD assertion library.

supertest

HTTP assertion library.

[](https://github.com/mayeaux/nodetube#faq)FAQ
----------------------------------------------

### [](https://github.com/mayeaux/nodetube#why-do-i-get-403-error-forbidden-when-submitting-a-form)Why do I get `403 Error: Forbidden` when submitting a form?

You need to add the following hidden input element to your form. This has been added in the [pull request #40](https://github.com/sahat/hackathon-starter/pull/40) as part of the CSRF protection.

```
input(type='hidden', name='_csrf', value=_csrf) 
```

**Note:** It is now possible to whitelist certain URLs. In other words you can specify a list of routes that should bypass CSRF verification check.

**Note 2:** To whitelist dynamic URLs use regular expression tests inside the CSRF middleware to see if `req.originalUrl` matches your desired pattern.

### [](https://github.com/mayeaux/nodetube#i-am-getting-mongodb-connection-error-how-do-i-fix-it)I am getting MongoDB Connection Error, how do I fix it?

That's a custom error message defined in `app.js` to indicate that there was a problem connecting to MongoDB:

```
mongoose.connection.on('error', () \=> { console.error('MongoDB Connection Error. Please make sure MongoDB is running.'); });
```

You need to have a MongoDB server running before launching `app.js`. You can download MongoDB [here](http://mongodb.org/downloads), or install it via a package manager. [![](https://camo.githubusercontent.com/224d85f99b5e58b0e8b534636f2cb381fe575b62/687474703a2f2f64633934326434313938343361663035353233622d66663734616531333533376130316265366366656335393237383337646366652e7231342e6366312e7261636b63646e2e636f6d2f77702d636f6e74656e742f75706c6f6164732f77696e646f77732d382d35307835302e6a7067)](https://camo.githubusercontent.com/224d85f99b5e58b0e8b534636f2cb381fe575b62/687474703a2f2f64633934326434313938343361663035353233622d66663734616531333533376130316265366366656335393237383337646366652e7231342e6366312e7261636b63646e2e636f6d2f77702d636f6e74656e742f75706c6f6164732f77696e646f77732d382d35307835302e6a7067) Windows users, read [Install MongoDB on Windows](https://docs.mongodb.org/manual/tutorial/install-mongodb-on-windows/).

**Tip:** If you are always connected to the internet, you could just use [mLab](https://mongolab.com/) or [Compose](https://www.compose.io/) instead of downloading and installing MongoDB locally. You will only need to update database credentials in `.env` file.

### [](https://github.com/mayeaux/nodetube#i-get-an-error-when-i-deploy-my-app-why)I get an error when I deploy my app, why?

Chances are you haven't changed the _Database URI_ in `.env`. If `MONGODB`/`MONGOLAB_URI` is set to `localhost`, it will only work on your machine as long as MongoDB is running. When you deploy to Heroku, OpenShift or some other provider, you will not have MongoDB running on `localhost`. You need to create an account with [mLab](https://mongolab.com/) or [Compose](https://www.compose.io/), then create a free tier database. See [Deployment](https://github.com/mayeaux/nodetube#deployment) for more information on how to setup an account and a new database step-by-step with mLab.

### [](https://github.com/mayeaux/nodetube#why-pug-jade-instead-of-handlebars)Why Pug (Jade) instead of Handlebars?

When I first started this project I didn't have any experience with Handlebars. Since then I have worked on Ember.js apps and got myself familiar with the Handlebars syntax. While it is true Handlebars is easier, because it looks like good old HTML, I have no regrets picking Jade over Handlebars. First off, it's the default template engine in Express, so someone who has built Express apps in the past already knows it. Secondly, I find `extends` and `block` to be indispensable, which as far as I know, Handlebars does not have out of the box. And lastly, subjectively speaking, Jade looks much cleaner and shorter than Handlebars, or any non-HAML style for that matter.

### [](https://github.com/mayeaux/nodetube#how-do-flash-messages-work-in-this-project)How do flash messages work in this project?

Flash messages allow you to display a message at the end of the request and access it on next request and only next request. For instance, on a failed login attempt, you would display an alert with some error message, but as soon as you refresh that page or visit a different page and come back to the login page, that error message will be gone. It is only displayed once. This project uses _express-flash_ module for flash messages. And that module is built on top of _connect-flash_, which is what I used in this project initially. With _express-flash_ you don't have to explicitly send a flash message to every view inside `res.render()`. All flash messages are available in your views via `messages` object by default, thanks to _express-flash_.

Flash messages have a two-step process. You use `req.flash('errors', { msg: 'Error messages goes here' }` to create a flash message in your controllers, and then display them in your views:

```
if messages.errors .alert.alert-danger.fade.in for error in messages.errors div\= error.msg
```

In the first step, `'errors'` is the name of a flash message, which should match the name of the property on `messages` object in your views. You place alert messages inside `if message.errors` because you don't want to show them flash messages are actually present. The reason why you pass an error like `{ msg: 'Error messages goes here' }` instead of just a string - `'Error messages goes here'`, is for the sake of consistency. To clarify that, _express-validator_ module which is used for validating and sanitizing user's input, returns all errors as an array of objects, where each object has a `msg` property with a message why an error has occurred. Here is a more general example of what express-validator returns when there are errors present:

```
\[ { param: "name", msg: "Name is required", value: "" }, { param: "email", msg: "A valid email is required", value: "" } \]
```

To keep consistent with that style, you should pass all flash messages as `{ msg: 'My flash message' }` instead of a string. Otherwise you will just see an alert box without an error message. That is because, in **partials/flash.pug** template it will try to output `error.msg` (i.e. `"My flash message".msg`), in other words it will try to call a `msg` method on a _String_ object, which will return _undefined_. Everything I just mentioned about errors, also applies to "info" and "success" flash messages, and you could even create a new one yourself, such as:

**Data Usage Controller (Example)**

```
req.flash('warning', { msg: 'You have exceeded 90% of your data usage' }); 
```

**User Account Page (Example)**

```
if messages.warning .alert.alert-warning.fade.in for warning in messages.warning div\= warning.msg
```

`partials/flash.pug` is a partial template that contains how flash messages are formatted. Previously, flash messages were scattered throughout each view that used flash messages (contact, login, signup, profile), but now, thankfully it is uses a _DRY_ approach.

The flash messages partial template is _included_ in the `layout.pug`, along with footer and navigation.

```
body include partials/header .container include partials/flash block content include partials/footer
```

If you have any further questions about flash messages, please feel free to open an issue and I will update this mini-guide accordingly, or send a pull request if you would like to include something that I missed.

* * *

### [](https://github.com/mayeaux/nodetube#how-do-i-create-a-new-page)How do I create a new page?

A more correct way to be to say "How do I create a new route". The main file `app.js` contains all the routes. Each route has a callback function associated with it. Sometimes you will see 3 or more arguments to routes. In cases like that, the first argument is still a URL string, while middle arguments are what's called middleware. Think of middleware as a door. If this door prevents you from continuing forward, you won't get to your callback function. One such example is a route that requires authentication.

```
app.get('/account', passportConfig.isAuthenticated, userController.getAccount);
```

It always goes from left to right. A user visits `/account` page. Then `isAuthenticated` middleware checks if you are authenticated:

```
exports.isAuthenticated \= (req, res, next) \=> { if (req.isAuthenticated()) { return next(); } res.redirect('/login'); };
```

If you are authenticated, you let this visitor pass through your "door" by calling `return next();`. It then proceeds to the next middleware until it reaches the last argument, which is a callback function that typically renders a template on `GET` requests or redirects on `POST` requests. In this case, if you are authenticated, you will be redirected to _Account Management_ page, otherwise you will be redirected to _Login_ page.

```
exports.getAccount \= (req, res) \=> { res.render('account/profile', { title: 'Account Management' }); };
```

Express.js has `app.get`, `app.post`, `app.put`, `app.delete`, but for the most part you will only use the first two HTTP verbs, unless you are building a RESTful API. If you just want to display a page, then use `GET`, if you are submitting a form, sending a file then use `POST`.

Here is a typical workflow for adding new routes to your application. Let's say we are building a page that lists all books from database.

**Step 1.** Start by defining a route.

```
app.get('/books', bookController.getBooks);
```

* * *

**Note:** As of Express 4.x you can define you routes like so:

```
app.route('/books') .get(bookController.getBooks) .post(bookController.createBooks) .put(bookController.updateBooks) .delete(bookController.deleteBooks)
```

And here is how a route would look if it required an _authentication_ and an _authorization_ middleware:

```
app.route('/api/twitter') .all(passportConfig.isAuthenticated) .all(passportConfig.isAuthorized) .get(apiController.getTwitter) .post(apiController.postTwitter)
```

Use whichever style that makes sense to you. Either one is acceptable. I really think that chaining HTTP verbs on `app.route` is very clean and elegant approach, but on the other hand I can no longer see all my routes at a glance when you have one route per line.

**Step 2.** Create a new schema and a model `Book.js` inside the _models_ directory.

```
const mongoose \= require('mongoose'); const bookSchema \= new mongoose.Schema({ name: String }); const Book \= mongoose.model('Book', bookSchema); module.exports \= Book;
```

**Step 3.** Create a new controller file called `book.js` inside the _controllers_ directory.

```
/\*\*  \* GET /books  \* List all books.  \*/ const Book \= require('../models/Book.js'); exports.getBooks \= (req, res) \=> { Book.find((err, docs) \=> { res.render('books', { books: docs }); }); };
```

**Step 4.** Import that controller in `app.js`.

```
const bookController \= require('./controllers/book');
```

**Step 5.** Create `books.pug` template.

```
extends layout block content .page-header h3 All Books ul for book in books li\= book.name
```

That's it! I will say that you could have combined Step 1, 2, 3 as following:

```
app.get('/books',(req, res) \=> { Book.find((err, docs) \=> { res.render('books', { books: docs }); }); });
```

Sure, it's simpler, but as soon as you pass 1000 lines of code in `app.js` it becomes a little difficult to navigate the file. I mean, the whole point of this boilerplate project was to separate concerns, so you could work with your teammates without running into _MERGE CONFLICTS_. Imagine you have 4 developers working on a single `app.js`, I promise you it won't be fun resolving merge conflicts all the time. If you are the only developer then it's fine. But as I said, once it gets up to a certain LoC size, it becomes difficult to maintain everything in a single file.

That's all there is to it. Express.js is super simple to use. Most of the time you will be dealing with other APIs to do the real work: [Mongoose](http://mongoosejs.com/docs/guide.html) for querying database, socket.io for sending and receiving messages over websockets, sending emails via [Nodemailer](http://nodemailer.com/), form validation using [express-validator](https://github.com/ctavan/express-validator) library, parsing websites using [Cheerio](https://github.com/cheeriojs/cheerio), and etc.

* * *

[](https://github.com/mayeaux/nodetube#license)License
------------------------------------------------------

The MIT License (MIT)

Copyright (c) 2014-2016 Anthony Mayfield

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

  
  
from Hacker News https://github.com/mayeaux/nodetube