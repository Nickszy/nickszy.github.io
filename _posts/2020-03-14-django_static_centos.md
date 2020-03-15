---
layout: post
title: django static 404
categories: 
  - 错误
tags:
  - python
  - django
excerpt: 访问静态资源失败
comments: true
---

## 环境

centos 7
python 3.68
django 3.04

## 问题

静态资源访问失败，报404的错。

```
[13/Mar/2020 16:49:13] "GET /static/map/js/china.js HTTP/1.0" 404 179
[13/Mar/2020 16:49:13] "GET /static/map/js/province/beijing.js HTTP/1.0" 404 179
[13/Mar/2020 16:49:13] "GET /static/map/js/china.js HTTP/1.0" 404 179
[13/Mar/2020 16:49:13] "GET /static/chinaMapJsonData/%E6%B5%99%E6%B1%9F%E7%9C%81/%E6%9D%AD%E5%B7%9E%E5%B8%82/datas.json HTTP/1.0" 404 179
```

## 解决

修改 setting.py,使用绝对路径

```
STATICFILES_DIRS = (
    '/root/citylist/static',
)
```

参考: [stack overflow](https://stackoverflow.com/questions/12809416/django-static-files-404)