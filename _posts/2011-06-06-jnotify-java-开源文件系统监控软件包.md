---
id: 2025
title: JNotify Java 开源文件系统监控软件包
date: 2011-06-06T13:42:41+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2025
permalink: '/2011/06/06/jnotify-java-%e5%bc%80%e6%ba%90%e6%96%87%e4%bb%b6%e7%b3%bb%e7%bb%9f%e7%9b%91%e6%8e%a7%e8%bd%af%e4%bb%b6%e5%8c%85/'
views:
  - "5238"
original_post_id:
  - "2025"
categories:
  - OpenSource
---
#### File system events library for Java

&#160;

<http://jnotify.sourceforge.net/>

#### JNotify java API

JNotify is a java library that allow java application to listen to file system events, such as: 

  * File created 
  * File modified 
  * File renamed 
  * File deleted

#### Supported platforms

  * Windows (2000 or newer) [Windows notes](http://jnotify.sourceforge.net/windows.html)
  * Linux with INofity support (2.6.14 or newer) [Linux notes](http://jnotify.sourceforge.net/linux.html)
  * Mac OS X (10.5 or newer) [Mac OS notes](http://jnotify.sourceforge.net/macos.html)

#### Usage example

JNotify can be tested by simply running the jar file with the followng commend:   
**java -Djava.library.path=. -jar jnotify-VER.jar [dir]**

JNotify will then monitor the specified dir (or the current directory if dir is not specified) and print detected events. Note that java.library.path should point to the location of the native libraries that comes with jnotify (dlls, so dylibs etc).

Check out the [code sample page](http://jnotify.sourceforge.net/sample.html).

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [JNotify Java 开源文件系统监控软件包](http://www.beansoft.biz/2011/06/06/jnotify-java-%e5%bc%80%e6%ba%90%e6%96%87%e4%bb%b6%e7%b3%bb%e7%bb%9f%e7%9b%91%e6%8e%a7%e8%bd%af%e4%bb%b6%e5%8c%85/)