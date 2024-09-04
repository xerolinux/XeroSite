---
title: MKDocs Install
tags:
  - Linux
  - MKDocs
  - Blogging
<!--cover: https://i.imgur.com/45QL4xk.jpeg-->
---
### What's This?

This for my own use. Use it if you want to. Just documenting the installation of [**MKDocs**](https://www.mkdocs.org) the way that works for me. You are free to go over this and take from it what suites you the best. Please do not ask me for help, it's all there on their site. Also this for **ArchLinux** if you don't use that distro, well, their site shows how to install for your distro.

### Installing MKDocs

We will need to install it with some extras. The 2 main packages exist on the **Arch** repos. The rest are on the **AUR**, so to grab everything in one go, I will be using **Paru**. Compiling might take a while, so sit back wile it finishes.

```Bash
paru -S --noconfirm mkdocs mkdocs-get-deps mkdocs-material
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
  palette:
    scheme: slate
    primary: deep purple
```

This will make it use the **Slate Material** Theme with **Deep Purple** accents. To know more about the theme check the [**MKDocs Material Wiki**](https://squidfunk.github.io/mkdocs-material/getting-started/). That's it go from there.

### Plugins & Extra Stuff

I have found a few that I liked on the **AUR**, let's install them via :

```Bash
paru -S --noconfirm mkdocs-autorefs mkdocs-rss-plugin mkdocs-htmlproofer-plugin mkdocs-glightbox mkdocs-backlinks-plugin mkdocs-static-i18n-plugin mkdocs-redirects mkdocs-ezlinks-plugin
```

To activate them we edit the same `mkdocs.yml` file as before like so :

```YAML
plugins:
  - search
```


