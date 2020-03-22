---
layout: post
title: nginx设置一
categories: 
  - 笔记
tags:
  - nginx
excerpt:  static & 子域名
comments: true
---

## 代码

```nginx

server{
        listen 80;
        listen [::]:80;
        server_name citylist.coldpoker.xyz;
        location / {
                            proxy_set_header  Host       $host;
                            proxy_set_header  X-Real-IP    $remote_addr;
                            proxy_set_header  X-Forwarded-For $proxy_add_x_forwarded_for;
                            proxy_pass http://127.0.0.1:1235;
        }
        location /static {
                root /root/citylist;
        }
}
```
我的服务器上部署了好几个服务，需要用nginx将信息传递到不同的端口。

新建一个server，然后将server_name命名为域名的名字。

static需要跟这个写的类似，不能多加一个反斜杠。


## 负载均衡

```

http {
  upstream localweb{
          server localhost:8001;
          server localhost:8002;
          server localhost:8003;
      }
  server {
      listen       80;
      server_name  localhost;
      location / {
        proxy_pass http://localweb; #请求转向localweb定义的服务器列表
      }
    }
  }

```

如果配置在多台服务器上也可以通过这种方法分发请求。