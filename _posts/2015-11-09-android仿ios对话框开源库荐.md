---
id: 3781
title: 'Android仿iOS对话框开源库[荐]'
date: 2015-11-09T11:04:21+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3781
permalink: '/2015/11/09/android%e4%bb%bfios%e5%af%b9%e8%af%9d%e6%a1%86%e5%bc%80%e6%ba%90%e5%ba%93%e8%8d%90/'
views:
  - "4558"
categories:
  - Android
tags:
  - Android
  - iOS
---
下载地址 https://github.com/saiwu-bigkoo/Android-AlertView

 

# Android-AlertView

仿iOS的AlertViewController 几乎完美还原iOS 的 AlertViewController ，同时支持Alert和ActionSheet模式，每一个细节都是精雕细琢，并把api封装成懒到极致模式，一行代码就可以进行弹窗.

##  

## Demo

<a href="https://github.com/saiwu-bigkoo/Android-AlertView/blob/master/preview/alertviewdemo.gif" target="_blank"><img style="max-width: 100%;" src="https://github.com/saiwu-bigkoo/Android-AlertView/raw/master/preview/alertviewdemo.gif" alt="" /></a>

demo是用Module方式依赖，你也可以使用gradle 依赖:

<div class="highlight highlight-source-java">
  <pre>   compile <span class="pl-s"><span class="pl-pds">'</span>com.bigkoo:alertview:1.0.1<span class="pl-pds">'</span></span></pre>
</div>

###  

### config in java code

<div class="highlight highlight-source-java">
  <pre style="background-color: #2b2b2b; color: #a9b7c6; font-family: 'Microsoft YaHei'; font-size: 14.0pt;"><span style="color: #cc7832;">new </span>AlertView(<span style="color: #6a8759;">"上传头像"</span><span style="color: #cc7832;">, null, </span><span style="color: #6a8759;">"取消"</span><span style="color: #cc7832;">, null,<br /></span><span style="color: #cc7832;"> new </span>String[]{<span style="color: #6a8759;">"拍照"</span><span style="color: #cc7832;">, </span><span style="color: #6a8759;">"从相册中选择"</span>}<span style="color: #cc7832;">,<br /></span><span style="color: #cc7832;"> this, </span>AlertView.Style.<span style="color: #9876aa; font-style: italic;">ActionSheet</span><span style="color: #cc7832;">, new </span>OnItemClickListener(){<br />    <span style="color: #cc7832;">public void </span><span style="color: #ffc66d;">onItemClick</span>(Object o<span style="color: #cc7832;">,int </span>position){<br />        Toast.<span style="font-style: italic;">makeText</span>(XWalkWebViewActivity.<span style="color: #cc7832;">this, </span><span style="color: #6a8759;">"点击了第" </span>+ position + <span style="color: #6a8759;">"个"</span><span style="color: #cc7832;">,<br /></span>Toast.<span style="color: #9876aa; font-style: italic;">LENGTH_SHORT</span>).show()<span style="color: #cc7832;">;<br /></span>}<br />}).show()<span style="color: #cc7832;">;</span></pre>
</div>

<div class="highlight highlight-source-java">
  <pre style="background-color: #2b2b2b; color: #a9b7c6; font-family: 'Microsoft YaHei'; font-size: 14.0pt;"><span style="color: #cc7832;">new </span>AlertView(<span style="color: #6a8759;">"标题"</span><span style="color: #cc7832;">, </span><span style="color: #6a8759;">"内容"</span><span style="color: #cc7832;">, null, new </span>String[]{<span style="color: #6a8759;">"确定"</span>}<span style="color: #cc7832;">, null, this,<br /></span>AlertView.Style.<span style="color: #9876aa; font-style: italic;">Alert</span><span style="color: #cc7832;">, null</span>).show()<span style="color: #cc7832;">;</span></pre>
  
  <pre>另外还支持窗口界面拓展，更多操作请下载Demo看。</pre>
</div>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Android仿iOS对话框开源库[荐]](http://www.beansoft.biz/2015/11/09/android%e4%bb%bfios%e5%af%b9%e8%af%9d%e6%a1%86%e5%bc%80%e6%ba%90%e5%ba%93%e8%8d%90/)