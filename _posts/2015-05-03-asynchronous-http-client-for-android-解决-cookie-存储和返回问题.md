---
id: 3758
title: Asynchronous Http Client for Android 解决 Cookie 存储和返回问题
date: 2015-05-03T19:52:54+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3758
permalink: '/2015/05/03/asynchronous-http-client-for-android-%e8%a7%a3%e5%86%b3-cookie-%e5%ad%98%e5%82%a8%e5%92%8c%e8%bf%94%e5%9b%9e%e9%97%ae%e9%a2%98/'
views:
  - "1663"
categories:
  - Android
tags:
  - Android
  - Cookie
---
Cookie 经常在后台开发中用来解决session问题，可以简化服务端的开发负担。当然如有资源，还是应尽量实现REST方案的服务端。

AsyncHttpClient解决Cookie的存储和返回采用下列代码即可：

AsyncHttpClient client = new AsyncHttpClient();

client.setCookieStore(new PersistentCookieStore(getApplicationContext()));

推荐将&nbsp;new PersistentCookieStore(getApplicationContext()) 缓存起来使用。

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Asynchronous Http Client for Android 解决 Cookie 存储和返回问题](http://www.beansoft.biz/2015/05/03/asynchronous-http-client-for-android-%e8%a7%a3%e5%86%b3-cookie-%e5%ad%98%e5%82%a8%e5%92%8c%e8%bf%94%e5%9b%9e%e9%97%ae%e9%a2%98/)