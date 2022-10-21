---
title:  Controlling the Mouse and Keyboard with Code
categories: [category]
tags: [tag]
---

## Python

**use the package**

---

### Each click of the mouse, output the x, y coordinates to XY.txt:
```python
from pynput.mouse import Listener

def on_click(x, y, button, pressed):
    if pressed:
        f = open("XY.txt", "a")
        f.write(str(x)+", "+str(y)+"\n")

def listener():
    # Collect events until released
    with Listener(
            on_click=on_click) as listener:
        listener.join()

listener()
```

---

## Xdotool

GitHub repo:
<a href="https://github.com/jordansissel/xdotool" target="_blank">https://github.com/jordansissel/xdotool</a>

---

- Get mouse location:
```sh
watch -t -n 0.001 xdotool getmouselocation
```
