---
layout: post
title: Revisiting HTTP
date: 2016-09-03
---

I'm finally revisiting, reviewing, and taking notes from this <ins><a href="https://launchschool.com/books/http">Introduction to HTTP</a></ins>, so this post will have some overlap with [this previous one]({% post_url 2016-01-20-the-internet %}), as well as [this one]({% post_url 2016-01-24-urls-man %}).

### An Overview

HTTP is known as a **request-response protocol**, wherein the client (often, but not always, a web browser) sends a **request** to a server and waits for a **response**. The server then sends the client a collection of resources (CSS, HTML, Javascript, videos, images, other assets).

Such a transaction might proceed like this:

- you enter a URL into your web browser
- your browser sends the request (some text) to your device's network interface
- the request goes over the internet where a search for the URL (and associated IP address) begins
- eventually, the server accepts the request, parses it, and sends a response over the internet back to your network interface, which hands it to your browser
- your browser processes the HTTP response strings and displays them in the form of a web page

HTTP is a **stateless** protocol in that each **request-response pair** is completely independent of the previous one: the server doesn't need to hang on to information (i.e., **state**) between requests. HTTP is **stateless**, but a stateful experience can be (and often is) simulated by employing various web development frameworks.

The Domain Naming System (**DNS**) is a distributed database which translates URL names to their respective IP addresses and maps the request to a remote server. DNS databases are stored on a worldwide network of hierarchically organized **DNS servers**; no single DNS server stores the entire database.

### What is a URL?

<table>
  <thead>
  	<tr>
  	  <th><strong>URL components</strong></th>
  	  <th>Description</th>
  	</tr>
  </thead>
  <tbody>
  	<tr>
  	  <td><strong>scheme</strong></td>
  	  <td> Tells the client how to access the resource (<strong>http</strong>, <strong>ftp</strong>, <strong>mailto</strong>, <strong>git</strong>)</td>
  	</tr>
  	<tr>
  	  <td><strong>host</strong></td>
  	  <td>Tells the client where the resource is hosted or located</td>
  	</tr>
  	<tr>
  	  <td><strong>path</strong></td>
  	  <td>Shows what local resource is being requested</td>
  	</tr>
  	<tr>
  	  <td><strong>port number</strong></td>
  	  <td>Is used by the host to listen to HTTP requests</td>
  	 </tr>
  </tbody>
</table>

The default port number for HTTP is **80**, and although it's not always specified, it's assumed to be part of every URL. To use anything other than the default, it has to be specified in the URL.

A query string or parameter within the URL usually contains some form of data to be sent to the server. A simple URL with query strings might look like: **http://www.example.com?search=ruby&results=10**

<table>
  <thead>
  	<tr>
  	  <th><strong>Query string component</strong></th>
  	  <th>Description</th>
  	</tr>
  </thead>
  <tbody>
  	<tr>
  	  <td><strong>?</strong></td>
  	  <td>A reserved character that marks the start of the query string</td>
  	</tr>
  	<tr>
  	  <td><strong>search=ruby</strong></td>
  	  <td>A parameter name/value pair</td>
  	</tr>
  	<tr>
  	  <td><strong>&</strong></td>
  	  <td>A reserved character that's used to separate multiple parameters</td>
  	</tr>
  </tbody>
</table>
