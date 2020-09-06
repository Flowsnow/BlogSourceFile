---
title: Sublime Text 3解决中文乱码
tags:
  - 工具
  - 总结
  - 编辑
  - 配置
id: 184
categories:
  - 工具使用
date: 2016-01-11 10:50:22
---

众所周知，Sublime Text 3（下面简称ST3）的默认编码是utf-8，因此需要把GB2312和GBK编码转换成utf-8。在Sublime Text 2中大家解决中文乱码的方法都是先装好Package Control，然后再通过这个安装ConvertToUTF8的Package。

<!--more-->

## 安装Package Control

但是在Sublime Text 3中安装Package Control的方法发生了变化，新的安装方法是，按Control + ~打开命令行，然后输入下面这一行代码

``` python
import urllib.request,os; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); open(os.path.join(ipp, pf), 'wb').write(urllib.request.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ','%20')).read())
```

执行之后，必须重启Sublime Text 3，才能继续下面的步骤。

## 安装ConvertToUTF8

打开Preference下面Package Control，输入Install Package回车，这时候会加载所有的packges列表。看到列表之后再输入ConvertToUTF8回车，就会下载安装这个包了。装好之后会看到这个包的说明文件。

至此中文乱码成功解决。

附：

Sublime Text 2的Package Control安装代码：

``` python
import urllib2,os; pf='Package Control.sublime-package'; ipp = sublime.installed_packages_path(); os.makedirs( ipp ) if not os.path.exists(ipp) else None; urllib2.install_opener( urllib2.build_opener( urllib2.ProxyHandler( ))); open( os.path.join( ipp, pf), 'wb' ).write( urllib2.urlopen( 'http://sublime.wbond.net/' +pf.replace( ' ','%20' )).read()); print( 'Please restart Sublime Text to finish installation')
```

参考：

[https://www.cnblogs.com/luoshupeng/archive/2013/09/09/3310777.html](https://www.cnblogs.com/luoshupeng/archive/2013/09/09/3310777.html)

[https://www.cnblogs.com/joeblackzqq/p/4485067.html](https://www.cnblogs.com/joeblackzqq/p/4485067.html)
