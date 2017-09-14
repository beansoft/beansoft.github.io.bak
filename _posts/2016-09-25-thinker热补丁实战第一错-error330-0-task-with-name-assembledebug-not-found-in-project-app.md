---
id: 3856
title: 'Thinker热补丁实战第一弹: Error:(330, 0) Task with name &#8216;assembleDebug&#8217; not found in project &#8216;:app&#8217;.'
date: 2016-09-25T12:17:47+00:00
author: 刘长炯
excerpt: 由于用的是最新版的Android Studio 2.2, 然后导入Thinker官方Demo: https://github.com/Tencent/tinker/tree/dev/tinker-sample-android
layout: post
guid: http://www.beansoft.biz/?p=3856
permalink: '/2016/09/25/thinker%e7%83%ad%e8%a1%a5%e4%b8%81%e5%ae%9e%e6%88%98%e7%ac%ac%e4%b8%80%e9%94%99-error330-0-task-with-name-assembledebug-not-found-in-project-app/'
views:
  - "3126"
image: /wp-content/uploads/2016/09/03fc44e831e362296d7cf5cfe3135dea.png
categories:
  - Android
---
由于用的是最新版的Android Studio 2.2, 然后导入Thinker官方Demo: <https://github.com/Tencent/tinker/tree/dev/tinker-sample-android>

在开发工具的建议下, 将gradle编译版本修改为 2.2.0:

dependencies {
  
    classpath <span style="color:#008000;font-weight:bold">&#8216;com.android.tools.build:gradle:2.2.0&#8217;</span>

<span style="font-size: 9pt"><span style="font-family: Menlo"><span style="color:#008000;font-weight:bold">   </span> classpath <span style="color:#008000;font-weight:bold">"com.tencent.tinker:tinker-patch-gradle-plugin:</span>${TINKER_VERSION}<span style="color:#008000;font-weight:bold">"</span></span></span>

**<span style="font-size: 9pt"><span style="font-family: Menlo"><span></span></span></span>**

<span style="font-family: Menlo">然后很不幸的, 项目编译报错:</span>

![](http://www.beansoft.biz/wp-content/uploads/2016/09/03fc44e831e362296d7cf5cfe3135dea.png)

解决方案很简单, 修改回 2.1.0 即可.</p> 

![](http://www.beansoft.biz/wp-content/uploads/2016/09/8453406f6aeab0c22a1d05ea9f44b5e9.png)</p> 

后面再给大家补充实际操作步骤视频.

2016-09-26 更新: 微信Thinker热补丁团队动作很快啊, 这个bug他们今天已经修复了! 可以直接用最新版的Android Studio开发了!

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Thinker热补丁实战第一弹: Error:(330, 0) Task with name &#8216;assembleDebug&#8217; not found in project &#8216;:app&#8217;.](http://www.beansoft.biz/2016/09/25/thinker%e7%83%ad%e8%a1%a5%e4%b8%81%e5%ae%9e%e6%88%98%e7%ac%ac%e4%b8%80%e9%94%99-error330-0-task-with-name-assembledebug-not-found-in-project-app/)