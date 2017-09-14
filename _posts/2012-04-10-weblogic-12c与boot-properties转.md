---
id: 2821
title: 'Weblogic 12c与boot.properties[转]'
date: 2012-04-10T20:10:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2821
permalink: '/2012/04/10/weblogic-12c%e4%b8%8eboot-properties%e8%bd%ac/'
views:
  - "13546"
image: /wp-content/uploads/2012/09/image_thumb12.png
categories:
  - WebLogic
tags:
  - 12c
  - WebLogic
---
</p> 

<div style="padding-bottom: 0px; overflow-x: hidden; overflow-y: hidden; widows: 2; text-transform: none; background-color: rgb(255,255,255); text-indent: 0px; margin: 0px; padding-left: 5px; padding-right: 0px; font: 12px/17px verdana, &#39;BitStream vera Sans&#39;, helvetica, sans-serif; white-space: normal; orphans: 2; letter-spacing: normal; color: rgb(85,85,85); word-spacing: 0px; padding-top: 5px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px" class="content">
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    转载自：<a href="http://blog.retailsolution.cn/archives/2992">http://blog.retailsolution.cn/archives/2992</a>
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    千呼万唤始出来
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    Weblogic 12c，在Oracle首页待了许久的weblogic 12c终于出来了
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    期待重大改变，期待Oracle应用更快更强大。
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    至于如何，有待深入探讨。文档！文档！文档！
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    <a style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; color: rgb(41,112,166); text-decoration: none; padding-top: 0px" href="http://blog.retailsolution.cn/wp-content/uploads/2011/12/image.png" rel="lightbox"><img style="padding-bottom: 0px; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; max-width: 600px; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px; border-image: initial" border="0" alt="image" src="http://blog.retailsolution.cn/wp-content/uploads/2011/12/image_thumb.png" width="505" height="125" /></a>
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    先上个console大图吧
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    <a style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; color: rgb(41,112,166); text-decoration: none; padding-top: 0px" href="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image002.jpg" rel="lightbox"><img style="padding-bottom: 0px; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; max-width: 600px; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px; border-image: initial" border="0" alt="clip_image002" src="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image002_thumb.jpg" width="511" height="232" /></a>
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    <a style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; color: rgb(41,112,166); text-decoration: none; padding-top: 0px" href="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image004.jpg" rel="lightbox"><img style="padding-bottom: 0px; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; max-width: 600px; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px; border-image: initial" border="0" alt="clip_image004" src="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image004_thumb.jpg" width="511" height="302" /></a>
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    安装过程：
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    需准备：
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    Redhat 5.4
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    JDK 1.6
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    1. 下载安装介质：
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    <a style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; color: rgb(41,112,166); text-decoration: none; padding-top: 0px" href="http://www.oracle.com/technetwork/middleware/weblogic/downloads/index.html">http://www.oracle.com/technetwork/middleware/weblogic/downloads/index.html</a>
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    <a style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; color: rgb(41,112,166); text-decoration: none; padding-top: 0px" href="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image006.jpg" rel="lightbox"><img style="padding-bottom: 0px; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; max-width: 600px; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px; border-image: initial" border="0" alt="clip_image006" src="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image006_thumb.jpg" width="501" height="332" /></a>
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    相关文档：
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    <a style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; color: rgb(41,112,166); text-decoration: none; padding-top: 0px" href="http://www.oracle.com/technetwork/middleware/weblogic/documentation/index.html">http://www.oracle.com/technetwork/middleware/weblogic/documentation/index.html</a>
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    <a style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; color: rgb(41,112,166); text-decoration: none; padding-top: 0px" href="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image008.jpg" rel="lightbox"><img style="padding-bottom: 0px; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; max-width: 600px; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px; border-image: initial" border="0" alt="clip_image008" src="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image008_thumb.jpg" width="516" height="183" /></a>
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    2. 创建中间件目录
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    mkdir –p /app/Oracle/Middleware2
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    3. 设置环境变量：
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    JAVA_HOME：export JAVA_HOME=/usr/java/jdk1.6.0_26
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    MW_HOM：export MW_HOME=/app/Oracle/Middleware2
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    4. 将安装介质拷贝到中间件目录下：
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    cp /install/wls1211_dev.zip /app/Oracle/Middleware2/
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    5. 进入到中间件目录下，并将介质解压：
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    cd /app/Oracle/Middleware2/
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    unzip wls1211_dev.zip
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    6. 运行配置脚本：
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    ./configure.sh
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    <a style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; color: rgb(41,112,166); text-decoration: none; padding-top: 0px" href="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image010.jpg" rel="lightbox"><img style="padding-bottom: 0px; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; max-width: 600px; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px; border-image: initial" border="0" alt="clip_image010" src="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image010_thumb.jpg" width="529" height="122" /></a>
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    <a style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; color: rgb(41,112,166); text-decoration: none; padding-top: 0px" href="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image012.jpg" rel="lightbox"><img style="padding-bottom: 0px; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; max-width: 600px; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px; border-image: initial" border="0" alt="clip_image012" src="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image012_thumb.jpg" width="524" height="362" /></a>
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    运行完毕。
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    7. 设置参数
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    . $MW_HOME/wlserver/server/bin/setWLSEnv.sh
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    <a style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; color: rgb(41,112,166); text-decoration: none; padding-top: 0px" href="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image014.jpg" rel="lightbox"><img style="padding-bottom: 0px; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; max-width: 600px; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px; border-image: initial" border="0" alt="clip_image014" src="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image014_thumb.jpg" width="534" height="113" /></a>
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    8. 扩展新的Domain：
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    cd wlserver/common/bin/
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    ./config.sh
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    <a style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; color: rgb(41,112,166); text-decoration: none; padding-top: 0px" href="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image016.jpg" rel="lightbox"><img style="padding-bottom: 0px; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; max-width: 600px; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px; border-image: initial" border="0" alt="clip_image016" src="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image016_thumb.jpg" width="532" height="382" /></a>
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    <a style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; color: rgb(41,112,166); text-decoration: none; padding-top: 0px" href="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image018.jpg" rel="lightbox"><img style="padding-bottom: 0px; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; max-width: 600px; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px; border-image: initial" border="0" alt="clip_image018" src="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image018_thumb.jpg" width="535" height="385" /></a>
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    <a style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; color: rgb(41,112,166); text-decoration: none; padding-top: 0px" href="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image020.jpg" rel="lightbox"><img style="padding-bottom: 0px; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; max-width: 600px; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px; border-image: initial" border="0" alt="clip_image020" src="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image020_thumb.jpg" width="539" height="387" /></a>
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    <a style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; color: rgb(41,112,166); text-decoration: none; padding-top: 0px" href="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image022.jpg" rel="lightbox"><img style="padding-bottom: 0px; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; max-width: 600px; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px; border-image: initial" border="0" alt="clip_image022" src="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image022_thumb.jpg" width="551" height="398" /></a>
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    <a style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; color: rgb(41,112,166); text-decoration: none; padding-top: 0px" href="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image024.jpg" rel="lightbox"><img style="padding-bottom: 0px; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; max-width: 600px; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px; border-image: initial" border="0" alt="clip_image024" src="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image024_thumb.jpg" width="552" height="394" /></a>
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    <a style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; color: rgb(41,112,166); text-decoration: none; padding-top: 0px" href="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image026.jpg" rel="lightbox"><img style="padding-bottom: 0px; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; max-width: 600px; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px; border-image: initial" border="0" alt="clip_image026" src="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image026_thumb.jpg" width="555" height="399" /></a>
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    <a style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; color: rgb(41,112,166); text-decoration: none; padding-top: 0px" href="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image028.jpg" rel="lightbox"><img style="padding-bottom: 0px; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; max-width: 600px; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px; border-image: initial" border="0" alt="clip_image028" src="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image028_thumb.jpg" width="559" height="402" /></a>
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    <a style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; color: rgb(41,112,166); text-decoration: none; padding-top: 0px" href="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image030.jpg" rel="lightbox"><img style="padding-bottom: 0px; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; max-width: 600px; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px; border-image: initial" border="0" alt="clip_image030" src="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image030_thumb.jpg" width="557" height="403" /></a>
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    <a style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; color: rgb(41,112,166); text-decoration: none; padding-top: 0px" href="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image032.jpg" rel="lightbox"><img style="padding-bottom: 0px; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; max-width: 600px; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px; border-image: initial" border="0" alt="clip_image032" src="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image032_thumb.jpg" width="568" height="408" /></a>
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    cd /app/Oracle/Middleware2/user_projects/domains/base_domain
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    ./startWebLogic.sh
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    输入用户名：weblogic
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    启动失败：
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    <a style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; color: rgb(41,112,166); text-decoration: none; padding-top: 0px" href="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image034.jpg" rel="lightbox"><img style="padding-bottom: 0px; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; max-width: 600px; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px; border-image: initial" border="0" alt="clip_image034" src="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image034_thumb.jpg" width="581" height="341" /></a>
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    1.进入到$DOMAIN_HOME/servers/<your server>/文件夹下
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    &#160;&#160;&#160;&#160; cd /u02/app/Oracle/Middleware/user_projects/domains/IDMDomain/servers/AdminServer/
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    2. 创建security目录
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    mkdir security
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    3.创建文件 c
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    &#160;&#160;&#160;&#160; touch boot.properties
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    4.编辑boot.properties如以下：
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    &#160;&#160;&#160;&#160; username=weblogic
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    &#160;&#160;&#160;&#160; password=weblogic1
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    5.启动weblogic
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    不需要提供用户名密码进行启动
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    6.启动好了以后查看 boot.properties
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    #Sun Nov 06 22:56:29 CST 2011
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    password={AES}KBg2GWUT2lAXHjrZFNTyTAKuht732pECQ8bv+duOknE\=<span class="Apple-converted-space">&#160;</span> <br style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; padding-top: 0px" />&#160; username={AES}YK2J5oCgBJo2r8V0w3mJZ7Zvxwu531CAMxZgt4oQcKA\=
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    重新启动：
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    cd /app/Oracle/Middleware2/user_projects/domains/base_domain
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    ./startWebLogic.sh
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    不需要输入用户名密码。
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    启动成功！
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    报了些警告，但还是起来了
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px 0px 10px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    <a style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; color: rgb(41,112,166); text-decoration: none; padding-top: 0px" href="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image036.jpg" rel="lightbox"><img style="padding-bottom: 0px; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; max-width: 600px; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px; border-image: initial" border="0" alt="clip_image036" src="http://blog.retailsolution.cn/wp-content/uploads/2011/12/clip_image036_thumb.jpg" width="557" height="223" /></a>
  </p>
  
  <div style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; clear: both; padding-top: 0px" class="fixed">
  </div></p>
