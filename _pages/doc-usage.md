---
layout: doc
---

# Usage

The overall principle is simple. `wlt` read informations in specific folders, transform it in css, js and html to create a static web site.

> convention over configuration

Here is the conventions for the folders:

### `_site`

Will contain all generated content. This is the folder to copy to your web server.

### `_posts`

Contains all blog posts. These are markdown files which name has the following structure:

    yyy-mm-dd-title-of-the-blog-post.md

* `yyyy` : year of publication
* `mm` : month of publication
* `dd` : day of publication
* `title-of-the-blog-post` : generally the title of the post, without any special character

The html file will be:

    yyyy/mm/dd/title-of-the-blog-post.html

### `_pages`

You can define some static files which are not blog post. These files are in `_pages` folder and are markdown files. The name of the markdown file will be the name of the html. By example `index.md` will become `index.html`.

Some a little more special files may be present, see the specific part.

### `_css`

All [sass][] files to be compiled in css. Root files are specified in the configuration file. The name of the css file will be the name of the root [sass][] file. By example `application.sass` will become `application.css`.

You can use all functionalities of [sass][], by example `@import` to split your css in multiple files.

If you want to use css-only files, please refer to the public part.

### `_js`

All [coffeescript][] files to be compiled in javascript. Files to compile must be specified in the configuration.

The name of the javascript file will be the name of the [coffeescript][]. By example `application.coffee` will become `application.js`.

For now there's no way to concat many [coffeescript][] files in one. That's simply not the principal goal. A system like [sprockets][] can be adding in the future.

If you want include plain javascript files, please refer to the public part.

### `_layouts`

All [haml][] template files, either root, partials or intermediary.

Contents (pages, posts) declare in a header the template to use. A template can call a parent template. This allows to have a template to include [markdown][] and a template for the page. To go further, see examples.

### `_pub`

This is the easier folder. All in this will be copied at the root of the website. This allows you to include css, javascript, pictures, resources, html, etc.

### `config.yaml`

The file `config.yaml` contains all necessary parameters to generate the site. Some are _system_ parameters (like the root url), some are simply informations to factorize like accounts, twitter informations, etc.

This is an example of config file :

```yaml
# URL of generated web site (to have absolute links)
site_url: http://log.winsos.net
# Deployement url (via rsync)
deploy_to: ...@www.....lan:/var/www/log/
# Page title
title: CrEv's log

# Twitter cards, opengraph, etc
# Author
name: Plop Plop
# Twitter site / creator -> twitter cards
twitter_site: _crev_
twitter_creator: _crev_
# Default description if no excerpt
default_description: My personal weblog

# Some accounts, to be displayes in an about page in default templates
accounts:
    twitter: https://twitter.com/_crev_
    gplus: https://plus.google.com/112813954986166280487
    github: http://github.com/CrEv
    coderwall: https://coderwall.com/crev
    linkedin: http://fr.linkedin.com/in/yvesbrissaud

# Assets, description of css/js to generate (name of files without extension)
assets:
    css: [application, cv]
    js: [application]

```
Except for the first which is really recommended, others are optional and depend of your templates. This is only an example, you can add all parameters you want. They will always be accessible in ruby objets.

### Headers

Every [markdown][] and [haml][] files can start with an header to add some meta data. All parameters are not mandatory and can vary depending on the case (pages, blog post, template). This is an example for a blog post.

First, the header **must** starts, at the first line of the file, with `---` and ends by a line containing only `---`.
All inside this lines is [yaml][].

* `layout` : name of the [haml][] file which will contain the [markdown][] output
* `tags` : Array containing tags
* `title` : Title of the article
* `author` : Name of the author
* `email` : Email of the author. It is only used for gravatar and will not be displayed
* `twitter` : twitter account of the author, optional
* `published` : if `false`, allow to not generate output for this content

By example :

    ---
    layout: post
    tags: [web_log_today]
    title: Web Log Today first release
    author: Yves
    email: plopplop@....com
    twitter: _crev_
    published: false
    ---

### Special files

Two special files can be present inside `_pages` folder, and on in `_layouts`.

The first is `atom.xml.haml`. It allows to generate an `atom.xml` file containing all blog posts.

Second is a `sitemap.xml.haml`. It allows to generate a `sitemap.xml` referencing all files.

Finally, the file `tags.haml` can be present in `_layouts` to generate files referencing all posts with a common tag. Contrary to all other files, this one can have multiples output, one file per tag in `tags` folder.

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