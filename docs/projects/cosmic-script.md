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

    The script shared herein was created for myself. Do not ask for it right now. It's currently just a proof of concept of what you can achieve once you put your mind to it.

It's a beautiful Sunday morning. What did I decide to do ? Well, if you know me well enough by now you wouldn't be surprised by this, if you don't, I just sat down in front of my computer and decided to, since I was gonna test it anyway, write a script that would automate the install of [**Cosmic DE**](https://xerolinux.xyz/posts/arch-cosmic/){:target="_blank"} with my tools.

### Script info

Well, it does what title says, it installs **Cosmic** in one of 2 ways, similar to how my [**Plasma Install**](https://xerolinux.xyz/news/xerolinux-plasma/){:target="_blank"} script does. I also discovered the **Cosmic** group on **Arch** does not include the `xdg-user-dirs` package which creates the `Documents, Music, Pictures, Downloads & Videos` folders in your `home` & `power-profiles-daemon` is missing which the `Cosmic Settings` will prompt you for; so I added them.

![type:video](https://www.youtube.com/embed/v0UPif52i5A)

- **Complete** : Just installs every Cosmic package available
- **Selective** : Allows selection of individual packages.

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

<p align="center">
  <img src="https://i.imgur.com/MY5yecT.png">
</p>

Although I have added a sort of *Hardware Checker* that will make the script check for compatible hardware before it moves on. In case of incompatibility, it should notify and exit. Still need help with that, since I do not know if I did a good job or not lol.

I also need to figure out what packages are missing from the **Arch Cosmic Group** that I would need to include in the script for a much better and problem free experience while it's being developed since it's just an **Alpha 1** meaning it's still missing a lot of features.

### Wrapping up

That's it for now. If you would like to help out so we can bring it to the public, you are more than welcome to. Especially when it comes to the *Hardware Checker* part which requires a lot of testing that I cannot do due to limited hardware availability. You can find the code >> [**Here**](https://github.com/xerolinux/xero-plasma/blob/main/xero-cosmic.sh){:target="_blank"}.

**Cosmic** is shaping up to be the DE that *might* break the current *Top 2* (KDE and Gnome) making it the *Top 3* DEs of all time. Who knows ? I wish the **System76** team all the best.

Cheers !