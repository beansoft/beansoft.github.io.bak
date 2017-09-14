---
id: 2066
title: 成功搭建OSB环境并运行HelloWorld项目（代码，视频）
date: 2011-07-17T21:43:18+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2066
permalink: '/2011/07/17/%e6%88%90%e5%8a%9f%e6%90%ad%e5%bb%baosb%e7%8e%af%e5%a2%83%e5%b9%b6%e8%bf%90%e8%a1%8chelloworld%e9%a1%b9%e7%9b%ae/'
views:
  - "16789"
original_post_id:
  - "2066"
categories:
  - SOA/WebService
tags:
  - OSB
  - SOA/WebService
  - Video
  - 视频
---
项目代码下载：[http://java.net/projects/oraclesoasuite11g/downloads/download/OSB/osb-101-helloworld.zip](http://java.net/projects/oraclesoasuite11g/downloads/download/OSB/osb-101-helloworld.zip "http://java.net/projects/oraclesoasuite11g/downloads/download/OSB/osb-101-helloworld.zip")

更多OSB学习资料，示例代码和视频参考：<http://java.net/projects/oraclesoasuite11g/pages/OSB>

本项目操作演示视频请移步至本文[末尾](#video)，拖放到后半段。

今天花了点时间, 研究了下OSB([Oracle Service Bus](http://www.oracle.com/technetwork/middleware/service-bus/overview/index.html))的入门. Service Bus是SOA中的一个重要的基础设施. 还好OSB 11gR1 (11.1.1.5.0)的安装相当的简单快速. 很快第一个HelloWorld的练习也做完了, 对Service Bus中Proxy的概念有了直接的体会. 和大多数SOA项目需要jDeveloper开发不同,OSB还是需要用OEPE+OSB插件来开发的.

这个HelloWorld的项目,只有一个wsdl定义和proxy, wsdl的定义最终通过proxy得到了实现, 而proxy可以部署到server上通过sbconsole来管理和动态修改, 我想这就是它的强大之处吧.

<img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="image" border="0" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2011/07/image2.png" width="382" height="371" />

<img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="image" border="0" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2011/07/image3.png" width="843" height="676" />

<img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="image" border="0" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2011/07/image4.png" width="981" height="733" />

<img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="image" border="0" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2011/07/image5.png" width="981" height="733" />

## <a name="video">操作及讲解视频：</a>

<div id="media">
</div>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [成功搭建OSB环境并运行HelloWorld项目（代码，视频）](http://www.beansoft.biz/2011/07/17/%e6%88%90%e5%8a%9f%e6%90%ad%e5%bb%baosb%e7%8e%af%e5%a2%83%e5%b9%b6%e8%bf%90%e8%a1%8chelloworld%e9%a1%b9%e7%9b%ae/)