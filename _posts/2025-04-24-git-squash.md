---
toc: false
layout: post
comments: true
description: A simple and powerful Git plugin to squash your commits before creating a Pull Request.
categories: [markdown, tech, tools]
title: Introducing git squash: A Simple Git Squashing Tool
---
# git-squash

A simple and powerful Git plugin to squash your commits before creating a Pull Request.

This tool provides a unified interface to squash commits:
- By base branch name (e.g., `main`, `master`)
- By number of recent commits
- By specific commit SHA

---
## 🚀 Installation

1. Download the `git-squash` script and save it to a directory in your `$PATH`, e.g.:

   ```bash
   curl -o ~/bin/git-squash https://raw.githubusercontent.com/Ian729/git-squash/main/git-squash
   chmod +x ~/bin/git-squash
    ```

2. Ensure the directory is in your $PATH. Add this to your .bashrc / .zshrc if needed:

    ```bash
    export PATH="$HOME/bin:$PATH"
    ```

## Usage
```bash
git squash <base-branch>
git squash <number-of-commits>
git squash --sha <commit-sha>
```

## Examples
✅ Squash all commits made since branching from main:
```bash
git squash main
```
✅ Squash the last 3 commits:
```bash
git squash 3
```
✅ Squash all commits made since a specific commit:
```bash
git squash --sha <commit-sha>
```

## Note
- This tool uses git reset --soft, preserving your working directory and staging area.

- After squashing, use git push --force-with-lease to update the remote branch:

    ```bash
    git push --force-with-lease
    ```

- Default commit message is Squashed commit, but you can provide a custom message during the prompt.

## 🛠️ Why use git-squash?
- Keep your PR history clean.

- Avoid git rebase -i complexity in simple squash workflows.

- Fast, scriptable, and beginner-friendly.

## 📄 License
MIT License
