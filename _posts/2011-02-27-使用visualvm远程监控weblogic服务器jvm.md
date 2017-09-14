---
id: 1809
title: 使用VisualVM远程监控WebLogic服务器JVM
date: 2011-02-27T22:20:18+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1809
permalink: '/2011/02/27/%e4%bd%bf%e7%94%a8visualvm%e8%bf%9c%e7%a8%8b%e7%9b%91%e6%8e%a7weblogic%e6%9c%8d%e5%8a%a1%e5%99%a8jvm/'
views:
  - "14457"
original_post_id:
  - "1809"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - VisualVM
  - WebLogic
---
作者: <BeanSoft@126.com> 网站: <http://www.beansoft.biz/> 日期: 2011-02-27

JDK 自带了一个很cool的工具: [**jvisualvm**](http://download.oracle.com/javase/6/docs/technotes/tools/share/jvisualvm.html). 今天笔者就简单探讨一下如何使用VisualVM来监控远程服务器上的WebLogic服务器. 本文主要研究在如何不设置密码的情况下进行监控, 此步骤无须特殊设置, 非常适用于局域网的情况, 但是也最不安全, 因此切不可用于生产机环境下.

本文环境:

<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td valign="top" width="142">
      <strong>服务器OS</strong>
    </td>
    
    <td valign="top" width="142">
      Windows XP
    </td>
    
    <td valign="top" width="142">
      <strong>客户端OS</strong>
    </td>
    
    <td valign="top" width="142">
      Oracle Linux 5
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="142">
      <strong>JDK</strong><strong>版本</strong>
    </td>
    
    <td valign="top" width="142">
      JDK 1.6
    </td>
    
    <td valign="top" width="142">
      <strong>WebLogic</strong><strong>版本</strong>
    </td>
    
    <td valign="top" width="142">
      WebLogic 10.3.4
    </td>
  </tr>
</table>

#### 实验1: 远程监控普通Java应用的运行

&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;..

下载本文(右键另存为): http://www.beansoft.biz/wp-content/uploads/2011/03/visualvm_wls.swf 238KB

提示: 点击最右上角的 **回** 按钮全屏阅读

<div style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; float: none; padding-top: 0px" id="scid:8C92A505-C66E-4dd0-A7AF-2692874158CA:d2f286c8-e7f8-4e01-b205-bfc7e34a5ccb" class="wlWriterEditableSmartContent">
  <p>
    <EMBED src="http://www.beansoft.biz/wp-content/uploads/2011/03/visualvm_wls.swf" quality="High" bgcolor="#FFFF00" width="100%" height="600" name="My Flash Object" align="Middle" type="application/x-shockwave-flash" pluginspace="http://www.macromedia.com/go/getflashplayer" />
  </p>
</div>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [使用VisualVM远程监控WebLogic服务器JVM](http://www.beansoft.biz/2011/02/27/%e4%bd%bf%e7%94%a8visualvm%e8%bf%9c%e7%a8%8b%e7%9b%91%e6%8e%a7weblogic%e6%9c%8d%e5%8a%a1%e5%99%a8jvm/)