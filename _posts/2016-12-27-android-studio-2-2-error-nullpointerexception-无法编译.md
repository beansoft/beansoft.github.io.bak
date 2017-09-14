---
id: 3867
title: Android Studio 2.2 Error NullPointerException, 无法编译
date: 2016-12-27T07:20:32+00:00
author: 刘长炯
excerpt: 有一次Studio卡顿导致Mac死机, 重启后一点Run或者Build就在Message下面报一行NPE, 无法编译, clean也无效.
layout: post
guid: http://www.beansoft.biz/?p=3867
permalink: '/2016/12/27/android-studio-2-2-error-nullpointerexception-%e6%97%a0%e6%b3%95%e7%bc%96%e8%af%91/'
views:
  - "1365"
categories:
  - Android
---
有一次Studio卡顿导致Mac死机, 重启后一点Run或者Build就在Message下面报一行NPE, 无法编译, clean也无效.

最终解决方案: 关闭Studio, 删除项目下的 .gradle文件夹.

参考: <http://stackoverflow.com/questions/39126874/android-studio-2-2-error-nullpointerexception>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Android Studio 2.2 Error NullPointerException, 无法编译](http://www.beansoft.biz/2016/12/27/android-studio-2-2-error-nullpointerexception-%e6%97%a0%e6%b3%95%e7%bc%96%e8%af%91/)