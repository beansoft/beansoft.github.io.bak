---
id: 3797
title: Android Studio 解决AIDL文件编译后提示找不到符号的问题
date: 2015-12-27T23:01:03+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3797
permalink: '/2015/12/27/android-studio-%e8%a7%a3%e5%86%b3aidl%e6%96%87%e4%bb%b6%e7%bc%96%e8%af%91%e5%90%8e%e6%8f%90%e7%a4%ba%e6%89%be%e4%b8%8d%e5%88%b0%e7%ac%a6%e5%8f%b7%e7%9a%84%e9%97%ae%e9%a2%98/'
views:
  - "4021"
categories:
  - Android
tags:
  - Android
---
AIDL文件不能像ADT Eclipse那样和普通的Java文件放在一起, 否则将不会进行编译. 正确做法:

项目中 新建 src/main/aidl 文件夹, 然后将AIDL定义放入其中, 即可解决.

 

<img style="float: left;" title="NewImage.png" src="http://www.beansoft.biz/wp-content/uploads/2015/12/NewImage1.png" alt="NewImage" width="143" height="83" border="0" />

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Android Studio 解决AIDL文件编译后提示找不到符号的问题](http://www.beansoft.biz/2015/12/27/android-studio-%e8%a7%a3%e5%86%b3aidl%e6%96%87%e4%bb%b6%e7%bc%96%e8%af%91%e5%90%8e%e6%8f%90%e7%a4%ba%e6%89%be%e4%b8%8d%e5%88%b0%e7%ac%a6%e5%8f%b7%e7%9a%84%e9%97%ae%e9%a2%98/)