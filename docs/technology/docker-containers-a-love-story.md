---
title: Docker A Love Story
tags:
  - Linux
  - Docker
  - Containers
cover: https://i.imgur.com/wewgLnu.png
---
### What is Docker ?

[**Docker**](https://docker.com/){:target="_blank"} is a platform that simplifies the process of developing, shipping, and running applications by using containerization. Containers package an application and its dependencies into a single, portable unit that can run consistently across different environments.

<p align="center">
    <img width="500" src="https://i.imgur.com/bbD4JDy.png" alt="logo">
</p>

### How it all started

It all started with [**Distrobox**](https://distrobox.it/){:target="_blank"}. Yes a highly unlikly scenario I know. But the more I dug into the world of containerization the more intrigued I got. And that's when I discovered **Docker** containers, their countless uses. What blew me away mostly, is the fact that I can run cloud services like [**Immich**](https://immich.app/){:target="_blank"} for images and videos, which would allow me to sync my devices locally rather than with [**Apple iCloud**](https://icloud.com){:target="_blank"} or **Google** making me the sole owner of my data. So freeing OMG !!! No longer bound by those shackles...

With that, I the deeper I went through this bottomless rabbit hole, the more truly useful containers I found. The idea that I can do whatever I wanted without having to deal with any 3rd party conglomerates made me fall in love more and more as time went by...

### My setup so far

Yep, I know, you are eager to see what I have managed to pull off with everything I found. First, let me say this, I will not be the one guiding you on how to acheive **MY** setup, since your needs might differ from mine. Heck I am sure of it. Anyway, here's a screenshot, and below it I will link to the various containers I am using in case you find them useful.

<p align="center">
    <img width="500" src="https://i.imgur.com/DhfbUBs.png" alt="logo">
</p>

- **Homepage**

To start off, let me tell you what am using for the page you see in the image, it's simply called [**Homepage**](https://gethomepage.dev){:target="_blank"}. Fitting name right ? I love its simplistic design, flexibility, and most of all what sold me on it is two-fold, the fact that everything is done via [**YAML**](https://en.wikipedia.org/wiki/YAML){:target="_blank"} configurations files, and that the community behind it are so damn friendly ! Yep, there is no *dumb* question for them, they answer any and all to the best of their abilities.If you have any, feel free to join their [**Discord Server**](https://discord.gg/k4ruYNrudu){:target="_blank"}.

- **File Browser**

As for the File Browser I use to share files between PCs, it's also has a *creative* name lol, just called [**FileBrowser**](https://filebrowser.org){:target="_blank"}, it serves one purpose, browsing files, with ability to upload & download from/to any PC. That's it. It just works nothing else to say about that.

- **Search Engine (Xoogle)**

Hehe, the only reason I called it *Xoogle* is coz it's Xero + Google, get it ? Anyway, this is using something called [**Whoogle**](https://whoogle.io){:target="_blank"}, weird name I know, loogs damn ugly too. It's just a search engine that uses **Google** stripping it of all A.I crap and ads. Does its job I prefer it to any other coz I get the power of **Google** the way it was back in the day..

- **Vaultwarden**

That's a 3rd-party [**Bitwarden**](https://bitwarden.com){:target="_blank"} server-as-a-container, endorsed by them so can be trusted called [**Vaultwarden**](https://github.com/dani-garcia/vaultwarden){:target="_blank"}. I use it coz I prefer to self-host private stuff like that. Where I have total control. I still keep a copy hosted by them. It's just in case they go under I am safe.

- **ShareX**

This one is not for everyone. It uses [**Zipline**](https://zipline.diced.sh){:target="_blank"}. It's a File upload server with a twist. I exposed mine to the web, using it to share files with friends. Use it if you need something like that.

- **My Comics**

I am a big fan of comic books, especially the ones from my childhood. This container uses [**Kavita**](https://kavitareader.com/){:target="_blank"}. I love it simplicity. I am also proud to say that I currently sponsor their work coz devs are very friendly so is this tool. It works for my needs, I hope it does for you in case you choose to use it. If you have any, feel free to join their [**Discord Server**](https://discord.gg/b52wT37kt7){:target="_blank"}.

- **Audiobookshelf**

I guess I do not need to explain that one. It's just a docker container for [**Audiobookshelf**](https://www.audiobookshelf.org){:target="_blank"}. In case you have some Audio books or podcasts. Have fun.

- **FreshRSS**

That too doesn't need an introduction, just that it's the feed agregator I chose to use. Called [**FreshRSS**](https://www.freshrss.org){:target="_blank"}. It's simple to use, looks good enough, and supports tons of plugins to extend it above and beyond.

- **Immich**

Now, this is one of the big ones, [**Immich**](https://immich.app){:target="_blank"} is an amazing image cloud like service. Allowing you to move away from **Apple** and **Google**. I love that as I said at the beginning of this long post. They even have companion apps for both [**Android**](https://play.google.com/store/apps/details?id=app.alextran.immich){:target="_blank"} and [**iOS**](https://apps.apple.com/sg/app/immich/id1613945652){:target="_blank"} which makes it even more amazing. Now we can sync out photos and videos between devices. I recommend this one to everyone who cares about their data.

### You get the idea

Now am not gonna go over each and ever one of the containers I use. I will list the rest below linking to their related pages, have fun discovering them. Be careful though, once you begin there will be no end in sight. It's **BIG** rabit hole. You have been warned lol ! It's a super fun and nerdy adventure. Trust me. I have been here for over 3 months.

- [**Plex Server**](https://plex.tv){:target="_blank"}
- [**meTube**](https://github.com/alexta69/metube){:target="_blank"}
- [**Koel**](https://koel.dev){:target="_blank"}
- [**Tautulli**](https://tautulli.com){:target="_blank"}
- [**Portainer**](https://www.portainer.io){:target="_blank"}
- [**PairDrop**](https://github.com/schlagmichdoch/pairdrop){:target="_blank"}
- [**IT-Tools**](https://github.com/CorentinTh/it-tools){:target="_blank"}
- [**Cockpit**](https://cockpit-project.org){:target="_blank"}

### Where to find more containers ?

Well, there are many places, but my favorite has to be [**Selfh.st**](https://selfh.st/apps/){:target="_blank"} hands down. I love how they keep the list up-to-date showing last commit date. Site is always updated removing old unmaintained projects replacing them with newer ones. I highly recommend you bookmark this site and keep visiting it from time to time.

### Closing words

Anyway, I hope you have enjoyed this post, and I have helped you discover something new. It's not always one finds something that re-ignites one's pation all over again. I know it did just that for me.

Thanks again for reading this. If you want to discuss the matter, you can *Toot* me on [**Fosstodon**](https://fosstodon.org/@XeroLinux){:target="_blank"} or by joining me on my [**Discord Server**](https://discord.gg/5sqxTSuKZu){:target="_blank"}.
