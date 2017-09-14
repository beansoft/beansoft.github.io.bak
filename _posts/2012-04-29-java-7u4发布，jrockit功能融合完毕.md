---
id: 2918
title: Java 7u4发布，JRockit功能融合完毕
date: 2012-04-29T15:42:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2918
permalink: '/2012/04/29/java-7u4%e5%8f%91%e5%b8%83%ef%bc%8cjrockit%e5%8a%9f%e8%83%bd%e8%9e%8d%e5%90%88%e5%ae%8c%e6%af%95/'
views:
  - "11401"
categories:
  - Java SE
tags:
  - Java7
---
<h1 style="margin: 17pt 0cm 16.5pt;">
  Java 7u4发布，JRockit功能融合完毕
</h1>

<p style="text-align: left; margin: 0cm 0cm 0pt; mso-pagination: widow-orphan; mso-margin-top-alt: auto; mso-margin-bottom-alt: auto;">
  本文为WebLogic中文博客原创，禁止转载。日期：2012-04-29
</p>

<p style="text-align: left; margin: 0cm 0cm 0pt; mso-pagination: widow-orphan; mso-margin-top-alt: auto; mso-margin-bottom-alt: auto;">
  美国时间2012年4月26日，甲骨文发布了Java 7u4（Java SE 7 Update 4），同时发布的还有JavaFX 2.1，该版本可通过网址<a href="http://www.oracle.com/technetwork/java/javase/downloads/index.html">http://www.oracle.com/technetwork/java/javase/downloads/index.html</a>下载。至此，JRockit虚拟机的功能已经完整的融入到新的单一版本Oracle JVM中。
</p>

<p style="text-align: left; margin: 0cm 0cm 0pt; mso-pagination: widow-orphan; mso-margin-top-alt: auto; mso-margin-bottom-alt: auto;">
  官方新闻地址：Oracle Releases Java SE 7 Update 4 and JavaFX 2.1 <a href="http://www.oracle.com/us/corporate/press/1603497">http://www.oracle.com/us/corporate/press/1603497</a>
</p>

<p style="text-align: left; margin: 0cm 0cm 0.75pt; background: white; mso-pagination: widow-orphan; mso-outline-level: 2;">
  <strong>Java™ SE 7 Update 4</strong>
</p>

