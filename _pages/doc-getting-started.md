---
layout: doc
---

# Getting started

This is a little tutorial to learn `wlt`.

1. Create a directory to contains your blog sources, in our case `my_new_blog`

    ```sh
    mkdir my_new_blog
    cd my_new_blog
    ```

2. We scaffold with the basic version

    Careful, `wlt scaffold` needs an empty directory
    
    ```sh
    wlt scaffold basic
    ```

    You now have all needed to start.

3. You can see your blog in action now:

    ```sh
    wlt serve
    ```
    
    Then browse http://localhost:4000
    
    And now, your blog is on its way!

4. Create a git repository (needed by gollum)

    ```sh
    git init
    git add .
    git ci -m "Initial scaffold"
    ```

5. Some configuration

    Edit the file `config.yaml`. Configuration is rather simple.

    Edit the file `_pub/robots.txt` to change the url of the sitemap file.
    
    If you want to deploy with [rake][], add a key `deploy_to`. You can see the usage in `Rakefile`.

6. Edit le content, add post, etc.

    If you want to edit an existing content, the easier way is to launch [gollum][]:
    
    ```sh
    wlt gollum
    ```
    
    And browse http://localhost:4567/pages
    
    You can edit the [markdown][] file by hand if you want.
    
    To create a new post:
    
    ```sh
    touch _posts/2013-01-29-web-log-today-is-so-nice.md
    git add _posts/2013-01-29-web-log-today-is-so-nice.md
    git ci -m "Add new post"
    wlt gollum
    ```
    
    Careful, [gollum][] create git commits!

7. Go further?

    ```sh
    wlt serve &
    guard
    ```
    
    With this, you can edit your files and see the generated version without building by hand.

8. Publication

    If you server supports rsync, just do:
    
    ```sh
    rake deploy
    ```

   That's all!

So easy, isn't it?

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