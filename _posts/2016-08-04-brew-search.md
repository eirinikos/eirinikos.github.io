---
layout: post
title: brew search
date: 2016-08-04
homebrew: true
---

![brainless cherries]({{site.github.url}}/images/2016-08/brainless-cherries.jpg)
<span class="caption">My friend Stephen's photo of a beer that we shared, one that was gifted by another friend, Etay</span>

There are a number of websites that allow you to search for Homebrew packages, such as [Braumeister](http://braumeister.org/). With Homebrew itself, this is done with <span style="background-color:#ffdb4d"><strong><code>brew search</code></strong></span>:

- **`brew search`**
	- lists all locally available formula files (i.e., the ones that live in the Taps you've installed on your system).

- **`brew search <text>`**
	- returns a list of formula names that match the search term.
	- For example, **`brew search audio`** currently yields six search results: [**audiofile**](https://audiofile.68k.org/), [**dromeaudio**](https://github.com/joshb/dromeaudio/), [**portaudio**](http://www.portaudio.com/), [**pulseaudio**](https://wiki.freedesktop.org/www/Software/PulseAudio/), [**rt-audio**](https://www.music.mcgill.ca/~gary/rtaudio/), and [**switchaudio-osx**](https://github.com/deweller/switchaudio-osx/).

- **`brew search /text/`**
	- returns a list of formula names that match the [regular expression](https://en.wikipedia.org/wiki/Regular_expression).
	- **`brew search /.+audio.+/`** yields only **switchaudio-osx**.

- **`brew search --desc (<text>|/text/)`**
	- returns a list of formulae with descriptions matching the search term.
	- For example, **`brew search --desc music`** currently returns 27 formulae and their descriptions:
		- **[abcm2ps](http://moinejf.free.fr/): ABC music notation software**
		- **[abcmidi](http://www.ifdo.ca/~seymour/runabc/top.html): Converts abc music notation files to MIDI files**
		- **[chordii](http://www.vromans.org/johan/projects/Chordii/): Text file to music sheet converter**
		- and so on...

- **`brew search (`**
[**`--debian`**](https://packages.debian.org/)`|`[**`--fedora`**](https://admin.fedoraproject.org/pkgdb/packages/)`|`[**`--fink`**](http://pdb.finkproject.org/pdb/index.php?phpLang=en)`|`[**`--macports`**](https://www.macports.org/ports.php)`|`[**`--opensuse`**](https://software.opensuse.org/421/en)`|`[**`--ubuntu`**](http://packages.ubuntu.com/)**`)<text>`**
	- performs a search for the search term on the given package manager's website.
	- For example, **`brew search --ubuntu abc`** navigates your web browser to [this page](http://packages.ubuntu.com/search?keywords=abc&searchon=names&suite=all&section=all).

**`brew search`** didn't have an integration test when I found it. My new [test](https://github.com/Homebrew/brew/pull/356/files) boosted its coverage from 16% to 71% (yay), though [a big chunk](https://github.com/Homebrew/brew/blob/master/Library/Homebrew/cmd/search.rb#L64-L96) of its behavior [still remains untested](https://github.com/Homebrew/brew/pull/356#issuecomment-226395993) (boo). Oh well. In the new test, a formula file is written to the **`Homebrew/homebrew-core`** tap (in the exact same way that it's done in several other integration tests, e.g., for [**`brew home`**](https://github.com/Homebrew/brew/pull/305/files) and [**`brew log`**](https://github.com/Homebrew/brew/pull/333/files)). As is done in the [test](https://github.com/Homebrew/brew/pull/314/files) for **`brew desc`**, it makes the same assertions that the **`desc_cache.json`** file is created during the course of the test (this time, when the **`--desc`** flag is passed to **`brew search`**). It also asserts that **`testball`** (the test formula file) is a search result for these four calls to **`brew search`**:

	brew search
	brew search testball
	brew search homebrew/homebrew-core/testball
	brew search --desc Some test

It then proceeds to test [these lines](https://github.com/Homebrew/brew/blob/master/Library/Homebrew/cmd/search.rb#L29-L40) in **`cmd/search.rb`**. Like [**`brew home`**](https://github.com/Homebrew/brew/blob/master/Library/Homebrew/cmd/home.rb), **`brew search`** employs Homebrew's **`exec_browser`** [utility method](https://github.com/Homebrew/brew/blob/master/Library/Homebrew/utils.rb) to navigate your web browser to the desired path. An efficient, [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) way to test the six different flags is to create a single [hash](https://en.wikipedia.org/wiki/Hash_table) and then iterate over the hash to make the relevant assertions:

- the hash associates each flag with its URL.
- inside the **`each...do`** block, each call to the **`cmd`** helper method sets the **`HOMEBREW_BROWSER`** [environment variable](https://en.wikipedia.org/wiki/Environment_variable) equal to **`echo`** (just like in the [test](https://github.com/Homebrew/brew/pull/305/files) for **`brew home`**).
- an assertion is made for each flag.
	- e.g., **`brew search --debian testball`** should spit out the string for [this webpage](https://packages.debian.org/search?keywords=testball&searchon=names&suite=all&section=all).
- at the end of test, as usual, the newly created files are removed from existence.
