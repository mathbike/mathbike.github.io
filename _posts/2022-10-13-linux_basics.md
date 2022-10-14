---
title:  Some Basic Linux Commands
categories: [Linux]
tags: [linux]
---

## Arch Linux

Update:
```terminal
sudo pacman -Syu
```

Update with ignore flag:
```terminal
sudo pacman -Syu --ignore package_name
```

## Mount

Create a mount point:
```terminal
mkdir /mnt/usbstick
```

Mount:
```terminal
sudo mount /dev/sdb1 /mnt/usbstick
```

Unmount:
```terminal
sudo umount /mnt/usbstick
```

## Xdotool

GitHub repo:
<a href="https://github.com/jordansissel/xdotool" target="_blank">https://github.com/jordansissel/xdotool</a>

Get mouse location:
```sh
watch -t -n 0.001 xdotool getmouselocation
```

---

{% include signature.md %}