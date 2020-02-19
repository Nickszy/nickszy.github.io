---
layout: post
title:  django-orm
categories: 
  - 笔记
tags:
  - django
  - orm
excerpt: 学了django中orm的部分操作，很是便捷
comments: true
---

## django 之 orm

### 查表

```python_django

# QuerySet 是给定模型的对象列表（list）。QuerySet 允许您从数据库中读取数据，对其进行筛选以及排序。
post.objects.all()[0:20]

post.objects.exclude(id__lt='100').values('ptime','author').filter(uname__contains/startswith/endswith="学习",tetx_isnull=True).filter(pid__gte/lt='100').order_by('-published_date')
```

### inspectdb

```
python manage.py inspectdb>/app/models.py   /可以通过数据库反推model，但是生成的文件是会覆盖原文件的
```