---
layout: post
title: I don't care!
date: 2016-02-15
---

![Roy Lichtenstein's Drowning Girl]({{site.github.url}}/images/2016-02/Roy_Lichtenstein_Drowning_Girl.jpg)

<span class="caption">Roy Lichtenstein's <a href="https://en.wikipedia.org/wiki/Drowning_Girl"><i>Drowning Girl</i></a></span>

One of the things I've been doing over the past week is explore Odin Project's [Web Development 101 curriculum](http://www.theodinproject.com/web-development-101). It's good stuff! I particularly enjoyed reading the [Bastards Book](http://ruby.bastardsbook.com/) chapters on [web scraping](http://ruby.bastardsbook.com/chapters/web-scraping/) and [web inspecting](http://ruby.bastardsbook.com/chapters/web-inspecting-html/), among other things.

Following Odin's chapter [on how the web works](http://www.theodinproject.com/web-development-101/how-does-the-web-work?ref=lc-pb) is a section that [delves into the command line](http://www.theodinproject.com/web-development-101/how-does-your-computer-work). I just finished the first item on the "syllabus" for this section ([Codecademy's command line tutorial](https://www.codecademy.com/learn/learn-the-command-line)) and it's given me a new layer of understanding, yay. Thought I'd record some of my notes here before I jump back and flail around in the ocean of Things I Don't Know.

---

Codecademy's tutorial first acquainted me with the concept of re-routing standard input, standard output, and standard error.

This nugget redirects `stdout` to a file:
<p style="padding-left: 30px;"><strong>$ echo "zane, zane, zane" > all_the_madmen.txt</strong></p>


This nugget redirects the `stdout` of the `cat` command into the text file on the right (overwriting the original contents of the latter file):
<p style="padding-left: 30px;"><strong>$ cat all_the_madmen.txt > man_who_sold_the_world.txt</strong></p>

This nugget appends the `stdout` of the `cat` command to the text file on the right (without overwriting any original content):
<p style="padding-left: 30px;"><strong>$ cat black_country_rock.txt >> man_who_sold_the_world.txt</strong></p>

This nugget takes the `stdin` from the file on the right and inputs it into the program on the left; so, `after_all.txt` is the `stdin` for the `cat` command, and the `stdout` appears in the terminal:

<p style="padding-left: 30px;"><strong>$ cat < after_all.txt</strong></p>

This nugget below pipes the `stdout` of the `cat` command as `stdin` to the command on the right, `wc` (which outputs the number of lines, words, and characters  in the text file). Multiple `|`s can be chained together.
<p style="padding-left: 30px;"><strong>$ cat running_gun_blues.txt | wc</strong></p>
---

More in a later post... someday.