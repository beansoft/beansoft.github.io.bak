---
id: 2254
title: '解决AppleSyncNotifier.exe &#8211; 无法找到入口的错误'
date: 2011-09-12T15:18:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2254
permalink: '/2011/09/12/%e8%a7%a3%e5%86%b3applesyncnotifier-exe-%e6%97%a0%e6%b3%95%e6%89%be%e5%88%b0%e5%85%a5%e5%8f%a3%e7%9a%84%e9%94%99%e8%af%af/'
views:
  - "9047"
original_post_id:
  - "2254"
categories:
  - iOS
---
最近一段时间，大概是因为安装了不同版本的itunes或者chrome，导致Windows登录后，显示一个错误对话框：

AppleSyncNotifier.exe &#8211; 无法找到入口   
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;   
无法定位程序输入点 sqlite3\_wal\_checkpoint 于动态链接库 SQLite3.dll 上。   
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;   
确定

然后 AppleSyncNotifier.exe 这个程序就提示非法退出了。

解决办法：

找到文件 c:\WINDOWS\system32\SQLite3.dll

其日期为：2010年10月26日 ，很显然文件相当老旧，很有可能是这个文件被某安装程序覆盖后导致API不够新造成的。于是到官方网站[http://www.sqlite.org/](http://www.sqlite.org/ "http://www.sqlite.org/")下载了最新版的SQLite3.dll [http://www.sqlite.org/sqlite-dll-win32-x86-3070701.zip](http://www.sqlite.org/sqlite-dll-win32-x86-3070701.zip "http://www.sqlite.org/sqlite-dll-win32-x86-3070701.zip")，然后覆盖，注销重登录后一切正常。

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [解决AppleSyncNotifier.exe &#8211; 无法找到入口的错误](http://www.beansoft.biz/2011/09/12/%e8%a7%a3%e5%86%b3applesyncnotifier-exe-%e6%97%a0%e6%b3%95%e6%89%be%e5%88%b0%e5%85%a5%e5%8f%a3%e7%9a%84%e9%94%99%e8%af%af/)