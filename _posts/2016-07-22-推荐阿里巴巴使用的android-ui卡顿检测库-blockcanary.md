---
id: 3822
title: '推荐阿里巴巴使用的Android UI卡顿检测库: BlockCanary'
date: 2016-07-22T03:17:43+00:00
author: 刘长炯
excerpt: https://github.com/moduth/blockcanary 如果不能查看到代码, 我们有万能的github fork上的完整代码: https://github.com/beansoftapp/blockcanary
layout: post
guid: http://www.beansoft.biz/?p=3822
permalink: '/2016/07/22/%e6%8e%a8%e8%8d%90%e9%98%bf%e9%87%8c%e5%b7%b4%e5%b7%b4%e4%bd%bf%e7%94%a8%e7%9a%84android-ui%e5%8d%a1%e9%a1%bf%e6%a3%80%e6%b5%8b%e5%ba%93-blockcanary/'
views:
  - "2232"
image: /wp-content/uploads/2016/07/9d93324419c98337f7a8bf36ad034d00.png
categories:
  - Android
---
<https://github.com/moduth/blockcanary> 如果不能查看到代码, 我们有万能的github fork上的完整代码: <https://github.com/beansoftapp/blockcanary>

然而奇怪的是截止今日撰稿时为止, 这个地址会重定向到 <https://github.com/markzhai/AndroidPerformanceMonitor>, 而且相关的代码在最新分支下也看不到了. 不过不用担心, 本周一看的时候代码还在.

查看提交历史有点怪异:

![](http://www.beansoft.biz/wp-content/uploads/2016/07/9d93324419c98337f7a8bf36ad034d00.png)

代码又删了, 记得上一次删就说是阿里巴巴不让公开. 但是maven库上相关的内容还好好的: <http://central.maven.org/maven2/com/github/moduth/>, 可以在上面下载相关aar和源码文件导入到自己项目中.

使用说明文档: 

<https://github.com/moduth/blockcanary/blob/master/README_CN.md>

原理解释文档见作者blog: <http://blog.zhaiyifan.cn/2016/01/16/BlockCanaryTransparentPerformanceMonitor/>

目前此库已经用于河狸家安卓App的卡顿优化检测了.

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [推荐阿里巴巴使用的Android UI卡顿检测库: BlockCanary](http://www.beansoft.biz/2016/07/22/%e6%8e%a8%e8%8d%90%e9%98%bf%e9%87%8c%e5%b7%b4%e5%b7%b4%e4%bd%bf%e7%94%a8%e7%9a%84android-ui%e5%8d%a1%e9%a1%bf%e6%a3%80%e6%b5%8b%e5%ba%93-blockcanary/)