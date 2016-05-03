---
layout: post
title: What's Homebrew?
date: 2016-05-02
---

![Homebrew](https://avatars0.githubusercontent.com/u/1503512?v=3&s=400)

[The missing package manager for OS X !...](http://brew.sh)

This post was meant to be a digestible e-mail to my significant other. I hadn't (and still haven't) managed to give a good verbal explanation of what Homebrew does. I *had* bookmarked a couple of Wikipedia pages over the weekend, with the intent to get a better understanding of Homebrew in particular and package managers in general. My explanation draws directly from the wording in the linked Wikipedia and Github pages, i.e., info that's more or less available to laypeople. When I realized it was going to take more than three fleshy paragraphs to develop a satisying explanation, this became a blog post.

**If your eyes start to glaze over while you read this post, just fast-forward to the last couple paragraphs to see why Homebrew is delightful from a beer-lover's point-of-view!!**

As you can see from this brief [Wikipedia article](https://en.wikipedia.org/wiki/Homebrew_(package_management_software)), Homebrew is a free and [open-source](https://en.wikipedia.org/wiki/Open-source_software) [software package management](https://en.wikipedia.org/wiki/Package_manager) system. It addresses the installation of software on Mac OS X and is run entirely on the [command-line interface (CLI)](https://en.wikipedia.org/wiki/Command-line_interface). In this [list of package management systems](https://en.wikipedia.org/wiki/List_of_software_package_management_systems), you'll see Homebrew listed twice -- once in the list of systems that distribute binary packages (alongside Apple's App Store), and also in the list of systems that distribute the source code of their apps.

With over 5,600 contributors at the moment, Homebrew is one of the most popular open-source projects on [Github](https://github.com). It has spawned several sub-projects, notably [Homebrew Cask](https://caskroom.github.io). Cask extends Homebrew to perform CLI installation for Mac [GUI](https://en.wikipedia.org/wiki/Graphical_user_interface) applications (e.g., Google Chrome). Cask currently has almost 2,500 Github contributors. Unlike Cask (and with a few exceptions), [Homebrew itself is used to install and build command line tools or libraries](https://github.com/Homebrew/brew/blob/master/share/doc/homebrew/Acceptable-Formulae.md#stuff-that-builds-a-app), not GUI applications. (Amazingly, though, someone has made a GUI app for Homebrew -- called [Cakebrew](https://www.cakebrew.com/)!)

As for how Homebrew is implemented -- Homebrew is written in Ruby and is meant to be compatible with the version of Ruby that comes installed with OS X (e.g., [Yosemite and Mavericks ship with Ruby 2.0](https://www.ruby-lang.org/en/documentation/installation/#homebrew)). It's installed in the `/usr/local` directory and consists of a [Git](https://en.wikipedia.org/wiki/Git_(software)) repo. Thus, updating Homebrew is effectively similar to how a user would update a local Git repository on their computer by synching with its source repository on Github.

As for how Homebrew installs and builds software packages -- it makes use of Ruby scripts that are constructed with [Homebrew's domain-specific language (DSL)](http://www.rubydoc.info/github/Homebrew/brew/master), i.e., a mini-language or programming library written especially for use within Homebrew. There are thousands of these scripts in Homebrew, one for each software package. These scripts are responsible for managing dependencies (i.e., other software packages that need to be installed beforehand), as well as downloading source files, and configuring and compiling software.

As seen earlier with Cask, **Homebrew incorporates lots of fun, beer-related terminology!** Homebrew's scripts are currently known as "formulae" in local parlance (they were once known as "recipes"). [Other terms include "keg", "cellar", "tap", and "bottle".](https://github.com/Homebrew/brew/blob/master/share/doc/homebrew/Formula-Cookbook.md#homebrew-terminology) (A "bottle" is a binary package that provides pre-built formulae with default options -- rather like how bottled beer packages the beverage in conveniently-contained servings.)

In the screenshot below, you'll see the command-line output resulting from running `brew install` [youtube-dl](https://rg3.github.io/youtube-dl/). After downloading and "pouring" the [tarball](https://en.wikipedia.org/wiki/Tar_(computing)#File_format) for Yosemite, voilà! Homebrew displays a cute beer mug emoji and confirms the files that were written to the Cellar (itself housed in `/usr/local`). Beer is [everywhere](http://braumeister.org/) in Homebrew! Every now and then I encounter [a reference I don't understand right away](https://github.com/Homebrew/homebrew-head-only), but I love it nonetheless.

![brew install]({{site.github.url}}/images/2016-05/brew-mug.png)

Cheers!