---
id: 246
title: 'Eclipse Tray 1.0 RC1 &#8211; 最小化 Eclipse 到托盘的插件(原创,源码)'
date: 2007-01-12T14:25:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=246
permalink: '/2007/01/12/eclipse-tray-1-0-rc1-%e6%9c%80%e5%b0%8f%e5%8c%96-eclipse-%e5%88%b0%e6%89%98%e7%9b%98%e7%9a%84%e6%8f%92%e4%bb%b6%e5%8e%9f%e5%88%9b%e6%ba%90%e7%a0%81/'
views:
  - "3661"
original_post_id:
  - "246"
image: /wp-content/uploads/2012/09/r_eclise_tray_1.0.1_menu.png
categories:
  - MyEclipse/Eclipse
---
<font color="#0080ff"></font><font color="#000000">作者: </font><beansoft@126.com> <font color="#000000">2007.01.02</font>

**<font color="#0080ff">已知问题 Known Bugs</font>**

1. 多个 window 不支持, 会出现窗口找不到的情况(多个进程的没问题); 

<font color="#0080ff"><strong>更新 History</strong></font>

1.0 RC1

启动时自动加载, 无需必须点击工具栏按钮才可激活插件, 直接点击窗口的最小化按钮即可(参考资料: 交口称赞的[让eclipse启动时执行指定的程序](http://www.blogjava.net/vip01/archive/2006/12/31/91156.aspx), 小小凉粉的改变RCP标题(原文已被作者删除));

菜单栏国际化支持(目前只有简体中文/英文两种语言);

修正恢复窗体后无法获取焦点的bug.

1.0.0

初始版本, 实现最小化到托盘功能.

<font color="#0080ff"><strong>下载 Download</strong></font>

插件二进制包(binary): [EclipseTray_1.0.1.zip](http://www.blogjava.net/Files/beansoft/EclipseTray_1.0.1.zip) 16KB 

源码(source): [EclipseTray\_1.0.1\_src.zip](http://www.blogjava.net/Files/beansoft/EclipseTray_1.0.1_src.zip) 5KB 

测试过的 Eclipse 版本: 3.1(MyEclipse 4), 3.2(MyEclipse 5), 3.3M6 on Windows 2003, Windows XP. 

<font color="#0080ff"><strong>用法 Usage</strong></font> 

下载后解压缩出 JAR 文件, 放到 plugins 目录下即可. 

通过点击最小化 Eclipse 窗口, 或者点击一下工具栏按钮或者菜单, 这时主窗口就会被隐藏, 托盘的图标就会显示. 鼠标移过托盘图标显示当前窗口的标题名称, 左键点击托盘图标可以恢复主窗口的显示, 同时隐藏托盘图标(托盘是个风水宝地, N 多软件都想常驻里面, 给大家节约点窄小的任务栏空间吧), 点击右键可以看到弹出菜单, 通过右键菜单可以退出主窗体. 

<font color="#0080ff"><strong>开发环境 Built-On</strong></font>   
Eclipse 3.3 + JDK 1.6 + LocalizationEditor 

注: **LocalizationEditor**   
此 LocalizationEditor 作者邮件为 <didier@ieee.org>, 没有网站, 在 Eclipse 2.1 的时候他的这个插件就开发出来了. 之后虽然我的 Eclipse 已经升级到了3.2, 这个插件依然可以用, 实在是难能可贵啊. 个头也比较小. 它的功能包括: 隐藏未翻译词条, 隐藏已翻译词条, 对比翻译等等. 下载: [LocalizationEditor.zip](http://www.blogjava.net/Files/beansoft/LocalizationEditor.zip) 222KB 截屏: [http://www.blogjava.net/images/blogjava\_net/beansoft/17648/o\_LocalizationEditorWorkbench.png](http://www.blogjava.net/images/blogjava_net/beansoft/17648/o_LocalizationEditorWorkbench.png) 

**<font color="#0080ff">许可协议 License</font>** 

LGPL(GNU LESSER GENERAL PUBLIC LICENSE), 2.1 or latter, as your wish. 

**<font color="#0080ff">截屏 Screenshots</font>** 

1.0.1 版本   
    <img style="border-right:black 2px solid;border-top:black 2px solid;border-left:black 2px solid;width:295px;border-bottom:black 2px solid;height:279px;" alt="Eclipse Tray 1.0.1 menu" src="http://www.blogjava.net/images/blogjava_net/beansoft/17648/r_eclise_tray_1.0.1_menu.png" />  
&#160;    <img style="border-right:black 2px solid;border-top:black 2px solid;border-left:black 2px solid;width:282px;border-bottom:black 2px solid;height:40px;" alt="Eclipse Tray 1.0.1 Tooltip" src="http://www.blogjava.net/images/blogjava_net/beansoft/17648/r_eclise_tray_1.0.1_tray_tooltip.png" />  
![Eclipse Tray 1.0.1 tray](http://www.blogjava.net/images/blogjava_net/beansoft/17648/r_eclise_tray_1.0.1_tray.png) <img style="border-right:black 2px solid;border-top:black 2px solid;border-left:black 2px solid;width:441px;border-bottom:black 2px solid;height:198px;" alt="Eclipse Tray 1.0.1 about" src="http://www.blogjava.net/images/blogjava_net/beansoft/17648/r_eclise_tray_1.0.1_about.png" />

1.0.0 版本 

![](http://www.blogjava.net/images/blogjava_net/beansoft/17648/r_eclipse_tray_2.png)![](http://www.blogjava.net/images/blogjava_net/beansoft/17648/o_eclipse_tray_1.png)![](http://www.blogjava.net/images/blogjava_net/beansoft/17648/r_eclipse_tray_3.png)

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Eclipse Tray 1.0 RC1 &#8211; 最小化 Eclipse 到托盘的插件(原创,源码)](http://www.beansoft.biz/2007/01/12/eclipse-tray-1-0-rc1-%e6%9c%80%e5%b0%8f%e5%8c%96-eclipse-%e5%88%b0%e6%89%98%e7%9b%98%e7%9a%84%e6%8f%92%e4%bb%b6%e5%8e%9f%e5%88%9b%e6%ba%90%e7%a0%81/)