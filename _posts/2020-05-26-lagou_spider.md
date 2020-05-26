---
layout: post
title: 拉勾网爬虫
categories: 
  - 爬虫
tags:
  - python
excerpt:  更换代理
comments: true
---

相比较 boss 直聘，拉勾网的反爬系统就直白很多了。

1. 10 次连续访问限制登录
2. 数据直接通过 api 的形式返回

## 代码

```py
import requests
import pandas as pd
class spider():
    @property
    def get_proxy(self):
        a = requests.get("my_proxy_pool_url").json()
        proxy = a.get("proxy")
        return {"http": "http://{}".format(proxy)}
proxy = spider() .get_proxy
headers = {
'Accept': 'text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8',
'Accept-Encoding': 'gzip, deflate, sdch',
'Accept-Language': 'zh-CN,zh;q=0.8',
'Upgrade-Insecure-Requests': '1',
'Referer':'https://www.lagou.com/jobs/list_java?labelWords=&fromSearch=true&suginput=&labelWords=hot',
'User-Agent': 'Mozilla/5.0 (iPhone; CPU iPhone OS 8_0 like Mac OS X) AppleWebKit/600.1.3 (KHTML, like Gecko) Version/8.0 Mobile/12A4345d Safari/600.1.4'
}


#设置一个会话
session = requests.session()
hr = dict()
job=[]
# 发送Get请求更新cookie
session.get('https://www.lagou.com/jobs/list_java?labelWords=&fromSearch=true&suginput=&labelWords=hot',proxies=proxy,headers=headers)
for i in range(1,31):
        data = {
        'first':'true',
        'pn':i,
        'kd':'金融科技'
        }
        rep = session.post('https://www.lagou.com/jobs/positionAjax.json?city=深圳&needAddtionalResult=false',proxies=proxy,headers=headers,data=data)  # 限定城市
#         rep = session.post('https://www.lagou.com/jobs/positionAjax.json?needAddtionalResult=false',proxies=proxy,headers=headers,data=data) # 全国
        # 请求成功，接下来就是提取想要的信息。
        datas = json.dumps(rep.json())  #ensure_ascii：使用中文保存，缩进为4个空格
        with open(f'./data/shenzhen_{i}.json','w+') as f: 
            f.write(datas)
        print(f'----------下载第{i}页---------------')
            # 每10次，换一个代理
            if i%10==0:
            session = requests.session()
            proxy = spider().get_proxy  
            session.get('https://www.lagou.com/jobs/list_java?labelWords=&fromSearch=true&suginput=&labelWords=hot',proxies=proxy,headers=headers)
            print(f'----------更换proxy---------------')  
print('down')
```

## 保存数据

```py
import json
datas = json.dumps(response.json())
with open(f'./data/{city_name}_{page}.json','w+') as f:
    f.write(datas)
```
