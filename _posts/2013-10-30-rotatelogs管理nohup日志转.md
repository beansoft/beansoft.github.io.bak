---
id: 3448
title: 'rotatelogs管理nohup日志[转]'
date: 2013-10-30T20:45:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3448
permalink: '/2013/10/30/rotatelogs%e7%ae%a1%e7%90%86nohup%e6%97%a5%e5%bf%97%e8%bd%ac/'
views:
  - "5194"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - nohup
  - rotatelogs
  - WebLogic
---
来源: [Wei&#8217;Logic](http://weixd.net/)

用nohup启动weblogic日志会无限增长，除非重启或清空。

可以采用一些脚本来帮助管理。

Oracle Support里有一篇WLS 8.1 SP1 – How can I rotate, by size, the nohup.out file? [ID 774807.1]。   
是在后台运行如下脚本来进行的，只能按大小滚动：

<pre>&#160;</pre>

<pre>#!/bin/bash</pre>

<pre>counter=1</pre>

<pre>file=nohup.out</pre>

<pre>while [ "$counter" != "0" ]</pre>

<pre>do</pre>

<pre>size=`ls -la nohup.out | awk '{print $5}'`</pre>

<pre>if [ $size -gt $1 ]</pre>

<pre>then</pre>

<pre>date=`date +%m%d%y-%H%M%S`</pre>

<pre>cp "$file" logs/"$file.$date"</pre>

<pre>cat /dev/null &gt; "$file"</pre>

<pre>fi</pre>

<pre>done</pre>

用rotatelogs管理nohup日志。使用Apche下自带的rotatelogs，可以按大小和时间来滚动。
    
  
rotatelogs有如下两个注意的特点，

1.如果日志文件名中不包含”%”，它会被自动加上以秒为单位的”.nnnnnnnnnn”后缀。如果包括”%”，则它会被视为用于strftime()的格式字符串，这两种格式都表示新的日志开始使用的时间。

2.直接使用rotatelogs取时间，其默认基准时间是GMT。如果在中国，一般时区都设置为+8。加参数-l可以使用本地时间代替GMT时间作为时间基准。

以下是我使用rotatelogs的范例，为了让tail获取日志文件句柄，我采用的策略是是查找目录中最新的日志文件。

<pre>&#160;</pre>

<pre>#!/bin/sh</pre>

<pre>OUT_LOG_PATH=/home/wei/bea/user_projects/domains/TestDomain.logs</pre>

<pre>nohup ./startWebLogic.sh | ./bin/rotatelogs $OUT_LOG_PATH/AdminServer-%Y-%m-%d-%H-%M.out 50M &</pre>

<pre>sleep 2 #似乎不停顿个一两秒，日志文件还不会生成</pre>

<pre>OUT_LOG_FILE=`ls -1t $OUT_LOG_PATH/AdminServer*.out|head -1` #查找目录中最新的AdminServer的.out日志文件</pre>

<pre>tail -f $OUT_LOG_FILE</pre>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [rotatelogs管理nohup日志[转]](http://www.beansoft.biz/2013/10/30/rotatelogs%e7%ae%a1%e7%90%86nohup%e6%97%a5%e5%bf%97%e8%bd%ac/)