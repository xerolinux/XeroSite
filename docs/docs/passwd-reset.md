---
title: Reset Password
tags:
  - Linux
  - Reset
  - Recovery
---
### Information

I have lost my root pass on **Linux** more times than I can count. This guide is here so I do not have to *Google* it lol. Might be useful to you I dunno. But it's here.

<p align="center">
    <img src="https://i.imgur.com/VFXV09r.jpeg">
</p>

### Let's do this 🚀

How to reset forgotten root password in a **GNU/Linux** distribution with `GRUB`?

If this is a laptop or a desktop which you have next to you then follow these steps.

1. Shut down the device.
2. Start it again. When you see GRUB menu, press the `e` key on the keyboard before the system starts booting.
3. In the `GRUB` boot options, scroll down and locate the line that begins with `linux`. In this line move the cursor to the end, right after `ro quiet`. Delete everything after that. Change `ro` to `rw`. Append the parameter `init=/bin/bash`
4. Press Ctrl+x, or F10, to boot.
5. You will see a root prompt.

```Bash
:#
```

Remount the filesystem in read/write mode:

```Bash
:# mount -no remount,rw /
```

6. Set the password of any user(s).

```Bash
:# passwd joe
```

7. Reboot with the command `reboot -f`.

That's it ! The new password should work now.
