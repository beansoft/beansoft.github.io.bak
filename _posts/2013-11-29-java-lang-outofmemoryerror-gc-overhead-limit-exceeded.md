---
id: 3472
title: java.lang.OutOfMemoryError, GC overhead limit exceeded
date: 2013-11-29T08:17:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3472
permalink: /2013/11/29/java-lang-outofmemoryerror-gc-overhead-limit-exceeded/
views:
  - "10300"
image: /wp-content/uploads/2012/09/1257252433_java.png
categories:
  - JVM
tags:
  - GC
  - JVM
---
Taken from: [http://www.chrisstucchio.com/blog/2013/gc\_overhead\_limit.html](http://www.chrisstucchio.com/blog/2013/gc_overhead_limit.html "http://www.chrisstucchio.com/blog/2013/gc_overhead_limit.html")

[http://www.cnblogs.com/twyth/articles/1895076.html](http://www.cnblogs.com/twyth/articles/1895076.html "http://www.cnblogs.com/twyth/articles/1895076.html")

**一、异常如下：   
** Exception in thread "main" java.lang.OutOfMemoryError: GC overhead limit exceeded

**二、解释：**   
JDK6新增错误类型。当GC为释放很小空间占用大量时间时抛出。   
一般是因为堆太小。导致异常的原因：没有足够的内存。

**三、解决方案：**

****

1、查看系统是否有使用大内存的代码或死循环。   
2、可以添加JVM的启动参数来限制使用内存：-XX:-UseGCOverheadLimit

One annoying error which I often see when running Hadoop jobs is this:

    java.lang.OutOfMemoryError: GC overhead limit exceeded
    

The cause of this error is that Java is spending a lot of time inside the garbage collector, and is not freeing up large chunks of memory. When this error occurs, it is a sign that your performance is being harmed due to object creation, and that you can mitigate it by reducing the number of objects. One mitigation strategy I’ve used is [deduplication](http://www.chrisstucchio.com/blog/2013/deduplication.html). Another I’ve used is mutability. Rather than doing this:

    case class Foo(var x: Int, var y: Boolean) extends Writable {
      def +(other: Foo): Foo = Foo(x+other.x, y && other.y)
      ...
    }
    

you can reduce object creation by doing this:

    case class Foo(var x: Int, var y: Boolean) extends Writable {
      def ++(other: Foo): Foo = {
          x += other.x
      y = y && other.y
        }
      ...
    }
    

Ultimately the solution to this problem is to tell the child Java process to ignore the fact that it is spending a lot of time inside GC. Then you might still waste a lot of time waiting for GC, but it won’t crash your job. For the sake of efficiency I still recommend trying to reduce object creation, but at the end of the day you can still do this (example is [scalding](https://github.com/twitter/scalding) code):

    class MyJob(args: Args) extends Job(args) {
      override def config(implicit mode: com.twitter.scalding.Mode) = super.config ++ Map("mapred.child.java.opts" -> "-XX:-UseGCOverheadLimit")
    
      ...your job goes here...
    }
    

(I don’t know how to pass jvm options to the child jvm in raw hadoop, but the one to pass in is ”-XX:-UseGCOverheadLimit”.)

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [java.lang.OutOfMemoryError, GC overhead limit exceeded](http://www.beansoft.biz/2013/11/29/java-lang-outofmemoryerror-gc-overhead-limit-exceeded/)