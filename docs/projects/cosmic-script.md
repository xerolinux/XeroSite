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

Well, it does what title says, it installs **Cosmic** in one of 2 ways, similar to how my [**Plasma Install**](https://xerolinux.xyz/news/xerolinux-plasma/){:target="_blank"} script does.

![type:video](https://www.youtube.com/embed/v0UPif52i5A)

- **Complete** : Just installs every Cosmic package available
- **Selective** : Allows selection of individual packages.

That's the main part. Rest of it is exactly the same as the **Plasma Install** script, where it prompts if you want to include the **XeroLinux** and **Chaotic-AUR** repos with the [**XeroLinux Toolkit**](https://wiki.xerolinux.xyz/xlapit/){:target="_blank"} among other neat things.

### To do list

Now the script is far from done. I have yet to figure some things out. For example, I just discovered the **Cosmic** group on **Arch** does not include the `xdg-user-dirs` package which creates the `Documents, Music, Pictures, Downloads & Videos` folders in your `home`.

<p align="center">
  <img src="https://i.imgur.com/MY5yecT.png">
</p>

Also, for whatever reason, if you do not install **nVidia** drivers n include required *kernel modules* the whole UI glitches out, crashes and hangs on *EGL Error*. Now, I haven't tested it on an **Intel** or **AMD** machine so dunno about those.

Finally will have to add some sort of *Hardware Checker* that will make the script check for compatible hardware before it moves on. In case of incompatibility, it should notify and exit.

### Wrapping up

That's it for now. If you would like to help out so we can bring it to the public, you are more than welcome to. Especially when it comes to the *Hardware Checker* part. You can fond the code >> [**Here**](https://github.com/xerolinux/xero-plasma/blob/main/xero-cosmic.sh){:target="_blank"}

Cheers !


