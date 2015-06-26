---
layout: post
title: "【转】Eclipse项目GBK编码转换"
date: 2013-08-26 11:45:38 +0800
comments: true
categories: Tools
---

相信很多人都有项目中文乱码的情况吧，对于代码中有中文注释的项目来说，如果编码不统一，移植起来可能会很头疼，因为有的人可能一直都是GBK编码，虽然我们都提倡UTF-8,但这和平台及eclipse的编码设置有关，对于windows开发者来说，如果默认设置，那建完项目开始写，后来才发现是GBK编码，后悔莫及，这样带来了很多不便和麻烦。鉴于上面的问题，我还是推荐windows平台开发者统一编码为UTF-8,养成良好的习惯避免不必要的麻烦。
<!-- more -->

至于原来gbk编码的项目该如何处理，我这里推荐一个eclipse插件--[**com.lifesting.tool.encoding_1.0.0.jar**]({{ root_url }}/files/com.lifesting.tool.encoding_1.0.0.jar)
 
###具体使用方法如下：

1.将插件jar文件放入eclipse目录/plugins/文件夹下，重启Eclipse

<img src="{{ root_url }}/images/blog-img/eclipse-gbk-to-utf8-1.jpeg" />
	
2.选中项目，打开属性（**Alt+Enter**）,现在Resource条目下将项目编码改为自身编码，如GBK,你还会看到多了一项**Convert Setting**，点击进入

<img src="{{ root_url }}/images/blog-img/eclipse-gbk-to-utf8-2.jpeg" />
	

3.设置好之后，点击**Apply**

4.最后一步，右键项目，**Lifesting Tools--Set Encode**.

<img src="{{ root_url }}/images/blog-img/eclipse-gbk-to-utf8-3.png" />
	

这样再把项目编码改为utf-8，你会发现中文ok,项目已经成功转码为UFT-8了


## **PS:**
请先将Eclipse编码设置GBK,工程代码正常情况下进行如上操作，否则无效

**转载自**：http://blog.csdn.net/songzhiyong1121/article/details/9252687