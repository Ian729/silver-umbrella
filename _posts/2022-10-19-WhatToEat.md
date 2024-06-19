---
toc: true
layout: post
comments: true
description: Some quick notes on automating small tasks using AppleScript and cron
categories: [markdown, tech, library]
title: AppleScript and Crontab
---

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
```
the random choice is stored in the variable `lunch`. Then we use the `osascript` command to display the notification.

The manual page of `osascript` can be found [here](https://ss64.com/osx/osascript.html).

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

## Upgrade
Recently I upgrade the tool to use [Gaode API](https://lbs.amap.com/api/webservice/guide/api/search#around) to find nearby restaurants, it will also sort based on its rating scores.

***it requires gaode account and `GAODE_API_KEY`***


### API
```
GET https://restapi.amap.com/v3/place/around?parameters 
```

### Source Code
`https://github.com/Ian729/what-to-eat/blob/master/gaode.py`

# References
1. <https://github.com/Ian729/what-to-eat>
2. <https://ss64.com/osx/osascript.html>
