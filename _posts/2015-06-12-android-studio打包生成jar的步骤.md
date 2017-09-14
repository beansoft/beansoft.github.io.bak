---
id: 3766
title: Android Studio打包生成jar的步骤
date: 2015-06-12T11:26:50+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3766
permalink: '/2015/06/12/android-studio%e6%89%93%e5%8c%85%e7%94%9f%e6%88%90jar%e7%9a%84%e6%ad%a5%e9%aa%a4/'
views:
  - "8578"
categories:
  - Android
---
<div style="font-family: 'Helvetica Neue'; font-size: 14px;">
  build.gradle添加下面的语句，然后在task上运行点右键 Gradle makeJar 即可。注意输出目录不能写为build/outputs. 如果项目已经在ide里编译成功，可注释掉最后一行代码直接打包。
</div>

<div style="font-family: 'Helvetica Neue'; font-size: 14px;">
   
</div>

<div style="font-family: 'Helvetica Neue'; font-size: 14px;">
  <div style="background-color: #2b2b2b; color: #a9b7c6; font-family: 'Microsoft YaHei'; font-size: 14.0pt;">
    <span style="background-color: #344134;">task</span> clearJar(<span style="color: #d0d0ff;">type</span>: Delete) {<br />     delete <span style="color: #6a8759;">&#8216;dist/android-validation-komensky.jar&#8217;<br /> </span>}</p> 
    
    <p>
      <span style="background-color: #344134;">task</span> makeJar(<span style="color: #d0d0ff;">type</span>: Copy) {<br />     from(<span style="color: #6a8759;">&#8216;build/intermediates/bundles/release/&#8217;</span>)<br />     into(<span style="color: #6a8759;">&#8216;dist/&#8217;</span>)<br />     include(<span style="color: #6a8759;">&#8216;classes.jar&#8217;</span>)<br />     rename (<span style="color: #6a8759;">&#8216;classes.jar&#8217;</span>, <span style="color: #6a8759;">&#8216;android-validation-komensky.jar&#8217;</span>)<br /> }
    </p>
    
    <p>
      makeJar.dependsOn(clearJar, build)
    </p>
  </div>
</div>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Android Studio打包生成jar的步骤](http://www.beansoft.biz/2015/06/12/android-studio%e6%89%93%e5%8c%85%e7%94%9f%e6%88%90jar%e7%9a%84%e6%ad%a5%e9%aa%a4/)