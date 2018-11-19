---
title: git基本命令
date: 2018-11-16 10:42:51
tags: git
---
在你想要打开的位置处右键打开 git bash
## 1.从远程克隆项目
``git clone git@github.com:xxx/xxx.git``
## 2.分支相关
* 查看本地分支  `git branch`
* 查看远程分支  `git branch -r`
* 查看所有分支  `git branch -a`
* 本地创建分支  `git branch [branch name]`
* 切换到另一个分支 `git checkout [branch name]`
* 创建+切换分支 `git checkout -b [branch name]`
* 将新分支推送到github `git push origin [branch name]`
* 删除本地分支 `git branch -d [branch name]`
* 删除github远程分支 `git push origin :[branch name]`
* 客户端删除分支 直接点击branches,将要删除的分支删除即可。
<!--more-->

## 3.git删除远程文件/文件夹
如下，我把src里的全部移除，但是本地文件还保留。主要是一下四个命令
* git rm -r -n --cached  */src/\* -n这个参数，执行命令时，是不会删除任何文件，而是展示此命令要删除的文件列表预览。
* git rm -r --cached  */src/\*      //最终执行命令
* git commit -m"移除src目录下所有文件的版本控制"    //提交
* git push origin master   //提交到远程服务器

## 4.git回退之前的版本
* 查看commit日志```git log```得到提交日志，日志格式如下：

```
commit 4d070ae5940ce43b74d5e9ac2d918ac2b21d15c3
Author: Edward <xxx>
Date:   Wed Oct 11 17:40:12 2018 +0800

    modify mt7688 gpio mmap

commit 208f8823cfa895b973b676cba1bc86d3109447e6
Author: Edward <xxx>
Date:   Wed Oct 11 17:39:07 2018 +0800

    del login

commit 88361fef82f60810618c2bd08453ebf71140b059
Author: Edward <xxx>
Date:   Wed Oct 11 17:36:49 2018 +0800

    add fxSmartGW platform

commit fdc5add13e13467bfa1ddec01fad9196d891fb89
```

* 版本回退

```
git reset --hard  [commit后对应版本的16进制码]
```

* 同步到远程代码仓库

```
git push origin [分支名] --force
```

* 回退到最近一个提交版本

```
git reset --hard HEAD
```

* 回退上一次提交版本

```
git reset --hard HEAD^
```

* 其他
根据–soft –mixed –hard，会对working tree和index和HEAD进行重置:
git reset –mixed：此为默认方式，不带任何参数的git reset，这种方式回退到某个版本，只保留源码，回退commit和index信息
git reset –soft：回退到某个版本，只回退了commit的信息，不会恢复到index file一级。如果还要提交，直接commit即可
git reset –hard：彻底回退到某个版本，本地的源码也会变为上一个版本的内容
