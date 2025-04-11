---
toc: false
layout: post
comments: true
description: ssh visual reminder
categories: [markdown, tech]
title: SSH Visual Reminder via A Zsh Function
---

## Introduction
This post describes a Zsh function that provides a visual reminder when using SSH to connect to remote servers. The function checks if the current shell is an SSH session and, if so, the tab color of the terminal is changed to green. This serves as a visual cue to remind users that they are in an SSH session, which can help prevent accidental commands being run on the wrong server.

## Code
```zsh
if [[ -n "$ITERM_SESSION_ID" ]]; then
    tab-color() {
        echo -ne "\033]6;1;bg;red;brightness;$1\a"
        echo -ne "\033]6;1;bg;green;brightness;$2\a"
        echo -ne "\033]6;1;bg;blue;brightness;$3\a"
    }
    tab-red() { tab-color 255 0 0 }
    tab-green() { tab-color 0 255 0 }
    tab-blue() { tab-color 0 0 255 }
    tab-reset() { echo -ne "\033]6;1;bg;*;default\a" }

    function iterm2_tab_precmd() {
        tab-reset
    }

    function iterm2_tab_preexec() {
        if [[ "$1" =~ "^ssh" ]]; then
            tab-color 160 255 160
        fi
    }

    autoload -U add-zsh-hook
    add-zsh-hook precmd  iterm2_tab_precmd
    add-zsh-hook preexec iterm2_tab_preexec
fi
```
## Explanation
- The function `tab-color` changes the background color of the terminal tab.
- The function `tab-red`, `tab-green`, and `tab-blue` are shortcuts for setting the tab color to red, green, and blue respectively.
- The function `tab-reset` resets the tab color to the default.
- The function `iterm2_tab_precmd` resets the tab color before each command prompt.
- The function `iterm2_tab_preexec` checks if the command being executed is an SSH command. If it is, it sets the tab color based on whether the command contains "prod" or not.
- The `add-zsh-hook` command is used to add the `iterm2_tab_precmd` and `iterm2_tab_preexec` functions to the precmd and preexec hooks, respectively.
- The `[[ -n "$ITERM_SESSION_ID" ]]` check ensures that the script only runs in iTerm2, which supports the tab color change escape sequences.
- The `[[ "$1" =~ "^ssh" ]]` check ensures that the tab color change only occurs for SSH commands.
- The `tab-green` function is called when an SSH command is executed, changing the tab color to green.
- The `tab-reset` function is called before each command prompt to reset the tab color to the default.


## Reference
- https://gist.github.com/wadey/1140259
