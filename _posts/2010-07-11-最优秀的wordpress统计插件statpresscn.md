---
id: 196
title: wordpress统计插件statpressCN
date: 2010-07-11T21:30:36+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=196
permalink: '/2010/07/11/%e6%9c%80%e4%bc%98%e7%a7%80%e7%9a%84wordpress%e7%bb%9f%e8%ae%a1%e6%8f%92%e4%bb%b6statpresscn/'
views:
  - "6218"
original_post_id:
  - "196"
categories:
  - OpenSource
---
注: 本人也正在试用此插件, 目前已经看到了初步的信息, 应该还不错, 包含中文语言包. 插件官方网站: [http://wordpress.org/extend/plugins/statpresscn/](http://wordpress.org/extend/plugins/statpresscn/ "http://wordpress.org/extend/plugins/statpresscn/")&#160; 中文网站: [http://heart5.com/?page_id=738](http://heart5.com/?page_id=738 "http://heart5.com/?page_id=738")

来源: [http://www.epavel.cn/archives/79](http://www.epavel.cn/archives/79 "http://www.epavel.cn/archives/79")&#160;

&#160;

一般而言用wordpress建立自己的网站后，首先确定的是自己的主题，然后是装插件了，统计插件的安装是必不可少的，Pavel这次推荐一款自用的感觉很不错的统计插件，statpress，这款插件是在wp后台进行统计的，数据值只能博主本人能看见。

首先下载该插件（见本文下方链接）

然后上传到空间plugin目录下，进入wp后台管理界面，激活插件，这时候你会看到和“撰写 管理 设计 ……”等选项平行的一栏多了stapress选项，选择进入后就可以看到最新的统计信息了！

这款插件不仅可以统计当日当月最近几月的浏览情况，还可以统计浏览者的Ip地址、操作系统、浏览器版本、访问方式等信息，更好的一方面是你可以在这里看到百度、google等蜘蛛来过的痕迹，来的次数越多被收录的可能性越大哦~~

好了，总之这款插件易用好懂，统计数据也相对准确（毕竟是机器统计，难免和实际值有些出入，可忽略不计），推荐大家使用~~

使用过程中若有不明白欢迎给我留言，大家一起讨论！

英文[点击下载](http://wordpress.org/extend/plugins/statpress/) 这里还有中文版本——[点击下载](http://wordpress.org/extend/plugins/statpresscn/)

&#160;

来自中文网站的说明:

&#160;

FAQ

### Q：这个blog访问统计插件相比其他类似产品和服务有什么特色？

A：StatPressCN是专为基于wordpress的blog开发的访问统计工具，有如下特色：

  1. 专门面向blog，更专业。和通用类访问统计服务如站长统计cnzz、Google Analytics以及雅虎统计相比，StatPressCN拥有很多针对blog的专有功能，前台的有最热博文（可以在widget中设定时段）、博文热度（用小太阳显性表达）、相关文章、当前访问（在选项中使能后就可以在blog的widget中显示动态的来访者信息），后台的有朋友来访（跟踪朋友们的访问情况并综合显示）、最近的被访问页面、最近的来访关键词（专指搜索引擎）、最近的页面参考（从哪里连接过来的），以及blog被访问的总体情况等等。
  2. 扩展性和定制性强。可以手动添加爬虫规则、搜索引擎规则、电脑操作系统定义规则、浏览器规则，这样就不用等StatPressCN主程序更新就可以识别最新的浏览器等（当然了，me会尽量及时更新的），再就是还可以给一些固定ip的朋友命名，免得他们来了你又不晓得。
  3. 针对中文用户优化。可以正确识别中文的搜索关键词（这也是me基于StatPress开发StatPressCN的直接原因），可以正确识别包含中文字符的固定连接地址，还可以设定中文的ip来源地查询服务（现在me用的是有道的，还不错，推荐）。
  4. 专人维护，更新及时。StatPressCN是me工作之余的主要乐趣所在，不会轻言放弃的，并且工作压力越大就越需要放松，也就意味着StatPressCN会得到更好的照顾。

### Q：安装StatPressCN很复杂吗？需要掌握编程知识吗？

A：完全不需要。StatPressCN是标准的插件，安装时不需要做其他手动调整等复杂操作。您只要已经架设好了基于wordpress程序的 blog，那应该可以很方便的安装并使用StatPressCN。更何况wordpress现在对插件安装和主题安装分别在2.7和2.8版本中作了很大变化，可以直接点两下就安装好了。

### Q：StatPressCN用起来方便吗？

A：应该是很方便。安装后启用StatPressCN，应该马上就可以看到访问情况了。如果您对来访情况向了解更多，还可以在选项菜单中做很多个性化的设定。但默认情况下是不需要做任何设定就可以很好的使用了的。

### Q：StatPressCN的数据库已经有二十多兆了，我该咋办？

A：因为StatPressCN会详细记录每个来访者的每次来访信息，所以数据库会随着时间增长，越来越大。数据库只要不是太大（比如超过50 兆），一般不会对blog速度有影响，但因为部分朋友的服务器对数据库大小是限制的，所以StatPressCN也提供了对数据大小进行限制的方式，那就是在选项中自己选择统计的时限，可以选择一周、两周、一个月、半年、一年之类的，这样之前的数据就会自动删除。

### Q：搜索关键词显示为问号（？），怎么办？

A：请检查“支持”信息中的mysql character\_set内容。这个问题的关键原因是mysql数据库字符集的设定混乱导致的。可以联系拥有后台数据库管理权限的同学把 character\_set\_client、character\_set\_connection、character\_set\_results和 collation\_connection都调整为table character set的默认设定。下面是我在测试环境下的设定示例：

> **table character set: DEFAULT CHARSET=latin1   
>** search column character set: search:text:latin1\_swedish\_ci:YES::   
> <span style="color:rgb(0,0,255);">character_set_client:latin1</span>   
> <span style="color:rgb(0,0,255);">character_set_connection:latin1</span>   
> character\_set\_database:latin1   
> character\_set\_filesystem:binary   
> <span style="color:rgb(0,0,255);">character_set_results:latin1</span>   
> character\_set\_server:latin1   
> character\_set\_system:utf8   
> character\_sets\_dir:D:toolsprogramxamppmysqlsharecharsets   
> <span style="color:rgb(0,0,255);">collation_connection:latin1_swedish_ci</span>   
> collation\_database:latin1\_swedish_ci   
> collation\_server:latin1\_swedish_ci

<span style="color:rgb(255,0,0);"><strong>另外</strong></span>，仲照宇用<a href="http://www.zjoyo.com/?p=1899" target="_blank">调整数据表中字段字符集的方式</a>解决了问题，碰到乱码的同学可以去看看。

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [wordpress统计插件statpressCN](http://www.beansoft.biz/2010/07/11/%e6%9c%80%e4%bc%98%e7%a7%80%e7%9a%84wordpress%e7%bb%9f%e8%ae%a1%e6%8f%92%e4%bb%b6statpresscn/)