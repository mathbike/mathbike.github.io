---
title:  Flameshot Screenshot Tool
categories: [Linux]
tags: [linux]
img_path: /images/flameshot/
---

**Flameshot is a cool program for taking screenshots.**

---

GitHub: 
<a href="https://github.com/flameshot-org/flameshot" target="_blank">https://github.com/flameshot-org/flameshot</a>

Docs: 
<a href="https://flameshot.org/docs/" target="_blank">https://flameshot.org/docs/</a>

Keybindings:
<a href="https://flameshot.org/docs/guide/key-bindings/" target="_blank">https://flameshot.org/docs/guide/key-bindings/</a>

Arch Wiki:
<a href="https://wiki.archlinux.org/title/Flameshot" target="_blank">https://wiki.archlinux.org/title/Flameshot</a>

![](flameshot-hero.jpg){: width="600" .normal }

---

## 1. Download the Flameshot package

Arch Linux:
```terminal
sudo pacman -S flameshot
```

## 2. Make sure you have Xbindkeys installed

Arch Linux:
```terminal
sudo pacman -S xbindkeys
```

If this is your first time setting up Xbindkeys, follow the instructions on the <a href="https://wiki.archlinux.org/title/Xbindkeys" target="_blank">ArchWiki</a> for:
- **2 Configuration**
- **3 Identifying keycodes**
- **4 Making changes permanent**

## 2. Bind your "Print Screen" key to launch Flameshot 

Open the Xbindkeys config file:

```terminal
~/.xbindkeysrc
```
Add this to the file to make Flameshot launch when you press "Print Screen":

```sh
"flameshot gui"
   Print
```
**(Use the keycode specific to your machine, in my case the keycode is Print)**

## 3. Set up the config

Open the configuration file:

```terminal
~/.config/flameshot/flameshot.ini
```

Add these lines to the file:

```ini
[General]
drawColor=#ffff00
drawThickness=2
savePath=<path_to_save_directory>
```
- Edit these values to change the initial draw color, line thickness, save directory, etc.

Open the config gui:

```terminal
flameshot config
```
- Under the "Interface" tab select "Increase Tool Size" and "Decrease Tool Size" to make those buttons available

- Under the "General" tab select "Allow multiple flameshot gui instances simultaneously" to allow multiple instances

## 4. Using Flameshot

| Command | Description |
| - | - |
| <kbd>PrntScr</kbd> | Take screenshot |
| `flameshot gui` | Launch from terminal |
| `flameshot config` | Edit config |
| Right Click | Change color of drawing tool |
| Mouse Wheel | Change thickness of drawing tool |
| <kbd>Spacebar</kbd> | Open side panel |
| <kbd>Ctrl</kbd>+<kbd>s</kbd> | Save image |

{% include signature.md %}