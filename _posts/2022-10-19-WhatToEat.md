---
toc: true
layout: post
comments: true
description: Some quick notes on automating small tasks using AppleScript and cron
categories: [markdown, tech, library]
title: AppleScript and Crontab
---

# Introduction

## Crontab
Add some crontab setting on your Mac:
```bash
crontab -e
```
then add the following line:
```bash
20 12 * * 1-7 sh ~/what-to-eat/show.sh
```
It literally means that the script `show.sh` will be executed every day at 12:20

Learn more about cron: [Crontab Guru](https://crontab.guru/)

## Shell Script
In Shell Script, we want to get the random choice from the list of food. We can use the following command:
```bash
#!/bin/sh
lunch=`python3 /Users/weixiang/what-to-eat/main.py`
osascript -e "display notification \"$lunch\" with title \"今天吃什么?\""
# 我叫 Mac 唸給妳聽！
# say $lunch
```
the random choice is stored in the variable `lunch`. Then we use the `osascript` command to display the notification.

The manual page of `osascript` can be found [here](https://ss64.com/osx/osascript.html).

```bash
osascript

Execute AppleScripts and other OSA language scripts. Executes the given script file, or standard input if none is given. Scripts can be plain text or compiled scripts. osascript was designed for use with AppleScript, but will work with any Open Scripting Architecture (OSA) language.

Syntax
      osascript [-l language] [-e command] [-s flags] [programfile]

Key:
   -e command
      Enter one line of a script.  Multiple -e commands can be given to build up a multi-line script.
      If -e is given, osascript will not look for a filename in the argument list.
 
      Because most scripts use characters that are special to many shell programs
      (e.g., Apple-Script uses single and double quote marks, (, ), and *), the command
      will have to be correctly quoted and escaped to get it past the shell intact.

   -i
      Interactive mode: osascript will prompt for one line at a time, and output the result, if applicable,
      after each line. Any script supplied as a command argument using -e or programfile will be loaded,
      but not executed, before starting the interactive prompt. 

   -l language
      Override the language for any plain text files.  Normally, plain text files are compiled as AppleScript.

   -s flags
     Modify the output style.  The flags argument is a string consisting of any of the
     modifier characters e, h, o, and s. 
     Multiple modifiers can be concatenated in the same string, and multiple -s options can be specified.

     The modifiers come in exclusive pairs;
     if conflicting modifiers are specified, the last one takes precedence.
     The meanings of the modifier characters are as follows:

        h  Print values in human-readable form (default).
        s  Print values in recompilable source form.

     osascript normally prints its results in human-readable form:
     strings do not have quotes around them, characters are not escaped,
     braces for lists and records are omitted, etc.  This is generally more useful, but can
     introduce ambiguities.  For example, the lists '{"foo", "bar"}' and '{{"foo", {"bar"}}}' would
     both be displayed as 'foo, bar'.  

     To see the results in an unambiguous form that could be recompiled into the same value, use
     the s modifier:

        e  Print script errors to stderr (default).
        o  Print script errors to stdout.
```

## AppleScript
We can also write the tool in AppleScript directly. The following is an example:
```bash
on run argv
    set lunch to do shell script "python3 ~/what-to-eat/main.py"
    display notification lunch with title "今天吃什么?"
end run
```
or 
```bash
set myList to {"重庆小面", "麻辣烫", "阳春面", "阿文汤包", "麻辣香锅", "安徽板面"} as list
set randomChoice to some item of myList
display notification randomChoice with title "今天吃什么？"
```


# References
1. <https://github.com/Ian729/what-to-eat>
2. <https://ss64.com/osx/osascript.html>
3. <https://github.com/Ian729/what-to-eat/blob/master/show.sh>