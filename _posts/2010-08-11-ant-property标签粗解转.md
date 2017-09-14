---
id: 545
title: 'ant property标签粗解[转]'
date: 2010-08-11T22:13:49+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=545
permalink: '/2010/08/11/ant-property%e6%a0%87%e7%ad%be%e7%b2%97%e8%a7%a3%e8%bd%ac/'
views:
  - "3494"
original_post_id:
  - "545"
categories:
  - Apache开源产品
---
#### 来自: [http://www.blogjava.net/wiflish/archive/2006/05/12/45814.html](http://www.blogjava.net/wiflish/archive/2006/05/12/45814.html "http://www.blogjava.net/wiflish/archive/2006/05/12/45814.html")

#### <a name="property">Property设置属性的7种方法：</a>

#### <a name="property"></a>

#### <a name="property"></a>

1、设置name和value属性值，比如：<property name="srcdir" value="${basedir}/src"/>   
2、设置name和refid属性值，比如：<property name="srcpath" refid="dao.compile.classpath"/>，其中&#160;&#160;&#160; dao.compile.classpath在别的地方定义。   
3、设置name和location属性值，比如：<property name="srcdir" location="src"/>，即将srcdir的值设&#160;&#160;&#160; 置为：当前项目根目录的/src目录。   
4、设置file属性值，比如：<property file="build.properties"/>， 导入build.properties属性文件中&#160;&#160;&#160; 的属性值   
5、设置resource属性值，比如：<propety resource="build.properties"/>,导入build.properties属性文&#160;&#160;&#160; 件中的属性值   
6、设置url属性值，比如：<property url="http://www.blogjava.net/wiflish/build.properties"/>,导&#160;&#160;&#160; 入http://www.blogjava.net/wiflish/build.properties属性文件中的属性值。   
7、设置环境变量，比如：<property environment="env"/>，设置系统的环境变量为前缀env.   
&#160;&#160;&#160;&#160; <property name="tomcat.home" value="${env.CATALINA_HOME}"/> 将系统的tomcat安装目录设置到&#160;&#160;&#160; tomcat.home属性中。

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [ant property标签粗解[转]](http://www.beansoft.biz/2010/08/11/ant-property%e6%a0%87%e7%ad%be%e7%b2%97%e8%a7%a3%e8%bd%ac/)