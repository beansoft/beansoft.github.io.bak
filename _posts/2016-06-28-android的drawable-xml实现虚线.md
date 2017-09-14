---
id: 3809
title: Android的drawable xml实现虚线
date: 2016-06-28T14:55:29+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3809
permalink: '/2016/06/28/android%e7%9a%84drawable-xml%e5%ae%9e%e7%8e%b0%e8%99%9a%e7%ba%bf/'
views:
  - "865"
categories:
  - Android
tags:
  - Android
  - 虚线
---
<div>
  <i>drawable/</i>bottom_dash_line.xml
</div>

<div>
  <b> </b>
</div>

<div>
  <?xml version=&#8221;1.0&#8243; encoding=&#8221;utf-8&#8243;?>
</div>

<div>
  <shape xmlns:android=&#8221;<a href="http://schemas.android.com/apk/res/android">http://schemas.android.com/apk/res/android</a>&#8221;<br /> android:shape=&#8221;line&#8221;><br /> <!&#8211; 显示一条虚线，破折线的宽度为dashWith，破折线之间的空隙的宽度为dashGap，当dashGap=0dp时，为实线 #d6dadd &#8211;><br /> <stroke<br /> android:width=&#8221;0.5dp&#8221;<br /> android:color=&#8221;#D6DADD&#8221;<br /> android:dashGap=&#8221;2dp&#8221;<br /> android:dashWidth=&#8221;2dp&#8221; />
</div>

<div>
  </shape>
</div>

<div>
</div>

<div>
  用的时候单个组件必须设置为software渲染, 否则虚线不能正常显示.
</div>

<div>
</div>

<div>
  <div>
    <ImageView<br /> android:id=&#8221;@+id/bottom_dash_line&#8221;<br /> android:layout_width=&#8221;match_parent&#8221;<br /> android:layout_height=&#8221;1dp&#8221;<br /> android:layerType=&#8221;software&#8221;<br /> android:src=&#8221;@drawable/dash_line&#8221; />
  </div>
</div>

&nbsp;

&nbsp;

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Android的drawable xml实现虚线](http://www.beansoft.biz/2016/06/28/android%e7%9a%84drawable-xml%e5%ae%9e%e7%8e%b0%e8%99%9a%e7%ba%bf/)