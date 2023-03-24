---
toc: true
layout: post
comments: true
description: Some quick notes on mouse and keyboard automation using Python
categories: [markdown, tech, library]
title: Pyautogui
---

# Introduction

## What is Pyautogui?

**Pyautogui** is a Python module for controlling the mouse and keyboard. It can be used to automate mouse clicks, keyboard presses, and other interactions with the computer. It can also be used to take screenshots, locate images on the screen, and perform other image recognition tasks.

# Usage

## Installation

```pip3 install pyautogui```

## Example

```python
import pyautogui
# move the mouse to the x, y coordinates 100, 100
pyautogui.moveTo(100, 100, duration=0.25)
# click the mouse
pyautogui.click()
# type some text
pyautogui.typewrite('Hello world!', interval=0.25)
# press the esc key
pyautogui.press('esc')
# press the enter key
pyautogui.press('enter')
```
```python
>>> distance = 200
>>> while distance > 0:
        pyautogui.drag(distance, 0, duration=0.5)   # move right
        distance -= 5
        pyautogui.drag(0, distance, duration=0.5)   # move down
        pyautogui.drag(-distance, 0, duration=0.5)  # move left
        distance -= 5
        pyautogui.drag(0, -distance, duration=0.5)  # move up
```
![](https://pyautogui.readthedocs.io/en/latest/_images/square_spiral.png)

# Reference
1. [Geeksforgeeks](https://www.geeksforgeeks.org/mouse-keyboard-automation-using-python/)
2. [Pyautogui](https://pyautogui.readthedocs.io/en/latest/)
3. [Medium](https://medium.com/@martin.lees/how-to-control-the-mouse-and-keyboard-with-python-for-automation-34231b62dc88)