---
title: New Toolkit Feature
date: 2024-05-30 11:02:39
tags:
  - Linux
  - Toolkit
  - Scripting
  - XeroLinux
  - ArchLinux
cover: https://i.imgur.com/gyOMiVr.png
---

### Drivers Install

As I have mentioned on an earlier post, I was stuck between using either `inxi -G` or `lspci` commands to list GPUs available during Driver install phase of my toolkit. I opted to go with the former simply because the latter only works for `dGPUs` connected over PCIe. Wouldn't work for `iGPUs`. Now, before going through with script, it will run `inxi -G` showing you your GPU setup, you are expected to understand output, if you don't, then you need to re-evaluate your decision coming to **ArchLinux** a distro that *requires* a minimum amount of **Linux** knowledge. Anyway here's what it looks like now.

<div align="center">

![GPU](https://i.imgur.com/s8jkwa7.png)

</div>

### How to proceed from here

Now that you know more about your specific GPU setup, you will need to answer prompts wisely. Otherwise you might end up with a broken system. So be very careful with that. If you don't know, either ask me or do some research on your own.

In the case of **Intel** be it an **Arc dGPU** or **Intel HD iGPU** just drivers and required codecs will be installed. Very simple, as nothing else is required, at least to my knowledge.

For **AMD** iGPU or dGPU you will be prompted if you intend to use **DaVinci Resolve** at the end, since the app requires extra *codecs* for seamless functionality. Simply because it's one that favors **nVidia** over **AMD**. It is what it is hehe.

Now for **nVidia**, you will be prompted for a few things, first if you are running a Desktop with a single dGPU or Hybrid Laptop with both **Intel** & **nVidia**, then it will ask if have a **900/1000** Series card or **2000** onwards simply because the former will be using standard **DKMS** drivers while the latter will be using the **Open-DKMS** ones.

Keep in mind that currently, my script only supports **Intel/nVidia** Hybrid setups. For **AMD/nVidia** and **AMD iGPU+AMD dGPU** you will have to find documentation elsewhere. Might I suggest the [**ArchWiki**](https://wiki.archlinux.org) or **Google** it lol. I don't know anything about those two nor do I have such setups. It's up to you.

I should also mention that for **nVidia**, my script will do all the necessary steps for seamless gaming & **Wayland** usage. Like injecting the required **modules** into *modprobe.d* among other things. That way you do not need to do anything yourself. Script will be updated for the upcoming **555 Series** drivers once they hit stable as they might require extra steps. keep an eye out for that.

Finally for clarification in case you don't know :

- **dGPU** : Dedicated/Discrete GPU
- **iGPU** : Integrated GPU (Onboard/on CPU)

I hope this post clarifies things for you, and that you are enjoying the [**XeroLinux Toolkit**](https://github.com/xerolinux/xlapit-cli). If you want to discuss it, share ideas on how I can improve it further, well the only place for that is my [**Discord Server**](https://discord.gg/5sqxTSuKZu).

See ya there ;)
