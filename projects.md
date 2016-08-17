---
layout:    page
permalink: /projects/
---

<h3><a href="https://github.com/Homebrew/brew">Homebrew/brew</a></h3>

>##### The missing package manager for OS X

So far, most of 2016 has been consumed with learning about what makes Homebrew tick and making some contributions in the process. Below (in reverse chronological order) is a list of the pull requests I've made that have (for the most part) been merged into the core codebase. My [Outreachy](https://www.gnome.org/outreachy/) summer internship has dealt with the task of increasing and improving Homebrew's test coverage, so these commits all involve code in the **`Library/Homebrew/test`** directory. I've written a series of blog posts on my Outreachy/Homebrew experience; you can find them <span style="background-color: #ffdb4d">highlighted in yellow</span> on the [main page]({{site.url}}/).

- [tests: allow **`brew tests`** to accept multiple **`--only`** args](https://github.com/Homebrew/brew/pull/726)
	- *not merged!*
- [tests: add **`cmd/audit`** unit tests](https://github.com/Homebrew/brew/pull/704)
- [tests: **`cmd/audit`** unit tests (2 commits)](https://github.com/Homebrew/brew/pull/682):
	- refactor **`FormulaTextTests`** in **`test_cmd_audit`**
	- add assertion to **`test_simple_valid_formula`**
- [tests: **`cmd/install`** integration test (2 commits)](https://github.com/Homebrew/brew/pull/626):
	- refactor installation and renaming of **`CoreTap`** formula
	- extend **`cmd/install`** integration test
- [tests: update **`cmd/analytics`** integration test](https://github.com/Homebrew/brew/pull/617)
- [tests: add **`cmd/migrate`** integration test](https://github.com/Homebrew/brew/pull/601)
- [tests: extend **`cmd_fail`** to all non-zero exit codes](https://github.com/Homebrew/brew/pull/595)
- [tests: fix code style issues](https://github.com/Homebrew/brew/pull/587)
- [tests: add **`cmd/switch`** integration test](https://github.com/Homebrew/brew/pull/559)
- [tests: add **`cmd/analytics`** integration test](https://github.com/Homebrew/brew/pull/558)
- [tests: nest **`HOMEBREW_TEMP`** inside **`TEST_TMPDIR`**](https://github.com/Homebrew/brew/pull/554)
- [tests: add **`cmd/pull`** integration test](https://github.com/Homebrew/brew/pull/525)
- [tests: add **`cmd/irb`** integration test](https://github.com/Homebrew/brew/pull/501)
- [tests: add **`cmd/test`** integration test](https://github.com/Homebrew/brew/pull/500)
- [tests: add **`cmd/link`**, **`cmd/unlink`** integration test](https://github.com/Homebrew/brew/pull/398)
- [tests: add **`cmd/style`** integration test](https://github.com/Homebrew/brew/pull/388)
	- *not merged!*
- [tests: refactor formula file creation](https://github.com/Homebrew/brew/pull/370)
- [tests: add **`cmd/search`** integration test](https://github.com/Homebrew/brew/pull/356)
- [tests: extend **`cmd/log`** integration test](https://github.com/Homebrew/brew/pull/333)
	- a few errors were overlooked in the initial PR, so Martin followed-up with [this one](https://github.com/Homebrew/brew/pull/350).
- [tests: extend **`cmd/desc`** integration test](https://github.com/Homebrew/brew/pull/314)
- [tests: add integration test for **`cmd/home`**](https://github.com/Homebrew/brew/pull/305)

<h3><a href="https://github.com/Homebrew/brew">Homebrew/homebrew-core</a></h3>

>##### Core formulae for the Homebrew package manager

This is a list of pull requests I've made for Homebrew's core formula tap. Getting to know Homebrew in the first place has meant running **`brew audit`** or **`brew audit --strict`** and fixing some of the warnings that arise for various core formula files. Sifting through formula files and even adding a test for one formula have been good ways to get acquainted with Homebrew's core functions.

- [**`brew audit`**: remove inreplace do block](https://github.com/Homebrew/homebrew-core/pull/3402)
	- 3 formulae: **pev**, **genstats**, and **flac**
- [**`brew audit`**: remove golang requirement](https://github.com/Homebrew/homebrew-core/pull/2917)
	- 6 formulae: **path-extractor**, **noti**, **fabio**, **emp**, **docker-machine-driver-xhyve**, and **assh**
- [aften: add **`test do`** block](https://github.com/Homebrew/homebrew-core/pull/304)
	- this fix added a test for a formula that didn't have one yet.
- [udis86: use **`assert_match`** instead of **`assert...include?`**](https://github.com/Homebrew/homebrew-core/pull/112)
- [txt2man: fix audit warnings](https://github.com/Homebrew/homebrew-core/pull/111):
	- use **`assert_match`** instead of **`assert...include?`**
	- use **`%q`** only for strings that contain both single quotes and double quotes
- [masscan: use **`assert_match`** instead of **`assert...include?`**](https://github.com/Homebrew/homebrew-core/pull/96)
- [pyenv-ccache: use **`assert_match`** instead of **`assert...include?`**](https://github.com/Homebrew/homebrew-core/pull/89)
- [tasksh: fix audit warnings](https://github.com/Homebrew/homebrew-core/pull/86):
	- use **`assert_match`** instead of **`assert...include?`**
	- move **`checksum`** before **`head`**
- [sleepwatcher: use the **`mv`** Ruby method instead of **`system "mv"`**](https://github.com/Homebrew/homebrew/pull/50503)
- [scrub: use **`assert_match`** instead of **`assert...include?`**](https://github.com/Homebrew/homebrew/pull/50328)
- [srmio: use the **`chmod`** Ruby method instead of **`system "chmod"`**](https://github.com/Homebrew/homebrew/pull/50189)
- [gf-complete: remove redundant version statement](https://github.com/Homebrew/homebrew/pull/50151)

<h3><a href="https://github.com/rhubarb-crew/la-region-library-map">LA Region Library Map</a></h3>

>##### A collaboration with fellow [Maptimers](https://github.com/maptimeLA/), Nina Kin and Kenny Lee.

My first library mapping project will map all public library locations in L.A. County, placing calls to the Google Maps API and government open data APIs (if available). This includes the City of L.A. and County of L.A. library systems, as well as all other city library systems within L.A. County (e.g., libraries in Pasadena and Santa Monica). The map will display an info window for each branch location, allowing the user to see branch names, addresses, hours, and URLs. Eventually, I’d like to implement the mapping with Leaflet or Mapbox (both of which are open-source) instead of Google Maps.

<h3><a href="https://github.com/eirinikos/ruby-bites#tictactoerb">Tic Tac Toe!</a></h3>

>##### A command-line tic-tac-toe game dispenser

It's written entirely in Ruby, so yes, it was fun not only to write and refactor the code, but also to debug it. I still need to implement testing. Play against another human or play against an arrogant computer adversary; play on a conventional 3 x 3 board or play on a 4 x 4 board.

<h3><a href="https://github.com/eirinikos/open-todo-api">Open Todo API</a></h3>

>##### An API for a to-do list client-side application.

This was the last of the four Bloc applications I made with Matt. It returns JSON representations of users, lists, and items. It relies on Rails serializers to convert Rails objects into JSON.

<h3><a href="https://kao-blocmetrics.herokuapp.com">Blocmetrics</a></h3>

>##### A analytics service API.

This project acquainted me with how a web analytics works, among other things. With the client-side JS snippet, a user tracks events on their website. The server-side API captures and save those events to a database, and the captured event data is displayed back to the user in the form of pretty pie and line charts.

<h3><a href="https://kao-bloccitoff.herokuapp.com">Bloccitoff</a></h3>

>##### A self-destructing to-do list application.

This classic to-do list project has an added twist - it automatically destroys items that aren't yet done after 7 days.

<h3><a href="https://kao-bloccit.herokuapp.com">Bloccit</a></h3>

>##### A replica of Reddit.

This was my first project with my Bloc mentor, Matthieu Tanguay-Carel.
