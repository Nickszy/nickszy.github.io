---
layout: post
title: django-重定向&Cookies&session
categories: 
  - 笔记
tags:
  - django
excerpt:  注册用到的一些功能
comments: true
---


## 重定向

```py
#views.py
def index(request):
    # return HttpResponceRedirect('url')
    
    # return redirect('url',permenant =False)

    response = HttpResponse()
    response.status_code = 302
    response['Location'] = url
    return response

```
浏览器端：
302
Location：url


## Cookies

```py
def set_cookie(request):
    response = HttpResponse()

    # 默认关闭浏览器数据就丢失
    response.set_cookie('key','value')
    # 增加时长
    response.set_cookie('key','value',max_age=24*60*60,exprise=datetime.datetime.now()+datetime.datedelta(days=2))
    # 加密
    response.set_signed_cookie('key','value',max_age=24*60*60,salt='sdasdad')
    
    return response

def ger_cookie(request):
    if request.COOKIES.has_key('uname'):
        uname = request.get_signed_cookie('uname',salt='sdasdad')
        return HttpResponse(uname)
    else:
        return HttpResponse('not exist')

```