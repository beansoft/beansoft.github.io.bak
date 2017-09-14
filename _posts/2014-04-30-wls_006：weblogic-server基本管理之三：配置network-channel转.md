---
id: 3639
title: 'WLS_006：WebLogic Server基本管理之三：配置Network Channel[转]'
date: 2014-04-30T17:58:27+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3639
permalink: '/2014/04/30/wls_006%ef%bc%9aweblogic-server%e5%9f%ba%e6%9c%ac%e7%ae%a1%e7%90%86%e4%b9%8b%e4%b8%89%ef%bc%9a%e9%85%8d%e7%bd%aenetwork-channel%e8%bd%ac/'
views:
  - "3180"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
来源: [http://maping930883.blogspot.jp/2009/03/wls006weblogic-servernetwork-channel.html](http://maping930883.blogspot.jp/2009/03/wls006weblogic-servernetwork-channel.html "http://maping930883.blogspot.jp/2009/03/wls006weblogic-servernetwork-channel.html")

除了可以使用HTTP协议访问WebLogic Server以外，你还可以使用其它协议来访问。   
[domain\_name]->Environment-> Servers->[server\_name]->Protocols ->Channels   
[<img border="0" alt="" src="http://2.bp.blogspot.com/--zegvqXdiWY/TtiuCOkzBmI/AAAAAAAACO4/5Nv3neFxu_Q/s1600/1.GIF" />](http://2.bp.blogspot.com/--zegvqXdiWY/TtiuCOkzBmI/AAAAAAAACO4/5Nv3neFxu_Q/s1600/1.GIF)   
Network Channel可以使用在以下场景：   
**1. 一台机器上有多块网卡**   
我们可以让网卡1接收HTTP请求，而网卡2接收HTTPS请求。   
这样的设计让网卡的分工明确，在分流不同请求的同时，缓解了网卡的压力。

[<img border="0" alt="" src="http://4.bp.blogspot.com/-qLwAJDZqOKM/TtivgGvhSSI/AAAAAAAACPE/hc7BPsd55uI/s1600/2.GIF" />](http://4.bp.blogspot.com/-qLwAJDZqOKM/TtivgGvhSSI/AAAAAAAACPE/hc7BPsd55uI/s1600/2.GIF)

**2. 使用访问效率比较高的其它协议，比如T3协议**   
如果不是Web应用的话，可以考虑使用其它访问效率比较高的其它协议，比如T3协议。   
**3. 建立两个Server之间的专属Channel**   
用一台机器接收客户端请求，然后通过专属Channel，访问另一台机器上的Server端组件，比如EJB。   
这样的设计在保护Server端组件的同时，也在一定程度上提高了访问效率。   
[<img border="0" alt="" src="http://3.bp.blogspot.com/-4miWPHj281E/TtivgSMT1iI/AAAAAAAACPM/77GjW4B9-LQ/s1600/3.GIF" />](http://3.bp.blogspot.com/-4miWPHj281E/TtivgSMT1iI/AAAAAAAACPM/77GjW4B9-LQ/s1600/3.GIF)

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [WLS_006：WebLogic Server基本管理之三：配置Network Channel[转]](http://www.beansoft.biz/2014/04/30/wls_006%ef%bc%9aweblogic-server%e5%9f%ba%e6%9c%ac%e7%ae%a1%e7%90%86%e4%b9%8b%e4%b8%89%ef%bc%9a%e9%85%8d%e7%bd%aenetwork-channel%e8%bd%ac/)