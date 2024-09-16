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

First we will need to download the [**Photo**](https://store.serif.com/update/windows/photo/2/){:target="_blank"}, [**Designer**](https://store.serif.com/update/windows/designer/2/){:target="_blank"} or [**Publisher**](https://store.serif.com/update/windows/publisher/2/){:target="_blank"} `exe` from the dropdown. Once we have it/them, we will need to go through the following script(s). Process might take time and a **Discreet GPU** is highly recommended for Hardware Acceleration & good performance.

!!! note

    Do not cut-paste installers into location indicated by scripts as they will get deleted once script is done. Before running the scripts below, check if you have the required [**Dependencies**](https://github.com/Twig6943/AffinityOnLinux/blob/main/Guide/Guide.md#required-dependencies){:target="_blank"}

- [**Affinity Photo**](https://affinity.serif.com/en-gb/photo/?#top){:target="_blank"}

Affinity Photo is a professional-grade photo editing software, designed for photographers, artists, and designers. Known for its robust performance, it offers a comprehensive suite of tools, including advanced retouching, color correction, RAW editing, and non-destructive layering, making it a versatile alternative to Adobe Photoshop.

```Bash
bash -c "$(curl -s https://raw.githubusercontent.com/Twig6943/AffinityOnLinux/main/AffinityScripts/AffinityPhoto.sh)"
```

- [**Affinity Designer**](https://affinity.serif.com/en-us/designer/?#top){:target="_blank"}

Affinity Designer is a versatile vector graphics design software, ideal for illustrators, graphic designers, and artists. It offers a comprehensive set of tools for vector illustration, typography, and layout, allowing for precise control over shapes, paths, colors, and gradients. Known for its smooth performance, even with complex designs.

```Bash
bash -c "$(curl -s https://raw.githubusercontent.com/Twig6943/AffinityOnLinux/main/AffinityScripts/AffinityDesigner.sh)"
```

- [**Affinity Publisher**](https://affinity.serif.com/en-us/designer/?#top){:target="_blank"}

Affinity Publisher is a professional desktop publishing software, designed for creating layouts for books, magazines, brochures, and other print and digital publications. It provides a range of powerful tools for precise typography, image placement, and page design, allowing users to create visually engaging documents.

```Bash
bash -c "$(curl -s https://raw.githubusercontent.com/Twig6943/AffinityOnLinux/main/AffinityScripts/AffinityPublisher.sh)"
```

### Wrap up

!!! tip

    Check the [**Written Guide**](https://github.com/Twig6943/AffinityOnLinux/blob/main/Guide/Guide.md){:target="_blank"} if you prefer doing it manually. Also the author posted his scripts on the **Affinity**'s forums, who knows maybe in the future a **Linux** native version ? Let's all cross our fingers 🤞

That's it. Once all done we can launch them from the shortcuts the scripts create. That's the closest to **Photoshop** I have ever gotten, without having to go through *WinBlows* if ya know what I mean.

Guide wasn't posted on main site due to the nature of the products included. Also this was, as I said earlier primarily written for myself so I do not have to go digging for it on the web. For archival purposes sorta.

