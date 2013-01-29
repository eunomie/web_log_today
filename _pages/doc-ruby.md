---
layout: doc
---

# Ruby objects

All [haml][] files can access some properties or method. All is not very unified for now, but it works and will be improve in the futur.

This is the main properties in [haml][] files:

* `name` : file name
* `@contents` : global properties

    * `config` : [yaml][] of the configuration file
    * `list` : all posts
    * `list_lasts(number)` : max `number` posts
    * `list_by_date` : all posts by year, month, day
    * `account?(name)` : check the presence of an account `name` in the configuration
    * `account(name)` : value of the account `name` in the configuration
    * `tag` : current tag, in `tags.haml`
    * `urls` : all urls of pages and posts

* `link_to(url)` : generate an absolute url using configuration
* `gravatar?` : check the presence of an email to display gravator
* `gravatar` : gravatar url
* `published?` : check the presence of `published` parameter
* `published` : value of the `published` parameter or `true`
* `date` : date, for a post
* `<...>?` : check the presence of `<...>` in the header
* `<...>` : value of `<...>` in the header
* `@scope` : similar parameters but specificaly for the [markdown][] content. It allows to access this header and the [haml][] header
* `content` : html content to add (generated from the [markdown][] or the [haml][])

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