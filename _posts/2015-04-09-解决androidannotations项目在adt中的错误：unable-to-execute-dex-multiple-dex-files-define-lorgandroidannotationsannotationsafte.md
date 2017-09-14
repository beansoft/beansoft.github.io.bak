---
id: 3754
title: '解决androidannotations项目在ADT中的错误：Unable to execute dex: Multiple dex files define Lorg/androidannotations/annotations/AfterExtras;'
date: 2015-04-09T17:07:10+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3754
permalink: '/2015/04/09/%e8%a7%a3%e5%86%b3androidannotations%e9%a1%b9%e7%9b%ae%e5%9c%a8adt%e4%b8%ad%e7%9a%84%e9%94%99%e8%af%af%ef%bc%9aunable-to-execute-dex-multiple-dex-files-define-lorgandroidannotationsannotationsafte/'
views:
  - "2089"
categories:
  - Android
---
编译无问题，当尝试运行时出错。

BeanSoft 2015-04-09



解决方法是通用的，参考：http://stackoverflow.com/questions/7870265/unable-to-execute-dex-multiple-dex-files-define-lcom-myapp-rarray



I had the same problem, quite weird because it was happening only when using Eclipse (but it was OK with Ant). This is how I fixed it:



Right click on the Project Name

Select Build Path -> Configure Build Path

In Java Build Path, go to the tab Order and Export



Uncheck your .jar library





Only sometimes: In Order and Export tab I did not have any jar library there, so I have unchecked Android Private Libraries item. Now my project is running.



转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [解决androidannotations项目在ADT中的错误：Unable to execute dex: Multiple dex files define Lorg/androidannotations/annotations/AfterExtras;](http://www.beansoft.biz/2015/04/09/%e8%a7%a3%e5%86%b3androidannotations%e9%a1%b9%e7%9b%ae%e5%9c%a8adt%e4%b8%ad%e7%9a%84%e9%94%99%e8%af%af%ef%bc%9aunable-to-execute-dex-multiple-dex-files-define-lorgandroidannotationsannotationsafte/)