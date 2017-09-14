---
id: 3789
title: Android中selector的匹配规律是从上到下
date: 2015-11-21T14:01:44+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3789
permalink: '/2015/11/21/android%e4%b8%adselector%e7%9a%84%e5%8c%b9%e9%85%8d%e8%a7%84%e5%be%8b%e6%98%af%e4%bb%8e%e4%b8%8a%e5%88%b0%e4%b8%8b/'
views:
  - "1285"
categories:
  - Android
tags:
  - Android
  - Selector
---
如代码:

<pre style="background-color: #2b2b2b; color: #a9b7c6; font-family: 'Microsoft YaHei'; font-size: 14.0pt;"><span style="color: #e8bf6a;">&lt;selector </span><span style="color: #bababa;">xmlns:</span><span style="color: #9876aa;">android</span><span style="color: #bababa;">=</span><span style="color: #a5c261;">"http://schemas.android.com/apk/res/android"</span><span style="color: #e8bf6a;">&gt;<br /></span><span style="color: #e8bf6a;"> &lt;item </span><span style="color: #9876aa;">android</span><span style="color: #bababa;">:state_checked=</span><span style="color: #a5c261;">"true" </span><span style="color: #9876aa;">android</span><span style="color: #bababa;">:color=</span><span style="color: #a5c261;">"#000" </span><span style="color: #e8bf6a;">/&gt;<br /></span><span style="color: #e8bf6a;"> &lt;item </span><span style="color: #9876aa;">android</span><span style="color: #bababa;">:state_pressed=</span><span style="color: #a5c261;">"true" </span><span style="color: #9876aa;">android</span><span style="color: #bababa;">:color=</span><span style="color: #a5c261;">"#000"</span><span style="color: #e8bf6a;">/&gt;<br /></span><span style="color: #e8bf6a;"> &lt;item </span><span style="color: #9876aa;">android</span><span style="color: #bababa;">:state_selected=</span><span style="color: #a5c261;">"true" </span><span style="color: #9876aa;">android</span><span style="color: #bababa;">:color=</span><span style="color: #a5c261;">"#000"</span><span style="color: #e8bf6a;">/&gt;<br /></span><span style="color: #e8bf6a;"> &lt;item </span><span style="color: #9876aa;">android</span><span style="color: #bababa;">:state_activated=</span><span style="color: #a5c261;">"true" </span><span style="color: #9876aa;">android</span><span style="color: #bababa;">:color=</span><span style="color: #a5c261;">"#000"</span><span style="color: #e8bf6a;">/&gt;<br /></span><span style="color: #e8bf6a;"> &lt;item </span><span style="color: #9876aa;">android</span><span style="color: #bababa;">:color=</span><span style="color: #a5c261;">"#F3F3F3" </span><span style="color: #e8bf6a;">/&gt;<br /></span><span style="color: #e8bf6a;">&lt;/selector&gt;</span></pre>

运行时的匹配顺序, 是从上到下.

如果把导数第二行挪到最上面, 那么所有的下部匹配规则都不会生效.

<pre style="background-color: #2b2b2b; color: #a9b7c6; font-family: 'Microsoft YaHei'; font-size: 14pt;"><span style="color: #e8bf6a;">&lt;item </span><span style="color: #9876aa;">android</span><span style="color: #bababa;">:color=</span><span style="color: #a5c261;">"#F3F3F3" </span><span style="color: #e8bf6a;">/&gt;</span></pre>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Android中selector的匹配规律是从上到下](http://www.beansoft.biz/2015/11/21/android%e4%b8%adselector%e7%9a%84%e5%8c%b9%e9%85%8d%e8%a7%84%e5%be%8b%e6%98%af%e4%bb%8e%e4%b8%8a%e5%88%b0%e4%b8%8b/)