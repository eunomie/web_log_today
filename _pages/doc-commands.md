---
layout: doc
---

# So, how does it works in fact?

This is main `wlt` commands:

## `wlt assets`

Compile all css (from [sass][]) and javascript (from [coffeescript][]).

## `wlt build`

Empty the output directory and build all the site.

## `wlt clean`

Empty the output directory.

## `wlt gollum`

Run [gollum][] to display and edit all [markdown][] files. Careful, only files added to [git][] are managed.

## `wlt serve`

Build all content and serve the output on http://localhost:4000

## `wlt scaffold`

Allow to generate a basic or a more complexe version, to start easily with `wlt`.

The two commands are `wlt scaffold basic` and `wlt scaffold full`.

The basic version contains the minimum to start:

* base css file
* base js file
* an index page which list all posts
* a template for the posts
* a page header containing twitter informations, opengraph, etc
* atom, sitemap
* a [rake][] file and [guard][] file

The full version adds:

* a better css (colors, layout, etc)
* tags, pages
* some partial [haml][]

[haml]: http://haml.info
[git]: http://git-scm.com
[markdown]: http://daringfireball.net/projects/markdown/
[ruby]: http://ruby-lang.org
[gem]: http://rubygems.org
[guard]: https://github.com/guard/guard
[rake]: http://rake.rubyforge.org/
[sass]: http://sass-lang.com/
[coffeescript]: http://coffeescript.org/
[bundler]: http://gembundler.com/
[redcarpet]: https://github.com/vmg/redcarpet
[gollum]: https://github.com/github/gollum
[jekyll]: jekyllrb.com
[sprockets]: https://github.com/sstephenson/sprockets
[yaml]: http://www.yaml.org/
[rake]: http://rake.rubyforge.org/