---
layout:     post
title:      Git 常用命令
author: Silver
categories: Blog
---

用了一百年GitHub Desktop的弱鸡表示: git命令？啥玩意啊，咋回事啊，那咋整啊

===================

经过了社会毒打之后，发现主要用到的命令还是这么几个

### 初始
#### 将远程仓库下载到本地
`git clone <url>`

### 开发相关
#### 查看上次提交后项目更改情况
`git status`

#### 将准备提交的文件添加到缓存区
`git add <file>`

#### 将缓存区中内容提交到本地仓库中
`git commit -m "commit message"`

### 提交相关
#### 添加远程仓库
`git remote add <repo alias> <url>`

#### 从远程仓库获取更新
`git fetch <repo alias>`

#### 合并代码
`git merge <repo>/<branch>`

#### 将远程仓库分支更新内容与本地分支合并
`git pull`

#### 将本地分支更新推送到远程仓库
`git push`

#### 查看当前分支
`git branch`

#### 还原文件/切换分支
`git checkout <file/branch name>`
