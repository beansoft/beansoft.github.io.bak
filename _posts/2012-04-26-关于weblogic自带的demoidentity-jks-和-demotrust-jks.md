---
id: 2907
title: 关于WebLogic自带的DemoIdentity.jks 和 DemoTrust.jks
date: 2012-04-26T21:46:03+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2907
permalink: '/2012/04/26/%e5%85%b3%e4%ba%8eweblogic%e8%87%aa%e5%b8%a6%e7%9a%84demoidentity-jks-%e5%92%8c-demotrust-jks/'
views:
  - "10406"
image: /wp-content/uploads/2012/04/flash.png
categories:
  - WebLogic
---
作者：**刘长炯** 来源：**WebLogic中文博客** 日期：**2012-04-26**

<p align="left">
  DemoIdentity.jks和DemoTrust.jks都是什么文件？打开的密码是什么？本文将会对此做一简要介绍。
</p>

## 启用SSL及相关文件

WebLogic安装后启动SSL的方式很简便，以安装后的默认单服务器域为例，进入控制台，即可启：http://localhost:7001/console è Servers è DefaultServer(Admin) è SSL Listen Port Enabled

WebLogic启用SSL连接需部署服务器证书、CA证书链、信任证书链，这三个文件分别对应于WebLogic安装目录下（路径$ WL_HOME/server/lib/）的DemoTrust.jks，DemoIdentity.jks和cacerts。前两个文件是非安全的，只能用于测试，不能用于生产；后一个文件是WebLogic的默认cacerts文件。

阅读全文：<a href="./wp-content/uploads/2012/04/WLSDemoIdentity.swf" target="_blank">wp-content/uploads/2012/04/WLSDemoIdentity.swf</a>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [关于WebLogic自带的DemoIdentity.jks 和 DemoTrust.jks](http://www.beansoft.biz/2012/04/26/%e5%85%b3%e4%ba%8eweblogic%e8%87%aa%e5%b8%a6%e7%9a%84demoidentity-jks-%e5%92%8c-demotrust-jks/)