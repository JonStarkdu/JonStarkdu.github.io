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
<!--more-->
## 3.git删除远程文件/文件夹
如下，我把src里的全部移除，但是本地文件还保留。主要是一下四个命令
* git rm -r -n --cached  */src/\* -n这个参数，执行命令时，是不会删除任何文件，而是展示此命令要删除的文件列表预览。
* git rm -r --cached  */src/\*      //最终执行命令
* git commit -m"移除src目录下所有文件的版本控制"    //提交
* git push origin master   //提交到远程服务器
