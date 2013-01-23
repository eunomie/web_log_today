---
layout: index
---

# Usage

```text
Usage: wlt <command> [<args>]

Some useful wlt commands are:
   assets    Build assets.
   build     Clean and build site
   clean     Clean site
   commands  List all wlt commands
   gollum    Run gollum
   scaffold  Initialize a web log today instance.
   serve     Serve after build

See 'wlt help <command>' for information on a specific command.
```

## Boostrap

Create an empty directory and add a full featured instance:

```sh
mkdir -p ~/tmp/my_log
cd ~/tmp/my_log
wlt scaffold full
wlt serve
```

That's it! You can browse to http://localhost:4000 to see the result!

Now, modify the config file `config.yaml` and all content.

## Files and directories

* _css

    Contains all sass files

* _js

    Contains all coffeescript files

* _layouts

    Haml templates and partials

* _pages

    Markdown files for pages

* _posts

    Blog posts in markdown

* _pub

    Public files to be copied at the root

* _site

    Contains all generated content

* config.yaml

    Configuration of accounts, title, etc

* Guardfile

    Allow guard to build when content changes

* Rakefile

    Used by guard and to easily deploy generated content
