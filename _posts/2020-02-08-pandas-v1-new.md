---
layout: post
title:  pandas 1.0 有了哪些重磅更新？
categories: 
  - 学习
tags:
  - python
  - pandas
excerpt: 重磅更新，pandas.<NA>
comments: true
---

主要参考依据：[pandas 官方文档](https://pandas.pydata.org/docs/whatsnew/v1.0.0.html#new-deprecation-policy)
## 新功能

### 有了pandas独有的 <NA>

<NA>做到了真正的无的意思，在使用中计算机能够忽略掉这个参数和他的类型。

1.描述类型

|符号|data type|
|-|-|
|np.nan|float|
|np.nan None|object_dtype|
|pd.NaT|datatime_like|
|pd.<NA>|nullable integer/booolean/string|

2.比较
3.


#### 如何使用

```py
df.convert_dtypes()  #可以将None，NaN自动转化为<NA>
```

## 功能增强

### 增加 to_markdown()

## 如何更新

首先看一下自己的版本号

```py
import pandas as pd
pd.__veision__
>>'0.25.0' 
```

因为 pandas 是我经常要用的库，所以就直接全局安装了。

```cmd
pip install --upgrade pandas
```