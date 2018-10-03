---
title: 使用Github管理Hexo博客的源文件
date: 2016-03-16 17:59:12
tags:
  - Github
  - Hexo
categories:
  - Hexo博客
---

使用Github管理Hexo博客的源文件

## 1.创建github仓库

Create a New Repository，用[https://github.com/repositories/new](https://github.com/repositories/new)来创建新仓库，填好名称后Create，之后会出现一些仓库的配置信息。这时候就表示配置好了。不需要用README来初始化仓库。我创建的仓库名称是BlogSourceFile。

![](https://flowsnow.oss-cn-shanghai.aliyuncs.com/history/github%E5%88%9B%E5%BB%BA%E4%BB%93%E5%BA%93.png)

<!--more-->

## 2.本地git操作

需要安装git for windows，可以从百度的软件中心[http://dlsw.baidu.com/sw-search-sp/soft/4e/30195/Git-2.7.2-32-bit_setup.1457942412.exe](http://dlsw.baidu.com/sw-search-sp/soft/4e/30195/Git-2.7.2-32-bit_setup.1457942412.exe)下载，也可以从github官网下载。

我自己的Hexo博客源文件的目录是d/Hexo/source/_posts。进入该目录之后，右键打开Git Bash。进行初始化init操作，在当前项目工程下履行这个号令相当于把当前项目git化

```
clg@020121345-NB MINGW32 /d/Hexo/source/_posts
$ git init
Initialized empty Git repository in D:/Hexo/source/_posts/.git/
```

此时会在当前目录下产生.git文件夹，这个文件夹默认是隐藏的。

add操作把当前目录下的全部文件（代码）加入git的跟踪中，意思就是交给git经管。

```
clg@020121345-NB MINGW32 /d/Hexo/source/_posts (master)
$ git add .
```

使用commit操作将暂存库中的改动提交到本地库，可以写一点提交信息，比如"first commit"或者"update"等等。

```
$ git commit -m "first commit"
```

现在需要把改动写入到github网站中。由于是第一次提交文件到远程仓库（github服务器上的仓库在本地就成为remote，其中给这个项目的远程仓库取的名字是origin，也可以取别的名字比如blog等等），需要先执行下面的命令，相当于指定本地库与github上的哪个项目相连，只有用git@这种形式才表示使用ssh，而不是使用https。

```
$ git remote add origin git@github.com:Flowsnow/BlogSourceFile.git
```

有时候可能出现错误fatal: remote origin already exists.这个错误的意思是远程已存在。

解决办法：先删除，再添加

```
$ git remote rm origin
$ git remote add origin https://github.com/Flowsnow/BlogSourceFile.git
```

接着就可以将本地库提交到github上的该远程仓库的master分支上。如果没有配置ssh，则需要输入github的用户名和密码。提交之后可以在网站上看到提交的内容。

```
git push -u origin master
```

如果下次需要写blog，需要先把master分支同步到本地库中。可以用下列命令,相当于获取远程更新，并且和本地库融合。也就是说每次写blog之前都需要更新本地库。

```
git pull origin master
```

## 3.配置ssh

Generating an SSH key:

[https://help.github.com/articles/generating-an-ssh-key/](https://help.github.com/articles/generating-an-ssh-key/)

**附：**

参考：[http://blog.csdn.net/binyao02123202/article/details/20130891](http://blog.csdn.net/binyao02123202/article/details/20130891)