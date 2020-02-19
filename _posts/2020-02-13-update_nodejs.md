---
layout: post
title:  update_nodejs
categories: 
  - 学习
tags:
  - nodejs
excerpt: 
comments: true
---

## 查看版本号

node -v

## 升级 node.js
node有一个模块叫n，是专门用来管理node.js的版本的。
首先安装n模块：
npm install -g n
第二步：
升级node.js到最新稳定版
n stable

n后面也可以跟随版本号比如：
n v0.10.26
或
n 0.10.26

## 其他 npm 的常用命令

npm install express #安装express模块

npm install -g express #全局安装express模块

npm list #列出已安装模块

npm show express #显示模块详情

npm update #升级当前目录下的项目的所有模块

npm update express #升级当前目录下的项目的指定模块

npm update -g express #升级全局安装的express模块

npm uninstall express #删除指定的模块

如果中途升级失败，可能就放弃了，反正老的也能用，以后再升，然后开始用旧的时，
发现运行node和npm命令出现“段错误”，在网上找了好多，这有下面这个解决方案最
靠谱：
自动更新node的时候path被指向了/usr/local/bin/node；而我自己配置的path是其他路径。更新导致前者替代了后者。由于更新中断，node命令运行不了。找到/usr/local/bin/node，删除nnode，source /etc/profile（自己配置的路径）。问题解决！
