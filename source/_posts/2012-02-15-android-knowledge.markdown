---
layout: post
title: "Android知识点"
date: 2012-02-15 11:20:38 +0800
comments: true
categories: Android
---
1、通过代码设置控件的layout_weight属性：
```java 
setLayoutParams(new LinearLayout.LayoutParams(0,LayoutParams.FILL_PARENT, (1.0f / 4)));
```
2、Assets 下的资源如何使用？
```java 
Context.getAssets().open(String path)
```
3、Android调用已安装市场，进行软件评分的功能实现
```java 
Uri uri = Uri.parse("market://details?id="+getPackageName());  
Intent intent = new Intent(Intent.ACTION_VIEW,uri);  
intent.addFlags(Intent.FLAG_ACTIVITY_NEW_TASK);  
startActivity(intent); 
```
<!-- more -->
4、动态设置android:drawableLeft|Right|Top|Bottom
```java 
setCompoundDrawables(drawable left, drawable top, drawable right, drawable bottom)
```