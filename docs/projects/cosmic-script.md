---
title: Cosmic Install Script
tags:
  - Linux
  - CosmicDE
  - XeroLinux
  - ArchLinux
cover: https://i.imgur.com/ejZ1ZQv.png
---

!!! warning

    The script shared herein is and will be a work-in-progress for a while. **Cosmic** is still in Alpha stages; so it needs time to reach full maturity. Please do not use it on your production machine. If you want to test in a VM, for best performance I would highly recommend [**ProxmoxVe**](https://www.proxmox.com/en/proxmox-virtual-environment/overview){:target="_blank"}.

It's a beautiful Sunday morning. What did I decide to do ? Well, if you know me well enough by now you wouldn't be surprised by this, if you don't, I just sat down in front of my computer and decided to, since I was gonna test it anyway, write a script that would automate the install of [**Cosmic DE**](https://xerolinux.xyz/posts/arch-cosmic/){:target="_blank"} with my tools.

### Script info

Well, it does what title says, it installs **Cosmic** in one of 2 ways, similar to how my [**Plasma Install**](https://xerolinux.xyz/news/xerolinux-plasma/){:target="_blank"} script does. I also discovered the **Cosmic** group on **Arch** does not include the `xdg-user-dirs` package which creates the `Documents, Music, Pictures, Downloads & Videos` folders in your `home` & `power-profiles-daemon` is missing which the `Cosmic Settings` will prompt you for; so I added them.

- **Complete** : Just installs every Cosmic package available
- **Selective** : Allows selection of individual packages.

<p align="center">
  <img src="https://i.imgur.com/Fvl9uRU.png">
</p>

Included are some useful packages, like a freaking web browser eg. **Firefox**, an archive manager, **Meld** and so much more. It's a start. We shall add more if you wish, just keep in mind that only packages coming from the official **Arch Repositories** are supported, none from the **AUR**.

### Execution Blockers

I have also implemented some checks making sure script is being run in *chroot* and on *ArchLinux* blocking execution anywhere else. This helps me in the long run not having to bang my head against the wall trying to provide support in case it was run on Distros I have no control over.

<p align="center">
  <img width="360" src="https://i.imgur.com/JlFRZRd.png">  <img width="360" src="https://i.imgur.com/uNilqW8.png">
</p>

The reason I blocked script execution completely in case of *Custom Arch Distros* and *Non-Chroot* environments, simply is, because in all the years I spent maintianing **XeroLinux** I have learned that some users absolutely *looooooooove* ignoring them, which always resulted in me providing support for things outside the project.

So to avoid the headaches, I decided to block the execution. Better for everyone. This will allow me to concentrate on the distro and other current/future projects, with support being limited within **XeroLinux**.

Anyway, the rest of the script is exactly the same as the **Plasma Install** one, where it prompts if you want to include the **XeroLinux** and **Chaotic-AUR** repos with the [**XeroLinux Toolkit**](https://wiki.xerolinux.xyz/xlapit/){:target="_blank"} among other neat things.

### To do list

The script is far from done. I have yet to figure some things out.

Although I have added a sort of *Hardware Checker* that will make the script check for compatible hardware before it moves on. In case of incompatibility, it should notify and exit. Still need help with that, since I do not know if I did a good job or not lol.

I also need to figure out what packages are missing from the **Arch Cosmic Group** that I would need to include in the script for a much better and problem free experience, while it's being developed, since it's just in **Alpha 1** stages, meaning it's still missing a lot of *essential* features.

------

### Installation

Let's start off by knowing what we need to get started. First off, we will need the latest version of the >> [**ArchLinux ISO**](https://archlinux.org/download/){:target="_blank"}, a USB stick to burn ISO onto, we can either use >> [**Balena Etcher**](https://etcher.balena.io/#download-etcher){:target="_blank"} or the highly recommended >> [**Ventoy**](https://www.ventoy.net/en/index.html){:target="_blank"}.

Those are the essentials. As to my **Cosmic Install** script will get to that a bit later down the line. Once we got everything, we shall begin...

Ok, so now that we have burned the ISO to the USB using either tools, boot the system we want to install it on using it. Am not gonna go through showing you how, you should know that by now lol.

!!! tip

    This guide expects you to be connected to the internet via ethernet. If you aren't and need to connect over WiFi, you can follow guide on the [**ArchWiki**](https://wiki.archlinux.org/title/Installation_guide#Connect_to_the_internet){:target="_blank"}

- **ArchInstall Script**

Once connected, first thing we will have to do is, make sure we have latest version of **ArchInstall**. We do that by running the following command :

```Bash
pacman -Syy archinstall && archinstall --advanced
```

Now some of you might be asking me, "why the `--advanced` flag ?", to which I answer, simply because devs still hide the *parallel downloads* behind it for whatever reason. It's fine at least now you know.

<p align="center">
  <img src="https://i.imgur.com/OVzwVYt.png">
</p>

Ok, now that we have the installer running, am not going to go through each and every option one by one, just the important ones. Those are explained in the video. Am also not gonna bother with *manual partitioning* since the guide is intended for single OS easy install.

That's why we will be using the **Best Guess** option, carefully selecting the correct drive we want install **ArchLinux** onto.

Don't forget to set parallel downloads to as many as you like for faster downloads. Also, we do not need to enable any extra repos like *multilib* since my script will do that for us later on.

Now once everything is configured and set, hit install, sit back, grab a cup of Tea/Coffee and watch it do its thing. Might take a while it all depends on Internet connection...

- **Installing Cosmic DE**

Once that's all done, we will be prompted if we want to `chroot` into our new install, we answer with yes of course since we still have no DE yet.

!!! warning

    **User Caution**. We do not recommend to blindly execute scripts without inspecting them first. You can find the code >> [**Here**](https://github.com/xerolinux/xero-plasma/blob/main/xero-cosmic.sh){:target="_blank"}.

Once you trust it, you can move on. Now, we type the following command :

```Bash
bash -c "$(curl -fsSL https://tinyurl.com/Xero-Cosmic)"
```

This will execute the script. Just go through the prompts. I would **Highly** recommend option **1) Complete Cosmic Install** to avoid any future headaches. But that's not to say we cannot select any of the other option, it's all up to you in the end.

At the end, script will prompt us if we want to enable the repos and install the Toolkit, to which we answer with yes, since we will be using it to set everything up later on.

You will notice that, the *multilib* repo was enabled as well. I made sure of that since most newcomers forget to do it. It's an essential repo required for the likes of **Steam**, and various drivers.

Finally, for now at least, once script is done, we will be prompted to exit and reboot the system. We do that by typing `exit` then `reboot`, that's it !

Now use my toolkit to install any drivers *especially* if you are using an **nVidia** GPU otherwise you will have a bad time. Besides that enjoy the DE, and more importantly report all the bugs related to it or any feature requests you might have upstream, to the [**Cosmic Bug Tracker**](https://github.com/pop-os){:target="_blank"}

### Wrapping up

That's it for now. If you would like to help out so we can bring it to the public, you are more than welcome to. Especially when it comes to the *Hardware Checker* part which requires a lot of testing that I cannot do due to limited hardware availability.

**Cosmic** is shaping up to be the DE that *might* break the current *Top 2* (KDE and Gnome) making it the *Top 3* DEs of all time. Who knows ? I wish the **System76** team all the best.

Cheers !
