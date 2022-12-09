---
title:  Arch Linux Install
categories: [Linux]
tags: [linux, arch linux]
math: true
---

pre:
```sh
# Boot from usb then:
# Delete partitions
fdisk /dev/sda
d /dev/sda #/dev/nvme0n1
w
# Connect to wifi:
iwctl
station wlan0 connect “SSID”
pacman -Sy archlinux-keyring
archinstall # if running archinstall
# reboot
sudo pacman -S git
git clone https://github.com/mathbike/archmathbike.git
cd archmathbike
sh archmathbike.sh
```

---

archinstall wheel:
```sh
su root
# add user to wheel group
usermod -aG wheel mike
# edit wheel file
vim /etc/sudoers
# uncomment wheel group (allow sudo)
%wheel ALL=(ALL) ALL
```
