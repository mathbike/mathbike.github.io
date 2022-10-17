---
title:  Some Basic Linux Commands
categories: [Linux]
tags: [linux]
---

## Arch Linux

- Update:
```terminal
sudo pacman -Syu
```

- Update with ignore flag:
```terminal
sudo pacman -Syu --ignore package_name
```

---

## Basics

- List files:
```terminal
ls -lah
```
    - The ls commands displays a list of files in a specific directory.  The -l flag lists the files in long format, the -a flag includes hidden files, and the -h flag shows the size in human readable form.

- Show disk space, with human readable flag:
```terminal
df -h
```
    - The df command

---

## Mount

- Create a mount point:
```terminal
mkdir /mnt/usbstick
```

- Mount:
```terminal
sudo mount /dev/sdb1 /mnt/usbstick
```

- Unmount:
```terminal
sudo umount /mnt/usbstick
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
    - The time command displays the time taken once completed, bs is the batch size, status shows the status while running.


### Create a bootable usb drive

- Unmount drive:
```terminal
umount /dev/"drive"
```

- Format drive:
```terminal
mkfs.ext4 /dev/"drive"
```

- Create the bootable usb drive:
```terminal
time dd if="input_file_path" of="output_file_path" bs=1M status=progress
```

{% include signature.md %}