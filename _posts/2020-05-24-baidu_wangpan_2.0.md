---
layout: post
title: 百度网盘视频倍速
categories: 
  - 技巧
tags:
  - js
excerpt:  代码控制速度
comments: true
---

一般来说，大家都使用的是[https://videojs.com/](https://videojs.com/)来播放视频。

## 浏览器代码控制

按 F12，可在控制台（console）输入以下代码，修改 rate 中的参数即可

```js
videojs.getPlayers("video-player").html5player.tech_.setPlaybackRate(2) //2倍速 
```

## ipad 视频悬浮

可购买 Alook 浏览器，使用解码器 1，即可在 ipad 中悬浮

缺点：过一段时间声音就会消失，需要重复之前的操作

## 购买会员

还是支持一波百度会员吧。

但视频只有转入自己的网盘才能在 windows 端调整速度。