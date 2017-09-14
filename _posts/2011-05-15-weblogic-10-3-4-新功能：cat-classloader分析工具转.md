---
id: 2008
title: 'WebLogic 10.3.4 新功能：CAT &#8211; Classloader分析工具[转]'
date: 2011-05-15T22:25:28+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2008
permalink: '/2011/05/15/weblogic-10-3-4-%e6%96%b0%e5%8a%9f%e8%83%bd%ef%bc%9acat-classloader%e5%88%86%e6%9e%90%e5%b7%a5%e5%85%b7%e8%bd%ac/'
views:
  - "8420"
original_post_id:
  - "2008"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
  - 转载区
---
作者: Andrew&#8217;s WebLogic Ranch 原文链接: [http://blog.iaskengineer.com/andrew/entry/weblogic\_10\_3\_4\_%E6%96%B0%E5%8A%9F%E8%83%BD](http://blog.iaskengineer.com/andrew/entry/weblogic_10_3_4_%E6%96%B0%E5%8A%9F%E8%83%BD)

在程序开发运行时，我们经常会遇到ClassCastException, ClassDefNotFoundException。尽管我们知道classloder的继承性，但是无法改变在WebLogic这样的容器中各种classloader的复杂性。一个类可以通过各种方式被load到当前JVM中：

  * 应用程序自带的jar 
  * 每个jar文件的MANIFEST路径 
  * WebLogic服务器自带应用程序和jar文件 
  * WebLogic的系统classpath

Classloader的分析有可能相当复杂。尽管我们可以打开一些debug，比如：

  * -Dweblogic.utils.classloaders.GenericClassLoader.Verbose=true
  * -Dweblogic.utils.classloaders.ChangeAwareClassLoader.Verbose=true 

但是当你看到输出的时候还是会被吓到的，一个英文单词很贴切：overwhelming！

于是WebLogic 10.3.4提供了这样一个工具： CAT &#8211; Classloader Analysis Tool。看[官方文档](http://download.oracle.com/docs/cd/E17904_01/web.1111/e13852/toc.htm#CHDBIEHJ)怎么说：

&#8230;&#8230;&#8230; 完整内容查看原文链接.

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [WebLogic 10.3.4 新功能：CAT &#8211; Classloader分析工具[转]](http://www.beansoft.biz/2011/05/15/weblogic-10-3-4-%e6%96%b0%e5%8a%9f%e8%83%bd%ef%bc%9acat-classloader%e5%88%86%e6%9e%90%e5%b7%a5%e5%85%b7%e8%bd%ac/)