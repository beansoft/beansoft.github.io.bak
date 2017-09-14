---
id: 3047
title: JVM崩溃相关的几个参数：-XX:+ShowMessageBoxOnError，-XX:OnError等
date: 2012-09-13T20:37:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3047
permalink: '/2012/09/13/jvm%e5%b4%a9%e6%ba%83%e7%9b%b8%e5%85%b3%e7%9a%84%e5%87%a0%e4%b8%aa%e5%8f%82%e6%95%b0%ef%bc%9a-xxshowmessageboxonerror%ef%bc%8c-xxonerror%e7%ad%89/'
views:
  - "5183"
image: /wp-content/uploads/2012/09/1257252433_java.png
categories:
  - JVM
tags:
  - Crash
  - Debug
  - JVM
---
### 崩溃前弹出提示框

Sun JVM: -XX:+ShowMessageBoxOnError

JRockit JVM: -Djrockit.waitonerror

### 内存溢出时转储内存堆栈

-XX:+HeapDumpOnOutOfMemoryError

### 崩溃后自动执行相关命令

Sun JVM:

-XX:OnError=”<cmd args>;<cmd args>”

-Xcheck:jni 检查JNI本机代码

例如：

<pre>-XX:OnError="gcore %p; dbx - %p"
  -XX:OnError="gdb %p"
  -XX:OnError="pmap %p"</pre>

<pre>&nbsp;</pre>

### 参考资料

<pre>Java 6 JVM参数选项大全（中文版）【转】<a title="http://www.beansoft.biz/?p=2923" href="http://www.beansoft.biz/?p=2923">http://www.beansoft.biz/?p=2923</a></pre>

Java TM 2 Platform, Standard Edition 5.0 Troubleshooting and Diagnostic Guide [http://java.sun.com/j2se/1.5/pdf/jdk50\_ts\_guide.pdf](http://java.sun.com/j2se/1.5/pdf/jdk50_ts_guide.pdf)

#### Troubleshooting Guide for Java SE 6 with HotSpot VM <http://www.oracle.com/technetwork/java/javase/toc-135973.html>

<http://www.oracle.com/technetwork/java/javase/tech/vmoptions-jsp-140102.html>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [JVM崩溃相关的几个参数：-XX:+ShowMessageBoxOnError，-XX:OnError等](http://www.beansoft.biz/2012/09/13/jvm%e5%b4%a9%e6%ba%83%e7%9b%b8%e5%85%b3%e7%9a%84%e5%87%a0%e4%b8%aa%e5%8f%82%e6%95%b0%ef%bc%9a-xxshowmessageboxonerror%ef%bc%8c-xxonerror%e7%ad%89/)