</div>

<div style="padding-bottom: 0px; widows: 2; text-transform: none; background-color: rgb(255,255,255); text-indent: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; font: 12px verdana, &#39;BitStream vera Sans&#39;, helvetica, sans-serif; white-space: normal; orphans: 2; letter-spacing: normal; color: rgb(85,85,85); word-spacing: 0px; padding-top: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px">
  <p style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    &#160;
  </p>
  
  <p style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; padding-top: 0px">
    &#160;
  </p></p>
</div>

<h4 style="padding-bottom: 0px; widows: 2; text-transform: none; background-color: rgb(255,255,255); text-indent: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; font: bold 16px arial; white-space: normal; orphans: 2; letter-spacing: normal; color: rgb(85,85,85); word-spacing: 0px; padding-top: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px">
  关于作者:
</h4>

昵称:dick.luo <br style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; padding-top: 0px" />档案信息:本人罗昌辉，英文名为dick，目前就职于上海汉得信息技术股份有限公司中间件事业部，担任中间件技术顾问，专注于Oracle融合中间件产品在企业中的应用以及二次开发。 <br style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; padding-top: 0px" />联系方式:你可以通过<a style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; color: rgb(41,112,166); text-decoration: none; padding-top: 0px" href="mailto:changhui.luo@gmail.com">changhui.luo@gmail.com</a>联系作者 <br style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; padding-top: 0px" />点击查看<a style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; color: rgb(41,112,166); text-decoration: none; padding-top: 0px" title="由 dick.luo 发表" href="http://blog.retailsolution.cn/archives/author/dick-luo/">dick.luo</a>发表过的所有文章&#8230; <br style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; padding-top: 0px" />本文永久链接：<a style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; color: rgb(41,112,166); text-decoration: none; padding-top: 0px" href="http://blog.retailsolution.cn/archives/2992"><span class="Apple-converted-space">&#160;</span>http://blog.retailsolution.cn/archives/2992</a>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Weblogic 12c与boot.properties[转]](http://www.beansoft.biz/2012/04/10/weblogic-12c%e4%b8%8eboot-properties%e8%bd%ac/)