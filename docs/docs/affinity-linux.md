---
title: Affinity on Linux
tags:
  - Linux
  - Affinity
  - Photoshop
---

!!! warning

    I am aware that these apps are what's called "**Proprietary**" and require us to purchase a one-time *License* in order to use them indefinitely. It's on you how you get them. I will not condone piracy anywhere on my sites. Please be aware of that while you follow this guide.

### What's This?

This for my own use. Use it if you want to. Just documenting the installation of [**Affinity Apps**](https://affinity.serif.com/en-us/){:target="_blank"} on **Linux** with the help of some scripts I found thanks to [**Twig6943**](https://github.com/Twig6943){:target="_blank"} who went out of his way to create them.

<p align="center">
  <img src="https://i.imgur.com/MABHj31.jpeg">
</p>

### Installation

Once we have created an account on the [**Affinity Site**](https://affinity.serif.com/en-us/){:target="_blank"} and downloaded and saved them in a safe location, we will need to go through the following scripts. Process might take time and a **Discreet GPU** is highly recommended for Hardware Acceleration & good performance.

!!! note

    Do not cut-paste installers into location indicated by scripts as they will get deleted once script is done. I recommend you do a copy-paste instead just so you do not have to download them all over again. Also self-updates are disabled. You will have to manually get the updated installers.

- [**Affinity Photo**](https://affinity.serif.com/en-gb/photo/?#top){:target="_blank"}

Affinity Photo is a professional-grade photo editing software, designed for photographers, artists, and designers. Known for its robust performance, it offers a comprehensive suite of tools, including advanced retouching, color correction, RAW editing, and non-destructive layering, making it a versatile alternative to Adobe Photoshop.

```Bash
bash -c "$(curl -s https://raw.githubusercontent.com/Twig6943/AffinityOnLinux/main/AffinityPhoto/Script.sh)"
```

- [**Affinity Designer**](https://affinity.serif.com/en-us/designer/?#top){:target="_blank"}

Affinity Designer is a versatile vector graphics design software, ideal for illustrators, graphic designers, and artists. It offers a comprehensive set of tools for vector illustration, typography, and layout, allowing for precise control over shapes, paths, colors, and gradients. Known for its smooth performance, even with complex designs.

```Bash
bash -c "$(curl -s https://raw.githubusercontent.com/Twig6943/AffinityOnLinux/main/AffinityDesigner/Script.sh)"
```

- [**Affinity Publisher**](https://affinity.serif.com/en-us/designer/?#top){:target="_blank"}

Affinity Publisher is a professional desktop publishing software, designed for creating layouts for books, magazines, brochures, and other print and digital publications. It provides a range of powerful tools for precise typography, image placement, and page design, allowing users to create visually engaging documents.

```Bash
bash -c "$(curl -s https://raw.githubusercontent.com/Twig6943/AffinityOnLinux/main/AffinityPublisher/Script.sh)"
```

### Wrap up

!!! tip

    For guide version check [**Affinity Photo**](https://github.com/Twig6943/AffinityOnLinux/blob/main/AffinityPhoto/Guide.md){:target="_blank"}, and [**Affinity Designer**](https://github.com/Twig6943/AffinityOnLinux/blob/main/AffinityDesigner/Guide.md){:target="_blank"} finally [**Affinity Publisher**](https://github.com/Twig6943/AffinityOnLinux/blob/main/AffinityPublisher/Guide.md){:target="_blank"}. For scripts, well here's an [**Example**](https://github.com/Twig6943/AffinityOnLinux/blob/main/AffinityPhoto/Script.sh). It's the same script basically just `exe` is different.

That's it. Once all done we can launch them from the shortcuts the scripts create. THat's the closest we will get to **Photoshop** I have ever gotten, without having to go through *WinBlows* if ya know what I mean.

Guide wasn't posted on main site due to the nature of the products in this guide. Also this was, as I said earlier primarily written for myself so I do not have to go digging for it on the web. For archival purposes sorta.
