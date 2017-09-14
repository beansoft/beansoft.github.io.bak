---
id: 606
title: 'shell内建命令exec[转]'
date: 2010-08-22T22:10:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=606
permalink: '/2010/08/22/shell%e5%86%85%e5%bb%ba%e5%91%bd%e4%bb%a4exec%e8%bd%ac/'
views:
  - "3339"
original_post_id:
  - "606"
categories:
  - Linux/Unix
tags:
  - Shell
  - Unix
---
来源: [http://blog.chinaunix.net/u2/72383/showart_1077024.html](http://blog.chinaunix.net/u2/72383/showart_1077024.html "http://blog.chinaunix.net/u2/72383/showart_1077024.html")

shell内建命令exec

&#160;&#160;&#160; shell的内建命令exec很有意思，它将并不启动新的shell，而是用要被执行命令替换当前的shell进程，并且将老进程的环境清理掉，而且 exec命令后的其它命令将不再执行。因此，如果你在一个shell里面，执行exec ls那么，当列出了当前目录后，这个shell就自己退出了，因为这个shell进程已被替换为仅仅执行ls命令的一个进程，执行结束自然也就退出了。为了避免这个影响我们的使用，一般将exec命令放到一个shell脚本里面，用主脚本调用这个脚本，调用点处可以用bash a.sh，（a.sh就是存放该命令的脚本），这样会为a.sh建立一个sub shell去执行，当执行到exec后，该子脚本进程就被替换成了相应的exec的命令。   
&#160;&#160;&#160; source命令或者"."，不会为脚本新建shell，而只是将脚本包含的命令在当前shell执行。

&#160;&#160;&#160; 不过，有例外哦，当exec命令来对文件描述符操作的时候，就不会替换shell，而且操作完成后，还会继续执行接下来的命令。

&#160;&#160;&#160; exec 3<&0

&#160;&#160;&#160; 这个命令就是将操作符3也指向标准输入。

&#160;

读后感: 如果shell中有cd命令, 又要执行后生效, 则应该用下列方式调用:

. /somepath/xxx.sh

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [shell内建命令exec[转]](http://www.beansoft.biz/2010/08/22/shell%e5%86%85%e5%bb%ba%e5%91%bd%e4%bb%a4exec%e8%bd%ac/)