---
id: 1789
title: 'HotSpot Java常用工具介绍-jps（Java Virtual Machine Process Status Tool）[转]'
date: 2011-02-25T18:14:41+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1789
permalink: '/2011/02/25/hotspot-java%e5%b8%b8%e7%94%a8%e5%b7%a5%e5%85%b7%e4%bb%8b%e7%bb%8d-jps%ef%bc%88java-virtual-machine-process-status-tool%ef%bc%89%e8%bd%ac/'
views:
  - "3730"
original_post_id:
  - "1789"
categories:
  - Java SE
  - 转载区
---
</p> 

<pre>来源: <a href="http://www.daniel-journey.com/archives/95">http://www.daniel-journey.com/archives/95</a> </pre>

##### **jps介绍**

jps简单理解就是一个java版的ps，用来提供一些简单的jvm信息（进程ID，进程启动的路径，命令行参数等等）。jps的语法格式如下

<pre><b>jps</b> [ <i>options</i> ] [ <i>hostid</i> ]</pre>

<pre><strong>options-- 命令行参数 ，可选</strong></pre>

> <pre>-q 不输出<i>classname</i>  或<i>JARfilename</i> –</pre>
> 
> <pre>-m 输出main 方法的参数</pre>
> 
> <pre>-l  输出main class的类全名(包含package)或者jar的全路径</pre>
> 
> <pre>-v(小写) JVM输入参数</pre>
> 
> <pre>-V(大写)  输出通过标志文件传给JVM的参数</pre>

<pre><strong>hostId是符合[<i>protocol</i>:][[//]<i>hostname</i>][:<i>port</i>][/<i>servername</i>]语法的字符串。</strong></pre>

<pre><i>protocol：</i>协议，缺省时rmi</pre>

<pre>hostname：主机名或IP地址，如果主机名忽略，就是localhost</pre>

<pre>port： 端口</pre>

<pre>如果hostId为空，jps会列出locahost上的Jvm进程信息。</pre>

<pre><strong>命令输出</strong></pre>

> <pre><i>lvmid</i> [ [ <i>classname</i> | <i>JARfilename</i> | "Unknown"] [ <i>arg</i>* ] [ <i>jvmarg</i>* ] ]</pre>
> 
> <pre>lvmId lvm进程ID</pre>
> 
> <pre>classname JVM启动类名</pre>
> 
> <pre>jarfilename  JVM启动的jar文件名</pre>
> 
> <pre>arg* 命令行参数</pre>
> 
> <pre>jvmarg jvm参数</pre>

<pre>&#160;</pre>

##### 参考资料

<http://java.sun.com/javase/6/docs/technotes/tools/share/jps.html>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [HotSpot Java常用工具介绍-jps（Java Virtual Machine Process Status Tool）[转]](http://www.beansoft.biz/2011/02/25/hotspot-java%e5%b8%b8%e7%94%a8%e5%b7%a5%e5%85%b7%e4%bb%8b%e7%bb%8d-jps%ef%bc%88java-virtual-machine-process-status-tool%ef%bc%89%e8%bd%ac/)