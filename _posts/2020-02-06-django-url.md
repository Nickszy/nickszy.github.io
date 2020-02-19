---
layout: post
title: django-url
categories: 
  - 笔记
tags:
  - python
  - django
  - url
excerpt: 学了django完整版的url设置
comments: true
---

## django url

### 正向

1. 直接正则
2. 传参

```
urlpatterns = [
  path('time/(\d{4})/\d{2}',views.post) //用正则表达式捕获后传入post中的year，mouth
]

//views.py

def post(request,year,month):
  return HttpResponse(year,month)

```

3. 关键字传参

```py
urlpatterns = [
  path('^time/(?P<year>[0-9]{4})/(?P<month>[0-9]{2}$',views.post) //与2不同的是在下面视图函数中若改变year month的顺序并没有关系
]

//views.py

def post(request,year,month):
  return HttpResponse(year,month)

```

4. include

```py
path('sad',include('sad.urls'))
```

5. 传参

'''
urlpatterns = [
  path('^time/(?P<year>[0-9]{4})/(?P<month>[0-9]{2}$',views.post,{hello:'123'})   //将hello传给views.post
]
'''

### 逆向

1. name

```
urlpatterns = [
  path('time/(\d{4})/\d{2}',views.post,name='q') //用正则表达式捕获后传入post中的year，mouth
]
```

```html
// index.html

<a href='{% raw %} { 'q' 113 %} {% endraw %}'>超链接</a> 

```

```py
// views.py

def post(request,num):   
  return HttpResponse(num)

```

2. 重定向 

```
def redirect(request):
  return HttpResponseRedirect(reverse('p',args=(66)))  //重定向

```

3. namespace

```
//urls.py
urlpatterns = [
  path('',include('app.urls',namespace='app',app_name='app_name'),name='q') //用正则表达式捕获后传入post中的year，mouth
]

// app/urls.py
urlpatterns = [
  path('time/(\d{4})/\d{2}',views.post,name='q') //用正则表达式捕获后传入post中的year，mouth
]
// index.html
{% raw %}
<a href='{% url 'app:q' 113 %}'>超链接</a>
{% endraw %}
// views.py

def post(request,num):   
  return HttpResponse(num)
def redirect(request):
  return HttpResponseRedirect(reverse('p',args=(66)))  //重定向

```