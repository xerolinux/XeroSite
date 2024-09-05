---
title: ArchISO Build
tags:
  - Linux
  - ArchISO
  - ArchLinux
---
### Information

This guide was written by following the **ArchWiki**. It's for my own use. The public version can be found on the official [**XeroLinux**](https://xerolinux.xyz/posts/build-archiso/){:target="_blank"}. This version will always be updated. Sometimes need to remind myself which files to modify...

<p align="center">
    <img width="500" src="https://i.imgur.com/QWqMIsr.png" alt="logo">
</p>

### Let's do this 🚀

First off we need to grab a few packages in order to be able to build the ISO.

```Bash
sudo pacman -S archiso
```

Create a `XeroArch` folder anywhere, in my case I did it in `Documents`, then copy over `releng` folder from `/usr/share/archiso/configs` then `cd` into it like so :

```Bash
mkdir -p ~/Documents/XeroArch
cp -rf /usr/share/archiso/configs/releng ~/Documents/XeroArch/
cd ~/Documents/XeroArch/
```

Now we need create two folders in our home directory or anywhere else, up to you, one called `XeroWork` for placing extracted files, another called `XeroOut` where final ISO will be located.

```Bash
mkdir ~/XeroWork && mkdir ~/XeroOut
```

Modify the `packages.x86_64` inside `releng` folder add the necessary required packages. Now that it's all done we can proceed to building a fresh new & updated **ArchISO**. Just use the command below and watch the magic happen.

```Bash
sudo mkarchiso -v -w ~/XeroWork -o ~/XeroOut releng
```

Finally we can delete the work directory to save space. just do `sudo rm -rf ~/XeroWork/`.

That's it !
