---
layout: post
title: What is Homebrew?
date: 2016-05-13
---

![Homebrew](https://avatars0.githubusercontent.com/u/1503512?v=3&s=400)

[The missing package manager for OS X !...](http://brew.sh)

This post was meant to be a digestible e-mail to my significant other. I hadn't (and still haven't) managed to give a good verbal explanation of what Homebrew does. I *had* bookmarked a couple of Wikipedia pages a few weekends ago, with the intent of getting a better understanding of Homebrew in particular and package managers in general. My explanation draws directly from the wording in the linked Wikipedia and Github pages, i.e., info that's more or less available to laypeople. When I realized it was going to take more than three fleshy paragraphs to develop a satisying explanation, this became a blog post.

**If your eyes start to glaze over while you read this post, just fast-forward to the last couple paragraphs to see why Homebrew is delightful from a beer-lover's point-of-view!!**

As you can see from this brief [Wikipedia article](https://en.wikipedia.org/wiki/Homebrew_(package_management_software)), Homebrew is a free and [open-source](https://en.wikipedia.org/wiki/Open-source_software) [software package management](https://en.wikipedia.org/wiki/Package_manager) system. It's run entirely on the [command-line interface (CLI)](https://en.wikipedia.org/wiki/Command-line_interface), and it installs Mac OS X software with a single line of text! In this [list of package management systems](https://en.wikipedia.org/wiki/List_of_software_package_management_systems), you'll see Homebrew listed twice -- once in the list of systems that distribute binary packages (alongside Apple's App Store), and also in the list of systems that distribute the source code of their apps.

With over 5,600 contributors at the moment, Homebrew is one of the most popular open-source projects on [Github](https://github.com). It has spawned several sub-projects, notably [Homebrew Cask](https://caskroom.github.io). Cask extends Homebrew to perform command-line installation for Mac [GUI](https://en.wikipedia.org/wiki/Graphical_user_interface) applications (e.g., Google Chrome, Ableton Live, or Vox) -- also with a single line of text! Many users find this much more convenient than going through the process of navigating to a software program's download page, downloading a file, and then dragging the icon to the Applications folder.

Cask currently has more than 2,500 Github contributors. Unlike Cask (and with a few exceptions), [Homebrew itself is used to install and build command line tools or libraries](https://github.com/Homebrew/brew/blob/master/share/doc/homebrew/Acceptable-Formulae.md#stuff-that-builds-a-app), not GUI applications. (Amazingly, though, someone has made a GUI app for Homebrew -- called [Cakebrew](https://www.cakebrew.com/)!)

As for how Homebrew is implemented -- Homebrew is written in Ruby and is meant to be compatible with the version of Ruby that comes installed with OS X (e.g., [Yosemite and Mavericks ship with Ruby 2.0](https://www.ruby-lang.org/en/documentation/installation/#homebrew)). It gets installed in the `/usr/local` directory on your computer and consists of a version-controlled [Git](https://en.wikipedia.org/wiki/Git_(software)) repo. Thus, updating Homebrew on your computer is effectively similar to how you would update a local Git repository on your computer by synching with its source repository on Github.

As for how Homebrew installs and builds software packages -- it makes use of Ruby scripts that are constructed with [Homebrew's domain-specific language (DSL)](http://www.rubydoc.info/github/Homebrew/brew/master), i.e., a mini-language or programming library written especially for use within Homebrew. There are thousands of these scripts in Homebrew, one for each software package. These scripts are responsible for managing dependencies (i.e., other software packages that need to be installed beforehand), as well as downloading source files and configuring and compiling software.

As glimpsed earlier with Cask, **Homebrew incorporates lots of fun, beer-related [terminology](https://github.com/Homebrew/brew/blob/master/share/doc/homebrew/Formula-Cookbook.md#homebrew-terminology)!**

Here's a brief overview:

- The aforementioned scripts are currently known as **formulae** in local parlance (they were once known as *recipes*). **Formulae** are stored in **Taps**. A **formula** defines how to download, compile, and install a **keg**.
- A **keg** is an installed Homebrew package. **Kegs** are stored in the **Cellar**.
- The **Cellar** is a directory that stores all **kegs**. The **Cellar** itself is housed in `/usr/local`.
- A **Tap** is a directory or collection of stored **formulae**. Every **Tap** corresponds to a Github repo, whether it's the [core formula repo](https://github.com/Homebrew/homebrew-core) for Homebrew, or one of the many other [main taps](https://github.com/Homebrew/brew/blob/master/share/doc/homebrew/Interesting-Taps-%26-Branches.md) in Homebrew-land.
- As mentioned [here](https://en.wikipedia.org/wiki/Homebrew_(package_management_software)#Implementation), a **bottle** is a binary package that provides pre-built formulae with default options -- rather like how bottled beer packages the beverage in individually bottled servings. **Bottles** reside within **formula** files, though not every formula has a bottle (yet). More on **bottles** can be found [here](https://github.com/Homebrew/brew/blob/master/share/doc/homebrew/Bottles.md).

Here's a table showing where everything resides on your computer:

<table>
  <thead>
    <tr>
      <th><span class="red">Thing</span></th>
      <th><span class="red">Location on your computer</span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Homebrew!</strong></td>
      <td><code>/usr/local/Library/</code></td>
    </tr>
    <tr>
      <td><strong>Tap</strong></td>
      <td><code>/usr/local/Library/Taps/homebrew/homebrew-core</code></td>
    </tr>
    <tr>
      <td><strong>formula</strong></td>
      <td><code>/usr/local/Library/Taps/homebrew/homebrew-core/Formula/foo.rb</code></td>
    </tr>
    <tr>
      <td><strong>Cellar</strong></td>
      <td><code>/usr/local/Cellar/</code></td>
    </tr>
    <tr>
      <td><strong>keg</strong></td>
      <td><code>/usr/local/Cellar/foo/0.1</code></td>
    </tr>
  </tbody>  
</table>

In the screenshot below, you'll see the command-line output resulting from running `brew install` <a href="https://rg3.github.io/youtube-dl/"><code>youtube-dl</code></a>. After downloading and "pouring" the [tarball](https://en.wikipedia.org/wiki/Tar_(computing)#File_format) for OS X Yosemite, voilà! Homebrew displays a cute beer mug emoji and confirms the files that were written to the Cellar. `youtube-dl` is ready to be used, all thanks to a single line of command-line input!!

![brew install]({{site.github.url}}/images/2016-05/brew-install.png)

Beer is [everywhere](http://braumeister.org/) in Homebrew! Every now and then I encounter [a reference](https://github.com/Homebrew/homebrew-head-only) I don't understand, but I love it nonetheless. Something else I recently learned is the fact that [anyone can create their own Homebrew Tap!](http://formalfriday.club/2015/01/05/creating-your-own-homebrew-tap-and-formula.html) While Homebrew's main taps are restricted to select formulae, creating your own Tap and formulae is a nice way to distribute your own software to the Homebrew user community.

Cheers!