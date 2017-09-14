---
id: 2819
title: 解决FlashPaper在Office 2010下非法退出的问题
date: 2012-04-10T22:23:39+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2819
permalink: '/2012/04/10/%e8%a7%a3%e5%86%b3flashpaper%e5%9c%a8office-2010%e4%b8%8b%e9%9d%9e%e6%b3%95%e9%80%80%e5%87%ba%e7%9a%84%e9%97%ae%e9%a2%98/'
views:
  - "2942"
image: /wp-content/uploads/2012/04/Flash-Paper.png
categories:
  - Flash/Flex
tags:
  - FlashPaper
---
经调试，发现是生成SWF时调用了一些flashplayerxxx.ocx的方法失败，解决办法：
  
1. 删除Flash Player;
  
2. 重装或修复Flash Paper，默认自带播放器版本为7.0，即可解决此问题。

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [解决FlashPaper在Office 2010下非法退出的问题](http://www.beansoft.biz/2012/04/10/%e8%a7%a3%e5%86%b3flashpaper%e5%9c%a8office-2010%e4%b8%8b%e9%9d%9e%e6%b3%95%e9%80%80%e5%87%ba%e7%9a%84%e9%97%ae%e9%a2%98/)