---
title: Linux in a Nutshell
tags:
  - Linux
  - Kernel
  - Packages
---
I thought I'd share this explanation about **Linux** a good friend and fellow Linux enthusiast [**REALERvolker1**](REALERvolker1){:target="_blank"} recently posted on **Discord**.

!!! tip

    Please do not take this as a complete walk-through, We did not even go through the various *Desktop Environments* or *Window Managers* that exist today, way too many to list. Still we hope it gives you some idea of what you are walking into when swtiching...

### What is Linux ?

Since not everyone's super familiar with Linux, here's a quick crash course.

Linux is a [**Monolithic Kernel**](https://en.wikipedia.org/wiki/Monolithic_kernel#:~:text=A%20monolithic%20kernel%20is%20an,virtual%20interface%20over%20computer%20hardware.){:target="_blank"}, so all the drivers and whatnot are compiled into the binary. The [**Nonfree software**](https://www.fsf.org/about/what-is-free-software){:target="_blank"} is usually put in the actual source repo as binary blobs, or in the case of **nVidia** drivers, built using a system called [**DKMS**](https://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support){:target="_blank"} and compiled into the kernel binary.

Once the computer boots up, an init process is started (the default is `/sbin/init`, usually a symlink to your init system), which is `PID 1`. This is when userspace is initialized. Due to security concerns and whatnot, you are restricted from having too much fun in userspace, so you need to ask the kernel to read files and allocate memory for you using syscalls.

Anyways, init starts all the userspace stuff (it itself is run in userspace) and this keeps the system secure. Since Linux is monolithic, you can't just throw a malicious library into kernel space at runtime somehow, you have to compile it in. Anyways, Linux is a lot like Unix, with one notable difference being that Linux Is Not UniX. This means it uses the typical Unixy way of doing things like restricting access based on users and groups, being [**POSIX**](https://en.wikipedia.org/wiki/POSIX){:target="_blank"} compliant, and not really caring about file extensions.

<p align="center">
    <img width="600" src="https://i.imgur.com/Mu7NHx9.png" alt="logo">
</p>

### Distros & PKG Managers

On [**Debian**](https://www.debian.org){:target="_blank"}, you install packages with `apt`. If you can't remember the package name you want, you can use apt to search for it, or use synaptic as a *GUI* frontend. If your desktop environment comes with one, you can use theirs, as that one should be easier to use, while still providing the exact same functionality. You don't install programs by downloading them from the internet. If you have any questions, the [**Debian Wiki**](https://wiki.debian.org/DontBreakDebian){:target="_blank"} is pretty mid, but the [**Arch Wiki**](https://wiki.archlinux.org){:target="_blank"} is amazing.

Since [**Arch Linux**](https://archlinux.org){:target="_blank"} is intended to be the most generic *Linux distro* ever, stuff written for **Arch** should also help with **Debian**, as long as the Arch package didn't get a bunch of major updates in the interim. There are also other ways of installing stuff, like **Flatpak** (sandboxed apps that "just work" on every distribution), and **Snap** (Ubuntu's sandboxed apps that they claim work on every distribution but have always been kind of sketchy). There are also **AppImages** which are basically like `.exe's` on **Windows**, but they're kind of a hassle to use compared to the others because you have to add executable permission to them, and then manually double click them. Plus they won't have a desktop entry.

### Filesystem & Updates

If you are connecting the system to the internet, you should update at least once a week, so you don't get your entire network hacked through a known vulnerability. If you aren't connecting it to the internet, you can choose whether to update or not --it might fix a bug.

As for the filesystem, `/etc` is where your Editable Text Configurations go. `/usr` is where program files go. `/usr/local` is where program files go for programs you manually installed. `/home` is where your stuff goes. `/dev` is for devices. there is no **C** drive or **D** drive, you have to mount the external drive to the place you choose, for example, `/mnt`. A *GUI* file manager mounts flash drives somewhere in `/run` usually, because it's temporary. `/opt` is where random stuff goes, and `/var` is for variable storage like system logs. `/tmp` is self-explanatory. `/dev/null` is a bottomless pit, and `/dev/urandom` is a quick and easy IO-based random number generator. In [**UNIX**](https://en.wikipedia.org/wiki/Unix){:target="_blank"}, everything is a file. This means you can see process details by reading the files in `/proc`, see system settings or driver configs in /sys, or see your bootloader in `/boot`

### Wrapping it all up

This here was a quick run-through explaining what **GNU/Linux** is written as mentioned earlier by a good friend. I did not post it on main site simply because I feel it's not as complete as I would like it to be.
