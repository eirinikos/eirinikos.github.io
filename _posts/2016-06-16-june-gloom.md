---
layout: post
title: June gloom
date: 2016-06-16
homebrew: true
---

![june gloom]({{site.github.url}}/images/2016-06/june-gloom.png)
<span class="caption">The view from home, on a late spring morning and on a late spring afternoon</span>

Nothing much to report from the past couple weeks other than that the [California primary election](https://en.wikipedia.org/wiki/California_Democratic_primary,_2016) happened, as did [_**yet another horrible mass shooting**_ in Florida](https://en.wikipedia.org/wiki/2016_Orlando_nightclub_shooting). And May Gray passed the torch to [June Gloom](https://en.wikipedia.org/wiki/June_Gloom). Today brought the first cloudless morning in a long time! I'd somewhat fallen off the exercise wagon since beginning this internship, but this week I've attempted to climb back aboard (huffing and puffing). A lot of hours have been spent indoors, hunched over and peering at code and occasionally typing code.

This post and the next few posts will give an overview of the first sets of Homebrew integration tests I've worked on so far. I figured I'd start with some relatively low-hanging fruit and work on testing commands that are primarily used to output text to the shell (or, whose functions as writ in code are similarly easy for me to grasp).

First, <span style="background-color:#ffdb4d"><strong><code>brew home</code></strong></span>.

<a href="https://github.com/Homebrew/brew/pull/305">My first pull request for the main Homebrew repository</a> updated the test for the **`home`** command, which opens [Homebrew's homepage](http://brew.sh/) -- or a formula's homepage -- in a web browser. There was already test coverage in place to ensure that **`brew home`** would open Homebrew's homepage (i.e., <span style="background-color:#b3ffb3">lines 9-10, in green, in the **`cmd/home.rb`** screenshot below</span>). So I [added some lines](https://github.com/Homebrew/brew/pull/305/files) that would ensure the same function for a formula's homepage, or for multiple formula homepages (<span style="background-color:#ffcccc">line 12 in the screenshot below</span>). For example, **`brew home aften`** opens the homepage for the <strong><a href="http://aften.sourceforge.net/">aften</a></strong> formula, and **`brew home aften sox`** opens the homepages for both **aften** and <strong><a href="http://sox.sourceforge.net/">sox</a></strong>.

![simplecov-home]({{site.github.url}}/images/2016-06/simplecov-home-before.png)

<span class="caption">The test coverage for <code><a href="https://github.com/Homebrew/brew/blob/master/Library/Homebrew/cmd/home.rb">brew home</a></code> -- at 80%, until recently.</span>

The updated test creates a test formula file in the <a href="https://github.com/Homebrew/homebrew-core">homebrew-core tap</a> and in the assertion it does something amazing -- amazing to me, at least.

{% highlight ruby %}
formula_file = CoreTap.new.formula_dir/"testball.rb"
formula_file.write <<-EOS.undent
  class Testball < Formula
    desc "Some test"
    homepage "https://example.com/testball"
    url "https://example.com/testball-0.1.tar.gz"
  end
EOS
{% endhighlight %}

By way of a helper method, **`cmd`** (which runs a **`brew`** command in a separate process and retrieves its output) this line not only runs **`brew home testball`**, it also sets the **`HOMEBREW_BROWSER`** environment variable equal to [**`echo`**](https://en.wikipedia.org/wiki/Echo_(command)):

{% highlight ruby %}
cmd("home", "testball", {"HOMEBREW_BROWSER" => "echo"})
{% endhighlight %}

Which is to say that instead of opening a web browser and navigating to the given homepage, this test temporarily fools your system into thinking that your browser is the equivalent of the **`/bin/echo`** command. **`echo`** simply parrots or *echoes* the string of text it's fed as an argument, which is "**`https://example.com/testball`**" in the test.

Why is the **`HOMEBREW_BROWSER`** environment variable is involved here? **`home.rb`** employs the **`exec_browser`** method to determine which application to use as a web browser, and **`exec_browser`** first checks if **`HOMEBREW_BROWSER`** has been set to point to a particular application. If it has, then **`brew home`** uses that application. If it hasn't, then **`exec_browser`** keeps checking other default settings until it finds a valid application (if it finds one at all).

In the end, the test asserts that both **`Formula["testball"].homepage`** and **`cmd("home", "testball", {"HOMEBREW_BROWSER" => "echo"})`** output the same string.

{% highlight ruby %}
assert_equal Formula["testball"].homepage,
             cmd("home", "testball", {"HOMEBREW_BROWSER" => "echo"})
{% endhighlight %}

As mentioned in my [previous post]({% post_url 2016-06-02-summer-begins %}), I forgot to include the crucial **`require "formula"`** statement at the beginning of the file when I updated my pull request; this was the first of several mistakes I've made so far. The [**`formula.rb`** file](https://github.com/Homebrew/brew/blob/master/Library/Homebrew/formula.rb) is needed because [this line](https://github.com/Homebrew/brew/pull/305/files#diff-9d56e3f04f25344c5ca3000c8ec67ca3R565) makes use of a **`Formula`** class method, which is defined only in that file. This mistake was soon fixed by one of the Homebrew maintainers, [Martin](https://github.com/uniqmartin).

I've since submitted pull requests to add test coverage for <span style="background-color:#ffdb4d"><strong><code>brew desc</code></strong></span>, <span style="background-color:#ffdb4d"><strong><code>brew log</code></strong></span>, and <span style="background-color:#ffdb4d"><strong><code>brew search</code></strong></span>, plus one more to [refactor the integration tests file](https://github.com/Homebrew/brew/pull/370) so that the creation of test formula files is consolidated in one or two methods. More later!
