---
toc: false
layout: post
comments: true
description: weather command line
categories: [markdown, tech]
title: Introducing command line weather
---

For those who spend most of their time in the terminal, checking the weather should be as simple as running a command. In this post, I’ll introduce two handy CLI tools: `weather` and `tianqi`, both of which provide detailed weather reports directly in the terminal.

---

## `weather`: Terminal Weather Powered by wttr.in

The `weather` command fetches weather data from [wttr.in](https://wttr.in), a terminal-friendly weather service. Below is an example output for Beijing:
```
┌┤  Weather report for: beijing  ├───────────────────────────────────────┐
│                                                                        │
│                                                                        │
│       Thu 20 Mar              Fri 21 Mar              Sat 22 Mar       │
│                       ╷                       ╷                        │
│                                                                        │
│                                                                        │
│+26                                      ⢀⡀                   ⢀⠒⠉⠉⠉⠒⢄   │
│               ⣀⡀                     ⡠⠔⠊⠁⠈⠣⡀                ⡔⠁      ⠑⡀ │
│             ⡠⠊ ⠈⠡⡀                 ⢀⠌      ⠙⡄              ⡜         ⠑⠂│
│            ⡰⠁    ⠈⢆               ⢠⠃        ⠐⢄            ⠜            │
│           ⡰⠁       ⠑⢄            ⢠⠃           ⠉⠉⠒⠤⡀      ⡜⠁            │
│          ⢠⠃          ⠑⢄⡀        ⢀⠆                ⠈⠢⣀  ⢀⠎              │
│         ⢀⠇             ⠈⠢⢄     ⢀⠎                    ⠉⠊⠁               │
│         ⡎                 ⠑⠤⡀ ⢀⠊                                       │
│⡏⠢⡀     ⡜                    ⠈⠉⠁                                        │
│+9⠈⠒⢄⢁⣀⠎                                                                │
│                                                                        │
│─────┴─────┼─────┴─────╂─────┴─────┼─────┴─────╂─────┴─────┼─────┴─────╂│
│     6    12    18           6    12    18           6    12    18      │
│                                                                        │
│                                                                        │
│                                                                        │
│                                                                        │
│                                                                        │
│                                                                        │
│                                                                        │
│                                                                        │
│                                                                        │
│ ☀️  ☀️  ☀️  ☀️  ☀️  ☀️  ☀️  ☀️  ☀️  ☀️  ☀️  ☀️  ☀️  ☀️  ☀️  ☀️  ☀️  ☀️  ☀️  ☀️  ☀️  ☀️  ☀️  ☀️ │
│ ↘  ↘  ↘  ↘  ↘  ↘  ↘  ↘  ↘  ↘  ↘  ↘  ↘  ↘  →  ↘  ↘  ↘  ↘  ↘  ↘  ↘  →  → │
│ 10 10 10 13 23 20 14 17 15 14 11 11 18 19 13 15 16 16 13 14 18 19 12 14│
│                                                                        │
│🌗                     🌗                      🌗                     🌗│
│      ─━━━━━━━━━━━━           ─━━━━━━━━━━━━─          ─━━━━━━━━━━━━─    │
│                                                                        │
│                                                                        │
└────────────────────────────────────────────────────────────────────────┘
Weather: ☀️   Sunny, +19°C, 8%, ↘20km/h, 1018hPa
Timezone: Asia/Shanghai
  Now:    11:22:29+0800 | Dawn:    05:50:58  | Sunrise: 06:18:25
  Zenith: 12:21:56      | Sunset:  18:26:00  | Dusk:    18:53:32
Location: 北京市, 东城区, 北京市, 100010, 中国 [39.9056,116.3913]

Follow @igor_chubin for wttr.in updates
```
### Installing and Using `weather`

The `weather` command is a simple shell alias for querying `wttr.in`:

```sh
weather () {
	curl https://v2.wttr.in/beijing
}
```

## tianqi: A More Compact Weather Report

Another useful command, tianqi, offers a more concise weather report, also powered by wttr.in. Below is an example output:

```
 ~/ tianqi
Weather report: Beijing, China

      \   /     Sunny
       .-.      19 °C
    ― (   ) ―   ↘ 20 km/h
       `-’      10 km
      /   \     0.0 mm
                                                       ┌─────────────┐
┌──────────────────────────────┬───────────────────────┤  Thu 20 Mar ├───────────────────────┬──────────────────────────────┐
│            Morning           │             Noon      └──────┬──────┘     Evening           │             Night            │
├──────────────────────────────┼──────────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│     \   /     Sunny          │     \   /     Sunny          │     \   /     Sunny          │     \   /     Clear          │
│      .-.      14 °C          │      .-.      20 °C          │      .-.      21 °C          │      .-.      18 °C          │
│   ― (   ) ―   ↘ 13-19 km/h   │   ― (   ) ―   ↘ 23-26 km/h   │   ― (   ) ―   ↘ 14-23 km/h   │   ― (   ) ―   ↘ 17-28 km/h   │
│      `-’      10 km          │      `-’      10 km          │      `-’      10 km          │      `-’      10 km          │
│     /   \     0.0 mm | 0%    │     /   \     0.0 mm | 0%    │     /   \     0.0 mm | 0%    │     /   \     0.0 mm | 0%    │
└──────────────────────────────┴──────────────────────────────┴──────────────────────────────┴──────────────────────────────┘
                                                       ┌─────────────┐
┌──────────────────────────────┬───────────────────────┤  Fri 21 Mar ├───────────────────────┬──────────────────────────────┐
│            Morning           │             Noon      └──────┬──────┘     Evening           │             Night            │
├──────────────────────────────┼──────────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│     \   /     Sunny          │     \   /     Sunny          │     \   /     Sunny          │     \   /     Clear          │
│      .-.      17 °C          │      .-.      22 °C          │      .-.      +24(23) °C     │      .-.      20 °C          │
│   ― (   ) ―   → 11-15 km/h   │   ― (   ) ―   ↘ 18-21 km/h   │   ― (   ) ―   → 13-21 km/h   │   ― (   ) ―   → 15-30 km/h   │
│      `-’      10 km          │      `-’      10 km          │      `-’      10 km          │      `-’      10 km          │
│     /   \     0.0 mm | 0%    │     /   \     0.0 mm | 0%    │     /   \     0.0 mm | 0%    │     /   \     0.0 mm | 0%    │
└──────────────────────────────┴──────────────────────────────┴──────────────────────────────┴──────────────────────────────┘
                                                       ┌─────────────┐
┌──────────────────────────────┬───────────────────────┤  Sat 22 Mar ├───────────────────────┬──────────────────────────────┐
│            Morning           │             Noon      └──────┬──────┘     Evening           │             Night            │
├──────────────────────────────┼──────────────────────────────┼──────────────────────────────┼──────────────────────────────┤
│     \   /     Sunny          │     \   /     Sunny          │     \   /     Sunny          │     \   /     Clear          │
│      .-.      19 °C          │      .-.      +24(23) °C     │      .-.      +25(24) °C     │      .-.      22 °C          │
│   ― (   ) ―   ↘ 14-19 km/h   │   ― (   ) ―   ↘ 18-21 km/h   │   ― (   ) ―   → 12-21 km/h   │   ― (   ) ―   → 14-27 km/h   │
│      `-’      10 km          │      `-’      10 km          │      `-’      10 km          │      `-’      10 km          │
│     /   \     0.0 mm | 0%    │     /   \     0.0 mm | 0%    │     /   \     0.0 mm | 0%    │     /   \     0.0 mm | 0%    │
└──────────────────────────────┴──────────────────────────────┴──────────────────────────────┴──────────────────────────────┘

Follow @igor_chubin for wttr.in updates
```
### Installing and Using `tianqi`
```
tianqi () {
	curl https://wttr.in/
}
```

## Reference
- [wttr.in](https://github.com/chubin/wttr.in)
- [TheAppleGeek](https://www.theapplegeek.co.uk/blog/wttr)
