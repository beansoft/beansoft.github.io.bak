---
id: 3632
title: WLS_003：图解安装 WebLogic 10gR3 （支持ADF Runtime）
date: 2014-04-30T17:51:59+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3632
permalink: '/2014/04/30/%e5%9b%be%e8%a7%a3%e5%ae%89%e8%a3%85-weblogic-10gr3-%ef%bc%88%e6%94%af%e6%8c%81adf-runtime%ef%bc%89/'
views:
  - "6009"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
来源:[http://maping930883.blogspot.jp/2009/03/wls003-weblogic-10gr3-adf-runtime.html](http://maping930883.blogspot.jp/2009/03/wls003-weblogic-10gr3-adf-runtime.html "http://maping930883.blogspot.jp/2009/03/wls003-weblogic-10gr3-adf-runtime.html")

&#160;

**1. 三种种安装方式**   
GUI、Console、Slient。   
**2. 支持平台**   
Windows 2000/2003 Server、Windows XP、Sun Solaris、HP-UX、Linux。   
详细支持平台信息，请访问<http://edocs.bea.com/platform/suppconfigs/index.html>。   
**3. 硬装安装最低需求：WebLogic Server 10g**   
CPU：1 GHz CPU   
硬盘：1 GB   
内存：1 GB RAM   
安装时要设置临时文件空间：set TMP=tmpdirpath （Windows）   
或在安装的命令行加入 -Djava.io.tmpdir=tmpdirpath （任何平台）   
一切就绪，开始安装吧！   
**4. 安装方法一**   
该方法适用于已经安装了WebLogic Server 10gR3，适用于生产环境。   
**（1） 安装Oracle WebLogic Server 10gR3**   
下载地址：<http://www.oracle.com/technology/software/products/ias/htdocs/wls_main.html>   
[<img style="background-image: none; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="Image(1)" border="0" alt="Image(1)" src="http://www.beansoft.biz/wp-content/uploads/2014/04/Image1_thumb.jpg" width="600" height="430" />](http://www.beansoft.biz/wp-content/uploads/2014/04/Image1.jpg)   
[<img style="background-image: none; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="Image(2)" border="0" alt="Image(2)" src="http://www.beansoft.biz/wp-content/uploads/2014/04/Image2_thumb.jpg" width="600" height="430" />](http://www.beansoft.biz/wp-content/uploads/2014/04/Image2.jpg)   
[<img style="background-image: none; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="Image(3)" border="0" alt="Image(3)" src="http://www.beansoft.biz/wp-content/uploads/2014/04/Image3_thumb.jpg" width="600" height="430" />](http://www.beansoft.biz/wp-content/uploads/2014/04/Image3.jpg)   
[<img style="background-image: none; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="Image(4)" border="0" alt="Image(4)" src="http://www.beansoft.biz/wp-content/uploads/2014/04/Image4_thumb.jpg" width="600" height="430" />](http://www.beansoft.biz/wp-content/uploads/2014/04/Image4.jpg)   
[<img style="background-image: none; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="Image(5)" border="0" alt="Image(5)" src="http://www.beansoft.biz/wp-content/uploads/2014/04/Image5_thumb.jpg" width="600" height="430" />](http://www.beansoft.biz/wp-content/uploads/2014/04/Image5.jpg)   
[<img style="background-image: none; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="Image(6)" border="0" alt="Image(6)" src="http://www.beansoft.biz/wp-content/uploads/2014/04/Image6_thumb.jpg" width="600" height="430" />](http://www.beansoft.biz/wp-content/uploads/2014/04/Image6.jpg)   
[<img style="background-image: none; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="Image(7)" border="0" alt="Image(7)" src="http://www.beansoft.biz/wp-content/uploads/2014/04/Image7_thumb.jpg" width="600" height="430" />](http://www.beansoft.biz/wp-content/uploads/2014/04/Image7.jpg)   
**（2）安装JDeveloper 11g**   
下载地址：<http://www.oracle.com/technology/software/products/jdev/htdocs/soft11.html> 。   
注意，这里要选择使用现有的中间件目录。   
[<img style="background-image: none; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="Image(8)" border="0" alt="Image(8)" src="http://www.beansoft.biz/wp-content/uploads/2014/04/Image8_thumb.jpg" width="600" height="430" />](http://www.beansoft.biz/wp-content/uploads/2014/04/Image8.jpg)   
如果只是为了让WebLogic Server 能运行ADF，那就不需要选择安装JDeveloper Studio。   
[<img style="background-image: none; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="Image(9)" border="0" alt="Image(9)" src="http://www.beansoft.biz/wp-content/uploads/2014/04/Image9_thumb.jpg" width="600" height="430" />](http://www.beansoft.biz/wp-content/uploads/2014/04/Image9.jpg)   
[<img style="background-image: none; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="Image(10)" border="0" alt="Image(10)" src="http://www.beansoft.biz/wp-content/uploads/2014/04/Image10_thumb.jpg" width="600" height="430" />](http://www.beansoft.biz/wp-content/uploads/2014/04/Image10.jpg)   
[<img style="background-image: none; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="Image(11)" border="0" alt="Image(11)" src="http://www.beansoft.biz/wp-content/uploads/2014/04/Image11_thumb.jpg" width="600" height="430" />](http://www.beansoft.biz/wp-content/uploads/2014/04/Image11.jpg)   
**（3）创建域（支持ADF）**   
[<img style="background-image: none; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="Image(12)" border="0" alt="Image(12)" src="http://www.beansoft.biz/wp-content/uploads/2014/04/Image12_thumb.jpg" width="780" height="559" />](http://www.beansoft.biz/wp-content/uploads/2014/04/Image12.jpg)   
[<img style="background-image: none; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="Image(13)" border="0" alt="Image(13)" src="http://www.beansoft.biz/wp-content/uploads/2014/04/Image13_thumb.jpg" width="780" height="559" />](http://www.beansoft.biz/wp-content/uploads/2014/04/Image13.jpg)   
[<img style="background-image: none; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="Image(14)" border="0" alt="Image(14)" src="http://www.beansoft.biz/wp-content/uploads/2014/04/Image14_thumb.jpg" width="658" height="142" />](http://www.beansoft.biz/wp-content/uploads/2014/04/Image14.jpg)   
注意：WLS 10.3.2以后，ADF 改称为JRF，因此要选择此项。   
[<img style="background-image: none; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="Image(15)" border="0" alt="Image(15)" src="http://www.beansoft.biz/wp-content/uploads/2014/04/Image15_thumb.jpg" width="780" height="559" />](http://www.beansoft.biz/wp-content/uploads/2014/04/Image15.jpg)   
对于生产环境，一般把ADF安装在Managed Server上。   
[<img style="background-image: none; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="Image(2)" border="0" alt="Image(2)" src="http://www.beansoft.biz/wp-content/uploads/2014/04/Image2_thumb.png" width="788" height="593" />](http://www.beansoft.biz/wp-content/uploads/2014/04/Image2.png)   
[<img style="background-image: none; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="Image(3)" border="0" alt="Image(3)" src="http://www.beansoft.biz/wp-content/uploads/2014/04/Image3_thumb.png" width="788" height="593" />](http://www.beansoft.biz/wp-content/uploads/2014/04/Image3.png)   
[<img style="background-image: none; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="Image(16)" border="0" alt="Image(16)" src="http://www.beansoft.biz/wp-content/uploads/2014/04/Image16_thumb.jpg" width="1115" height="368" />](http://www.beansoft.biz/wp-content/uploads/2014/04/Image16.jpg)   
**4. 安装方法二**   
该方法适用于未安装WebLogic Server 10gR3，适用于开发环境。   
JDeveloper 11g安装包已经包含一个WebLogic Server 10gR3，因此安装JDeveloper 即可。   
[<img style="background-image: none; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="Image(17)" border="0" alt="Image(17)" src="http://www.beansoft.biz/wp-content/uploads/2014/04/Image17_thumb.jpg" width="600" height="430" />](http://www.beansoft.biz/wp-content/uploads/2014/04/Image17.jpg)   
[<img style="background-image: none; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="Image(18)" border="0" alt="Image(18)" src="http://www.beansoft.biz/wp-content/uploads/2014/04/Image18_thumb.jpg" width="600" height="430" />](http://www.beansoft.biz/wp-content/uploads/2014/04/Image18.jpg)   
[<img style="background-image: none; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="Image(19)" border="0" alt="Image(19)" src="http://www.beansoft.biz/wp-content/uploads/2014/04/Image19_thumb.jpg" width="600" height="430" />](http://www.beansoft.biz/wp-content/uploads/2014/04/Image19.jpg)   
**5. 安装方法三 该方法适用于已经创建了ADF enabled的 Domain，只是为指定的WLS enable ADF，适用于生产环境**。   
注意，本方法通过Enterprise Manager 操作，因此创建Domain时，要先选择EM。   
[<img style="background-image: none; border-right-width: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="Image(4)" border="0" alt="Image(4)" src="http://www.beansoft.biz/wp-content/uploads/2014/04/Image4_thumb.png" width="661" height="438" />](http://www.beansoft.biz/wp-content/uploads/2014/04/Image4.png)   
参考文献：   
1. http://one-size-doesnt-fit-all.blogspot.com/2009/01/configuring-weblogic-server.html   
2. http://biemond.blogspot.com/2008/11/installing-adf-11g-runtime-on-weblogic.html   
3. http://blog.whitehorses.nl/2010/01/06/extending-your-weblogic-standalone-environment-with-adf-runtime-libraries/ 

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [WLS_003：图解安装 WebLogic 10gR3 （支持ADF Runtime）](http://www.beansoft.biz/2014/04/30/%e5%9b%be%e8%a7%a3%e5%ae%89%e8%a3%85-weblogic-10gr3-%ef%bc%88%e6%94%af%e6%8c%81adf-runtime%ef%bc%89/)