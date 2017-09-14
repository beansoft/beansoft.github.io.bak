---
id: 1614
title: 修改Oracle XE HTTP 监听程序端口
date: 2011-01-19T12:34:51+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1614
permalink: '/2011/01/19/%e4%bf%ae%e6%94%b9oracle-xe-http-%e7%9b%91%e5%90%ac%e7%a8%8b%e5%ba%8f%e7%ab%af%e5%8f%a3/'
views:
  - "6086"
original_post_id:
  - "1614"
categories:
  - Oracle
---
</p> 

<div id="codeSnippetWrapper">
  Oracle XE默认端口为8080, 如果需要修改为其它端口, 需要执行下列SQL:
</div>

<div>
  &#160;
</div>

<span class="Apple-style-span" style="word-spacing:0;font:medium simsun;text-transform:none;color:rgb(0,0,0);text-indent:0;white-space:normal;letter-spacing:normal;border-collapse:separate;orphans:2;widows:2;"><span class="Apple-style-span" style="font-size:14px;color:rgb(102,102,102);line-height:21px;border-collapse:collapse;"><span style="line-height:1.5em important;"><font size="2"><span class="keyword" style="line-height:1.5em important;"><strong><font color="#993366">begin</font></strong></span><span style="line-height:1.5em important;">&#160;&#160;&#160;&#160; </span></font></span> </p> 

<p style="line-height:21px;margin:0 0 10px;padding:0;">
  <font size="2"><span style="line-height:1.5em important;">&#160;&#160; <strong><font color="#333399">dbms_xdb</font></strong>.sethttpport(</span><span class="string" style="line-height:1.5em important;"><font color="#3366ff">&#8216;8088&#8217;</font></span><span style="line-height:1.5em important;">);&#160;&#160;&#160;&#160; </span></font>
</p>

<p style="line-height:21px;margin:0 0 10px;padding:0;">
  <span style="line-height:1.5em important;"></span><font size="2"><span class="keyword" style="line-height:1.5em important;"><strong><font color="#993366">end</font></strong></span><span style="line-height:1.5em important;">;&#160; </span></font>
</p>

<p style="line-height:21px;margin:0 0 10px;padding:0;">
  <font color="#333399" size="2"><span style="line-height:1.5em important;">/</span></font><span style="line-height:1.5em important;"><font size="2">&#160;&#160; </font></span>
</p>

<p>
  </span></span>
</p>

<div>
  之后即可通过 <a title="http://127.0.0.1:8088/apex" href="http://127.0.0.1:8088/apex">http://127.0.0.1:8088/apex</a> 访问数据库主页.
</div>

<p>
  转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2011/01/19/%e4%bf%ae%e6%94%b9oracle-xe-http-%e7%9b%91%e5%90%ac%e7%a8%8b%e5%ba%8f%e7%ab%af%e5%8f%a3/">修改Oracle XE HTTP 监听程序端口</a>
</p>