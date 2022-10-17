---
title:  Gpg Keys and Password Management
categories: [Security]
tags: [gpg, passwords]
---

## Gpg Keys

---

## Pass Password Manager

Website:
<a href="https://www.passwordstore.org/" target="_blank">https://www.passwordstore.org/</a>

Arch Wiki:
<a href="https://wiki.archlinux.org/title/Pass" target="_blank">https://wiki.archlinux.org/title/Pass</a>

---

- Install:
```terminal
sudo pacman -S pass
```

- Initialize new password store:
```terminal
pass init gpg-id_or_email
```

- View password store:
```terminal
pass
```

- dmenu list:
```terminal
passmenu
```

- Show password:
```terminal
pass archlinux.org/wiki/username
```

- Copy password to clipboard:
```terminal
pass -c archlinux.org/wiki/username
```

- Insert password to password store:
```terminal
pass insert archlinux.org/wiki/username
```

- Insert multiline password to password store:
```terminal
pass insert -m archlinux.org/wiki/username
```

- Edit password:
```terminal
pass edit archlinux.org/wiki/username
```

- Generate password of n characters long:
```terminal
pass generate archlinux.org/wiki/username n
```

- Generate password with no symbols:
```terminal
pass generate -n archlinux.org/wiki/username
```

- Remove password:
```terminal
pass rm archlinux.org/wiki/username
```

{% include signature.md %}