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

---

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

---

## Xdotool

GitHub repo:
<a href="https://github.com/jordansissel/xdotool" target="_blank">https://github.com/jordansissel/xdotool</a>

---

Get mouse location:
```sh
watch -t -n 0.001 xdotool getmouselocation
```

---

## dd

Arch Wiki:
<a href="https://wiki.archlinux.org/title/Dd" target="_blank">https://wiki.archlinux.org/title/Dd</a>

---

- Zero fill drive:
```terminal
time dd if=/dev/zero of="drive" bs=1024 status=progress
```

- Random fill drive:
```terminal
time dd if=/dev/urandom of="drive" bs=1024 status=progress
```

The time command displays the time taken once completed.  The status flag shows the status while running.


### Create a bootable usb drive

- Unmount drive:
```terminal
umount /dev/"drive"
```

- Format drive:
```terminal
mkfs.ext4 /dev/"drive"
```

- Create the bootable usb:
```terminal
time dd if=/home/mike/iso/archlinux-2021.10.01-x86_64.iso of=/dev/"drive" bs=1M status=progress
```

---
<br>
{% include signature.md %}