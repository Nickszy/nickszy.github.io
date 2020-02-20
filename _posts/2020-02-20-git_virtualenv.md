---
layout: post
title:  git_virtualenv
categories: 
  - 笔记
tags:
  - python
  - git
  - virtualenv
excerpt:  一个python工程开始需要做的步骤
comments: true
---

```shell
mkdir filename
cd filename
git init
python -m venv .venv  # 执行python中的venv模块，到.venv中
source .venv/bin/activate #加载虚拟环境

# 下载包
pip install django==1.11.15 redis 
pip ipython
# 将配置的包导出或下载
pip freeze > requirements.txt
pip install -r requirements.txt

git add .
git status

# 测试位置
which django-admin
>>> xxx

django-admin startproject projectname ./
git commit -m "项目初始化"

# 退出环境
deactivate
```

[更多请见](https://pythonguidecn.readthedocs.io/zh/latest/dev/virtualenvs.html)





