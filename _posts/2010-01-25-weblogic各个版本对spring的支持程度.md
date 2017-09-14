---
id: 41
title: WebLogic各个版本对Spring的支持程度
date: 2010-01-25T12:15:00+00:00
author: 刘长炯
layout: post
guid: http://www.blogjava.net/beansoft/archive/2010/01/25/310714.html
permalink: '/2010/01/25/weblogic%e5%90%84%e4%b8%aa%e7%89%88%e6%9c%ac%e5%af%b9spring%e7%9a%84%e6%94%af%e6%8c%81%e7%a8%8b%e5%ba%a6/'
views:
  - "2432"
original_post_id:
  - "41"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
现在很多人在使用SSH架构(Spring, Struts, Hibernate)开发, Tomcat 上开发完了, 认为往WebLogic上一放, 就可以正常的运行. 然而实际情况并非这么简单.

首先是JDK支持问题, Tomcat 5.0 开始都支持 Java 5和 Java EE 5, 但 WebLogic 8 只支持 JDK 1.4, J2EE 1.3; WebLogic 9 之后才能支持 Java 5, J2EE 1.4; WebLogic 10 支持Java 6, Java EE 5.

然后我们在看看 WebLogic 官方的说法:

WebLogic 一直大力支持开源项目, 认证的Spring 版本如下:

Spring 1.2.0 WebLogic 8

Spring 1.2.5 WebLogic 9

Spring 2.0.1 WebLogic 10

讲了这么多, 是什么意思呢? 那就是您使用SSH架构的时候, 最好看看 WebLogic 最多支持 Spring 多少, 还有 JDK 版本, 否则出了问题, 相对来说您只能去改Spring源码才能解决问题了, 而不是简单的改一下你的应用配置就能搞定. 另外一个建议就是不要搞什么都用最新版, 因为老版本用的人多, 相对来说要稳定很多, 所以不要一看Spring升级了你也跟着升级, 这在WebLogic上是行不通的.

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [WebLogic各个版本对Spring的支持程度](http://www.beansoft.biz/2010/01/25/weblogic%e5%90%84%e4%b8%aa%e7%89%88%e6%9c%ac%e5%af%b9spring%e7%9a%84%e6%94%af%e6%8c%81%e7%a8%8b%e5%ba%a6/)