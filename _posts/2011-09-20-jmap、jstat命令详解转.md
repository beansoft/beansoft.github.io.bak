---
id: 2263
title: 'JMAP、jstat命令详解[转]'
date: 2011-09-20T19:48:31+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2263
permalink: '/2011/09/20/jmap%e3%80%81jstat%e5%91%bd%e4%bb%a4%e8%af%a6%e8%a7%a3%e8%bd%ac/'
views:
  - "4871"
original_post_id:
  - "2263"
image: /wp-content/uploads/2012/09/1257252433_java.png
categories:
  - JVM
---
来源: <http://blog.chinaunix.net/space.php?uid=531464&do=blog&id=2354636>

JMAP、jstat命令详解 (2011-08-23 10:41) 

&#160;

显示java进程内存使用的相关信息

· jmap pid #打印内存使用的摘要信息

· jmap –heap pid #java heap信息

· jmap -histo:live pid #统计对象count ，live表示在使用

· jmap -histo pid >mem.txt #打印比较简单的各个有多少个对象占了多少内存的信息，一般重定向的文件

· jmap -dump:format=b,file=mem.dat pid #将内存使用的详细情况输出到mem.dat 文件

用jhat命令可以参看 jhat -port 7000 mem.dat   
然后使用：http://127.0.0.1:7000/ 查看类相关信息   
各个className 

<table cellspacing="0" cellpadding="0" border="1">
  <tr>
    <td valign="top">
      <p>
        <b>BaseType Character </b>
      </p>
    </td>
    
    <td valign="top">
      <p>
        <b>Type </b>
      </p>
    </td>
    
    <td valign="top">
      <p>
        <b>Interpretation </b>
      </p>
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <p>
        B
      </p>
    </td>
    
    <td valign="top">
      <p>
        byte
      </p>
    </td>
    
    <td valign="top">
      <p>
        signed byte
      </p>
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <p>
        C
      </p>
    </td>
    
    <td valign="top">
      <p>
        char
      </p>
    </td>
    
    <td valign="top">
      <p>
        Unicode character
      </p>
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <p>
        D
      </p>
    </td>
    
    <td valign="top">
      <p>
        double
      </p>
    </td>
    
    <td valign="top">
      <p>
        double-precision floating-point value
      </p>
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <p>
        F
      </p>
    </td>
    
    <td valign="top">
      <p>
        float
      </p>
    </td>
    
    <td valign="top">
      <p>
        single-precision floating-point value
      </p>
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <p>
        I
      </p>
    </td>
    
    <td valign="top">
      <p>
        int
      </p>
    </td>
    
    <td valign="top">
      <p>
        integer
      </p>
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <p>
        J
      </p>
    </td>
    
    <td valign="top">
      <p>
        long
      </p>
    </td>
    
    <td valign="top">
      <p>
        long integer
      </p>
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <p>
        L<classname>;
      </p>
    </td>
    
    <td valign="top">
      <p>
        reference
      </p>
    </td>
    
    <td valign="top">
      <p>
        an instance of class <classname>
      </p>
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <p>
        S
      </p>
    </td>
    
    <td valign="top">
      <p>
        short
      </p>
    </td>
    
    <td valign="top">
      <p>
        signed short
      </p>
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <p>
        Z
      </p>
    </td>
    
    <td valign="top">
      <p>
        boolean
      </p>
    </td>
    
    <td valign="top">
      <p>
        true or false
      </p>
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <p>
        [
      </p>
    </td>
    
    <td valign="top">
      <p>
        reference
      </p>
    </td>
    
    <td valign="top">
      <p>
        one array dimension
      </p>
    </td>
  </tr>
</table>

内存泄漏一般都是有一定特征的，任何代码和数据都要占用内存，我简单总结内存泄漏的特征是内存占用不可控制，GC不可回收。我追踪内存使用量的曲线发现一些特征，在估计虚拟机即将崩溃时，使用   
jmap **-histo** pid >mem.txt 发现相关内存泄漏的对象占用非常大比例的内存空间，然后很容易猜测问题大概的位置，一下子就解决了。

Jstat是Sun JDK中自带的监控工具，利用了JVM内建的指令对Java应用程序的资源和性能进行实时的命令行的监控，包括了对Heap size和垃圾回收状况的监控等等。JStat是命令行方式运行，对系统资源占用很小，在大压力下很少影响性能。并且运行要求低，只要通过Telnet或SSH等方式远程登录到服务器所在机器，就可以进行监控。在与Jmap、JStack等工具结合使用时非常方便。

使用jstat命令监测如下内存使用和垃圾回收统计数据：   
**$ <JDK>/bin/jstat –gcutil [-h<lines>] <pid> <interval>**     **  
** jstat &#8211; gcutil选项打印所运行应用程序进程ID <pid>在指定抽样间隔<interval>下，堆使用及垃圾回收时间摘要，并且每<lines>行显示一次头信息。这产生出以下样例输出：   
S0 S1 E O P YGC YGCT FGC FGCT GCT   
0.00 0.00 24.48 46.60 90.24 142 0.530 104 28.739 29.269   
0.00 0.00 2.38 51.08 90.24 144 0.536 106 29.280 29.816   
0.00 0.00 36.52 51.08 90.24 144 0.536 106 29.280 29.816   
0.00 26.62 36.12 51.12 90.24 145 0.538 107 29.552 30.090   
名列含义：

S0：Survivor space 0 utilization as a percentage of the space&#8217;s current capacity.   
S1：Survivor space 1 utilization as a percentage of the space&#8217;s current capacity.   
E：Eden space utilization as a percentage of the space&#8217;s current capacity.   
O：Old space utilization as a percentage of the space&#8217;s current capacity.   
P：Permanent space utilization as a percentage of the space&#8217;s current capacity.   
YGC：Number of young generation GC events.   
YGCT：Young generation garbage collection time.   
FGC：Number of full GC events.   
FGCT：Full garbage collection time.   
GCT：Total garbage collection time.

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [JMAP、jstat命令详解[转]](http://www.beansoft.biz/2011/09/20/jmap%e3%80%81jstat%e5%91%bd%e4%bb%a4%e8%af%a6%e8%a7%a3%e8%bd%ac/)