---
id: 2205
title: CryENGINE 3 SDK如何玩自己开发的游戏地图?
date: 2011-08-28T11:53:21+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2205
permalink: '/2011/08/28/cryengine-3-sdk%e5%a6%82%e4%bd%95%e7%8e%a9%e8%87%aa%e5%b7%b1%e5%bc%80%e5%8f%91%e7%9a%84%e6%b8%b8%e6%88%8f%e5%9c%b0%e5%9b%be/'
views:
  - "5412"
original_post_id:
  - "2205"
categories:
  - Game
tags:
  - Cryengine
  - Game
  - SDK
---
CryENGINE 3 SDK 附带了两个最主要的程序:

1. Launcher.exe 地图运行程序

2. Editor.exe 地图编辑程序(SandBox Editor)

SDK 已经自带了一个地图 Forest, 那么如何运行它呢?

&#160;

2012-09 更新：最新版Launcher已经带了相关的操作菜单，无需再通过键入命令的方式载入地图了。

&#160;

首先, 启动 Launcher.exe, 输入crydev帐号启动成功后, 依次点击菜单 Single Player > Forest， 即可运行地图。

<img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="image_thumb2" border="0" alt="image_thumb2" src="http://www.beansoft.biz/wp-content/uploads/2012/09/image_thumb21.png" width="872" height="574" />

&#160;

<img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="image_thumb6" border="0" alt="image_thumb6" src="http://www.beansoft.biz/wp-content/uploads/2012/09/image_thumb61.png" width="875" height="582" />

<img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="image_thumb7" border="0" alt="image_thumb7" src="http://www.beansoft.biz/wp-content/uploads/2012/09/image_thumb71.png" width="944" height="556" />

<img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="Launcher2012092110314879_thum" border="0" alt="Launcher2012092110314879_thum" src="http://www.beansoft.biz/wp-content/uploads/2012/09/Launcher2012092110314879_thum1.png" width="1024" height="768" />

Ctrl + PrintScreen 打开调试菜单。Alt + Enter 切换全屏。

<strike>, 在界面上看不到任何多余的按钮和菜单. 请按下键盘上的 ~ 键, 输入命令:</strike>

<strike>map Forest</strike>

<strike>即可载入并执行地图了.</strike>

<strike>如果是自己开发的地图, 需要首先在Editor中选择菜单 File > Export to engine, 然后在键入 map <地图名> 即可测试运行了.</strike>

<strike>如果需要全屏执行, 需要修改 system.cfg</strike>

<strike>&#8212; Disable fullscreen mode   
**r_Fullscreen=1**</strike>

****

相关地图开发视频教程可在youtube上找到, 很多功能和SandBox Editor 2很相似.

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [CryENGINE 3 SDK如何玩自己开发的游戏地图?](http://www.beansoft.biz/2011/08/28/cryengine-3-sdk%e5%a6%82%e4%bd%95%e7%8e%a9%e8%87%aa%e5%b7%b1%e5%bc%80%e5%8f%91%e7%9a%84%e6%b8%b8%e6%88%8f%e5%9c%b0%e5%9b%be/)