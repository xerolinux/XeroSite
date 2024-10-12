---
title: SDDM Display
tags:
  - Linux
  - SDDM
  - Display
---
### Information

Login session appears on an unexpected display. It can happen that the **SDDM** login session appears on a different display than your primary display if multiple displays are connected. This problem can be annoying if the secondary display is rotated and the primary display is not. A simple fix to this problem is to use `xrandr` to configure the displays before the login session using Xsetup script. E.g. here `xrandr` reports that there are two or more connected displays where the secondary display (DP-2) is left of the primary display (DP-4).

<p align="center">
    <img src="https://i.imgur.com/c6fj1u4.png">
</p>

### Let's fix it 🚀

We need to be logged in to an *X-Session* meaning `X11` to gat the correct display names, we cannot use display names from `Wayland` session won't work for some reason, maybe because **SDDM** runs in `X11` ? No idea, now run this command in terminal to get their names. Need to have `xrandr` package installed.

```Bash
xrandr | grep -w connected
```

Output should be like this (mine)

> HDMI-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 521mm x 293mm <br />
  DP-2 connected primary 2560x1440+1920+0 (normal left inverted right x axis y axis) 598mm x 336mm <br />
  HDMI-0 connected 1920x1080+4480+0 (normal left inverted right x axis y axis) 531mm x 299mm

This is my own `Xsetup` for the login window, yours may differ :

```Bash
#!/bin/sh
# Xsetup - run as root before the login dialog appears

xrandr --output DP-2 --auto --primary
xrandr --output HDMI-1 --auto --left-of DP-2 --noprimary
xrandr --output HDMI-0 --auto --right-of DP-2 --noprimary
```

If you want to manually edit the file

```Bash
sudo nano /usr/share/sddm/scripts/Xsetup
```

Paste the output of your `xrandr` command as I did above in there save & reboot.

That's it y'all..
