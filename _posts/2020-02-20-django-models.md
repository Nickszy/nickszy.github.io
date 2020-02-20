---
layout: post
title:  django-models
categories: 
  - 笔记
tags:
  - python
  - django
  - model
excerpt:  一个工程开始需要做的步骤
comments: true
---

## 输入

```python

class User(models.Models):
  nickname = models.CharField(max_length=32,unique=32,verbose_name='昵称')
  phonenum = models.IntegerField()
  SEX =(
  ('M','男'),
  ('S','女')
  )
  sex = models.CharField(max_length=8,chioces=SEX)
  # 图片一般保存url地址，静态数据储存在其他地方
  birth_year = models.IntegerField(default=18)
  birth_month = models.IntegerField()
  birth_day = models.IntegerField()

  @property  #方法属性化
  def age(self):
    now = datetime.date.today()
    birth_date = datetime.date(self.birth_year,self.birth_month,self.birth_day)
    return (now-birth).day//365

# 懒加载
## 法一:借助python中__dict__
  @property
  def porfile(self):
  '''用户配置'''
  if '_profile' not in self.__dict__:  # 可用 hasattr(self,_profile) 替代
    _profile,created =Profile.objects.get_or_create(self.id=123)
    self._profile = _profile
    return self._profile
## 法二：用django自带的cached_property
from django.utils.functional import cached_property

@cashed_property
def porfile(self):
  '''用户配置'''
    _profile,created =Profile.objects.get_or_create(self.id=123)
    self._profile = _profile
    return self._profile
```


```python
class Profile():
  
```


```
manage.py makemigrates
```


tips:

```shell
pip install ipython
./manage.py shell  #进入django的ipy调试环境
```

