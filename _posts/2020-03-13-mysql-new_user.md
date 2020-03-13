---
layout: post
title:  新增一个用户并给予其权限
categories: 
  - 笔记
tags:
  - mysql
excerpt: 新开一个账户
comments: true
---

```sql
create user zhangsan identified by 'password';  # 创造一个用户zhangsan
create database database_name;  # 新建一个数据库
grant all privileges on database_name.* to zhangsan@'host' identified by 'password';  #给予zhangsan某数据库全部权限
flush privileges;   # 刷新

show grants for 'zhangsan';  # 查看权限
```

解释：
1. host可为 `121.21.32.312` 或者 无限制 `%`

2.privilegesCode表示授予的权限类型，常用的有以下几种类型：

- all privileges：所有权限。
- select：读取权限。
- delete：删除权限。
- update：更新权限。
- create：创建权限。
- drop：删除数据库、数据表权限。

3.dbName.tableName表示授予权限的具体库或表，常用的有以下几种选项：

- . :授予该数据库服务器所有数据库的权限。
- dbName.*：授予dbName数据库所有表的权限。
- dbName.dbTable：授予数据库dbName中dbTable表的权限。


## 更多

```
update mysql.user set password = password('zhangsannew') where user = 'zhangsan' and host = '%';  #修改密码
drop user zhangsan@'%'; # 删除用户
```

---
参考：[MySQL用户管理：添加用户、授权、删除用户](https://www.cnblogs.com/pejsidney/p/8945934.html)