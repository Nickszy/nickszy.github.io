---
layout: post
title: django & redis
categories: 
  - 笔记
tags:
  - django
  - redis
excerpt:  运用缓存提高django的运行效率
comments: true
---

django 默认的缓存是基于内存的，同时它还支持一些方式，其中 mecheme 是最推荐的，因为它可以进行分布式的内存数据库。

因为之前就装了 redis，我们就使用第三方的这个 django-redis 项目。

## 下载

```shell
pip install django-redis
```

## 设置

```
CACHES = {
    "default": {
        "BACKEND": "django_redis.cache.RedisCache",
        "LOCATION": "redis://127.0.0.1:6379",
        "OPTIONS": {
            "CLIENT_CLASS": "django_redis.client.DefaultClient",
            "CONNECTION_POOL_KWARGS": {"max_connections": 100}
            "DECODE_RESPONSES":True
            # "PASSWORD": "密码",
        }
    }
}
```

## 使用

```
# 视图中使用
from django_redis import get_redis_connection
conn = get_redis_connection("default")
```

a. 全站缓存（在Django的setting配置中间件）

```
'django.middleware.cache.UpdateCacheMiddleware',
# 其他中间件...
'django.middleware.cache.FetchFromCacheMiddleware',
```

b. 单视图缓存

```
from django.views.decorators.cache import cache_page
# 方法I
@cache_page(60 * 15)
def my_view(request):
   ...
# 方法II
urlpatterns = [url(r'^foo/([0-9]{1,2})/$', cache_page(60 * 15)(my_view)),]
```

c. 在页面中局部进行缓存

```
步骤I. 引入TemplateTag
{% raw %}
        {% load cache %}
步骤II. 使用缓存
        {% cache 5000 缓存key %}
            缓存内容
        {% endcache %}
{% endraw %}
```

