---
toc: true
layout: post
comments: true
description: Some quick notes on iterm2 shortcut
categories: [markdown, tech]
title: Enable shortcut to jump one word back and forward in iTerm2
---

iTerm2 is commonly used as a terminal emulator on macOS. It is a great tool for developers. However, it does not have a shortcut to jump one word back and forward. This is a quick note on how to enable this feature.

Killing a fly with a cannon:

1. Go to Preferences... > Profiles > Keys (not Preferences... > Keys)
2. On current versions (3.14+) you then switch to the Key Mappings tab
3. Press Presets... dropdown button.
4. Select Natural Text Editing
![](https://user-images.githubusercontent.com/18030843/155436778-b4812d4d-34ad-4d7d-b2bc-890e101716db.png)

Then, you can

- move a word backwards Option ⌥ + ←
- move a word forwards Option ⌥ + →
- move to the start of the line fn + ←
- move to the end of the line fn + →
- delete a word backwards Option ⌥ + ⌫
- delete the whole line Command ⌘ + ⌫

# Reference
1. <https://apple.stackexchange.com/a/293988>