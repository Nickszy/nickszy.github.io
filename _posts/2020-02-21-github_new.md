---
layout: post
title:  github与本地git
categories: 
  - 笔记
tags:
  - git
excerpt:  与github进行互动
comments: true
---

# 2020-02-21-github_new


## 添加 SSH key

1. 创建一个 SSH key 。
      在命令行（即Git Bash）输入以下命令， 回车三下即可：
      
```shell
ssh-keygen -t rsa -C "邮箱地址"（你创建github账号的邮箱）
# 成功后会出现密钥文件内容路径（形如C:\Users\Administrator.ssh\id_rsa.pub）
```

2. 将 ssk 添加到 github
    打开密钥文件，复制里面的内容，粘贴到 github 设置中的 New SSH Key即可。

3. 测试是否添加成功。

```shell
ssh -T git@github.com
# 若成功将出现你的昵称
```

## 本地项目 git 初始化
```shell
git init
git add . #-A
git commit -m 'xxxxx'
git status
```

更多：[git-branch](https://nickszy.coldpoker.xyz/articles/2020-01/git-chackout)

## 与远程项目链接

1. 先在 github 中新建一个项目
2. 在本地项目中输入以下代码：
```shell
git remote add origin git@github.com:xxxx/xxx.git
git pull origin master
git push -u origin master
git push -u origin master -f # 如果本地版本较低，直接force将远程仓库替代
git status  # 查看目前仓库状态 如无意外将出现origin/master
```

origin 是仓库别名，以后推送可用 origin 代替 git 链接

参考：
  
1.  [检查现有 SSH 密钥](https://help.github.com/cn/articles/checking-for-existing-ssh-keys)
2.  [# 生成新 SSH 密钥并添加到 ssh-agent](https://help.github.com/cn/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
3.  [# 新增 SSH 密钥到 GitHub 帐户](https://help.github.com/cn/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account)