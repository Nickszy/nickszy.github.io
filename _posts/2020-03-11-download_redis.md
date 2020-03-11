---
layout: post
title:  centos下载redis
categories: 
  - 笔记
tags:
  - redis
  - deploy
excerpt: redis是一个内存型的kv数据库，可以与mysql配合使用
comments: true
---

## 下载

```shell
yum install epel-release   # 据说yum官方源有问题，使用fedora的epel仓库
yum install redis  # 安装redis
service redis start  #启动Redis服务
redis-cli  #打开客户端
127.0.0.1:6379>keys *  # 输入keys *检查是否可以进入

service redis status # 查看运行情况
ps -ef | grep redis # 查看进程
```

## 配置

### 设置密码
```shell
# 方法一
1. 打开 `/etc/redis.conf`
2. 找到 #requirepass foobared，取消注释   # 在很下面
3. 将 foobared 改为自己想要设置的密码。

# 方法二（推荐）
打开redis-cli后，输入
config  set  requirepass  password
```


### 设置开机自启动

```shell
chkconfig redis on
```

## 使用

### 登录

```shell
# 方法一
redis-cli -a password

# 方法二
redis-cli
auth password

# 远程登录
$ redis-cli -h host -p port -a password
```

### 

查看所有的key列表

```sql
keys *
```


设置、获取、删除参数

```sql
set name 'val'
get name
del name
```