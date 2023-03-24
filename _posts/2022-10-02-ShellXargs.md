---
toc: true
layout: post
comments: true
description: Some quick notes on Shell Command Xargs
categories: [markdown, tech]
title: Shell Command xargs
---

# Introduction
`xargs` is a command that reads data from the standard input and executes a command with the data as arguments. It is used to build and execute command lines from standard input.

# Usage
Normally when we want to create a file with a specific name, we would do something like this:
```bash
touch NewFile.txt
```
With `xargs`, we can do the same thing:
```bash
echo "NewFile.txt" | xargs touch
```

# Differences between `xargs` and pipe
In Linux, pipe is used to connect the output of one command to the input of another command. For example, we can use `ls` to list all files in the current directory, and then use `grep` to filter the files that contain a specific string. The following command will list all files that contain the string `test`:
```bash
ls | grep test
```
This works when the second command accepts standard input. However, if the second command does not accept standard input, e.g. `touch` we need to use `xargs` to parse the content into argument list.
For example:
```bash
# if you echo new filename and pipe to touch
# it will prompt error
$ echo "NewFile" | touch
usage: touch [-A [-][[hh]mm]SS] [-achm] [-r file] [-t [[CC]YY]MMDDhhmm[.SS]]
       [-d YYYY-MM-DDThh:mm:SS[.frac][tz]] file 
# This happens when the second command does not accept standard input
# touch is a command that only accepts filename as argument

# Correct Usage:
$ touch "NewFile.txt"

# Using xargs to transform the content into argument list
$ echo "NewFile.txt" | xargs touch
```
Another Example is `wc`:
```bash
# if you echo a string and pipe to wc
$ echo "hello world" | wc
       1       2      12
# this is because wc only accepts standard input instead of argument list
$ wc
Hello World
       1       2      12
# therefore, we do not need to use xargs
```

# References
1. [Linux manual page](https://man7.org/linux/man-pages/man1/xargs.1.html)
2. [Linux Command List](https://www.runoob.com/linux/linux-command-manual.html)