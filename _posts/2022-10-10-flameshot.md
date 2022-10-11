---
title:  Flameshot Screenshot Tool
categories: [Linux]
tags: [linux]
---

**Flameshot is a cool program for taking screenshots.**

Docs: <https://flameshot.org/docs/>

Arch Wiki: <https://wiki.archlinux.org/title/Flameshot>

![](/images/flameshot-hero.jpg){: width="600" .normal }

## 1. Download the Flameshot package:

Arch Linux:
```sh
sudo pacman -S flameshot
```

**To launch Flameshot from terminal:**

```sh
flameshot gui
```

## 2. Make sure you have Xbindkeys installed:

Arch Linux:
```sh
sudo pacman -S xbindkeys
```

If this is your first time setting up Xbindkeys, follow the instructions on the <a href="https://wiki.archlinux.org/title/Xbindkeys" target="_blank">ArchWiki</a> for:
- **2 Configuration**
- **3 Identifying keycodes**
- **4 Making changes permanent**

## 2. Bind your "Print Screen" key to launch Flameshot 

Open the Xbindkeys config file in your favourite editor:

```sh
~/.xbindkeysrc
```
Add Flameshot to launch when you press "Print Screen":

```sh
"flameshot gui"
   Print
```
**(Use the keycode specific to your machine, in my case the keycode is Print)**

## 3. Set up the Flameshot config file:

Open the configuration file in your favourite text editor:

```sh
~/.config/flameshot/flameshot.ini
```

Add these lines to the file:

```ini
[General]
drawColor=#ffff00
drawThickness=2
savePath=<path to save directory>
```
(Edit these values to change the initial draw color, line thickness, save directory, etc.)

## 4. Using Flameshot:

**Now when you press the "Print Screen" key it will launch Flameshot.**

The docs are here: https://flameshot.org/docs/guide/key-bindings/

- To change the color of the drawing tool: 

    > **Right click**

- To change the thickness of the drawing tool: 

    > **Mouse wheel**

- To open the side panel: 

    > **Space**

<kbd>CTRL</kbd>+<kbd>Z</kbd>

<br>

![](/images/flameshot-color.png){: width="800" .normal }
