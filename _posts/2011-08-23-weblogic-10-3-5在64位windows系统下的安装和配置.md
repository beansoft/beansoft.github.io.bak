---
id: 2183
title: Weblogic 10.3.5在64位Windows系统下的安装和配置
date: 2011-08-23T23:04:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2183
permalink: '/2011/08/23/weblogic-10-3-5%e5%9c%a864%e4%bd%8dwindows%e7%b3%bb%e7%bb%9f%e4%b8%8b%e7%9a%84%e5%ae%89%e8%a3%85%e5%92%8c%e9%85%8d%e7%bd%ae/'
views:
  - "26149"
original_post_id:
  - "2183"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
<h3 style="MARGIN: auto 0cm">
  2011-08-23 Weblogic 10.3.5在64位Windows系统下的安装和配置
</h3>

<p style="LINE-HEIGHT: 19.2pt; MARGIN: 0cm 0cm 0pt">
  作者: BeanSoft 日期: 2011-8-23
</p>

<p style="LINE-HEIGHT: 19.2pt; MARGIN: 0cm 0cm 0pt">
  今天, 笔者将向大家介绍Oracle Weblogic 10.3.5 在 64位Windows环境下的安装. 本文内容稍加变动后也适用于Linux,Solaris,AIX,HPUX等系统下的安装过程(参考文末). 因为总是看到网上有很多朋友在询问同样的问题:BEA-000438: loading performance pack issue, 希望本文能对这个问题的解决有所帮助.
</p>

<p style="LINE-HEIGHT: 19.2pt; MARGIN: 0cm 0cm 0pt">
  1. 首先, 确保下载了正确版本的WebLogic安装程序, 此处为wls1035_generic.jar;
</p>

<p style="LINE-HEIGHT: 19.2pt; MARGIN: 0cm 0cm 0pt">
  2. 下载64位的Oracle Java JDK 6 (2011年8月23日的版本为jdk-6u27-windows-x64.exe <a href="http://www.oracle.com/technetwork/java/javase/downloads/jdk-6u27-download-440405.html">下载地址</a>)或Oracle JRockit JDK 28.1.4 for Java version 6 (jrockit-jdk1.6.0_26-R28.1.4-4.0.1-windows-x64.exe <a href="http://www.oracle.com/technetwork/middleware/jrockit/downloads/index.html">下载地址</a>), 如有可能, 请尽量在Windows/Linux平台下使用JRockit虚拟机;
</p>

<p style="LINE-HEIGHT: 19.2pt; MARGIN: 0cm 0cm 0pt">
  3. 通用的64位 Weblogic 安装程序本身并不绑定任何版本的64位 JVM, 因此请安装第二步下载到的Java安装程序.默认的安装路径(C:\Program Files)必须进行修改, 因为Weblogic和很多Java类库都不能<strong>很好</strong>的支持带有空格的目录名.请确保将JDK安装到不带任何空格的目录下(例如 C:\Java);
</p>

<p style="LINE-HEIGHT: 19.2pt; MARGIN: 0cm 0cm 0pt">
  4. 现在, 打开命令提示符窗口, 执行下列命令来安装64位Weblogic 10.3.5:
</p>

<p style="LINE-HEIGHT: 19.2pt; MARGIN: 0cm 0cm 0pt">
  java -D64 -jar wls1035_generic.jar (-D64 确保WebLogic安装选择64位JDK);
</p>

<p style="LINE-HEIGHT: 19.2pt; MARGIN: 0cm 0cm 0pt">
  java -D64 -jar wls1035_generic.jar -mode=console 控制台安装
</p>

<p style="LINE-HEIGHT: 19.2pt; MARGIN: 0cm 0cm 0pt">
  java -jar wls1034_generic.jar -mode=console -silent_xml=/path_to_silent.xml 静默安装
</p>

<p style="LINE-HEIGHT: 19.2pt; MARGIN: 0cm 0cm 0pt">
  更多信息参考: <a href="http://www.beansoft.biz/?p=1882" title="Permanent Link to Linux下Weblogic 11g jar格式安装包如何安装?"><strong>Linux</strong><strong>下</strong><strong>Weblogic 11g jar</strong><strong>格式安装包如何安装</strong><strong>?</strong></a>
</p>

<p style="LINE-HEIGHT: 19.2pt; MARGIN: 0cm 0cm 0pt">
  5. 跟随 Weblogic 10.3.5 安装过程中提示步骤进行 &#8211; 安装过程中将会提示选择WebLogic所使用的JDK, 请确保此时所用版本为64位JDK, 例如选择上文提到的目录C:\Java ;
</p>

<p style="LINE-HEIGHT: 19.2pt; MARGIN: 0cm 0cm 0pt">
  6. 现在创建域并启动服务器, 或许会发现如下提示的错误信息: <br /><Error> <Socket> <BEA-000438> <Unable to load performance pack. Using Java I/O instead. Please ensure that wlntio.dll is in: &#8216;C:\O <br />racle\fmwhome\wlserver_10.3\server\native\win\32;C:\Oracle\fmwhome\wlserver_10.3 <br />\server\bin;C:\WINDOWS\system32;C:\WINDOWS;C:\Oracle\fmwhome\wlserver_10.3\serve <br />r\native\win\32\;C:\Oracle\fmwhome\wlserver_10.3\server\bin;C:\Program~\Java\jdk <br />1.6.0_24\jre\bin;C:\\Java\jdk1.6.0_24\bin; &#8216; <br />7. 解决方法
</p>

<p style="LINE-HEIGHT: 19.2pt; MARGIN: 0cm 0cm 0pt">
  1) 进入如下目录: <<Weblogic_Home_Directory>>\wlserver_10.3\server\native\win\x64, 复制文件wlntio.dll 并将其粘贴到 C:\Java\bin 目录下 (假设JDK事先已安装至 C:\Java);
</p>

<p style="LINE-HEIGHT: 19.2pt; MARGIN: 0cm 0cm 0pt">
  2)或者修改系统的PATH变量使其包含<<Weblogic_Home_Directory>>\wlserver_10.3\server\native\win\x64, 此为推荐做法;
</p>

<p style="LINE-HEIGHT: 19.2pt; MARGIN: 0cm 0cm 0pt">
  8. 启动服务器后, 问题应消失并可在Thread Dump中看到Muxer相关线程.
</p>

<p style="LINE-HEIGHT: 19.2pt; MARGIN: 0cm 0cm 0pt">
  Linux/Unix下的解决方案:
</p>

<p style="LINE-HEIGHT: 19.2pt; MARGIN: 0cm 0cm 0pt">
  需找到对应目录下的文件libmuxer.so或者libmuxer.sl, 将其加入系统的PATH或者LD_LIBRARY_PATH环境变量, 并确保WebLogic进程的所有者用户对其有读和执行的权限.
</p>

<p style="LINE-HEIGHT: 19.2pt; MARGIN: 0cm 0cm 0pt">
  <p style="MARGIN: 0cm 0cm 0pt">
    <p style="MARGIN: 0cm 0cm 0pt">
      <p>
        转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2011/08/23/weblogic-10-3-5%e5%9c%a864%e4%bd%8dwindows%e7%b3%bb%e7%bb%9f%e4%b8%8b%e7%9a%84%e5%ae%89%e8%a3%85%e5%92%8c%e9%85%8d%e7%bd%ae/">Weblogic 10.3.5在64位Windows系统下的安装和配置</a>
      </p>