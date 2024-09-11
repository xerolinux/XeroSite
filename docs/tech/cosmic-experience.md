---
title: My Cosmic Experience
tags:
  - Linux
  - Cosmic
  - ArchLinux
---
!!! note

    Contents of this post reflect my own opinion and mine alone. Do not take anything written here as set in stone. It's my own bare-metal experience with the hardware I own. I cannot and will not speak for others. Maybe you had a better experience, and I am glad you did. Just keep that in mind.

### Installation

The [**Cosmic DE**](https://xerolinux.xyz/posts/arch-cosmic/){:target="_blank"} hype is real. I saw many reviews of it and was immediately pulled in and got the urge to install it n try it out for myself to see if it was being over-hyped/sensationalized or not. Simply because new things tend to be, it's the norm by now.

<p align="center">
  <img src="https://i.imgur.com/Fvl9uRU.png">
</p>

Since I am an avid **ArchLinux** user, that's how I installed it. I did not use the **Pop!_OS 24.04 LTS alpha** ISO from >> [**Cosmic Downloads**](https://system76.com/cosmic){:target="_blank"}. So my views come from there. So I cannot compare.

Anyway, before I talk about my experience using the DE, I would like to mention that, I did not use the **ArchInstall** profile to install it. Why you ask ? Simply because due to past experience, I learned the hard way not to fully trust them, they tend to be way too basic, missing a lot of essential packages. Don't get me wrong here, I am not saying that you shouldn't use them, far from it, if you just want basics doing everything else yourselves, feel free, but from a new user perspective who expect things to be more complete, please use Distros who do all that for you.

Now on to the more detailed things I have done to install **Cosmic**. I first installed **Arch Minimal** using the **ArchInstall** script, meaning that I avoided the profiles, & drivers sections completely, I always choose `Grub` as my bootloader, no swap since I have 32GB RAM, no Encryption either. And once in `chroot` I installed the DE the following way, knowing that, we can skip the use of `sudo` since we are still logged in as root...

```Bash
pacman -Syy && pacman -S cosmic linux-headers pacman-contrib xdg-user-dirs power-profiles-daemon wayland-protocols wayland-utils
```

<p align="center">
  <img src="https://i.imgur.com/tR8WJJI.png">
</p>

Now, that needs a bit of explaining. In case you were wondering why so few packages, well, it's because [**cosmic**](https://archlinux.org/packages/?sort=&q=cosmic&maintainer=&flagged=){:target="_blank"} is not a single one, it's a *Group* of packages or a *meta-package* as it is known as. That said, the reason I installed `linux-headers` is because for whatever reason, they were not included, same goes for the rest. Especially `xdg-user-dirs` without which no `Documents, Pictures, Videos...` folders will be created. Strange I know.

What I also found weird, is the fact that `cosmic-greeter` service was not being enabled after install which was netting me a boot to `TTY` session. So I had to enable it while at the same time generating the `user-dirs` via...

```Bash
systemctl enable cosmic-greeter.service && xdg-user-dirs-update
```

Keep in mind that I am doing all this while still in `chroot` post-install. Once I was done with this I exited the live environment and rebooted crossing my fingers and hoping that all went well.

### Experience

Now on to what y'all came here for. All was good, weel sorta, system rebooted into `Grub`, selected the OS and waitied... That's when I started to sweat a little, coz I was greeted with some `TTY dmsg` errors, flickering on and off. But after a few seconds I finally saw the **Cosmic Greeter** login screen, relief finally.

<p align="center">
  <img src="https://i.imgur.com/TPjWMjR.png">
</p>

I type my super secure password in n wait to see the Desktop. So far so good, or so I thought. More anxiety, as when I opened the Cosmic file manager, what I saw wasn't so great. Being n **nVidia** user, I thought could be a driver issue since on first boot it uses the not so great `nouveau` ones. That's why my first reflex was to install them GPU drivers. So I did.

After driver install was done, I rebooted and that's when my heart sank so deep I couldn't feel it anymore. Why ? How about a screen with so many errors in many colors complaining about `EGL drm` crap ? Yep wasn't showing the login screen anymore. OH NO! Failed already ?!?!?!?!?

As it turns out I had forgotten to include the `nVidia drm kernel modules` lol. What am I talking about ? How to do that you ask ? Well, for me that's what I did, could be different for you I dunno.

```Bash
sudo sed -i '/^MODULES=(/ s/)$/nvidia nvidia_modeset nvidia_uvm nvidia_drm)/' /etc/mkinitcpio.conf
sudo systemctl enable nvidia-suspend.service nvidia-hibernate.service nvidia-resume.service nvidia-powerd.service
echo -e 'options nvidia NVreg_UsePageAttributeTable=1 NVreg_InitializeSystemMemoryAllocations=0 NVreg_DynamicPowerManagement=0x02' | sudo tee -a /etc/modprobe.d/nvidia.conf
echo -e 'options nvidia_drm modeset=1 fbdev=1' | sudo tee -a /etc/modprobe.d/nvidia.conf && sudo mkinitcpio -P
```

After doing that, I rebooted again, heart in hand, fingers n toes crossed lol. Once rebooted, a sigh of relief, I could see the login screen again. So I login, and this time everything was great. Performance was so smooth n fast, sorta felt like **XFCE**. Fired up `top` to see memory usage, and to my surprise, it was only using 800mb RAM on fresh boot, that's almost 500MB less than **KDE Plasma** ! Nice !

Now came the time to configure the DE. Since I had watched so many videos regarding it, I had a general idea of what to do. Since I have 2 Nics (1 for each ISP), first order of business was to disable one keeping the other active. So I hover mouse over the tray icon, click it then attempt to click to disable the one I do not need, only to see that I couldn't do shit. They seem to just be static indicators, at least for now. So arming myself with all that knowledge I fire up terminal and run `nmtui` and deactivate it from there making sure it doesn't automatically reconnect on login.

Now on to the `System Settings`. I will not bore you with the details, suffice it to say, that's where the biggest Alpha cracks started to show up big time. User profile modification missing, Default Apps too. I mean I could barely do anything besides modify top panel, color scheme, applets, keyboard shortcuts (keybinds) and power profiles. There isn't even a way to enable autologin..

That's when I began to get frustrated. I mean, how were users online saying they had a great experience when some of the most important things were missing ? I don't understand.

Anyway, I then took my attention to the included apps. I open the launcher from the bottom dock and click a random one, didn't open, I thought was a mouse issue, so I click again, and again, only after a few clicks did app decide to finally run. WTF!! Angry, I open File Manager again n try to open a document, nothing... OMG!!! I mean not even default app to handle simple text document ? I mean **Cosmic-Notes** was there, just not handling documents...

I try to right-click > open with, only to see that part was missing as well, I mean it shows the open-with panel to the right, only nothing's there, it's empty. I kept repeating to myself "It's Alpha Software, calm down Steve".

To relax a bit n make things easier, I installed my toolkit. Then when I tried launching it from the app menu thingy, no matter how many times I clicked it wouldn't launch. So I tried adding a keyboard shortcut for it, still nothing. I guess it's because it's a `CLI` and no default app set ? I dunno.

Finally I decided to try out the thing that almost everyone's raving about, **Tiling/Stacking**. And yes, that part was amazing, worked out great no major deal breaking issues to speak of, just minor nit-picks. Nothing that wasn't mentioned in all them videos on the Tubes. Oh Great ! I thought to myself, sarcastically, coz the only thing that works best is the thing I will never use since I do not like that Tiling stuff. Meh...

That's where I gave up and decided to go back home to **KDE Plasma**.

### Final words

Now I know this wasn't a complete experience, but when the most essential features are either missing or incomplete, there's no point in going any further, simply because, the more I used it the more frustrated I got.

It's barely usable in its current state. I will be keeping it installed, revisiting it once every month to see progress. I will not, however attempt using it on a daily, or put in too much work into it, since it's not yet ready.

Now, I can't be mean to the devs, they are doing a great job. It was all a false expectation on my part. **Cosmic** has come a long way in such a short time. I mean, writing a DE from scratch using **Rust** a sorta new programming language is no easy feat.

I will end the post by congratulating the **System76** dev team on work well done. I cannot wait to see what the future holds. I wish them the best of luck. Oh and also, who knows if it wins me over, I might add a **XeroCosmic** to the family.. Just don't hold your breath on that, it ain't set in stone.
