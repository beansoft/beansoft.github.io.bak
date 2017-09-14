---
id: 1234
title: 'weblogic9 jdbc日志跟weblogic8的区别[转]'
date: 2010-09-22T18:13:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1234
permalink: '/2010/09/22/weblogic9-jdbc%e6%97%a5%e5%bf%97%e8%b7%9fweblogic8%e7%9a%84%e5%8c%ba%e5%88%ab%e8%bd%ac/'
views:
  - "10241"
original_post_id:
  - "1234"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
BeanSoft 备注: 此文内容适应于 WebLogic 9, 10, 11.

<span class="Apple-style-span" style="word-spacing:0;font:medium 微软雅黑;text-transform:none;color:rgb(0,0,0);text-indent:0;white-space:normal;letter-spacing:normal;border-collapse:separate;orphans:2;widows:2;"><span class="Apple-style-span" style="font-size:12px;color:rgb(85,85,85);line-height:17px;font-family:verdana, &#039;"> </p> 

<p style="margin:0 0 10px;padding:0;">
  <strong>转载此文请保留原作者信息及出处:<span class="Apple-converted-space">&#160;</span></strong><a style="color:rgb(41,112,166);text-decoration:none;" href="http://beansoft.biz/"><strong>http://www.tonyxu.net</strong></a>
</p>

<p style="margin:0 0 10px;padding:0;">
  在wls8.1我们很容易可以在console找到打开jdbc.log的开关，但是9版本呢，找了半天实在很难发现。其实隐藏在另外一个地方。如下图：
</p>

<p style="margin:0 0 10px;padding:0;">
  <a style="color:rgb(41,112,166);text-decoration:none;" href="http://www.tonyxu.net/wp-content/uploads/2010/09/051.jpg"><img title="截图05" style="display:inline;max-width:600px;border-width:0;" height="308" alt="截图05" src="http://www.tonyxu.net/wp-content/uploads/2010/09/05_thumb1.jpg" width="573" border="0" /></a>
</p>

<p style="margin:0 0 10px;padding:0;">
  &#160;
</p>

<p style="margin:0 0 10px;padding:0;">
  <a style="color:rgb(41,112,166);text-decoration:none;" href="http://www.tonyxu.net/wp-content/uploads/2010/09/061.jpg"><img title="截图06" style="display:inline;max-width:600px;border-width:0;" height="224" alt="截图06" src="http://www.tonyxu.net/wp-content/uploads/2010/09/06_thumb1.jpg" width="572" border="0" /></a>
</p>

<p style="margin:0 0 10px;padding:0;">
  具体的路径：
</p>

<p style="margin:0 0 10px;padding:0;">
  Admin Console 对 Servers -> yourServer -> Debug -> weblogic -> jdbc 下面的各项进行Enable来实现打开详细的日志。
</p>

<p style="margin:0 0 10px;padding:0;">
  应该说，weblogic9版本的这个JDBC日志跟weblogic8相比，在控制台上可调试的选项丰富多了，之前我发过一篇关于8版本的文章，地址为：
</p>

<p style="margin:0 0 10px;padding:0;">
  <a title="http://www.tonyxu.net/weblogic/201009295/weblogic8-1-jdbc-log-trace.html" style="color:rgb(41,112,166);text-decoration:none;" href="http://www.tonyxu.net/weblogic/201009295/weblogic8-1-jdbc-log-trace.html">http://www.tonyxu.net/weblogic/201009295/weblogic8-1-jdbc-log-trace.html</a>
</p>

<p>
  </span></span>
</p>

<p>
  转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2010/09/22/weblogic9-jdbc%e6%97%a5%e5%bf%97%e8%b7%9fweblogic8%e7%9a%84%e5%8c%ba%e5%88%ab%e8%bd%ac/">weblogic9 jdbc日志跟weblogic8的区别[转]</a>
</p>