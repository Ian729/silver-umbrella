---
toc: true
layout: post
comments: true
description: Some quick notes on Chrome Dinosaur
categories: [markdown, tech, game]
title: Hacking Chrome Dinosaur Game
---

# Introducing Chrome Dinosaur Game
The Dinosaur Game (also known as the Chrome Dino) is a browser game developed by Google and built into the Google Chrome web browser. The player guides a pixelated Tyrannosaurus rex across a side-scrolling landscape, avoiding obstacles to achieve a higher score. The game was created by members of the Chrome UX team in 2014.

The game we are talking about in this blog refers to the Dino game ripped off from The Chromium Projects.

# How to play
Using the spacebar to jump over the cacti and the birds. The game ends when the dinosaur collides with an obstacle or when the dinosaur falls into a pit.

# Usage
Open Chrome Console and paste the following code:
```javascript
Runner.prototype.gameOver() = function() {}
```
This will disable the game over function and you can play the game forever.

```javascript
Runner.instance_.config.SPEED
```
This will return the current speed of the game. You can change the speed by changing the value of the variable.

```javascript
Runner.instance_.setSpeed(60) // set speed to 10 times faster
```

In order to end the game, you can cache the `gameOver` function and call it when you want to end the game.

```javascript
var cachedGameOver = Runner.prototype.gameOver;
Runner.prototype.gameOver = function() {
}
```
When you want to end the game and appear on the leaderbaord
```javascript
Runner.prototype.gameOver = cachedGameOver;
```
Have Fun Hacking Games!

# References
[1] [Wikipedia](https://en.wikipedia.org/wiki/Dinosaur_Game)

[2] [The Chromium Projects](https://chromium.googlesource.com/apps/libapps/+/master/nassh/doc/dino.md)

[3] [Chrome Dino Game](https://chromedino.com/)

[4] [Chrome Dino Game Source Code](https://github.com/wayou/t-rex-runner.git)