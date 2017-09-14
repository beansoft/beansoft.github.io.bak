---
id: 402
title: 转:脚本调试工具 Microsoft Script Debugger(略有改动)
date: 2010-07-21T14:17:41+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=402
permalink: '/2010/07/21/%e8%bd%ac%e8%84%9a%e6%9c%ac%e8%b0%83%e8%af%95%e5%b7%a5%e5%85%b7-microsoft-script-debugger%e7%95%a5%e6%9c%89%e6%94%b9%e5%8a%a8/'
views:
  - "3730"
original_post_id:
  - "402"
image: /wp-content/uploads/2012/09/20070928205650796.jpg
categories:
  - AJAX/JavaScript
tags:
  - Debugger
  - JavaScript
---
原文: [http://www.cnblogs.com/pcjim/archive/2007/09/28/909894.html](http://www.cnblogs.com/pcjim/archive/2007/09/28/909894.html "http://www.cnblogs.com/pcjim/archive/2007/09/28/909894.html") 本文属于经典文章回顾系列.

转注: IE 8 已经内置了脚本调试器, 不需要单独进行安装.

&#160;

&#160; 脚本调试工具 Microsoft Script Debugger ，配合IE在调Ajax脚本代码时用得到，用 debugger; 设断点。安装后，将Internet 选项->高级->禁用脚本调试(Internet Explorer) 前的“√”去掉。   
安装包下载地址：[http://www.microsoft.com/downloads/details.aspx?FamilyID=e606e71f-ba7f-471e-a57d-f2216d81ec3d&displaylang=zh-cn](http://www.microsoft.com/downloads/details.aspx?FamilyID=e606e71f-ba7f-471e-a57d-f2216d81ec3d&displaylang=zh-cn "http://www.microsoft.com/downloads/details.aspx?FamilyID=e606e71f-ba7f-471e-a57d-f2216d81ec3d&displaylang=zh-cn")<u><font color="#669966">&#160;</font></u>

    <img height="452" alt="20070928205650796.jpg" src="http://images.cnblogs.com/cnblogs_com/pcjim/Microsoft%20Script%20Debugger/20070928205650796.jpg" width="431" border="0" />  
<img height="369" alt="20070928211705828.jpg" src="http://images.cnblogs.com/cnblogs_com/pcjim/Microsoft%20Script%20Debugger/20070928211705828.jpg" width="527" border="0" />

&#160;&#160;&#160; 补充：   
&#160;&#160;&#160; 新添了一个结合IE7.0 一起使用的例子，测试页面是一个aspx的前台页面，里面含有待测试的javascript。   
&#160;&#160;&#160; 1、当待测页面在IE7.0里打开后，点击 “查看->脚本调试程序->打开”，出来如下窗口。

<img height="500" alt="msd1.jpg" src="http://images.cnblogs.com/cnblogs_com/pcjim/MSD/msd1.jpg" width="700" border="0" />

2、选择“Microsoft 脚本调试器的新实例”

    <img height="500" alt="msd2.jpg" src="http://images.cnblogs.com/cnblogs_com/pcjim/MSD/msd2.jpg" width="700" border="0" />  
<img height="500" alt="msd3.jpg" src="http://images.cnblogs.com/cnblogs_com/pcjim/MSD/msd3.jpg" width="700" border="0" />

3、在checkLogin()函数内按F9 设置断点（F8单步执行），点击测试页面上的“登录”按钮则会激活这个断点。在命令窗口中添加对lname.value的监视，因为在用户名没有输的情况下按下了“登录”按钮，所以现在监视下来lname.value（用户名）是空的。如下图所示：

    <img height="500" alt="msd4.jpg" src="http://images.cnblogs.com/cnblogs_com/pcjim/MSD/msd4.jpg" width="700" border="0" />  
<img height="500" alt="msd5.jpg" src="http://images.cnblogs.com/cnblogs_com/pcjim/MSD/msd5.jpg" width="700" border="0" />

&#160;&#160;&#160; 附：国外网站上的相关参考资料（Debugging JavaScript in Your Applications）   
<http://www.codestore.net/store.nsf/unid/DOMT-5UBUVW>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [转:脚本调试工具 Microsoft Script Debugger(略有改动)](http://www.beansoft.biz/2010/07/21/%e8%bd%ac%e8%84%9a%e6%9c%ac%e8%b0%83%e8%af%95%e5%b7%a5%e5%85%b7-microsoft-script-debugger%e7%95%a5%e6%9c%89%e6%94%b9%e5%8a%a8/)