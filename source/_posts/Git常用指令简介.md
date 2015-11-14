title: Git常用指令简介
date: 2015-11-14 13:42:08
categories: linux
tags:
 - git
 - linux
 - 编程
---

`Just for Record`
***
本文只是记录常用的指令，并没有对这些指令进行解释。
主要用于本人的一个笔记。
<!--more-->
创建Git仓库：
```
$ git init
```
把文件添加、提交到仓库：
```
$ git add filename
$ git commit -m "comment"
```
懒人(本人)常用commit指令：
```
$ git add .
$ git commit -a -m "comment"
```
查看git状态：
```
$ git status
```
查看git提交记录：
```
$ git log
```
回退到指定版本：
```
$ git reset --hard [<commit id>] #commit id是指定的版本的id；
```
查看操作记录，主要是为了不小心回退时恢复的：
```bash
$ git reflog
```
撤销修改：
```bash
$ git checkout -- filename
```
可以把filename回到最近一次"git commit"或"git add"时的状态；

从服务器克隆git仓库：
```bash
$ git clone xxx/xx
```
xxx/xx是git仓库在远程服务器的路径；
例如：192.168.1.11/gittest

创建"dev"分支：
```bash
$ git branch dev
```
创建"dev"分支，然后切换到"dev"分支：
```bash
$ git checkout -b dev
```
切换分支到"master"：
```bash
$ git checkout master
```
查看分支：
```bash
$ git branch #查看本地分支
$ git branch -a #查看全部分支，包括远程分支
$ git branch -av #查看全部分支，包括分支的最新的版本信息
```
删除"dev"分支：
```bash
$ git branch -d dev
```
把"dev"分支工作成果合并到当前分支上：
```bash
$ git merge dev
```
查看分支合并图：
```bash
$ git log --graph
```
查看所有标签：
```bash
$ git tag
```
增加一个新的标签：
```bash
$ git tag <tag name>
```
给历史分支补添加标签：
```bash
$ git tag <tag name> <commit id>
```
查看标签信息：
```bash
$ git show <tag name>
```
删除标签：
``` bash
$ git tag -d <tag name>
```
从远程同步到本地：
``` bash
$ git pull origin master
$ git pull <远程主机名> <远程分支名>:<本地分支名>
$ git pull origin next:master #取回远程next分支，与本地master分支合并
$ git pull origin next
#上面命令表示，取回origin/next分支，再与当前分支合并。
#实质上，这等同于先做git fetch，再做git merge，如下：
$ git fetch origin
$ git merge origin/next
```
提交本地修改至远程：
``` bash
$ git push origin master
#git push命令用于将本地分支的更新，推送到远程主机。它的格式与git pull命令相仿。
$ git push <远程主机名> <本地分支名>:<远程分支名>
#分支推送顺序的写法是<来源地>:<目的地>，所以git pull是<远程分支>:<本地分支>，而git push是<本地分支>:<远程分支>。
#如果省略本地分支名，则表示删除指定的远程分支，因为这等同于推送一个空的本地分支到远程分支。
$ git push origin :master
# 等同于
$ git push origin --delete master

$ git push -u origin master
#上面命令将本地的master分支推送到origin主机，同时指定origin为默认主机，后面就可以不加任何参数使用git push了。
#不带任何参数的git push，默认只推送当前分支，这叫做simple方式。
$ git push origin --tags  #git push不会推送标签(tag)，除非使用–tags选项。
```
