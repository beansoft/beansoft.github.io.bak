---
id: 1034452802
title: VisualGC Java 8 修正版
date: 2020-05-22T22:34:46+00:00
author: 刘长炯
layout: post
guid: 8e4a4e35-dfd4-47c3-af73-37cd25489bbb
permalink: '2020/05/22/VisualGC+Java+8+%E4%BF%AE%E6%AD%A3%E7%89%88'
categories:
  - JVM
---

VisualGC是我最早接触的JVM工具之一. 然而Java 8之后运行就会崩溃(NPE), 不过 VisualVM里面的插件版却不会. 经过努力, 终于在不改原始代码的情况下, 正常运行了.

主要功能和原VisualGC 3.0基本保持一致.

下载地址: [visualgc_patch.zip 64kb](/static/visualgc_patch.zip)

1. 支持Java 5 到 Java 14, 修复NPE, Mac,Win10测试通过
2. 支持启动时选择本地进程列表
3. 支持浅色模式显示图表和界面
4. 支持检测IDEA进程显示
5. 标题栏显示当前进程ID和主类

![启动窗口](/static/img/visualgc_patch.png)

![主界面](/static/img/visualgc_patch_main.png)

参考文档:

https://www.oracle.com/technetwork/java/jvmstat-142257.html