---
id: 234
title: BeanSoft MySQL Java 开发套装(服务器,管理工具,JDBC驱动,示例代码) 无中文问题
date: 2007-07-14T17:03:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=234
permalink: '/2007/07/14/beansoft-mysql-java-%e5%bc%80%e5%8f%91%e5%a5%97%e8%a3%85%e6%9c%8d%e5%8a%a1%e5%99%a8%e7%ae%a1%e7%90%86%e5%b7%a5%e5%85%b7jdbc%e9%a9%b1%e5%8a%a8%e7%a4%ba%e4%be%8b%e4%bb%a3%e7%a0%81-%e6%97%a0/'
views:
  - "9173"
original_post_id:
  - "234"
image: /wp-content/uploads/2012/09/image6.png
categories:
  - MySQL
---
BeanSoft MySQL Java 开发套装(服务器,管理工具,JDBC驱动,示例代码)

小更新: 为了减轻负担, 用 MySQL-Front 2.5 来管理, 这个软件无中文问题. 如果以后开源版本HeidiSQL的解决了中文问题, 就用开源的.

下载:

[MySQL Java 开发套装.7z](https://skydrive.live.com/redir.aspx?cid=519b3f7aa2172030&resid=519B3F7AA2172030!1458&parid=519B3F7AA2172030!890) 4.02MB (7z压缩包)

参考文档: [MySQL 5 绿色版(BAT版本)](http://www.beansoft.biz/?p=229)   
2007-10-01   
版权所有 2007 刘长炯(BeanSoft@126.com)   
Blog: <http://www.beansoft.biz/>   
本软件套装采用的协议: GPL, 参考 gpl.txt   
Java 初学者最头疼的, 莫过于安装数据库, 寻找数据库管理工具, 寻找 JDBC 驱动, 然后编写代码来测试, 然后遇到了乱码问题, 头大的要命, 不知道如何解决.

在此, 我搜集了几个开源软件, 组合到一起, 来方便大家的数据库开发. 数据库我选择 MySQL 5.0.41 绿色版(本站开发), 管理工具我选择 MySQL-Front 2.5 免费软件(这个版本可以正确显示中文), 然后选择了 MySQL JDBC 驱动, 并编写了测试代码, 这些代码解决了中文问题, 最后使用免费的 PStart 2.11 制作了启动工具.

用法: 下载后解压缩到硬盘的任意位置, 然后双击 PStart.exe 开始, 先启动 MySQL 服务器, 然后即可编译运行 JDBC 测试代码.

注意事项: 这个版本的 MySQL 绿色版默认采用的字符集是 GBK, 如果你修改成了别的字符集, MySQLFront 将显示为乱码.

感谢以下软件:

MySQL <http://www.mysql.com/> GPL 协议   
MySQL Front 2.5 <http://www.mysqlfront.de/> FreeWare   
MySQL 绿色版 BeanSoft@126.com GPL 协议   
MySQL ConnectorJ(即 JDBC 驱动) <http://dev.mysql.com/downloads/connector/j/> GPL 协议   
MySQL JDBC 示例代码 BeanSoft@126.com GPL 协议   
PStart <http://www.pegtop.net/start/> FreeWare

截图:

<img src="http://www.beansoft.biz/wp-content/uploads/2010/07/image6.png" style="BORDER-RIGHT-WIDTH: 0px; BORDER-TOP-WIDTH: 0px; BORDER-BOTTOM-WIDTH: 0px; BORDER-LEFT-WIDTH: 0px" height="429" width="526" alt="image" border="0" />

主界面, 双击 mysql_start 启动 MySQL 服务器

<img src="http://www.beansoft.biz/wp-content/uploads/2010/07/image7.png" style="BORDER-RIGHT-WIDTH: 0px; BORDER-TOP-WIDTH: 0px; BORDER-BOTTOM-WIDTH: 0px; BORDER-LEFT-WIDTH: 0px" height="444" width="602" alt="image" border="0" />

内置开源 MySQL 管理工具, 双击主界面的 &#8220;MySQL-Front&#8221; 启动

<img src="http://www.beansoft.biz/wp-content/uploads/2010/07/portable_mysql_jdbc.png" style="BORDER-RIGHT-WIDTH: 0px; BORDER-TOP-WIDTH: 0px; BORDER-BOTTOM-WIDTH: 0px; BORDER-LEFT-WIDTH: 0px" height="514" width="569" alt="portable_mysql_jdbc" border="0" />

双击主界面 &#8220;运行JDBC&#8221; 进行插入和读取数据测试, 开箱即用, 无需配置.

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [BeanSoft MySQL Java 开发套装(服务器,管理工具,JDBC驱动,示例代码) 无中文问题](http://www.beansoft.biz/2007/07/14/beansoft-mysql-java-%e5%bc%80%e5%8f%91%e5%a5%97%e8%a3%85%e6%9c%8d%e5%8a%a1%e5%99%a8%e7%ae%a1%e7%90%86%e5%b7%a5%e5%85%b7jdbc%e9%a9%b1%e5%8a%a8%e7%a4%ba%e4%be%8b%e4%bb%a3%e7%a0%81-%e6%97%a0/)