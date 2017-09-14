---
id: 1882
title: Linux下Weblogic 11g jar格式安装包如何安装?
date: 2011-03-16T19:06:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1882
permalink: '/2011/03/16/linux%e4%b8%8bweblogic-11g-jar%e6%a0%bc%e5%bc%8f%e5%ae%89%e8%a3%85%e5%8c%85%e5%a6%82%e4%bd%95%e5%ae%89%e8%a3%85/'
views:
  - "25144"
original_post_id:
  - "1882"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - Install
  - jar
  - WebLogic
---
在[WebLogic 10.3.4正式发布,提供下载,支持JSF 2.0, JPA 2.0和JAX-RS 1.1[图]](http://www.beansoft.biz/?p=1582)一文中, 笔者提到了WebLogic有一种generic格式的安装包, 压缩包为jar格式, 那么这种安装包如何使用呢? 很简单, 首先自行下载JDK进行安装, 然后键入命令

**java -jar wls1034_generic.jar** 

即可启动安装过程, 默认启动的是图形界面的安装向导. 命令行方式的安装命令用如下方式启动:

**java -jar wls1034_generic.jar <font color="#008000">-mode=console</font>**

; 静默安装用如下方式启动:

**java -jar wls1034_generic.jar <font color="#008000">-mode=console -silent_xml=/path_to_silent.xml</font>**

关于静默安装的更多信息, 请浏览: [WebLogic静默卸载与安装[Slient Install and Uninstall]](http://www.beansoft.biz/?p=1055)

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Linux下Weblogic 11g jar格式安装包如何安装?](http://www.beansoft.biz/2011/03/16/linux%e4%b8%8bweblogic-11g-jar%e6%a0%bc%e5%bc%8f%e5%ae%89%e8%a3%85%e5%8c%85%e5%a6%82%e4%bd%95%e5%ae%89%e8%a3%85/)