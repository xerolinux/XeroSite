---
title: "NixOS Challenge"
description: "Trials & Tribulations of an Arch Maintainer"
date: "2025-07-14"
aliases: ["foss","linux","nixos"]
author: "DarkXero"
---

# Background

In case you don't know by now, or are new to this site/blog, let me give you some background before going through with this post. I am and have been an [**ArchLinux**](https://archlinux.org) user for the past 7 years, or so, maintaining my very own *Arch-Based* Distro for past 4 almost 5 called [**XeroLinux**](https://xerolinux.xyz). I haven't really used anything else long-term since. Until now that is...<br /><br />

{{< youtube lsYg6-wUWXw >}}<br />

# The Challenge

With the introduction out of the way, let me explain the so-called *Challenge*. I’m setting out to use **NixOS** as my daily driver for an entire year. However, for the sake of transparency, I won’t be using it exclusively all the time.

As I mentioned earlier, I’m a distro maintainer, and there are some critical tasks that simply can’t be done on NixOS. For example, I can’t compile or build **Arch** packages on it, I can’t maintain my Wiki which uses **MKDocs** because some plugins are missing on Nix, and I can’t even build any of the ISOs either.

I know some of you might suggest *"Just use DistroBox"* in the comments. I wish it were that simple. **DistroBox** provides a minimal environment, but I need a full GUI to stay productive. So, no, that’s not a viable solution. Unfortunately, there isn’t one. That’s why during this challenge, I’ll be alternating between **NixOS** and **Arch**, using Arch only when I have specific work to do.

Oh, and did I mention that **NixOS** is installed on an external NVMe SSD? That makes it very portable!

# NixOS Early days

Having established my background and perspective, it's important to state that it's still too early for me to offer a complete judgment on the distribution or its underlying language. I will be regularly updating this post as I continue my journey, so feel free to bookmark it if you're interested in further insights. As of writing this post, I have been using the system for 7 Days.<br /><br />

![nixos](https://i.imgur.com/sDDUARJ.png)<br />

As you can see from the image above, I was able to import my [**Xero-Layan**](https://wiki.xerolinux.xyz/rices/) **KDE Plasma** rice from **XeroLinux**. It wasn't that hard once you got the required knowledge. The only complex part was finding all packages I needed on **NixOS**. Which I have luckily enough. Though the package names were weird to say the least. 

# The NixOS Config File

After almost a decade of following what I’ll call “The Linux Way,” I’ve become very comfortable with the traditional methods, mounting drives, installing packages, and updating my system, knowing that these processes are nearly identical across distributions like **Debian** or **Arch**.

**NixOS**, however, takes a different approach. While familiar tools like mount are still available, the recommended method is to handle these configurations through the `hardware-configuration.nix` file or by defining them in `configuration.nix`. The same goes for mounting the various drives, they belong in the config files.

I’ve just finalized my **NixOS Configuration**, successfully mounting all my drives, setting **Wayland** as the default, enabling **ZSH/OhMyZSH**, and much more. The process was fairly straightforward, made even easier thanks to the support of some good friends.

# NixOS Packages & Updates

Installing packages on NixOS is quite different from other distributions. Instead of using a package manager directly, you add the packages you want to the `configuration.nix` file and then run sudo nixos-rebuild switch. This command pulls the packages from the Nix store and applies the changes declaratively.

Updating the system also differs from traditional distros. You run sudo nixos-rebuild switch --upgrade, which compares versions and upgrades to the latest available packages accordingly.

This approach emphasizes a *declarative* and *reproducible* system configuration, rather than manual package installs.

# NixOS Generations

Long story short, every time the system state is rebuilt using `nixos-rebuild switch`, a new [*generation*](https://nixos.wiki/wiki/Overview_of_the_NixOS_Linux_distribution#Generations) is created. You can revert to the previous generation at any time, which is useful if a configuration change (or system update) turns out to be detrimental.

This can quickly become overwhelming, particularly when dealing with the *bootloader*. Accumulating over 100 generations isn't ideal, which is why I've added an alias to my `.bashrc` file. This alias automatically removes all old generations, keeping only the most recent one after I've confirmed its stability. Feel free to add it to your setup if you find it useful.<br /><br />

```bash
alias ncg="nix-collect-garbage --delete-old && sudo nix-collect-garbage -d && sudo /run/current-system/bin/switch-to-configuration boot"
```

# Flakes & Home-Manager

From the get-go I decided I will never use [**Home-Manager**](https://nix-community.github.io/home-manager/index.xhtml#ch-introduction) thing. I do not like the ideology behind it. I want to keep it simple.

However, I am willing to go to the next level with something called [**Flakes**](https://wiki.nixos.org/wiki/Flakes). Right now though, I am still at the beginning of my **NixOS** adventure/challenge. 

# Update 1

After about **2 weeks** of poking around and tweaking things, I finally felt chill enough to jump into the world of **Flakes**. If I’m honest, the biggest reason was my growing obsession with **Flatpaks**. I wanted a straightforward, *declarative* way to install them, and **Flakes** was basically my only escape hatch for making it happen. So, I finally crossed that line.

Not a ton else has changed, you know how it goes with these setups, but I did have my own little victory: I managed to get **Virt-Manager** all set up, with the networking actually working for once (which, if you know, you know how annoying that can be). It felt pretty nice pulling all these pieces together. There’s something satisfying about seeing everything actually work after a bunch of trial and error !

Access my **Flakes** on the [**XeroNix Repo**](https://github.com/DarkXero-dev/XeroNix)

# Conclusion

After two weeks of use, the system is fully functional for everyday activities like web browsing, watching movies, writing blog posts, and even gaming. I managed to set up **Steam** and everything needed to enjoy my favorite games. Interestingly, the performance feels slightly better than on **Arch**, which I find both surprising and impressive.

I'm still taking things slow and steady, moving forward at my own comfortable pace. 

Wish me luck...


