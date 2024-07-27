---
title: VMWare Workstation Pro Free ? Why ?
date: 2024-05-30 13:14:15
tags:
  - Linux
  - VMWare
  - Virtualization
cover: https://i.imgur.com/JtaoqqU.jpeg
---

### What's VMWare ?

[**VMWare Workstation Pro**](https://www.vmware.com/) is a powerful software tool that allows users to create and manage multiple virtual machines on a single physical computer. It enables users to run different operating systems simultaneously, providing a versatile environment for testing, development, and learning. With VMWare Workstation Pro, you can easily switch between virtual machines, share files, and even emulate entire networks, making it an essential tool for IT professionals and enthusiasts who need a flexible and efficient way to work with multiple systems without the need for separate hardware.

### What happened ?

Ever since [**Broadcom**](https://investors.broadcom.com/news-releases/news-release-details/broadcom-completes-acquisition-vmware)'s acquisition of **VMware**, we have seen them drop the hammer on many existing customers by ditching perpetual licenses, in favor of a subscription-based licensing model.

They even shut down the VMware Cloud Services Provider program, while only inviting a select few vendors back into the fold under the **Broadcom Expert Advantage Partner** program.

Interestingly, in a recent announcement, they have chosen to give something back to their community by making two popular **VMware** products free. It was a surprise.

### Generous ? Maybe not.

In an unexpected move, **Broadcom** has made **VMWare Fusion Pro** and **VMWare Workstation Pro** free for all kinds of personal usage. We will focus on **Workstation Pro**, as that is available for **Linux**; **Fusion Pro** is a **macOS**-only affair.

Now, if you are someone who wants to use a hypervisor for a personal project or want one just to check out a couple of Linux distros. You do not have to pay a dime to access the advanced features that Workstation Pro offers.

However, for commercial usage, you still have to pay for a subscription, which can be sourced through a [**Broadcom Advantage Partner**](https://www.broadcom.com/how-to-buy/software-partners/partnering-with-broadcom).

Additionally, **VMware** is retiring the previous player versions of both **Workstation** and **Fusion**, with a detailed process for existing users on how to upgrade to the pro variants.

They also shared a helpful table to guide users with the migration. 👇

<div align="center">

![GPU](https://i.imgur.com/L8ojsV2.jpeg)

</div>

To dive deeper into what's going on, you may refer to the [**announcement blog**](https://blogs.vmware.com/teamfusion/2024/05/fusion-pro-now-available-free-for-personal-use.html?ref=news.itsfoss.com).

### Get VMware Workstation Pro

You can get the latest builds of **VMware Workstation Pro** from the **Broadcom** customer portal. Unfortunately, you will have to sign in using a Broadcom account to get access. If you don't have an account, then you will have to make one.

<div align="center">

### [Download VMWare Pro](https://support.broadcom.com/group/ecx/productdownloads?subfamily=VMware+Workstation+Pro)

</div>

You would think the download process would be straightforward, but no. First, you have to log in, then choose the “Personal” variants; otherwise, it will throw an error saying “Not Entitled”.

Then, you have to fill out a *“Trade Compliance Verification”* form before the portal allows you to download anything. Remember the simpler days, when getting VMware was just a matter of a few clicks ?

### My thoughts on this...

First let me thank [**It's FOSS**](https://news.itsfoss.com/vmware-workstation-free/) for the original post. Now on with my thoughts on this whole situation. Let me start by asking you this, why does one still need to use any of these products on **Linux** ? We are more inclined to prioritize **FOSS** applications over **Proprietary** ones.

Well if you answered with, "coz am used to it and it just works", then I am totally onboard with you. But we still have the likes of [**KVM/QEmu**](https://www.linux-kvm.org/page/Main_Page) which is totally **FOSS**. The only reason I can see to prefer **VMWare** over it is if one wanted to use **Windows** VMs. Yes, they behave better on **VMWare** over **KVM** unless ones goes through the whole **GPU Passthrough** ordeal. Or we even have the likes of [**Proxmox VE**](https://www.proxmox.com/en/proxmox-virtual-environment/overview) that has tons of features, be it for **Windows** or **Linux**.

All this to just say, if you are an **Open Source** afficionado like I am, I would recommend you stick with either of the 2 I mentioned, and save yourself the headache. There are tons of others that I did not list here, just as long as you skip any of the **VMWare** products. But hey you do you, those were my 2 cents on the matter. If you still want to stick with **VMWare** on **Linux** don't forget to check out my guide over on the [**XeroLinux Forums**](https://forum.xerolinux.xyz/thread-129.html).

Thanks for reading. If you want to discuss this subject, see ya on my [**Discord Server**](https://discord.gg/5sqxTSuKZu).
