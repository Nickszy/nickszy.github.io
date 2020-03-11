---
layout: post
title:  django第一次部署
categories: 
  - 笔记
tags:
  - django
  - python
  - deploy
excerpt: 不大如意，略有曲折
comments: true
---

1. 使用 git 克隆到 centos 中，然后创建 python 虚拟环境。
```
python -m venv venv 
source venv/bin/activate  # 激活环境
whereis python # 可查看运行环境 
```

2. 激活后下载 python 依赖环境 
```shell
pip install -r requirements.txt
```

3. 继承数据库
```shell
python manage.py migrate
```

4. 后台一直运行
```shell
nohup python manage.py runserver 1235 & # no hang up & 一直进行
jobs -l  #同一个终端可查看
ps -ef  # 查看系统进程
kill -9 xxx # 杀死进程
```

参考：

- [venv 官网](https://docs.python.org/3/library/venv.html)

- [more about nohup](https://blog.csdn.net/jenyzhang/article/details/76210920)