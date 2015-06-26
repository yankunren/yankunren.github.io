---
layout: post
title: "Android客户端集成百度推送服务"
date: 2014-06-26 18:38:23 +0800
comments: true
categories: Android
---

**1、创建项目：**http://developer.baidu.com/console#app/create

<img src="{{ root_url }}/images/blog-img/android-integrate-baidu-push-1.png" /><!-- more -->

**2、推送设置**

<img src="{{ root_url }}/images/blog-img/android-integrate-baidu-push-2.png" />

<img src="{{ root_url }}/images/blog-img/android-integrate-baidu-push-3.png" />

**3、客户端集成**
http://developer.baidu.com/wiki/index.php?title=docs/cplat/push

下载Android-sdk

1>>Application 文件需要继承
```java 
public class DemoApplication extends FrontiaApplication 
```
2>>AndroidManifest.xml 添加以下代码段
```xml 
        <!-- push必须的receviver和service声明 -->
        <receiver android:name="com.baidu.android.pushservice.PushServiceReceiver"
            android:process=":bdservice_v1">
            <intent-filter>
                <action android:name="android.intent.action.BOOT_COMPLETED" />
                <action android:name="android.net.conn.CONNECTIVITY_CHANGE" />
                <action android:name="com.baidu.android.pushservice.action.notification.SHOW" />
                <action android:name="com.baidu.android.pushservice.action.media.CLICK" />
            </intent-filter>
        </receiver>
        <receiver android:name="com.baidu.android.pushservice.RegistrationReceiver"
            android:process=":bdservice_v1">
            <intent-filter>
                <action android:name="com.baidu.android.pushservice.action.METHOD" />
                <action android:name="com.baidu.android.pushservice.action.BIND_SYNC" />
            </intent-filter>
            <intent-filter>
                <action android:name="android.intent.action.PACKAGE_REMOVED"/>
                <data android:scheme="package" />
            </intent-filter>
        </receiver>
        <service
            android:name="com.baidu.android.pushservice.PushService"
            android:exported="true"
            android:process=":bdservice_v1" >
            <intent-filter>
                <action android:name="com.baidu.android.pushservice.action.PUSH_SERVICE" />
            </intent-filter>
        </service>
        <!-- push结束 -->
       
    <!-- Push service 运行需要的权限 -->
    <uses-permission android:name="android.permission.RECEIVE_BOOT_COMPLETED" />
    <uses-permission android:name="android.permission.WRITE_SETTINGS" />
    <uses-permission android:name="android.permission.VIBRATE" />
    <uses-permission android:name="android.permission.ACCESS_DOWNLOAD_MANAGER" />
    <uses-permission android:name="android.permission.DOWNLOAD_WITHOUT_NOTIFICATION" />
    <uses-permission android:name="android.permission.DISABLE_KEYGUARD" />
    <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
```