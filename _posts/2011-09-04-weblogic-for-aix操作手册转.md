---
id: 2245
title: 'AIX下WebLogic安装操作手册[转]'
date: 2011-09-04T11:00:50+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2245
permalink: '/2011/09/04/weblogic-for-aix%e6%93%8d%e4%bd%9c%e6%89%8b%e5%86%8c%e8%bd%ac/'
views:
  - "4645"
original_post_id:
  - "2245"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - AIX
  - Install
  - WebLogic 9
---
原作者: 未知

&#160;

### 1.操作环境：

<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td width="168">
      <p>
        操作系统
      </p>
    </td>
    
    <td width="350">
      <p>
        AIX 5L
      </p>
    </td>
  </tr>
  
  <tr>
    <td width="168">
      <p>
        服务器程序
      </p>
    </td>
    
    <td width="350">
      <p>
        Weblogic924
      </p>
    </td>
  </tr>
  
  <tr>
    <td width="168">
      <p>
        数据库程序
      </p>
    </td>
    
    <td width="350">
      <p>
        Oracle 9i
      </p>
    </td>
  </tr>
</table>

### 2. WebLogic9.2 FOR AIX 5L安装：

#### 2.1安装JDK

1、在tmp目录下创建jdk目录，命令：

#mkdir jdk(此文件名可自己定义的)

&#160;

2、确认是否成功，输入命令ls

&#160;

3、通过FTP工具，将安装包Java5_64.sdk传输到JDK目录下

5、安装路径的选择，输入/tmp/jdk

&#160;

6、

&#160;

7、用鼠标单击，选中，再点击OK，

&#160;

8、将ACCEPT new license agreements值改为yes;

&#160;

下载全文: </wp-content/uploads/2011/09/wlsaix.swf> 1.70MB

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [AIX下WebLogic安装操作手册[转]](http://www.beansoft.biz/2011/09/04/weblogic-for-aix%e6%93%8d%e4%bd%9c%e6%89%8b%e5%86%8c%e8%bd%ac/)