---
toc: false
layout: post
comments: true
description: oh my zsh plugins syntax highlight and auto suggest
categories: [markdown, tech]
title: Oh My Zsh syntax-highlighting and autosuggest
---

## Introduction
Oh My Zsh is a delightful, open source, community-driven framework for managing your Zsh configuration. It comes bundled with a ton of helpful functions, helpers, plugins, themes, and a few things that make you shout... "Oh My Zsh!"

## Installation
URL: https://ohmyz.sh/  
To install Oh My Zsh, run the following command:
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## Plugins
Oh My Zsh comes with a lot of plugins that can be enabled by adding the plugin name to the `plugins` array in the `.zshrc` file. Two of the most useful plugins are `syntax-highlighting` and `autosuggestions`.

### Syntax Highlighting
URL: https://github.com/zsh-users/zsh-syntax-highlighting
1. Clone this repository in oh-my-zsh's plugins directory:
```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```
2. Activate the plugin in ~/.zshrc:
```
plugins=( [plugins...] zsh-syntax-highlighting)
```
3. Restart zsh (such as by opening a new instance of your terminal emulator).

### Autosuggestions
URL: https://github.com/zsh-users/zsh-autosuggestions
1. Clone this repository into $ZSH_CUSTOM/plugins (by default ~/.oh-my-zsh/custom/plugins)
```
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

2.  Add the plugin to the list of plugins for Oh My Zsh to load (inside ~/.zshrc):
```
plugins=( 
    # other plugins...
    zsh-autosuggestions
)
```

3. Start a new terminal session

## Reference
- [Oh My Zsh](https://ohmyz.sh/)
- [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)
- [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)
