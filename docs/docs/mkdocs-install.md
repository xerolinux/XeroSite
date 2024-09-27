---
title: MKDocs Install
tags:
  - Linux
  - MKDocs
  - Blogging
---
### What's This?

This for my own use. Use it if you want to. Just documenting the installation of [**MKDocs**](https://www.mkdocs.org){:target="_blank"} the way that works for me. You are free to go over this and take from it what suites you the best. Please do not ask me for help, it's all there on their site. Also this for **ArchLinux** if you don't use that distro, well, their site shows how to install for your distro.

![type:video](https://www.youtube.com/embed/9V0NpLPXS-Y)

### Installing MKDocs

We will need to install it with some extras. The 2 main packages exist on the **Arch** repos. The rest are on the **AUR**, so to grab everything in one go, I will be using **Paru**. Compiling might take a while, so sit back wile it finishes.

```Bash
paru -S --noconfirm mkdocs mkdocs-get-deps mkdocs-material python-pipx python-pillow python-cairosvg mkdocs-material-extensions python-regex pymdown-extensions mkdocs-material-pymdownx-extras
```

Donce that's done we need to create the site. There's a command for that.

```Bash
mkdocs new my-project
cd my-project
```

Now that we initialized the new site we need to configure it. We do so by editing the `mkdocs.yml` file putting in the following info :

```YAML
site_name: Sitename

theme:
  name: material
  logo: assets/Tux.gif
  favicon: assets/favicon.ico
  palette:
    scheme: slate
    primary: deep purple
  features:
   - navigation.top
   - navigation.footer
   - navigation.indexes
   - content.code.copy
   - search.suggest
   - search.highlight
   - search.share
   - navigation.expand
```

This will make it use the **Slate Material** Theme with **Deep Purple** accents. To know more about the theme check the [**MKDocs Material Wiki**](https://squidfunk.github.io/mkdocs-material/getting-started/){:target="_blank"}. That's it go from there.

### Plugins & Extra Stuff

I have found a few that I liked on the **AUR**, let's install them via :

```Bash
paru -S --noconfirm mkdocs-rss-plugin mkdocs-video mkdocs-autorefs mkdocs-section-index mkdocs-glightbox mkdocs-backlinks-plugin mkdocs-redirects mkdocs-ezlinks-plugin mkdocs-literate-nav
```

To activate them we edit the same `mkdocs.yml` file as before like so :

```YAML
plugins:
  - rss
  - social
  - search
  - autorefs
  - glightbox
```

There are some cool features we can enable too. Only gotta figure out why some are not working. Besides that, this is how we add them :

```YAML
markdown_extensions:

  # Python Markdown
   - abbr
   - admonition
   - attr_list
   - def_list
   - footnotes
   - md_in_html
   - toc:
      permalink: true

  # Python Markdown Extensions
   - pymdownx.arithmatex:
       generic: true
   - pymdownx.betterem:
       smart_enable: all
   - pymdownx.caret
   - pymdownx.details
   - pymdownx.emoji:
      emoji_index: !!python/name:material.extensions.emoji.twemoji
      emoji_generator: !!python/name:material.extensions.emoji.to_svg
   - pymdownx.highlight:
      anchor_linenums: true
      line_spans: __span
      pygments_lang_class: true
   - pymdownx.inlinehilite
   - pymdownx.keys
   - pymdownx.mark
   - pymdownx.smartsymbols
   - pymdownx.superfences
   - pymdownx.tabbed:
       alternate_style: true
   - pymdownx.tasklist:
       custom_checkbox: true
   - pymdownx.tilde

extra:
  social:
    - icon: fontawesome/brands/github
      link: https://github.com/darkxero-dev
    - icon: fontawesome/brands/youtube
      link: https://youtube.com/XeroLinuxOfficial
    - icon: fontawesome/brands/x-twitter
      link: https://twitter.com/xerolinuxop
    - icon: fontawesome/brands/mastodon
      link: https://fosstodon.org/@xerolinux
```

That's it for now. I will be updating this post as I learn more. Still need to figure out a few things. I am just starting with this. Thanks to [**@JustAGuyLinux**](https://github.com/drewgrif){:target="_blank"} for helping out a little hehe.


