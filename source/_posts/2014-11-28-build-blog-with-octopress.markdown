---
layout: post
title: "搭建Octopress博客"
date: 2014-11-28 10:58:24 +0800
comments: true
categories: Octopress
tags: [octopress]
---
###Windows搭建###
转载：http://www.cnblogs.com/oec2003/archive/2013/05/27/3100896.html

您需要掌握的
使用Octopress来搭建博客，还是有一定门槛的，看完本文后，希望您不会觉得很难。

Octopress 是一款基于 Jekyll 的静态站点生成系统，使用Ruby实现，所以您需要懂点Ruby的知识，其实会几个命令就行；
<!-- more -->
Octopress的博客内容是通过Markdown来书写，所以您需要了解Markdown的编写规则，Markdown 语法说明可以让你在几分钟之内熟悉Markdown的语法，在Windows下可以使用MarkDown Pad或是使用在线的编辑器http://mahua.jser.me/ 进行编辑；

Octopress通常会部署在GitHub上，所以您需要会一些简单的Git命令以及Gtihub的使用。

准备
系统：Windows 2003 Server、Windows 7、Windows 2008R2 Server，这三个系统用下面的版本都安装成功过；

> - Git：http://msysgit.googlecode.com/files/Git-1.8.1.2-preview20130201.exe
> - Ruby：http://files.rubyforge.vm.bytemark.co.uk/rubyinstaller/rubyinstaller-1.9.3-p429.exe
> - DevKit：http://cloud.github.com/downloads/oneclick/rubyinstaller/DevKit-tdm-32-4.5.2-20111229-1559-sfx.exe
> - Python：http://www.python.org/ftp/python/2.7.5/python-2.7.5.msi
> - Octopress：git://github.com/imathis/octopress.git

安装
安装Git
Windows下安装Git很简单，一路next就可以了。

安装Ruby
Ruby的安装也是一路next就可以，不过记得勾选“Add Ruby executables to your PATH”，将Ruby的执行路径加入到环境变量中，如果忘记勾选，也可以手动设置。安装完后可以在命令提示符中输入ruby –version 来确认是否安装成功。

安装DevKit
DevKit下载下来的是一个自压缩文件，我们将其解压到D:/DevKit，有两点需要注意：

> 1. 解压目录中没有有中文和空格；

> 2. 必须先安装Ruby，而且Ruby需要是RubyInstallser安装。

解压DevKit后，在命令行输入以下命令来进行安装：
``` 
d: 
cd DevKit
ruby dk.rb init 
ruby dk.rb install
```
安装Python
安装Python,也是一路next就可以，博客的代码高亮用到了Python的Pygments模块，在Python中安装第三方库需要使用easy_install，在下面地址下载跟Python相对应的安装程序安装后就可以使用easy_install了。

https://pypi.python.org/pypi/setuptools

easy_install会安装在Python安装目录的Scripts目录中，例如我的Python目录是C:\Python27，所以需要将C:\Python27\Scripts目录加入到环境变量中才能在命令提示符中使用easy_install命令。

在命令提示符中输入如下命令就可以安装Pygments了。
``` 
easy_install pygments
```
安装Octopress
首先在GitBash中输入如下命令将Octopress代码拉到本地，
``` 
cd d:/GitProject
git clone git://github.com/imathis/octopress.git octopress
```
然后需要安装Octopress的依赖项，安装依赖项需要用到Ruby的gem，使用下面的命令可以更换gem的更新源，使用国内的淘宝镜像速度相对快点。
``` 
gem sources -a http://ruby.taobao.org/
gem sources -r http://rubygems.org/
gem sources -l
```
修改Octopress目录下的Gemfile文件，将第一行的http://rubygems.org/ 修改为http://ruby.taobao.org/

在命令提示符中进入到Octopress目录，输入下面命令进行依赖项的安装
``` 
gem install bundler
bundle install
```
输入下面的命令来安装Octopress的默认主题
``` 
rake install
```
到此所有的安装工作已经结束，输入下面的命令可以在本地进行预览。
``` 
rake preview
```