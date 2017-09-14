---
id: 2260
title: 使用JDK自带工具jps,jmap和jhat分析内存数据
date: 2011-09-19T21:06:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2260
permalink: '/2011/09/19/%e4%bd%bf%e7%94%a8jdk%e8%87%aa%e5%b8%a6%e5%b7%a5%e5%85%b7jpsjmap%e5%92%8cjhat%e5%88%86%e6%9e%90%e5%86%85%e5%ad%98%e6%95%b0%e6%8d%ae/'
views:
  - "4100"
original_post_id:
  - "2260"
image: /wp-content/uploads/2012/09/1257252433_java.png
categories:
  - JVM
tags:
  - jhat
  - JVM
---
D:>jps   
684   
8136 Jps 

D:>jmap -dump:format=b,file=heap.bin 684   
Dumping heap to D:heap.bin &#8230;   
Heap dump file created 

D:>jhat -port 7000 heap.bin   
Reading from heap.bin&#8230;   
Dump file created Mon Sep 18 14:49:50 CST 2011   
Snapshot read, resolving&#8230;   
Resolving 119495 objects&#8230;   
Chasing references, expect 23 dots&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;..   
Eliminating duplicate references&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;..   
Snapshot resolved.   
Started HTTP server on port 7000   
Server is ready.

<img title="jhat" style="display:inline;" height="608" alt="jhat" src="http://www.beansoft.biz/wp-content/uploads/2011/09/jhat.gif" width="608" />

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [使用JDK自带工具jps,jmap和jhat分析内存数据](http://www.beansoft.biz/2011/09/19/%e4%bd%bf%e7%94%a8jdk%e8%87%aa%e5%b8%a6%e5%b7%a5%e5%85%b7jpsjmap%e5%92%8cjhat%e5%88%86%e6%9e%90%e5%86%85%e5%ad%98%e6%95%b0%e6%8d%ae/)