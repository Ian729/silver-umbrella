---
toc: true
layout: post
comments: true
description: Some quick notes on daily frequently used git commands
categories: [markdown, tech]
title: Daily Git Commands
---

# Introduction
`git` is a version control system that is widely used in software development. It is a distributed version control system that allows developers to work on the same project at the same time. It is also a powerful tool that can be used to track changes in files and revert to previous versions.
## Git Workflow
![Git Workflow](https://git-scm.com/book/en/v2/images/areas.png)
## Git Stages
![Git Stages](https://git-scm.com/book/en/v2/images/lifecycle.png)
Staging area is a concept that is often used in `git`. It is a temporary area where files are stored before they are committed to the repository.

# Usage
## Create a new repository
```bash
# create a new directory
$ mkdir myproject
# change directory
$ cd myproject
# initialize the directory as a git repository
$ git init
```
## Clone an existing repository
```bash
# clone the repository
$ git clone https://github.com/ian729/silver-umbrella.git
```

## Add files to the staging area
```bash
# add all files in the current directory to the staging area
$ git add -A
# add a specific file to the staging area
$ git add README.md
```

## Commit changes
```bash
# commit all changes in the staging area
$ git commit -m "commit message"
```

## Push changes to remote repository
```bash
# push changes to remote repository
$ git push
```

## Mixed reset(default)
```bash
# reset all changes in the staging area
$ git reset
$ git reset --mixed
# reset a specific file in the staging area
$ git reset README.md
```

## Hard reset
```bash
# hard reset all changes in the staging area
$ git reset --hard
# hard reset a specific file in the staging area
$ git reset --hard README.md
```

## Soft reset
```bash
# soft reset all changes in the staging area
$ git reset --soft
# soft reset a specific file in the staging area
$ git reset --soft README.md
```

## Difference between three reset types
| Type | Staging Area | Working Directory |
| --- | --- | --- |
| Mixed | Reset | Not Reset |
| Hard | Reset | Reset |
| Soft | Not Reset | Not Reset |

![Git Reset](https://www.howtogeek.com/wp-content/uploads/csit/2021/07/f5026f58.png?width=1200&trim=1,1&bg-color=000&pad=1,1)



## Revert changes
```bash
# revert all changes in the staging area
$ git checkout -- .
# revert a specific file in the staging area
$ git checkout -- README.md
```

## Squash commits
```bash
# squash the last 3 commits into one
$ git rebase -i HEAD~3
```

## Pull changes from remote repository
```bash
# pull changes from remote repository
$ git pull
# pull changes while rebasing local commits
$ git pull --rebase
```
![Rebase](https://miro.medium.com/max/720/1*pzT4KMiZDOFsMOKH-cJjfQ.png)


# References
1. [Git Documentation](https://git-scm.com/doc)
2. [Git Tutorial](https://www.runoob.com/git/git-tutorial.html)
3. [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
4. [Git Cheat Sheet](https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet)
5. [Git Cheat Sheet](https://www.git-tower.com/blog/git-cheat-sheet/)