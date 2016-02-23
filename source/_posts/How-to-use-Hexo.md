title: 使用Hexo写blog
date: 2016-01-13 21:18:33
categories: linux
tags:
  - life
  - linux
---
`Just for Record`
***
Hexo搭建的过程略显繁琐，不是本文讨论的重点，如果需要了解如何搭建Hexo，可以点击[这里](http://ibruce.info/2013/11/22/hexo-your-blog/)；
<!--more-->

日常使用只需要下面三个步骤就可以完成blog的编写，生成及部署；
```
hexo n #写文章
hexo g #生成
hexo d #部署
```

# 写文章
执行下面new命令，会自动生成指定名称的文章至hexp/source/_posts/postName.md
```
hexo new [layout] "postName"	#新建文章
```
其中[*layout*]是可选参数，默认值为post；有哪些layout，请到scaffolds目录下查看，这些文件名称就是layout名称。当然也可以添加自己的layout，方法就是添加一个文件即可，同时也可以编辑现有的layout。

# 生成静态页面
辛苦写完blog，当然是要编译生成，并且查看效果；执行下面代码就可以生成静态页面至hexo/public目录下；
```
hexo generate
```
命令也可以简化成：
```
hexo n
```
>命令必须在init目录下执行，否则不成功，但是也不会报错。
>当你修改文章Tag或内容，不能正确重新生成内容，可以删除hexo/db.json后重试，还不行就到public目录删除对应的文件，重新生成。

# 本地预览
生成了静态页面，下一步就是浏览自己的成果，如果不预览一下就发布出去，可能会带来一些小麻烦；
执行下面的命令，可以启动本地服务，对文章进行预览调试。
```
hexo server
```
也可以简化成：
```
hexo s
```
然后在浏览器输入<http://localhost:4000>就可以看到效果。

# blog发布
上面的步骤都完成了，文章也ok了，那就发布吧！！！
使用下面的命令：
```
hexo deploy
```
同样也可以简写成：
```
hexo d
```

***
***
## 附录
** 常用命令： **
```
hexo new "newpostname"    #新建文章
hexo new page "pagename"  #新建页面
hexo generate             #生成静态页面至public目录
hexo server               #开启预览访问端口(http://localhost:4000)
```
** 常用复合命令： **
```
hexo deploy -g
hexo server -g
```
** 简写： **
```
hexo n == hexo new
hexo g == hexo generate
hexo s == hexo server 
hexo d == hexo deploy
```
