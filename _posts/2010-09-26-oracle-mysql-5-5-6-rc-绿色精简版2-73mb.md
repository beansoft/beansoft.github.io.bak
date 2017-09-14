---
id: 1263
title: 'Oracle MySQL 5.5.6 RC 绿色精简版[2.73MB]'
date: 2010-09-26T12:26:09+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1263
permalink: '/2010/09/26/oracle-mysql-5-5-6-rc-%e7%bb%bf%e8%89%b2%e7%b2%be%e7%ae%80%e7%89%882-73mb/'
views:
  - "9366"
original_post_id:
  - "1263"
categories:
  - MySQL
tags:
  - 5.5.6
  - Green
  - MySQL
  - RC
---
### Oracle MySQL 5.5.6 RC 绿色精简版[2.73MB]

By <http://www.beansoft.biz/> 2010-09-26 Email: <wlsmon@qq.com>

软件许可: GPL , 参考 COPYING 和 README.

下载地址: [http://cid-519b3f7aa2172030.office.live.com/self.aspx/Public/%E6%95%B0%E6%8D%AE%E5%BA%93/mysql%5E\_5.5.6%5E\_rc%5E_green.7z](http://cid-519b3f7aa2172030.office.live.com/self.aspx/Public/%E6%95%B0%E6%8D%AE%E5%BA%93/mysql%5E_5.5.6%5E_rc%5E_green.7z) 2.73MB

Oracle MySQL 5.5.6 RC 是Oracle收购MySQL后, 进行了大幅度优化后的产品, 相关新闻可Google.

为了做一套开源的 MySQL 5 绿色精简版, 完全控制启动停止, 我把 Mysql 绿色版用BAT文件重新包装了一遍, 并更新到性能大幅度提升后的 MySQL 5.5.6 RC版(性能提升参见: <http://www.beansoft.biz/?p=1262> MySQL 产品战略和RoadMap 发布视频  ).
  
使用: 下载后解压缩到磁盘上的任意目录, 可以看到多出了一个 **_mysql\_5.5.6\_rc_green_** 的目录. 打开这个目录, 有以下的几个文件:

<table border="1" width="100%">
  <tr>
    <td width="50%">
      <strong>文件</strong>
    </td>
    
    <td width="50%">
      <strong>说明</strong>
    </td>
  </tr>
  
  <tr>
    <td width="50%">
      [bin]
    </td>
    
    <td width="50%">
      MySQL 的二进制文件
    </td>
  </tr>
  
  <tr>
    <td width="50%">
      [data]
    </td>
    
    <td width="50%">
      MySQL 数据库文件
    </td>
  </tr>
  
  <tr>
    <td width="50%">
      [data_empty]
    </td>
    
    <td width="50%">
      空的数据库文件备份, 可用来复制到data目录覆盖后重置数据库.
    </td>
  </tr>
  
  <tr>
    <td width="50%">
      [share]
    </td>
    
    <td width="50%">
      MySQL 英文资源文件
    </td>
  </tr>
  
  <tr>
    <td width="50%">
      [lib]
    </td>
    
    <td width="50%">
      InnoDB等库文件
    </td>
  </tr>
  
  <tr>
    <td width="50%">
      erase_log.bat
    </td>
    
    <td width="50%">
      清空日志
    </td>
  </tr>
  
  <tr>
    <td width="50%">
      mysql_start.bat
    </td>
    
    <td width="50%">
      启动 MySQL, 双击后如果没有错误的话可以在系统进程中看到 mysqld.exe, 并且可以通过 mysql 管理工具连接上, 端口 3306, 用户名 root, 密码为空
    </td>
  </tr>
  
  <tr>
    <td width="50%">
      mysql_stop.bat
    </td>
    
    <td width="50%">
      停止 MySQL
    </td>
  </tr>
  
  <tr>
    <td width="50%">
      mysql绿色版.htm
    </td>
    
    <td width="50%">
      介绍文件
    </td>
  </tr>
  
  <tr>
    <td width="50%">
      tail.exe
    </td>
    
    <td width="50%">
      Windows 版的tail
    </td>
  </tr>
  
  <tr>
    <td width="50%">
      view_log.bat
    </td>
    
    <td width="50%">
      跟踪查看 MySQL 的工作日志
    </td>
  </tr>
</table>

原理: 首先只保留了 MySQL 的最少运行文件来减少所占用的空间. 当然如果你愿意的话留下所有的 Mysql 5 文件也没有问题. 然后根据 mysqladmin.exe 和 mysqld.exe 的命令行参数进行工作. mysqld.exe &#8211;verbose &#8211;help 可以看到所有能够使用的参数.

推荐配套非商业免费客户端: Navicat <http://www.navicat.com/cn/download/download.html>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Oracle MySQL 5.5.6 RC 绿色精简版[2.73MB]](http://www.beansoft.biz/2010/09/26/oracle-mysql-5-5-6-rc-%e7%bb%bf%e8%89%b2%e7%b2%be%e7%ae%80%e7%89%882-73mb/)