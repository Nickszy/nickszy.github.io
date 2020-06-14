---
layout: post
title: fbprophet安装
categories: 
  - 错误
tags:
  - python
excerpt:  安装的血与泪
comments: true
---

装了好一会，好麻烦

## 安装 c++ 14.0

问题一： **Microsoft Visual C++ 14.0 is required**

解决方案：安装 Microsoft Visual C++ 2015 生成工具（在 vs 中搜一下工具包就好）

## 安装 C++编译器

问题二：** C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Tools\MSVC\14.16.27023\bin\HostX86\x64\cl.exe 中有内 部编译器错误。系统将会提示你稍后向 Microsoft 发送错误报告。**

问题三： **用msys2安装，进度条丝毫不动**

解决代码：

```
conda install libpython m2w64-toolchain #不要加 -c msys2
pip install fbprophet
```

## 安装 C++开发环境

问题四：import 无问题，但是开始 fit 后 python 就 restart。

解决方案： 安装 visual studio 的 c++开发环境（10G+)，装完就解决问题了