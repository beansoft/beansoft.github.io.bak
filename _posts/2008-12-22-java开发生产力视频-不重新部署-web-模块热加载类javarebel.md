---
id: 378
title: 'Java开发生产力视频: 不重新部署 Web 模块热加载类(JavaRebel)'
date: 2008-12-22T14:15:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=378
permalink: '/2008/12/22/java%e5%bc%80%e5%8f%91%e7%94%9f%e4%ba%a7%e5%8a%9b%e8%a7%86%e9%a2%91-%e4%b8%8d%e9%87%8d%e6%96%b0%e9%83%a8%e7%bd%b2-web-%e6%a8%a1%e5%9d%97%e7%83%ad%e5%8a%a0%e8%bd%bd%e7%b1%bbjavarebel/'
views:
  - "3464"
original_post_id:
  - "378"
categories:
  - Java SE
tags:
  - JavaRebel
  - JRebel
  - Video
---
视频完整大小(1024&#215;768) 12分钟 文件大小5.2MB

视频文件下载(需要Flash播放器, 或者用MediaPlayer打开): <http://www.beansoft.biz/swf/javarebel.swf>

用 Eclipse 3.4 + Sysdeo Eclipse Tomcat Launcher plugin + JavaRebel 实现无重载 Web 应用开发

1. <http://java.sun.com/javase/downloads/index.jsp> 下载 JDK 6 Update 7 并安装

2. <http://www.eclipse.org/downloads/> 下载 Eclipse IDE for Java Developers (85 MB) eclipse-java-ganymede-win32.zip   
解压缩到硬盘即可完成安装过程   
3. <http://www.eclipsetotale.com/tomcatPlugin.html> 下载 Sysdeo Eclipse Tomcat Launcher plugin 3.2.1   
tomcatPluginV321.zip 10 May 2007 Works with Eclipse 3.1, 3.2, 3.3 and 3.4   
4. <http://www.zeroturnaround.com/download/> 下载 JavaRebel   
Devel 1.2-M1 (changes) javarebel-1.2-M1.zip 809 Kb 9th June 2008   
解压缩到硬盘d:完成安装过程.   
5. 配置 Tomcat 使用 JavaRebel 作为类加载器   
Window > Preferences > Tomcat > JVM Settings > Append to JVM Parameters:   
-noverify -javaagent:d:/javarebel.jar

6. 创建 Tomcat 项目并进行 JavaBean 开发

7. 设置项目为不可 reload 并检验运行效果

beansoft@126.com

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Java开发生产力视频: 不重新部署 Web 模块热加载类(JavaRebel)](http://www.beansoft.biz/2008/12/22/java%e5%bc%80%e5%8f%91%e7%94%9f%e4%ba%a7%e5%8a%9b%e8%a7%86%e9%a2%91-%e4%b8%8d%e9%87%8d%e6%96%b0%e9%83%a8%e7%bd%b2-web-%e6%a8%a1%e5%9d%97%e7%83%ad%e5%8a%a0%e8%bd%bd%e7%b1%bbjavarebel/)