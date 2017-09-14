---
id: 3906
title: 今天大批iOS应用因使用热补丁技术被拒, 会影响React Native吗?不会!
date: 2017-03-08T13:38:20+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3906
permalink: '/2017/03/08/%e4%bb%8a%e5%a4%a9%e5%a4%a7%e6%89%b9ios%e5%ba%94%e7%94%a8%e5%9b%a0%e4%bd%bf%e7%94%a8%e7%83%ad%e8%a1%a5%e4%b8%81%e6%8a%80%e6%9c%af%e8%a2%ab%e6%8b%92-%e4%bc%9a%e5%bd%b1%e5%93%8dreact-native%e5%90%97/'
views:
  - "1571"
categories:
  - Uncategorized
---
</p> 

<div>
  传的沸沸扬扬的iOS App因为用了在线热补丁技术而被苹果商店拒的事情会不会影响React Native呢? 答案是: 否. 甚至在线热更新RN也不受影响. &nbsp; 参考: &nbsp;https://github.com/facebook/react-native/issues/12778 摘要:&nbsp;
</div>

<div>
  苹果开发者协议3.3.2节:
</div>

<div>
</div>

<div>
  一个应用程序不应该下载或安装任何可执行代码。解释执行的代码可以在应用内使用，如果所有的脚本、代码、和解释器都被打包在应用内而没有被下载。前述内容的唯一的例外在于下载的脚本和代码使用了Apple内置的WebKit框架或JavascriptCore，并且对应的脚本或代码并没有改变这个应用提供功能和特性的主要目的，与提交到AppStore的版本以及相应的宣传描述相符。
</div>

<div>
</div>

<div>
  其中重要的地方：
</div>

<div>
</div>

<div>
  一个应用程序不应该下载或安装任何可执行代码
</div>

<div>
  React Native没有做这件事情。所以React Native不会让你受前述条款的影响。
</div>

<div>
</div>

<div>
  另一方面，使用React Native，你还可能会使用叫做OTA更新的方式（俗称热更新），类似Code Push或中文网提供此热更新服务。这同样是被3.3.2章节的后续内容允许的：
</div>

<div>
</div>

<div>
  前述内容的唯一的例外在于下载的脚本和代码使用了Apple内置的WebKit框架或JavascriptCore
</div>

<div>
</div>

<div>
  所以这事情和React Native并无关系。我觉得收到邮件的人应该关注和苹果的交流，再次检查是什么导致了这个警告。
</div>

<div>
</div>

</body></html>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [今天大批iOS应用因使用热补丁技术被拒, 会影响React Native吗?不会!](http://www.beansoft.biz/2017/03/08/%e4%bb%8a%e5%a4%a9%e5%a4%a7%e6%89%b9ios%e5%ba%94%e7%94%a8%e5%9b%a0%e4%bd%bf%e7%94%a8%e7%83%ad%e8%a1%a5%e4%b8%81%e6%8a%80%e6%9c%af%e8%a2%ab%e6%8b%92-%e4%bc%9a%e5%bd%b1%e5%93%8dreact-native%e5%90%97/)