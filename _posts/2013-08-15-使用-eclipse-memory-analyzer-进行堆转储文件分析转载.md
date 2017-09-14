---
id: 3417
title: '使用 Eclipse Memory Analyzer 进行堆转储文件分析[转载]'
date: 2013-08-15T20:47:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3417
permalink: '/2013/08/15/%e4%bd%bf%e7%94%a8-eclipse-memory-analyzer-%e8%bf%9b%e8%a1%8c%e5%a0%86%e8%bd%ac%e5%82%a8%e6%96%87%e4%bb%b6%e5%88%86%e6%9e%90%e8%bd%ac%e8%bd%bd/'
views:
  - "3910"
categories:
  - Java SE
tags:
  - HeapDump
  - JVM
  - MAT
  - OOM
---
<a name="major2">概述</a>

对于大型 JAVA 应用程序来说，再精细的测试也难以堵住所有的漏洞，即便我们在测试阶段进行了大量卓有成效的工作，很多问题还是会在生产环境下暴露出来，并且很难在测试环境中进行重现。JVM 能够记录下问题发生时系统的部分运行状态，并将其存储在堆转储 (Heap Dump) 文件中，从而为我们分析和诊断问题提供了重要的依据。

通常内存泄露分析被认为是一件很有难度的工作，一般由团队中的资深人士进行。不过，今天我们要介绍的 MAT（Eclipse Memory Analyzer）被认为是一个“傻瓜式“的堆转储文件分析工具，你只需要轻轻点击一下鼠标就可以生成一个专业的分析报告。和其他内存泄露分析工具相比，MAT 的使用非常容易，基本可以实现一键到位，即使是新手也能够很快上手使用。

MAT 的使用是如此容易，你是不是也很有兴趣来亲自感受下呢，那么第一步我们先来安装 MAT。

* * *

[回页首](http://www.ibm.com/developerworks/cn/opensource/os-cn-ecl-ma/#ibm-pcon)

<a name="major3">准备环境和测试数据</a>

我们使用的是 Eclipse Memory Analyzer V0.8，Sun JDK 6

<a name="minor3.1">安装 MAT</a>

和其他插件的安装非常类似，MAT 支持两种安装方式，一种是“单机版“的，也就是说用户不必安装 Eclipse IDE 环境，MAT 作为一个独立的 Eclipse RCP 应用运行；另一种是”集成版“的，也就是说 MAT 也可以作为 Eclipse IDE 的一部分，和现有的开发平台集成。

集成版的安装需要借助 Update Manager。

如图 1 所示，首先通过 Help -> Software Updates&#8230; 启动软件更新管理向导。

<a name="fig1"><b>图 1. 安装插件第一步</b></a>   
<img alt="图 1. 安装插件第一步" src="http://www.ibm.com/developerworks/cn/opensource/os-cn-ecl-ma/image001.jpg" width="282" height="322" />

选择“Available Software“然后按如图 2 所示的方式添加 MAT 的更新地址 <http://download.eclipse.org/technology/mat/0.8/update-site/>。

全文请阅读原文: [http://www.ibm.com/developerworks/cn/opensource/os-cn-ecl-ma/](http://www.ibm.com/developerworks/cn/opensource/os-cn-ecl-ma/ "http://www.ibm.com/developerworks/cn/opensource/os-cn-ecl-ma/")

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [使用 Eclipse Memory Analyzer 进行堆转储文件分析[转载]](http://www.beansoft.biz/2013/08/15/%e4%bd%bf%e7%94%a8-eclipse-memory-analyzer-%e8%bf%9b%e8%a1%8c%e5%a0%86%e8%bd%ac%e5%82%a8%e6%96%87%e4%bb%b6%e5%88%86%e6%9e%90%e8%bd%ac%e8%bd%bd/)