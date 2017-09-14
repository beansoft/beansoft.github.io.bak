---
id: 1380
title: VMWare Player VS Oracle VM VirtualBox
date: 2010-11-05T20:19:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1380
permalink: /2010/11/05/vmware-player-vs-oracle-vm-virtualbox/
views:
  - "5822"
original_post_id:
  - "1380"
image: /wp-content/uploads/2012/09/cloudy.png
categories:
  - Cloud/VM
---
**VMWare Player**

优势: 虚拟盘可以修改大小, 压缩(通过虚拟机内的VMTools托盘点击压缩来进行); 支持双核CPU; 虚拟机文件和虚拟硬盘可存放在相同目录, 便于迁移; 复制文件方便(可直接拖放及复制粘贴).

缺点: 占用内存过高, 分配512MB, 但物理内存竟然用到了768MB, 几乎没有虚拟内存, 导致宿主机爆卡; 不支持其它格式虚拟硬盘; 安装包过大.

&#160;

**Oracle VM VirtualBox**

优势: 支持快照和无缝模式; 占用内存少(非常少, 需要时才分配); 启动快; 运行后响应速度快; 兼容多种虚拟硬盘格式如VMWare等;安装包小.

缺点: 虚拟盘大小固定, 无法扩大, 也无法压缩; 不支持双核CPU; 虚拟机配置文件只能存放在C盘.

&#160;

**结论:**

可使用VMWare Player来创建虚拟机, 压缩后导入到VirtualBox中运行.

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [VMWare Player VS Oracle VM VirtualBox](http://www.beansoft.biz/2010/11/05/vmware-player-vs-oracle-vm-virtualbox/)