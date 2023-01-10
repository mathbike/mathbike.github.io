---
title:  VirtualBox
categories: [Virtual Machines]
tags: [virtual machines]
---

Arch Wiki:
<a href="https://wiki.archlinux.org/title/VirtualBox" target="_blank">https://wiki.archlinux.org/title/VirtualBox</a>

---

**Host:**

Install VirtualBox and Guest Additions packages:
```terminal
sudo pacman -S virtualbox virtualbox-guest-iso
```

---

**Guest:**

Install guest additions:
```
sudo pacman -S virtualbox-guest-utils
```
Do not install guest additions, enable shared clipboard, drives, or usb, if guest is intended to be exposed to potential viruses/malware.


