---
id: 1403
title: 关于进程监视工具中的Private Bytes,Commit Size和Working Set
date: 2010-11-14T21:03:39+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1403
permalink: '/2010/11/14/%e5%85%b3%e4%ba%8e%e8%bf%9b%e7%a8%8b%e7%9b%91%e8%a7%86%e5%b7%a5%e5%85%b7%e4%b8%ad%e7%9a%84private-bytescommit-size%e5%92%8cworking-set/'
views:
  - "6168"
original_post_id:
  - "1403"
image: /wp-content/uploads/2012/09/image_thumb17.png
categories:
  - Windows
---
在Win7的进程管理器和资源监视器中, 有这么几列:

**Private** – Amount of physical memory in use by the process that cannot be used by other processes, 即不可共享的进程独占的**物理内存**数

**Commit** – Amount of virtual memory reserved by the operating system for the process, 即操作系统为进程所保留的**虚拟内存**, 也即旧版本Windows中的"虚拟内存", Virtual Size

**Working Set** &#8211; Amount of physical memory currently in use by the process , 即进程所占用的**物理内存**数

**Shareable** &#8211; Amount of physical memory in use by the process that can be shared with other processes, 即可共享的进程占用的**物理内存**数

&#160;

[<img style="background-image:none;border-bottom:0;border-left:0;padding-left:0;padding-right:0;display:inline;border-top:0;border-right:0;padding-top:0;" title="image" border="0" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2010/11/image_thumb.png" width="589" height="428" />](http://www.beansoft.biz/wp-content/uploads/2010/11/image.png)

[<img style="background-image:none;border-bottom:0;border-left:0;padding-left:0;padding-right:0;display:inline;border-top:0;border-right:0;padding-top:0;" title="image" border="0" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2010/11/image_thumb1.png" width="514" height="131" />](http://www.beansoft.biz/wp-content/uploads/2010/11/image1.png)

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [关于进程监视工具中的Private Bytes,Commit Size和Working Set](http://www.beansoft.biz/2010/11/14/%e5%85%b3%e4%ba%8e%e8%bf%9b%e7%a8%8b%e7%9b%91%e8%a7%86%e5%b7%a5%e5%85%b7%e4%b8%ad%e7%9a%84private-bytescommit-size%e5%92%8cworking-set/)