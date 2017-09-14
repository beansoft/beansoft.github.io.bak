---
id: 2124
title: GCViewer,开源GC日志分析工具
date: 2011-08-03T23:13:23+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2124
permalink: '/2011/08/03/gcviewer%e5%bc%80%e6%ba%90gc%e5%88%86%e6%9e%90%e5%b7%a5%e5%85%b7/'
views:
  - "13086"
original_post_id:
  - "2124"
image: /wp-content/uploads/2012/09/1257252433_java.png
categories:
  - JVM
tags:
  - GCViewer
---
官方主页: <http://www.tagtraum.com/gcviewer.html>

下载:

   <span class="Apple-style-span" style="word-spacing:0;font:medium simsun;text-transform:none;color:rgb(0,0,0);text-indent:0;white-space:normal;letter-spacing:normal;border-collapse:separate;orphans:2;widows:2;"></p> 

<table cellspacing="0" cellpadding="5" width="100%" border="0">
  <tr>
    <th>
      日期
    </th>
    
    <th>
      二进制 GZIP TAR 格式
    </th>
    
    <th>
      二进制 ZIP 格式
    </th>
  </tr>
  
  <tr>
    <td style="font:12px/16px &#039;">
      28.5.08
    </td>
    
    <td style="font:12px/16px &#039;">
      <a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/download/gcviewer-1.29-bin.tar.gz">gcviewer-1.29-bin.tar.gz</a><span class="Apple-converted-space">&#160;</span>[1,301,014字节]
    </td>
    
    <td style="font:12px/16px &#039;">
      <a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/download/gcviewer-1.29-bin.zip">gcviewer-1.29-bin.zip</a><span class="Apple-converted-space">&#160;</span>[1,300,651字节]
    </td>
  </tr>
</table>

<p style="font:12px/16px &#039;margin:8px 16px;">
  <p style="font:12px/16px &#039;margin:8px 16px;">
    <table cellspacing="0" cellpadding="5" width="100%" border="0">
      <tr>
        <th>
          日期
        </th>
        
        <th>
          源码 GZIP TAR 格式
        </th>
        
        <th>
          源代码 ZIP 格式
        </th>
      </tr>
      
      <tr>
        <td style="font:12px/16px &#039;">
          28.5.08
        </td>
        
        <td style="font:12px/16px &#039;">
          <a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/download/gcviewer-1.29-src.tar.gz">gcviewer-1.29-src.tar.gz</a><span class="Apple-converted-space">&#160;</span>[2,351,373字节]
        </td>
        
        <td style="font:12px/16px &#039;">
          <a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/download/gcviewer-1.29-src.zip">gcviewer-1.29-src.zip</a><span class="Apple-converted-space">&#160;</span>[2,424,539字节]
        </td>
      </tr>
    </table>
    
    <p>
      </span>
    </p>
    
    <p>
      运行:
    </p>
    
    <p>
      <code>java -jar gcviewer-1.2x.jar</code>
    </p>
    
    <p>
      支持的JVM:
    </p>
    
    <ul>
      <li>
        Sun JDK 1.4/1.5 with the options <code>&lt;a href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.loggc">-Xloggc:&lt;file&gt;&lt;/a> [&lt;a href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.PrintGCDetails">-XX:+PrintGCDetails&lt;/a>]</code>
      </li>
      <li>
        Sun JDK 1.2.2/1.3.1/1.4 with the option <code>&lt;a href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.verbose">-verbose:gc&lt;/a></code>
      </li>
      <li>
        IBM JDK 1.3.1/1.3.0/1.2.2 with the option <code>&lt;a href="http://www.tagtraum.com/gcviewer-vmflags.html#ibm.verbose">-verbose:gc&lt;/a></code>
      </li>
      <li>
        IBM iSeries Classic JVM 1.4.2 with <code>option -verbose:gc</code>
      </li>
      <li>
        HP-UX JDK 1.2/1.3/1.4.x with the option <code>&lt;a href="http://www.hp.com/products1/unix/java/infolibrary/prog_guide/hotspot.html#-Xverbosegc">-Xverbosegc&lt;/a></code>
      </li>
      <li>
        BEA JRockit 1.4.2/1.5 with the option <code>&lt;a href="http://edocs.bea.com/wljrockit/docs142/userguide/start.html#1015662">-verbose:memory&lt;/a></code>
      </li>
    </ul>
    
    <p>
      <code>截图:</code>
    </p>
    
    <p>
      <a href="http://www.tagtraum.com/gcviewer-screenshot.html"><img height="168" alt="GCViewer Small Screenshot - Click to enlarge!" src="http://www.tagtraum.com/images/gcviewer-screenshot-small.png" width="220" border="0" /></a>
    </p>
    
    <p>
      转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2011/08/03/gcviewer%e5%bc%80%e6%ba%90gc%e5%88%86%e6%9e%90%e5%b7%a5%e5%85%b7/">GCViewer,开源GC日志分析工具</a>
    </p>