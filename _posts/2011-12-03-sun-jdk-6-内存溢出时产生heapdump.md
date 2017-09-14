---
id: 2627
title: Sun JDK 6 内存溢出时自动产生HeapDump
date: 2011-12-03T11:33:32+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2627
permalink: '/2011/12/03/sun-jdk-6-%e5%86%85%e5%ad%98%e6%ba%a2%e5%87%ba%e6%97%b6%e4%ba%a7%e7%94%9fheapdump/'
views:
  - "3821"
original_post_id:
  - "2627"
image: /wp-content/uploads/2012/09/1257252433_java.png
categories:
  - JVM
---
java -XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=C:/temp/oom.hprof &#8230;.

&#160;

完整的Sun JDK JVM参数可参考官方文章:[http://www.oracle.com/technetwork/java/javase/tech/vmoptions-jsp-140102.html](http://www.oracle.com/technetwork/java/javase/tech/vmoptions-jsp-140102.html "http://www.oracle.com/technetwork/java/javase/tech/vmoptions-jsp-140102.html")

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Sun JDK 6 内存溢出时自动产生HeapDump](http://www.beansoft.biz/2011/12/03/sun-jdk-6-%e5%86%85%e5%ad%98%e6%ba%a2%e5%87%ba%e6%97%b6%e4%ba%a7%e7%94%9fheapdump/)