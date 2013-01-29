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

Contient l'ensemble des fichiers [sass][] destinés à être compilés en css. Les fichiers "racines" sont spécifiés dans la configuration (voir plus loin). Le fichier généré est le nom du fichier [sass][] avec l'extension css. Par exemple `application.sass` donnera `application.css`

Vous pouvez utiliser toutes les fonctionnalités de [sass][], entre autre les `@import` vous permettant de factoriser vos css.

Si vous avez des fichiers `css` à inclure, et donc ne nécessitant pas une compilation, se référer à la partie publique.

_Note :_ il est bien sur possible d'avoir plusieurs fichiers css de sortie.

### `_js`

Contient l'ensemble des fichiers [coffeescript][] destinés à être compilés en javascript. Les fichiers à compilés sont à spécifier dans la configuration.

Le fichier généré est le nom du fichier [coffeescript][] avec l'extension js. Par exemple `application.coffee` donnera `application.js`.

Pour le moment il n'y a pas de mécanismes permettant de concaténer plusieurs fichiers [coffeescript][] en un. Dans un premier temps ce n'est pas réellement nécessaire car le but était de faire un site/blog simple et non une application web. Néanmoins un système type [sprockets][] pourra être envisagé par la suite.

Si vous avez des fichiers `js` à inclure, et donc ne nécessitant pas une compilation, se référer à la partie publique.

_Note :_ il est bien sur possible d'avoir plusieurs fichiers javascript de sortie.

### `_layouts`

Contient l'ensemble des fichiers [haml][] de templates. Il peut s'agir aussi bien de fichiers "racines" fournissant l'html de base que de fichiers partiels (à charger avec `render :partial => "..."`) ou des fichiers "intermédiaires".

Les contenus (pages, posts) déclarent dans leur entête le template à utiliser. Un template peut également faire appel à un template parent. Ceci permet par exemple d'avoir un premier template correspondant à tout ce qui tourne autour du contenu généré par le markdown, et un autre dédié à la page en elle-même. Pour plus d'explications, je vous suggère juste d'aller voir les exemples.

### `_pub`

Ce répertoire est probablement le plus simple. Tout ce qui est contenu dedans sera copié à la racine du site. Il permet donc d'inclure des fichiers css, des javascript, des images, des resources diverses, des fichiers html générés par d'autres moyens, etc.

### `config.yaml`

Le fichier `config.yaml` contient les paramètres nécessaire à la génération du site. Il s'agit de paramètres "systèmes" (par exemple l'url, le chemin de déploiement) ou simplement des paramètres destinés à être factorisés (comptes, infos twitter, etc).

Voici un exemple de fichier, commenté :

```yaml
# URL du site généré (les liens sont tous absolus)
site_url: http://log.winsos.net
# URL de déploiement, via rsync
deploy_to: ...@www.....lan:/var/www/log/
# Titre des pages
title: CrEv's log

# Informations twitter cards, opengraph, etc
# Nom de l'auteur
name: Plop Plop
# Twitter site / creator -> twitter cards
twitter_site: _crev_
twitter_creator: _crev_
# Description par défaut si non fournie
default_description: My personal weblog

# Divers comptes, permettant d'être affichés dans une page about dans les templates par défaut
accounts:
    twitter: https://twitter.com/_crev_
    gplus: https://plus.google.com/112813954986166280487
    github: http://github.com/CrEv
    coderwall: https://coderwall.com/crev
    linkedin: http://fr.linkedin.com/in/yvesbrissaud

# Assets, description des css/js à générer (nom des fichiers sans extension)
assets:
    css: [application, cv]
    js: [application]

```

A part le premier (`site_url`) qui est réellement conseillé, le reste est toujours optionel et dépend de vos templates. Ceci n'est donc qu'un exemple et vous pouvez en rajouter autant que vous voulez. Ils seront donc accessible de partour via les objets ruby.

### Headers

Chaque fichier [markdown][] et [haml][] peut débuter par un entête ajouter quelques méta données. Selon les cas (pages, billet, template) les paramètres ne sont pas forcément tous obligatoire. Voici les paramètres dans le cas d'un billet de blog.

Tout d'abord l'entête doit **toujours** débuter à la première lighe du fichier, par `---` et termine par une ligne contenant uniquement `---`.
Ce qui est entre ces lignes est du [yaml][].

Voici donc les données les plus courantes :

* `layout` : nom du fichier [haml][] qui va recueillir la sortie de [markdown][]
* `tags` : tableau contenant les tags relatif au billet
* `title` : Titre clair, avec accents et autres
* `author` : Nom de l'auteur
* `email` : email de l'auteur. L'email n'est pas affiché, il est utilisé pour afficher le gravatar correspondant
* `twitter` : compte twitter de l'auteur. Optionel, il peut être défini dans la configuration
* `published` : si `false` permet de ne pas généré la sortie. Cela permet de versionner certains contenus avant qu'ils soit publiés

Par exemple :

    ---
    layout: post
    tags: [web_log_today]
    title: Web Log Today est juillet
    author: Yves
    email: plopplop@....com
    twitter: _crev_
    published: false
    ---

_Note :_ vous pouvez rajouter sans aucun problème des métadonnées propres. Elles seront accessibles via les objets ruby comme détaillé plus bas. Cela peut vous permettre d'améliorer vos templates, votre site, en posant le maximum de données dans les fichiers [markdown][] ce qui permet de rendre la saisie plus agréable.

### Fichiers spéciaux

Deux fichiers un peu plus spéciaux peuvent être présent dans le répertoire `_pages` et un dans le répertoire `_layouts`.

Le premier est simplement le fichier `atom.xml.haml`. Comme son nom l'indique il permet de générer un fichier `atom.xml` et donc permet d'offrir à vos lecteurs un flux à placer dans un quelconque lecteur. Par défaut il permet de générer un flux basé sur les articles de blogs uniquement.

Le deuxième, un peu dans le même veine, est le fichier `sitemap.xml.haml`. Il permet de générer un fichier `sitemap.xml` listant l'ensemble des ressources html de votre site.

Enfin le fichier `tags.haml` peut être présent dans le répertoire `_layouts` afin d'afficher tous les billets d'un tag commun. Contrairement à tous les autres cas, ce fichier aura de multiples sorties, un fichier par tag, présent dans le répertoire `tags`.
