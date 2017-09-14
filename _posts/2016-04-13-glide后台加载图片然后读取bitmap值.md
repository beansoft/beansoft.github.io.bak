---
id: 3804
title: Glide后台加载图片然后读取bitmap值
date: 2016-04-13T17:16:43+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3804
permalink: '/2016/04/13/glide%e5%90%8e%e5%8f%b0%e5%8a%a0%e8%bd%bd%e5%9b%be%e7%89%87%e7%84%b6%e5%90%8e%e8%af%bb%e5%8f%96bitmap%e5%80%bc/'
views:
  - "1333"
categories:
  - Android
tags:
  - Android
---
Glide.with(getContext()).load(NetUtils.urlString(
              
thwartData.getBackGroundImage())).into(new SimpleTarget<GlideDrawable>() {
          
@Override
          
public void onResourceReady(GlideDrawable resource, GlideAnimation<? super GlideDrawable> glideAnimation) {


              
rootLayout.setBackgroundDrawable(resource);
          
}
      
});

有图片的情况如下:
  
Glide.with(getContext()).load(NetUtils.urlString(
          
thwartData.getBackGroundImage())).into(bgImage);]

如果要指定加载后的图片大小, 用另一个构造方法:

/**
       
* Constructor for the target that takes the desired dimensions of the decoded and/or transformed resource.
       
*
       
* @param width The width in pixels of the desired resource.
       
* @param height The height in pixels of the desired resource.
       
*/
      
public SimpleTarget(int width, int height) {
          
this.width = width;
          
this.height = height;
      
}

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Glide后台加载图片然后读取bitmap值](http://www.beansoft.biz/2016/04/13/glide%e5%90%8e%e5%8f%b0%e5%8a%a0%e8%bd%bd%e5%9b%be%e7%89%87%e7%84%b6%e5%90%8e%e8%af%bb%e5%8f%96bitmap%e5%80%bc/)