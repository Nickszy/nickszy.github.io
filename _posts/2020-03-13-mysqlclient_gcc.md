---
layout: post
title: 安装mysqlclient失败
categories: 
  - 错误
tags:
  - mysql
  - python
  - centos
excerpt: csdn 查了好久都没有，还是stackoverflow牛逼
comments: true
---

## 环境

centos 7
python 3.68
mysql 5.7

## 问题

```
gcc -pthread -Wno-unused-result -Wsign-compare -DNDEBUG -O2 -g -pipe -Wall -Wp,-D_FORTIFY_SOURCE=2 -fexceptions -fstack-protector-strong --param=ssp-buffer-size=4 -grecord-gcc-switches -m64 -mtune=generic -D_GNU_SOURCE -fPIC -fwrapv -fPIC -Dversion_info=(1,4,6,'final',0) -D__version__=1.4.6 -I/usr/include/mysql -I/root/citylist/venv/include -I/usr/include/python3.6m -c MySQLdb/_mysql.c -o build/temp.linux-x86_64-3.6/MySQLdb/_mysql.o -m64
    MySQLdb/_mysql.c:38:20: fatal error: Python.h: No such file or directory
     #include "Python.h"
                        ^
    compilation terminated.
    error: command 'gcc' failed with exit status 1
```

感觉是缺少gcc的环境，但是安装后依旧没有反应。

## 解决

我也不知道到底少装了那个东西，反正下面的全装了就行了。

```
yum -y install gcc gcc-c++ kernel-devel
yum -y install python-devel libxslt-devel libffi-devel openssl-devel

yum install python36 python36-devel python36-libs python36-tools  # 这个我和第一句一起装的，感觉是python3.6的问题
```

参考: [stack overflow](https://stackoverflow.com/questions/19955775/error-command-gcc-failed-with-exit-status-1-on-centos)