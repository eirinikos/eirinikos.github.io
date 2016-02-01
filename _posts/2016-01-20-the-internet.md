---
layout: post
title: THE INTERNET
date: 2016-01-20
---

![]({{site.github.url}}/images/2016-01/the-internet.png)

<figcaption class="caption">Image is from<a href="http://webmastersolusindo.com/wp-content/uploads/2014/12/internet.png"> here</a>; the internet is just the earth's wig.</figcaption>

As promised to myself by myself, I've begun reading about and taking notes on HTTP and its request-response protocol, with IP addresses as analogues to phone numbers, and port numbers as analogues to company phone extensions. Many thanks to Launch School né [Tea Leaf](http://gotealeaf.com)) for making <ins><a href="https://launchschool.com/books/http">Introduction to HTTP</a></ins> available via their Open Book Shelf. My notes are directly attributable to the content from their book.

To liven things up a bit, here's a gratuitous image of a bright red telephone:

![]({{site.github.url}}/images/2016-01/red_telephone.jpg)
<figcaption class="caption">Image is from <a href="https://www.flickr.com/photos/curtisperry/322049960">here</a>.</figcaption>

DNS databases, which are distributed across DNS servers, translate URLs to IP addresses and map browser requests to remote servers. If a particular DNS server doesn't contain a requested domain name, that server routes the request to another DNS server up the hierarchy and the address is eventually located in the DNS database on a particular DNS server.

When a client (web browser) makes a request, it's simply sending some text to an IP address. Because the client and the receiving server have a protocol in the form of HTTP, the server can deconstruct the request, understand its components, and return a response to the client. The client will then process the response strings into content that can be understood by the end user.

![]({{site.github.url}}/images/2016-01/internet_tea_leaf.png)
<figcaption class="caption">Image is from <a href="https://launchschool.com/books/http">here</a>.</figcaption>

HTTP is *stateless* - it's designed in such a way that each request-response pair is completely independent of the previous one. In the context of HTTP, statelessness refers to the fact the server doesn't need to hang on to information, or *state*, between requests. Web applications may simulate a *stateful* experience, but in the end, the web is still entirely built on HTTP, a stateless protocol. This is apparently what makes the web so resilient, distributed, and hard to control, as well as what makes it so difficult to secure and build on.

*State, statelessness*, and *statefulness* - so existentialist!