<p style="text-align: left; line-height: 12pt; margin: 0cm 0cm 12.75pt; background: white; mso-pagination: widow-orphan;">
  此次发布的更新包内部版本号为1.7.0_04-b20 (&#8220;b&#8221; 的含义是&#8221;build&#8221;). 外部版本号是7u4.
</p>

<p style="text-align: left; margin: 0cm 0cm 0pt; background: white; mso-pagination: widow-orphan; mso-outline-level: 3;">
  <strong>亮点</strong>
</p>

· Oracle JDK 正式支持 Mac OS X

· 新的JVM (Java HotSpot Virtual Machine, 版本 23)

· 新增垃圾收集器: Garbage First (G1)

· JavaFX 2.1 运行时将会在 JRE 7 自动更新时捆绑安装

· JAXP 升级至1.4.6

· Java DB 升级至10.8.2.2

· 针对SPARC T4 在安全领域进行了优化

· 解锁商业版功能的新参数

完整的更新内容可以查看 <http://www.oracle.com/technetwork/java/javase/7u4-relnotes-1575007.html>。

关注下其中的新JVM（含JRockit功能），G1和Commercial Features：

<p style="line-height: 12pt; margin: 0cm 0cm 0pt; background: white;">
  <strong>New JVM (Java HotSpot Virtual Machine, version 23)</strong>
</p>

<p style="text-align: left; line-height: 12pt; margin: 0cm 0cm 12.75pt; background: white; mso-pagination: widow-orphan;">
  <strong>HotSpot 23 features JRockit JVM feature convergence</strong><strong>（</strong><strong>HotSpot 23</strong><strong>已经完整的提供了</strong><strong>JRockit JVM</strong><strong>的功能集合）</strong><strong>.</strong> Some of the value-add features of the JRockit JVM are re-implemented in the HotSpot JVM. These features include:
</p>

· Text dumps with buffered data: buffered JVM state information available in text crash dumps and core/mdmp

· Diagnostics command framework (jcmd) and diagnostic commands

· Enhanced JMX Agent

<p style="text-align: left; line-height: 12pt; margin: 0cm 0cm 0pt; background: white; mso-pagination: widow-orphan;">
  Parallel Old GC (-XX:+UseParallelOldGC) is now enabled by default whenever -XX:+UseParallelGC is enabled. To revert to the previous default behavior, use the option -XX:-UseParallelOldGC on the java command line.
</p>

<p style="text-align: left; line-height: 12pt; margin: 0cm 0cm 12.75pt; background: white; mso-pagination: widow-orphan;">
  According to specification, the JVM should not maintain any particular order of methods being returned by reflection. In previous versions, the JVM used to return the methods in the declaration order and some user code may have relied on this behavior. Starting from Java SE 7, the JVM no longer guarantees constant order of methods and JMX MBeanInfo no longer guarantees equality of MBeanInfo between two identical MBeans.
</p>

<p style="text-align: left; line-height: 12pt; margin: 0cm 0cm 0pt; background: white; mso-pagination: widow-orphan;">
  <strong>New Supported Garbage Collector: Garbage First (G1)</strong>
</p>

<p style="text-align: left; line-height: 12pt; margin: 0cm 0cm 0pt; background: white; mso-pagination: widow-orphan;">
  Starting in Java SE 7u4 the Garbage First Collector is fully supported. The G1 collector is targeted for applications that fully utilize the large amount of memory available in today&#8217;s multiprocessor servers, while still keeping garbage collection latencies under control. Applications that require a large heap, have a big active data set, have bursty or non-uniform workloads or suffer from long Garbage Collection induced latencies should benefit from switching to G1. For more detailed information about G1 see the <a href="http://docs.oracle.com/javase/7/docs/technotes/guides/vm/G1.html">G1 documentation</a> page and <a href="http://www.oracle.com/technetwork/java/javase/tech/vmoptions-jsp-140102.html">command line options</a>.
</p>

<h2 style="margin: 2.25pt 0cm 0pt;">
  <a id="tuning_examples" name="tuning_examples"></a>Performance Tuning Examples
</h2>

<p style="widows: 2; margin: 1.5pt 0cm 12.75pt; orphans: 2; word-spacing: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px;">
  The following examples show how to use experimental tuning flags to optimize either throughput or faster response time.
</p>

<h3 style="widows: 2; margin: 2.25pt 0cm 0pt; orphans: 2; word-spacing: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px;">
  <a id="throughput" name="throughput"></a>Tuning for Higher Throughput
</h3>

<pre style="widows: 2; orphans: 2; word-spacing: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px;">java -d64 -server -XX:+AggressiveOpts -XX:+UseLargePages -Xmn10g  -Xms26g -Xmx26g</pre>

<h3 style="widows: 2; margin: 2.25pt 0cm 0pt; orphans: 2; word-spacing: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px;">
  <a id="response" name="response"></a>Tuning for Lower Response Time
</h3>

<pre style="widows: 2; orphans: 2; word-spacing: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px;">java -d64 -XX:+UseG1GC -Xms26g Xmx26g -XX:MaxGCPauseMillis=500 -XX:+PrintGCTimeStamps</pre>

<p style="text-align: left; line-height: 12pt; margin: 0cm 0cm 0pt; background: white; mso-pagination: widow-orphan;">
  <strong>New flag to unlock Commercial Features</strong>
</p>

<p style="text-align: left; line-height: 12pt; margin: 0cm 0cm 0pt; background: white; mso-pagination: widow-orphan;">
  The Java SE 7 Update 4 release introduces a new flag, -XX:+UnlockCommercialFeatures. This flag enables Oracle Java SE users to control when licensed features are allowed to run. All commercial features started or controlled via the command line or dynamically during execution will be gated by this flag. By default, commercial features are not allowed to execute, and any usage requires an active unlocking either on the command line or dynamically during runtime, to help remove any accidental usage.
</p>

<p style="text-align: left; line-height: 12pt; margin: 0cm 0cm 0pt; background: white; mso-pagination: widow-orphan;">
  For information on command line flags, see the command line documentation for <a href="http://docs.oracle.com/javase/7/docs/technotes/tools/#basic">Windows</a> and<a href="http://docs.oracle.com/javase/7/docs/technotes/tools/solaris/java.html">Solaris/Linux</a> platforms. For information about commercial features in Oracle Java SE and the license requirement please refer to <a href="http://www.oracle.com/us/technologies/java/standard-edition/advanced-suite/overview/index.html">Oracle Java SE Advanced and Suite</a>, and the <a href="http://www.oracle.com/technetwork/java/javase/terms/license/index.html">Binary Code License</a>.
</p>

<p style="margin: 0cm 0cm 0pt;">
  其它值得注意的是用户应尽快升级到Java 7，因为Oracle将在明年年底终止对JDK 6的支持：
</p>

<table style="width: 100%; mso-padding-alt: 0cm 0cm 0cm 0cm; mso-cellspacing: 0cm; mso-yfti-tbllook: 1184;" width="100%" border="0" cellspacing="0" cellpadding="0">
  <tr style="mso-yfti-irow: 0; mso-yfti-firstrow: yes;">
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;" colspan="7">
      <h2 style="text-align: center; margin: 0cm 0cm 0pt;" align="center">
        Oracle Java SE Support Roadmap*
      </h2>
    </td>
  </tr>
  
  <tr style="mso-yfti-irow: 1;">
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;" colspan="6">
      <hr align="center" size="2" width="100%" />
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
    </td>
  </tr>
  
  <tr style="mso-yfti-irow: 2;">
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
      <p style="text-align: center; margin: 0cm 0cm 0pt;">
        <strong>Major<br /> Release</strong>
      </p>
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
      <p style="text-align: center; margin: 0cm 0cm 0pt;">
        <strong>GA Date</strong>
      </p>
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
      <p style="text-align: center; margin: 0cm 0cm 0pt;">
        <strong>Premier Support<br /> Until**</strong>
      </p>
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
      <p style="text-align: center; margin: 0cm 0cm 0pt;">
        <strong>Extended Support<br /> Until**</strong>
      </p>
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
      <p style="text-align: center; margin: 0cm 0cm 0pt;">
        <strong>Sustaining<br /> Support</strong>
      </p>
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
    </td>
  </tr>
  
  <tr style="mso-yfti-irow: 3;">
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;" colspan="6">
      <hr align="center" size="2" width="100%" />
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
    </td>
  </tr>
  
  <tr style="mso-yfti-irow: 4;">
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
      <p style="margin: 0cm 0cm 0pt;">
        1.4
      </p>
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
      <p style="margin: 0cm 0cm 0pt;">
        Feb 2002
      </p>
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
      <p style="margin: 0cm 0cm 0pt;">
        Feb 2010
      </p>
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
      <p style="margin: 0cm 0cm 0pt;">
        Feb 2013
      </p>
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
      <p style="margin: 0cm 0cm 0pt;">
        Indefinite
      </p>
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
    </td>
  </tr>
  
  <tr style="mso-yfti-irow: 5;">
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;" colspan="6">
      <hr align="center" size="2" width="100%" />
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
    </td>
  </tr>
  
  <tr style="mso-yfti-irow: 6;">
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
      <p style="margin: 0cm 0cm 0pt;">
        5.0
      </p>
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
      <p style="margin: 0cm 0cm 0pt;">
        May 2004
      </p>
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
      <p style="margin: 0cm 0cm 0pt;">
        May 2011
      </p>
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
      <p style="margin: 0cm 0cm 0pt;">
        May 2014
      </p>
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
      <p style="margin: 0cm 0cm 0pt;">
        Indefinite
      </p>
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
    </td>
  </tr>
  
  <tr style="mso-yfti-irow: 7;">
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;" colspan="6">
      <hr align="center" size="2" width="100%" />
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
    </td>
  </tr>
  
  <tr style="mso-yfti-irow: 8;">
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
      <p style="margin: 0cm 0cm 0pt;">
        6
      </p>
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
      <p style="margin: 0cm 0cm 0pt;">
        Dec 2006
      </p>
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
      <p style="margin: 0cm 0cm 0pt;">
        Dec 2013
      </p>
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
      <p style="margin: 0cm 0cm 0pt;">
        Dec 2016
      </p>
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
      <p style="margin: 0cm 0cm 0pt;">
        Indefinite
      </p>
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
    </td>
  </tr>
  
  <tr style="mso-yfti-irow: 9;">
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;" colspan="6">
      <hr align="center" size="2" width="100%" />
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
    </td>
  </tr>
  
  <tr style="mso-yfti-irow: 10;">
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
      <p style="margin: 0cm 0cm 0pt;">
        7
      </p>
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
      <p style="margin: 0cm 0cm 0pt;">
        July 2011
      </p>
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
      <p style="margin: 0cm 0cm 0pt;">
        July 2016
      </p>
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
      <p style="margin: 0cm 0cm 0pt;">
        July 2019
      </p>
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
      <p style="margin: 0cm 0cm 0pt;">
        Indefinite
      </p>
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
    </td>
  </tr>
  
  <tr style="mso-yfti-irow: 11; mso-yfti-lastrow: yes;">
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;" colspan="6">
      <hr align="center" size="2" width="100%" />
    </td>
    
    <td style="background-color: transparent; border: #d4d0c8; padding: 0cm;">
    </td>
  </tr>
</table>

<p style="line-height: 12pt; margin: 0cm 0cm 0pt; background: white;">
  * Oracle Java SE commercial offering EOL dates are provided here as <strong>examples</strong> to illustrate the Oracle Java SE Support, Oracle Java SE Advanced, and Oracle Java SE Suite EOL Policy. Customers should refer to <a href="http://www.oracle.com/us/support/lifetime-support-068561.html">Oracle Lifetime Support policy</a> for the most up-to-date information.
</p>

<p style="line-height: 12pt; margin: 0cm 0cm 12.75pt; background: white;">
  ** Oracle will honor the support periods for legacy contracts with the dates stated in those contracts.
</p>

<p style="margin: 0cm 0cm 0pt;">
  参考文档：
</p>

<p style="margin: 0cm 0cm 0pt;">
  <a href="http://docs.oracle.com/javase/7/docs/technotes/tools/windows/java.html">http://docs.oracle.com/javase/7/docs/technotes/tools/windows/java.html</a>
</p>

<p style="margin: 0cm 0cm 0pt;">
  <a href="http://docs.oracle.com/javase/7/docs/technotes/tools/solaris/java.html">http://docs.oracle.com/javase/7/docs/technotes/tools/solaris/java.html</a>
</p>

<p style="margin: 0cm 0cm 0pt;">
  <a href="http://www.oracle.com/technetwork/java/javase/terms/products/index.html">http://www.oracle.com/technetwork/java/javase/terms/products/index.html</a>
</p>

<http://docs.oracle.com/javase/7/docs/technotes/guides/vm/index.html>

<p style="margin: 0cm 0cm 0pt; background: white;">
  <a href="http://www.oracle.com/technetwork/java/javase/overview/index-jsp-138218.html" target="_top">Java Platform, Standard Edition</a>
</p>

<p style="margin: 0cm 0cm 0pt; background: white;">
  <a href="http://www.oracle.com/java" target="_top">Java at Oracle</a>
</p>

<p style="margin: 0cm 0cm 0pt; background: white;">
  <a href="http://www.oracle.com/technetwork/java/javase/downloads/index.html" target="_top">Java SE Downloads on OTN</a>
</p>

<p style="margin: 0cm 0cm 0pt; background: white;">
  <a href="http://www.oracle.com/technetwork/java/javase/7u4-relnotes-1575007.html" target="_top">Java SE 7 Update 4 Release Notes</a>
</p>

<p style="margin: 0cm 0cm 0pt; background: white;">
  <a href="http://www.oracle.com/us/technologies/javafx/overview/index.html" target="_top">JavaFX</a>
</p>

<p style="margin: 0cm 0cm 0pt; background: white;">
  <a href="http://www.oracle.com/technetwork/java/javafx/overview/index.html" target="_top">JavaFX on OTN</a>
</p>

<p style="margin: 0cm 0cm 0pt; background: white;">
  <a href="http://openjdk.java.net/" target="_top">OpenJDK Community</a>
</p>

<p style="margin: 0cm 0cm 0pt; background: white;">
  <a href="http://planetjdk.org/" target="_top">Planet JDK</a> (JDK developer blogs)
</p>

<p style="margin: 0cm 0cm 0pt; background: white;">
  <a href="http://blogs.oracle.com/java" target="_top">Java Source Blog</a>
</p>

<p style="margin: 0cm 0cm 0pt; background: white;">
  <a href="https://blogs.oracle.com/henrik/" target="_top">Henrik on Java</a>
</p>

<p style="margin: 0cm 0cm 0pt; background: white;">
  <a href="https://blogs.oracle.com/javafx/" target="_top">The JavaFX Blog</a>
</p>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Java 7u4发布，JRockit功能融合完毕](http://www.beansoft.biz/2012/04/29/java-7u4%e5%8f%91%e5%b8%83%ef%bc%8cjrockit%e5%8a%9f%e8%83%bd%e8%9e%8d%e5%90%88%e5%ae%8c%e6%af%95/)