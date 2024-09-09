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

Included are some useful package for a more complete experience, like a freaking web browser eg. **Firefox**, an archive manager, **Meld** and so much more. It's a start. We shall add more if you wish, just keep in mind that only packages coming from the official **Arch Repositories** are supported, none from the **AUR**.

That's the main part. Rest of it is exactly the same as the **Plasma Install** script, where it prompts if you want to include the **XeroLinux** and **Chaotic-AUR** repos with the [**XeroLinux Toolkit**](https://wiki.xerolinux.xyz/xlapit/){:target="_blank"} among other neat things.

### To do list

Now the script is far from done. I have yet to figure some things out.

<p align="center">
  <img src="https://i.imgur.com/MY5yecT.png">
</p>

Although I have added a sort of *Hardware Checker* that will make the script check for compatible hardware before it moves on. In case of incompatibility, it should notify and exit. Still need help with that, since I do not know if I did a good job or not lol.

### Wrapping up

That's it for now. If you would like to help out so we can bring it to the public, you are more than welcome to. Especially when it comes to the *Hardware Checker* part which requires a lot of testing that I cannot do due to limited hardware availability. You can find the code >> [**Here**](https://github.com/xerolinux/xero-plasma/blob/main/xero-cosmic.sh){:target="_blank"}. This thing can become something awesome !

Cheers !
