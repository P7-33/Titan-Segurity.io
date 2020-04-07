---
title: 'Web of Documents (2019)'
date: 2020-01-23T04:35:00+01:00
draft: false
---

In 1960, Ted Nelson envisioned a web of documents.

It was called [Xanadu](https://en.wikipedia.org/wiki/Project_Xanadu). It was a grand, holistic vision: of documents that, once published, are available basically forever; of bidirectional links that could glue together not just documents, but parts thereof; of managing copyright and royalties. It was complex. And it never really came to fruition.

But thirty-one years later, another web of documents took off. A much more modest undertaking than Xanadu, with a simple markup language, simple protocol to retrieve the documents, unidirectional, ever-rotting links, and not much else. The World Wide Web. It was prototyped by one man in a few months. And then its popularity exploded.

As the WWW spread, it grew features. Soon, it was not enough for the documents to contain just text: support for images was added. People wanted to customize the look of the documents, so HTML gained presentational markup abilities, eventually obsoleted by CSS. It was not enough to be able to view the menu of your local pizza store – people wanted to actually order a pizza: the need for sessions yielded cookies and non-idempotent HTTP methods. And people wanted the pages to be interactive, so they became scriptable.

All these features were good. They helped the Web meet actual needs. But having them has a significant consequence, one that is seldom realized:

We don’t have a Web of Documents anymore.

Let me pause at this point. I’ve been using the word “document” intuitively and vaguely so far, so let’s try to pinpoint it. I don’t have a precise definition in mind, but I’ll share some examples. A book is a document, to me. So is a picture, an illustrated text, a scientific paper, a MP3 song, or a video. By contrast, a page that lets you play Tetris isn’t. The essence of this distinction seems to be that documents have well-defined _content_ that does not change between viewings and does not depend on the state of the outside world. A document is stateless. It exists in and of itself; it is its own microcosm. It may be experienced interactively, but only insofar as it enables the experiencer to focus their attention on the part of their own choosing; the potential state of that interaction is external to the document, not part of itself.

Obviously, this is not very accurate: there are border cases. For example, does a film DVD with a menu qualify as a document? Or how about a choose-your-own-adventure book? Or a HTML page with links to other pages? On the surface, the latter does provide out-of-microcosm interactivity; but viewed from another angle, it is no different than putting a reference in a book. The browser just makes it very easy to go to a shelf and pick another book.

The distinction is there, and it’s important. And with it in mind, let me reiterate:

_We don’t have a Web of Documents anymore._

These days, the WWW is mostly a _Web of Applications_. An application is a broader concept: it can display text or images, but also lets you interact not just with itself, but with the world at large. And that’s all well and good, as long as you consciously intend these interactions to happen.

A document is safe. A book is safe: it will not explode in your hands, it will not magically alter its contents tomorrow, and if it happens to be illegal to possess, it will not call the authorities to denounce you. You can implicitly trust a document by virtue of it being one. An application, not so much.

I don’t want to name names, but it’s all too easy these days to follow a link to a news site, expecting an article, only to be greeted with “You have read N articles this month, please register to continue”. Definitely an application-y thing to say, not a document-y one. Now, the purveyors of such sites typically have legitimate economic interest in doing so—but once you sign up, they are able to record your actions, link them with your identity and build your shadow profile. This way, we have applications actively _masquerading_ as documents, when in reality they _do non-documenty things_ without telling you.

Legislation such as the EU Cookie Law and the GDPR (insofar as it requires disclosure of data processing) tries to remedy this. But the more I think about it, the more sense it makes to me to attack the problem closer to its root: to decomplect the notions of a document and an application; to keep the Web of Applications as it is, and to recreate a Web of Documents—either parallel to it, or as its sub-web.

To do this, we need to take a step back. (Or do a clean start and invent a whole new technology, but this is unlikely to succeed). Fortunately, we don’t have to travel all the way back to 1992, when the WWW was still a Web of Documents. (I still remember table-based layouts and spacer gifs, and the very memory makes me shudder). I think we can base the new Web of Documents on ol’ trusty HTTP (or, better, HTTPS), HTML and CSS as we know them today, with just three restraints:

1.  _No methods other than GET_ (and perhaps HEAD). POST, PUT, DELETE and friends just have no place in a world of documents. They are not idempotent; they potentially modify the state of the world, which documents should not be able to do. (I was also thinking “no forms”, but with #1 in place, it seems like an unnecessary refinement. After all, forms that translate to GET requests just facilitate creating URLs: a user could just as well have typed the resulting URL by hand.)
2.  _No scripts of any kind._ Not JavaScript, not WebAssembly. Not even to enrich a document, such as syntax-highlight the code snippets. This one may seem too stringent, but I think it’s better to err on the safe side, and it’s very easy to enforce.
3.  _No cookies._ Cookies by themselves aren’t interactive, but having them makes it all too easy to abuse the semantics of HTTP to recreate sessions, and on top of them reinvent the app-wheel and eventually forfeit the Web of Documents again.

Again, there may be corner cases that may have escaped me. But if a WWW page conforms to these restrictions, I think it may be pretty safe to call it a “document” and make it a part of the Web of Documents.

How do we achieve this? I don’t know, really. I don’t have a concrete proposal. Perhaps we could have dedicated browsers for the WoD; perhaps we could make existing browsers prominently advertise to the user whether they are browsing a document or an application. On top of all the technical decisions to make, there’ll be significant campaigning and lobbying needed if the idea is ever to take off.

I don’t dare dream that it ever will. My intent in this article is to provide food for thought. All I ask from you, my reader, is consideration and attention. And if you got this far, chances are I got them. I’m grateful.

This page is a document. Thank you for reading it.

  
  
from Hacker News https://ift.tt/30ZqhlL