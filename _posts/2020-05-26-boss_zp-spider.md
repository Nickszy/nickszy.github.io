---
layout: post
title: boss 直聘 爬虫
categories: 
  - 爬虫
tags:
  - js
  - python
excerpt:  js加密，逆向
comments: true
---

boss 直聘是真的坑，也无法使用 selenium 等工具。

使用 requests 库，主要有一下两个反爬限制：

1. 多次爬取封 ip，感觉在几十次左右（403，关小黑屋一天）
2. cookie 中需要带有`__zp_stoken_`（重复请稍候页面）

## js 逆向

1. debugger  忽略
2. 发现是 ABC.z 做个函数在进行加密，需要 ts 和 seed 这两个来自之前 response 中 cookie 的数据 
3. 加密需要加 window document 等信息 
4. 用 pyexecjs 这个库去使用 js（需要安装 node 环境）
5. 挂代理（使用 github 上开源的免费 ip 代理池）

逆向 js 文件
```js
var window = {
    navigator: {
        userAgent: ""
    },
    moveTo: function () {
    },
    moveBy: function () {
    },
    screen: {
        availHeight: 1040,
        availWidth: 1920
    },
    open: function () {
        [nativecode]
    }
};
var document = {
    getElementById: function () {
        glcanvaxs = {}
    },
    createElement: function () {
        caption = {
            tagName: "CAPTION",
        };
        return caption
    },
    title: ""
};
var top = {
    location: {
        href: "https://www.zhipin.com/web/common/security-check.html"
    },
};
var nativecode = "";

function setInterval() {
    [nativecode]
};
var sessionStorage = {};
delete global;
delete Buffer;
function encryption(seed, ts) {
    var code = new ABC().z(seed, parseInt(ts) + (480 + new Date().getTimezoneOffset()) * 60 * 1000);
    return code
}

load(xxxxxxx.js)  //这个加密的js文件每天更新，要是难得使用直接人工拷贝替换就行
```

## python 加密

python 获得加密 cookie
```py
 def cookies_generate(self, response):
        query_str = parse.urlparse(response.url).query
        query_dict = {i.split("=")[0]: i.split("=")[1] for i in query_str.split("&")}
        seed = parse.unquote(query_dict.get("seed"))
        ts = query_dict.get("ts")
        print(seed,ts)
        code = self.js.call("encryption", seed, ts)
        code = parse.quote(code).replace("/", "%2F")
        print(code)
        input('code')
        return f"__zp_stoken__={code};"
```

参考资料
1. [2019年末逆向复习系列之Boss直聘Cookie加密字段__zp_stoken__逆向分析](https://zhuanlan.zhihu.com/p/97720699)

鸣谢
qq 上的 大二软工 呆呆同学