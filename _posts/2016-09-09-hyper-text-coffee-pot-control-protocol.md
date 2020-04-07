---
title: 'Hyper Text Coffee Pot Control Protocol'
date: 2020-01-24T04:35:00+01:00
draft: false
---

April Fool's joke about facetious communications protocol

The **Hyper Text Coffee Pot Control Protocol** (**HTCPCP**) is a facetious [communication protocol](https://en.wikipedia.org/wiki/Communication_protocol "Communication protocol") for controlling, monitoring, and diagnosing [coffee pots](https://en.wikipedia.org/wiki/Coffee_pot "Coffee pot"). It is specified in [RFC 2324](https://tools.ietf.org/html/rfc2324), published on 1 April 1998 as an [April Fools' Day RFC](https://en.wikipedia.org/wiki/April_Fools%27_Day_Request_for_Comments "April Fools' Day Request for Comments"),[\[2\]](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_note-2) as part of an [April Fools prank](https://en.wikipedia.org/wiki/April_Fools%27_Day_Request_for_Comments "April Fools' Day Request for Comments").[\[3\]](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_note-3) An extension, HTCPCP-TEA, was published as [RFC 7168](https://tools.ietf.org/html/rfc7168) on 1 April 2014[\[4\]](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_note-rfc7168-4) to support brewing teas, which is also an April Fools' Day RFC.

Protocol
--------

[RFC 2324](https://tools.ietf.org/html/rfc2324) was written by Larry Masinter, who describes it as a satire, saying "This has a serious purpose – it identifies many of the ways in which [HTTP](https://en.wikipedia.org/wiki/HTTP "HTTP") has been extended inappropriately."[\[5\]](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_note-5) The wording of the protocol made it clear that it was not entirely serious; for example, it notes that "there is a strong, dark, rich requirement for a protocol designed [espressoly](https://en.wikipedia.org/wiki/Espresso "Espresso") \[sic\] for the brewing of coffee".

Despite the joking nature of its origins, or perhaps because of it, the protocol has remained as a minor presence online. The editor [Emacs](https://en.wikipedia.org/wiki/Emacs "Emacs") includes a fully functional client side implementation of it,[\[6\]](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_note-6) and a number of bug reports exist complaining about [Mozilla](https://en.wikipedia.org/wiki/Mozilla "Mozilla")'s lack of support for the protocol.[\[7\]](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_note-7) Ten years after the publication of HTCPCP, the _Web-Controlled Coffee Consortium_ (_WC3_) published a first draft of "HTCPCP Vocabulary in [RDF](https://en.wikipedia.org/wiki/Resource_Description_Framework "Resource Description Framework")"[\[8\]](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_note-8) in parody of the [World Wide Web Consortium](https://en.wikipedia.org/wiki/World_Wide_Web_Consortium "World Wide Web Consortium")'s (W3C) "HTTP Vocabulary in RDF".[\[9\]](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_note-9)

On April 1, 2014, [RFC 7168](https://tools.ietf.org/html/rfc7168) extended HTCPCP to fully handle teapots.[\[4\]](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_note-rfc7168-4)

Commands and replies
--------------------

HTCPCP is an extension of [HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol "Hypertext Transfer Protocol"). HTCPCP requests are identified with the [Uniform Resource Identifier](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier "Uniform Resource Identifier") (URI) scheme `coffee` (or the corresponding word in any other of the 29 listed languages) and contain several additions to the HTTP methods:

`BREW` or `POST`

Causes the HTCPCP server to brew [coffee](https://en.wikipedia.org/wiki/Coffee "Coffee"). Using POST for this purpose is deprecated. A new [HTTP request header field](https://en.wikipedia.org/wiki/HTTP_header#Requests "HTTP header") "Accept-Additions" is proposed, supporting optional additions including Cream, Whole-milk, Vanilla, Raspberry, Whisky, Aquavit, etc.

`GET`

"Retrieves" coffee from the HTCPCP server.

`PROPFIND`

Returns [metadata](https://en.wikipedia.org/wiki/Metadata "Metadata") about the coffee.

`WHEN`

[Says "when"](https://en.wiktionary.org/wiki/say_when "wikt:say when"), causing the HTCPCP server to stop pouring [milk](https://en.wikipedia.org/wiki/Milk "Milk") into the coffee (if applicable).

It also defines two [error responses](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes#4xx_Client_Error "List of HTTP status codes"):

`406 Not Acceptable`

The HTCPCP server is unable to provide the requested addition for some reason; the response should indicate a list of available additions. The RFC observes that "In practice, most automated coffee pots cannot currently provide additions."

`418 I'm a teapot`

The HTCPCP server is a [teapot](https://en.wikipedia.org/wiki/Teapot "Teapot"); the resulting entity body "may be short and stout" (a reference to the song "[I'm a Little Teapot](https://en.wikipedia.org/wiki/I%27m_a_Little_Teapot "I'm a Little Teapot")"). Demonstrations of this behaviour exist.[\[1\]](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_note-JR-1)[\[10\]](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_note-10)

Save 418 movement
-----------------

On 5 August 2017, [Mark Nottingham](https://en.wikipedia.org/wiki/Mark_Nottingham "Mark Nottingham"), chairman of the [IETF](https://en.wikipedia.org/wiki/IETF "IETF") HTTPBIS Working Group, called for the removal of status code 418 "I'm a teapot" from the [Node.js](https://en.wikipedia.org/wiki/Node.js "Node.js") platform, a code implemented in reference to the original 418 "I'm a teapot" established in Hyper Text Coffee Pot Control Protocol.[\[11\]](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_note-11) On 6 August 2017, Nottingham requested that references to 418 "I'm a teapot" be removed from the programming language [Go](https://en.wikipedia.org/wiki/Go_(programming_language) "Go (programming language)")[\[12\]](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_note-12) and subsequently from [Python](https://en.wikipedia.org/wiki/Python_(programming_language) "Python (programming language)")'s [Requests](https://en.wikipedia.org/wiki/Requests_(software) "Requests (software)")[\[13\]](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_note-13) and [ASP.NET](https://en.wikipedia.org/wiki/ASP.NET "ASP.NET")'s HttpAbstractions library[\[14\]](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_note-14) as well.

In response, 15 year old developer Shane Brunswick created a website, save418.com,[\[15\]](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_note-15) and established the "Save 418 Movement", asserting that references to 418 "I'm a teapot" in different projects serve as "a reminder that the underlying processes of computers are still made by humans". Brunswick's site went viral in the hours following its publishing, garnering thousands of upvotes on the social platform [Reddit](https://en.wikipedia.org/wiki/Reddit "Reddit"),[\[16\]](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_note-16) and causing the mass adoption of the "#save418" [Twitter](https://en.wikipedia.org/wiki/Twitter "Twitter") hashtag he introduced on his site. Heeding the public outcry, Node.js, Go, Python's Requests, and ASP.NET's HttpAbstractions library decided against removing 418 "I'm a teapot" from their respective projects. The unanimous support from the aforementioned projects and the general public prompted Nottingham to begin the process of having 418 marked as a reserved HTTP status code,[\[17\]](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_note-17) ensuring that 418 will not be replaced by an official status code for the foreseeable future.

See also
--------

References
----------

1.  ^ [_**a**_](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_ref-JR_1-0) [_**b**_](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_ref-JR_1-1) Reddington, Joseph, [_Illustrated implementation of Error 418_](https://web.archive.org/web/20150906071854/http://joereddington.com/projects/418-error-code-teapot/), archived from [the original](http://joereddington.com/projects/418-error-code-teapot/) on 2015-09-06, retrieved 2014-10-18
2.  **[^](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_ref-2)** "Request for Comments 2324", [_Network Working Group_](http://tools.ietf.org/html/rfc2324), [IETF](https://en.wikipedia.org/wiki/Internet_Engineering_Task_Force "Internet Engineering Task Force")
3.  **[^](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_ref-3)** DeNardis, Laura (30 September 2009). [_Protocol Politics: The Globalization of Internet Governance_](https://books.google.com/books?id=Secqz0XQJIsC&pg=PA27). MIT Press. pp. 27ff. [ISBN](https://en.wikipedia.org/wiki/International_Standard_Book_Number "International Standard Book Number") [978-0-262-04257-4](https://en.wikipedia.org/wiki/Special:BookSources/978-0-262-04257-4 "Special:BookSources/978-0-262-04257-4"). Retrieved 8 May 2012.
4.  ^ [_**a**_](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_ref-rfc7168_4-0) [_**b**_](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_ref-rfc7168_4-1) "Request for Comments 7168", [_The Hyper Text Coffee Pot Control Protocol for Tea Efflux Appliances (HTCPCP-TEA)_](https://tools.ietf.org/html/rfc7168), [IETF](https://en.wikipedia.org/wiki/Internet_Engineering_Task_Force "Internet Engineering Task Force")
5.  **[^](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_ref-5)** Larry Masinter. ["IETF RFCs"](https://web.archive.org/web/20130327202242/http://larry.masinter.net/). Archived from [the original](http://larry.masinter.net) on 2013-03-27.
6.  **[^](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_ref-6)** "Emacs extension: coffee.el", [_Emarsden_](http://emarsden.chez.com/downloads/), Chez.
7.  **[^](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_ref-7)** "Bug 46647 – (coffeehandler) HTCPCP not supported (RFC2324)", [_Bugzilla_](https://bugzilla.mozilla.org/show_bug.cgi?id=46647), Mozilla
8.  **[^](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_ref-8)** [_HTCPCP Vocabulary in RDF – WC3 RFC Draft_](https://cstrobbe.github.io/WC3/TR/2008/RFC-htcpcp-in-rdf-20080401/), Chief Arabica (Web-Controlled Coffee Consortium), 1 April 2008, retrieved 27 April 2017
9.  **[^](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_ref-9)** Koch, Johannes (ed.), [_HTTP Vocabulary in RDF_](http://www.w3.org/TR/HTTP-in-RDF/), et al, [W3](https://en.wikipedia.org/wiki/World_Wide_Web_Consortium "World Wide Web Consortium"), retrieved 17 August 2009
10.  **[^](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_ref-10)** ["A Goblin Teasmade teamaker with an implementation of Error 418"](https://web.archive.org/web/20141206053112/http://www.qdh.org.uk/wordpress/?p=546). Archived from [the original](http://www.qdh.org.uk/wordpress/?p=546) on 2014-12-06. Retrieved 2014-07-26.
11.  **[^](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_ref-11)** [Mark Nottingham](https://en.wikipedia.org/wiki/Mark_Nottingham "Mark Nottingham"). ["418 I'm A Teapot #14644"](https://github.com/nodejs/node/issues/14644#issue-248218948).
12.  **[^](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_ref-12)** Mark Nottingham. ["net/http: remove support for status code 418 I'm a Teapot"](https://github.com/golang/go/issues/21326#issue-248234750).
13.  **[^](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_ref-13)** Mark Nottingham. ["418 418 I'm a Teapot #4238"](https://github.com/requests/requests/issues/4238#issue-249497185).
14.  **[^](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_ref-14)** Mark Nottingham. ["418 I'm a Teapot #915"](https://github.com/aspnet/HttpAbstractions/issues/915).
15.  **[^](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_ref-15)** Shane Brunswick. ["The Save 418 Movement – We are the teapots"](http://save418.com).
16.  **[^](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_ref-16)** ["HTTP Error Code 418 I'm a Teapot is about to be removed from Node. We've gotta do something. \[x-post /r/webdev\]"](https://www.reddit.com/r/programming/comments/6sxea0/http_error_code_418_im_a_teapot_is_about_to_be/).
17.  **[^](https://en.wikipedia.org/wiki/Hyper_Text_Coffee_Pot_Control_Protocol#cite_ref-17)** Mark Nottingham. ["Reserving 418"](https://lists.w3.org/Archives/Public/ietf-http-wg/2017JulSep/0332.html).

External links
--------------

<img src="https://en.wikipedia.org/wiki/Special:CentralAutoLogin/start?type=1x1" alt="" title="" />

  
  
from Hacker News https://ift.tt/Nwj3QX