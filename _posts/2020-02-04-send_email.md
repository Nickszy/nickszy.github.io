---
layout: post
title: 在django中如何发邮件
categories: 
  - 笔记
tags:
  - python
  - 加密
  - django
  - celery
excerpt: 发送邮件
comments: true
---

## Django

### itsdangerous

```
pip install itsdangerous
from itsdangerous import TimestampSigner
s = TimestampSigner('secret-key')
string = s.sign('foo')
s.unsign(string, max_age=5)
```

## email

1.  首先要开启邮箱的 mtp ，将密钥记录下来后放入 django 的 setting 中。
2. django 的邮箱服务可直接调用 3. 


## 异步

[请看 celery 的相关信息](https://nickszy.coldpoker.xyz/articles/2020-02/python_celery)

