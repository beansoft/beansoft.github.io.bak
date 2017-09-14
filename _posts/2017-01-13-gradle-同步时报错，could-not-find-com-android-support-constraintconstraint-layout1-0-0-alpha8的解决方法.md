---
id: 3882
title: Gradle 同步时报错，Could not find com.android.support.constraint:constraint-layout:1.0.0-alpha8的解决方法
date: 2017-01-13T19:46:42+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3882
permalink: '/2017/01/13/gradle-%e5%90%8c%e6%ad%a5%e6%97%b6%e6%8a%a5%e9%94%99%ef%bc%8ccould-not-find-com-android-support-constraintconstraint-layout1-0-0-alpha8%e7%9a%84%e8%a7%a3%e5%86%b3%e6%96%b9%e6%b3%95/'
views:
  - "8042"
categories:
  - Android
---
&nbsp;

<div>
  <pre style="background-color: #ffffff; font-family: Menlo; font-size: 9pt;">compile <span style="color: #008000; font-weight: bold;">'com.android.support.constraint:constraint-layout:1.0.0-alpha8'</span></pre>
</div>

<div>
  然后用Studio同步时报错:
</div>

<div>
  Error:Could not find com.android.support.constraint:constraint-layout:1.0.0-alpha8.
</div>

<div>
  Required by:
</div>

<div>
      ARouter:test-module-1:unspecified
</div>

<div>
  <a href=&#8221;searchInBuildFiles&#8221;>Search in build.gradle files</a>
</div>

<div>
</div>

<div>
  原因:
</div>

<div>
  SDK 中可能是没有安装ConstraintLayout的支持包
</div>

<div>
</div>

<div>
  解决办法:
</div>

<div>
  <p>
    在SDK中安装ConstraintLayout 支持包, Android Studio下的操作:
  </p>
  
  <ol>
    <li>
      Preferences > Appearance & Behavior > System Settings > Android
    </li>
    <li>
      点开窗口右边的SDK Tools 标签
    </li>
    <li>
      展开Suport Repository, 并点击 Show Package Details,
    </li>
    <li>
      把ConstraintLayout for Android和Solver for ConstraintLayout的对应版本 勾上安装, 注意版本号!
    </li>
  </ol>
</div>

<div>
</div>

<div>
  <img src="http://www.beansoft.biz/wp-content/uploads/2017/01/950DEE99-A1BB-43DC-AD09-D08ED86C3579-2860-00000FA5928C4C98_file.png" />
</div>

<div>
</div>

<div>
</div>

&nbsp;

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Gradle 同步时报错，Could not find com.android.support.constraint:constraint-layout:1.0.0-alpha8的解决方法](http://www.beansoft.biz/2017/01/13/gradle-%e5%90%8c%e6%ad%a5%e6%97%b6%e6%8a%a5%e9%94%99%ef%bc%8ccould-not-find-com-android-support-constraintconstraint-layout1-0-0-alpha8%e7%9a%84%e8%a7%a3%e5%86%b3%e6%96%b9%e6%b3%95/)