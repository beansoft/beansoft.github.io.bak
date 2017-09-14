---
id: 795
title: 'MyEclipse 6 Java 开发中文教程独家连载 &#8211; 第一章 安装配置开发环境'
date: 2010-09-09T20:14:08+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=795
permalink: '/2010/09/09/myeclipse-6-java-%e5%bc%80%e5%8f%91%e4%b8%ad%e6%96%87%e6%95%99%e7%a8%8b%e7%8b%ac%e5%ae%b6%e8%bf%9e%e8%bd%bd-%e7%ac%ac%e4%b8%80%e7%ab%a0-%e5%ae%89%e8%a3%85%e9%85%8d%e7%bd%ae%e5%bc%80%e5%8f%91/'
views:
  - "16237"
  - "16237"
original_post_id:
  - "795"
image: /wp-content/uploads/2012/09/clip_image002_thumb11.jpg
categories:
  - MyEclipse6中文教程
---
   <span style="font-family: &quot;Arial&quot;,&quot;sans-serif&quot;; font-size: 10.5pt; mso-bidi-font-family: &#39;Times New Roman&#39;; mso-font-kerning: 1.0pt; mso-ansi-language: en-us; mso-fareast-font-family: 宋体; mso-fareast-language: zh-cn; mso-bidi-language: ar-sa" lang="EN-US"></p> 

<p style="text-indent: 21pt; mso-char-indent-count: 2.0" class="MsoNormal">
  <strong><font color="#ff0000">如果您需要转载本书内容, 请与本站联系! Email: <a href="mailto:beansoft@126.com">beansoft@126.com</a></font></strong><strong><font color="#ff0000">.</font></strong>
</p>

<p style="text-indent: 21pt; mso-char-indent-count: 2.0" class="MsoNormal">
  <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">本章内容供你来了解</span><span lang="EN-US">Java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">和数据库软件的常见下载地址，安装和运行，当然也可以直接跳到</span><span lang="EN-US"><a href="#_1.7.2.1_ALL_in_ONE 版本的安装">1.7.2.1 ALL in ONE <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial" lang="EN-US"><span lang="EN-US">版本的安装</span></span></a></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">一节进行学习，暂时先不用关心这些细节的内容。</span><span lang="EN-US"> </span>
</p></p> </p> 

<p style="text-indent: 21pt; mso-char-indent-count: 2.0" class="MsoNormal">
  <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">如果是在</span><span lang="EN-US">Windows</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">下安装</span><span lang="EN-US">MyEclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，可以不用单独下载和配置</span><span lang="EN-US"> JDK</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，</span><span lang="EN-US">Eclipse 3.3, </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">您可以直接参考</span><span lang="EN-US">MyEclipse <a href="#_1.7.2.1_ALL_in_ONE 版本的安装">ALL in ONE <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial" lang="EN-US"><span lang="EN-US">版本的安装</span></span></a></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">说明。未加说明的情况下，本文的操作均在</span><span lang="EN-US">Windows XP</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">简体中文版操作系统下进行。</span><span lang="EN-US"> </span>
</p></p> </p> 

<p>
  <span lang="EN-US"> </p> 
  
  <p>
    </span>
  </p>
  
  <h2>
    <a name="_Toc201479537"><span lang="EN-US">1.1</span></a><span style="mso-bookmark: _toc201479537"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">系统需求</span></span><span lang="EN-US"> </p> 
    
    <p>
      </span></h2> 
      
      <p class="MsoNormal">
        <span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">如果只是安装</span><span lang="EN-US">JDK</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">和</span><span lang="EN-US">MySQL</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">等数据库，只需要</span><span lang="EN-US">256MB</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">内存的电脑就可以了。反过来，如果要安装并使用</span><span lang="EN-US">MyEclipse 6</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，那么建议电脑配置至少</span><span lang="EN-US">512MB</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">内存，推荐</span><chmetcnv unitname="g" sourcevalue="1" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on"><span lang="EN-US">1G</span></chmetcnv><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">或者更多内存，因为</span><span lang="EN-US">MyEclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">启动后经常会占用</span><span lang="EN-US">200</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">多</span><span lang="EN-US">MB</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的常驻内存。安装后所占据的空间有</span><span lang="EN-US">600 MB</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，因此建议磁盘上至少有</span><chmetcnv unitname="g" sourcevalue="1" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on"><span lang="EN-US">1G</span></chmetcnv><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">空闲空间。换句话说，做</span><span lang="EN-US">Java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">开发需要大量的内存和磁盘空间。</span><span lang="EN-US"> </span>
      </p>
    </p></p> 
    
    <h2>
      <a name="_Toc201479538"></a><a name="_JDK_的下载，安装和配置（可选）"></a><span style="mso-bookmark: _toc201479538"><span lang="EN-US">1.2 JDK </span></span><span style="mso-bookmark: _toc201479538"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的下载，安装和配置（可选）</span></span><span lang="EN-US"> </p> 
      
      <p>
        </span></h2> 
        
        <p style="text-indent: 21pt" class="MsoNormal">
          <b style="mso-bidi-font-weight: normal"><span style="font-family: 宋体; color: red; mso-ascii-font-family: arial; mso-hansi-font-family: arial">注意：</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">如果安装</span><span lang="EN-US">MyEclipse ALL In ONE</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">版本，因为它自带了</span><span lang="EN-US">JRE</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，不需要单独下载和安装</span><span lang="EN-US">JDK</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，也可以进行开发；但是因为</span><span lang="EN-US">JRE</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">不带</span><span lang="EN-US">Java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">类的源代码，因此不安装</span><span lang="EN-US">JDK</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">将无法看到</span><span lang="EN-US">JDK</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">类的源代码，但不影响项目的开发。</span><span lang="EN-US"> </span>
        </p>
      </p></p> 
      
      <h3>
        <a name="_Toc201479539"></a><chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False"><span style="mso-bookmark: _toc201479539"><span lang="EN-US">1.2.1</span></span></chsdate><span style="mso-bookmark: _toc201479539"><span lang="EN-US"> </span></span><span style="mso-bookmark: _toc201479539"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">下载</span><span lang="EN-US">JDK</span></span><span lang="EN-US"> </p> 
        
        <p>
          </span></h3> 
          
          <p style="text-indent: 21.1pt; mso-char-indent-count: 2.0" class="MsoNormal">
            <a name="_Toc201479540"><b style="mso-bidi-font-weight: normal"><span lang="EN-US">JDK</span></b><span lang="EN-US"> </span></a><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的全称是</span> <b style="mso-bidi-font-weight: normal"><span lang="EN-US">Java(TM) SE Development Kit</span></b></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，即</span><span lang="EN-US">Java</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">标准版（</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">Standard Edition</span></b></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">）开发工具包。这是</span><span lang="EN-US">Java</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">开发和运行的基本平台。换句话说所有用</span><span lang="EN-US">Java</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">语言编写的程序要运行都离不开它，而用它就可以编译</span><span lang="EN-US">Java</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">代码为类文件。</span><span lang="EN-US"> </span></span>
          </p>
        </p></p> 
        
        <p style="text-indent: 21.1pt; mso-char-indent-count: 2.0" class="MsoNormal">
          <span style="mso-bookmark: _toc201479540"><b style="mso-bidi-font-weight: normal"><span style="font-family: 宋体; color: red; mso-ascii-font-family: arial; mso-hansi-font-family: arial">注意：</span></b></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">不要下载</span><span lang="EN-US"> JRE</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">（</span><span lang="EN-US">Java Runtime Environment, Java</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">运行时环境），因为</span><span lang="EN-US"> JRE </span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">不包含</span><span lang="EN-US"> Java </span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">编译器和</span><span lang="EN-US">JDK</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">类的源码。</span><span lang="EN-US"> </span></span>
        </p></p> </p> 
        
        <p style="text-indent: 21pt; mso-char-indent-count: 2.0" class="MsoNormal">
          <span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">下载</span><span lang="EN-US">JDK</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">可以访问官方网站</span></span><a href="http://java.sun.com/javase/downloads/index.jsp"><span style="mso-bookmark: _toc201479540"><span lang="EN-US">http://java.sun.com/javase/downloads/index.jsp</span></span><span style="mso-bookmark: _toc201479540"></span></a><span style="mso-bookmark: _toc201479540"><span lang="EN-US"> </span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，一般来说下载最新版本即可，目前的稳定版本是</span><span lang="EN-US">JDK 6</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。打开下载页后，首先点击页面中的</span> <b style="mso-bidi-font-weight: normal"><span lang="EN-US">Download</span></b><span lang="EN-US"> </span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">按钮，如图</span><span lang="EN-US">1.1</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">所示。注意上方显示的版本是</span><span lang="EN-US">Java SE 6 Update 10 Beta</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">（即</span><span lang="EN-US">Java </span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">标准版</span><span lang="EN-US">6</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">更新</span><span lang="EN-US">10</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">测试版），因为</span><span lang="EN-US">Beta</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">版本一般来说会存在比较多的</span><span lang="EN-US">Bug</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，在这里除非是体验新版本，否则开发的时候不建议采用，尤其不建议作为正式服务器或者产品运行的时候来使用。因此，我们这里需要下载的是下方的稳定版本：</span><span lang="EN-US">JDK 6 Update 6</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">（</span><span lang="EN-US">JDK 6 </span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">更新</span><span lang="EN-US">6</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">）。下方的文字说明为：</span><span lang="EN-US">The Java SE Development Kit (JDK) includes the Java Runtime Environment (JRE) and command-line development tools that are useful for developing applets and applications</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">；这段话翻译过来就是：</span><span lang="EN-US">Java SE </span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">开发工具包（简称</span><span lang="EN-US">JDK</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">）包含了</span><span lang="EN-US">Java</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">运行时环境（</span><span lang="EN-US">JRE</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">）和对开发</span><span lang="EN-US">applets</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">（</span><span lang="EN-US">Java</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">小应用程序）和应用程序很有用的命令行工具。</span><span lang="EN-US"> </span></span>
        </p></p> </p> 
        
        <p style="text-align: center; text-indent: 21pt; mso-char-indent-count: 2.0" class="MsoNormal" align="center">
          <span style="mso-bookmark: _toc201479540"><span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0021.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image002" border="0" alt="clip_image002" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image002_thumb1.jpg" width="553" height="608" v:shapes="_x0000_i1025" /></a> </span></span>
        </p></p> </p> 
        
        <p style="text-align: center; text-indent: 21pt; mso-char-indent-count: 2.0" class="MsoNormal" align="center">
          <span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span><span lang="EN-US">1.1<span style="mso-spacerun: yes">&#160; </span></span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">在</span><span lang="EN-US">JDK </span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">下载页面点击</span> <b style="mso-bidi-font-weight: normal"><span lang="EN-US">Download</span></b></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">按钮</span><span lang="EN-US"> </span></span>
        </p></p> </p> 
        
        <p class="MsoNormal">
          <span style="mso-bookmark: _toc201479540"><span lang="EN-US"></span></span>
        </p>
        
        <p>
          &#160;
        </p></p> </p> 
        
        <p style="text-indent: 21pt" class="MsoNormal">
          <span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">随后看到的页面如图</span><span lang="EN-US">1.2</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">所示，在这里可以选择操作系统（</span><span lang="EN-US">Platform</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">）和语言（</span><span lang="EN-US">Language</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">），对于我们一般的开发来说，使用的是</span><span lang="EN-US">Windows</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，语言则选择</span><span lang="EN-US">Multi-language</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">（多国语言），然后选中复选框</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">I agree to the Java SE Development Kit 6 License Agreement</span></i></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">来接受许可协议，然后点击</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">Continue</span></b></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">按钮进入文件列表页面。如图</span><span lang="EN-US">1.3</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">所示。</span><span lang="EN-US"> </span></span>
        </p></p> </p> 
        
        <p style="text-indent: 21pt" class="MsoNormal">
          <span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">在这一页可以看到有两个版本的安装程序，点击超链接</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">jdk-6u6-windows-i586-p.exe</span></i></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">后就可以下载</span><span lang="EN-US">JDK </span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的安装文件了。两个文件中，第一个文件长度较小的名为</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">Windows Online Installation</span></b></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，是需要在线安装的，安装的时候电脑必须上网才可以，鉴于一般用户的电脑网速并不快，甚至根本无法上网，因此不推荐使用。而下面的那个文件</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">Windows Offline Installation</span></b></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">是</span><span lang="EN-US">Windows</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">完整离线安装包，支持多国语言的版本，个头比较大，一般用户点击链接下载这个版本的就可以了。点击下载链接后保存文件到硬盘上即可，例如这里我们下载到的文件名是</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">jdk-6u6-windows-i586-p.exe</span></b></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。</span><span lang="EN-US"> </span></span>
        </p></p> </p> 
        
        <p class="MsoNormal">
          <span style="mso-bookmark: _toc201479540"><span lang="EN-US"></span></span>
        </p>
        
        <p>
          &#160;
        </p></p> </p> 
        
        <p style="text-align: center; text-indent: 21pt; mso-char-indent-count: 2.0" class="MsoNormal" align="center">
          <span style="mso-bookmark: _toc201479540"><span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image004.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image004" border="0" alt="clip_image004" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image004_thumb.jpg" width="512" height="284" v:shapes="_x0000_i1026" /></a> </span></span>
        </p></p> </p> 
        
        <p style="text-align: center; text-indent: 21pt; mso-char-indent-count: 2.0" class="MsoNormal" align="center">
          <span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span><span lang="EN-US">1.2 </span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">选择操作系统并接受下载协议</span><span lang="EN-US"> </span></span>
        </p></p> </p> 
        
        <p style="text-align: center; text-indent: 21pt; mso-char-indent-count: 2.0" class="MsoNormal" align="center">
          <span style="mso-bookmark: _toc201479540"><span lang="EN-US"></span></span>
        </p>
        
        <p>
          &#160;
        </p></p> </p> 
        
        <p style="text-align: center; text-indent: 21pt; mso-char-indent-count: 2.0" class="MsoNormal" align="center">
          <span style="mso-bookmark: _toc201479540"><span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image006.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image006" border="0" alt="clip_image006" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image006_thumb.jpg" width="416" height="248" v:shapes="_x0000_i1027" /></a> </span></span>
        </p></p> </p> 
        
        <p style="text-align: center; text-indent: 21pt; mso-char-indent-count: 2.0" class="MsoNormal" align="center">
          <span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span><span lang="EN-US"> 1.3</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">选择要下载的文件</span><span lang="EN-US"> </span></span>
        </p></p> </p> 
        
        <p style="text-align: center; text-indent: 21pt; mso-char-indent-count: 2.0" class="MsoNormal" align="center">
          <span style="mso-bookmark: _toc201479540"><span lang="EN-US"></span></span>
        </p>
        
        <p>
          &#160;
        </p></p> </p> 
        
        <p style="text-indent: 21pt; mso-char-indent-count: 2.0" class="MsoNormal">
          <span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">另外</span><span lang="EN-US"> JDK </span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">支持多个主流操作系统和硬件平台的安装，</span> </span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">包括</span><span lang="EN-US">Windows</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，</span><span lang="EN-US">Linux</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，</span><span lang="EN-US">Solaris</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">这些是操作系统软件的版本。而每个平台又区分了针对不同的硬件环境的（主要是</span><span lang="EN-US">CPU</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的），</span><span lang="EN-US">x86</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">就是一般的家用电脑的</span><span lang="EN-US">32</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">位</span><span lang="EN-US">CPU</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，例如</span><span lang="EN-US">Intel</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">和</span><span lang="EN-US">AMD</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的；</span><span lang="EN-US">x64</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">则是</span><span lang="EN-US">64</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">位</span><span lang="EN-US">CPU</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，一般用在服务器上。因此，对于普通的开发用户来说，我们只要关注</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">Windows x86</span></b></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">版本的就可以了。而</span><span lang="EN-US">Linux </span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">下面的文件版本呢，又分为</span><span lang="EN-US">executable</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">（可执行）和</span><span lang="EN-US">self-extracting</span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">（自解压）两种安装类型，下载后不要忘了用命令</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">chmod +x xxx.bin</span></i></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">来给文件加执行权限后再安装。具体的细节限于篇幅暂时不讨论了。</span><span lang="EN-US"> </span></span>
        </p></p> </p> 
        
        <h3>
          <span style="mso-bookmark: _toc201479540"><chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False"><span lang="EN-US">1.2.2</span></chsdate><span lang="EN-US"> </span></span><span style="mso-bookmark: _toc201479540"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">安装</span><span lang="EN-US">JDK</span></span><span lang="EN-US"> </p> 
          
          <p>
            </span></h3> 
            
            <p style="text-indent: 21.75pt" class="MsoNormal">
              <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">双击下载后的带有</span> <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image008.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image008" border="0" alt="clip_image008" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image008_thumb.jpg" width="37" height="36" v:shapes="_x0000_i1028" /></a><span style="mso-spacerun: yes">&#160;</span></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图标的</span><span lang="EN-US">JDK</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">安装程序</span><span lang="EN-US">EXE</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">文件，接着就会使用</span><span lang="EN-US">Windows Installer</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">开始安装过程，如下图所示：</span><span lang="EN-US"> </span>
            </p>
          </p></p> 
          
          <p style="text-align: center; text-indent: 21.75pt" class="MsoNormal" align="center">
            <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image010.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image010" border="0" alt="clip_image010" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image010_thumb.jpg" width="386" height="155" v:shapes="_x0000_i1029" /></a> </span>
          </p></p> </p> 
          
          <p style="text-align: center; text-indent: 21.75pt" class="MsoNormal" align="center">
            <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span><span lang="EN-US">1.4 </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">启动</span><span lang="EN-US"> JDK </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">安装程序</span><span lang="EN-US"> </span>
          </p></p> </p> 
          
          <p style="text-indent: 21.75pt" class="MsoNormal">
            <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">如果这一过程失败，请下载并安装最新版本的</span><span lang="EN-US">Windows Installer</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">后再试，并检查电脑的</span><span lang="EN-US">Windows Installer</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">服务已经启动</span><span lang="EN-US">(</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">下载地址：</span><span lang="EN-US"><a href="http://www.microsoft.com/downloads/details.aspx?FamilyID=889482fc-5f56-4a38-b838-de776fd4138c&displaylang=zh-cn">http://www.microsoft.com/downloads/details.aspx?FamilyID=889482fc-5f56-4a38-b838-de776fd4138c&displaylang=zh-cn</a><b style="mso-bidi-font-weight: normal"> Windows Installer 3.1 Redistributable (v2)</b>)</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。接下来的安装界面是中文的，点击下一步或者继续按钮，当出现许可证协议对话框时点击<b style="mso-bidi-font-weight: normal">接受</b></span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">(A)></span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">按钮方可继续安装。这时候将会出现<b style="mso-bidi-font-weight: normal">自定义安装</b>对话框，如下图所示：</span><span lang="EN-US"> </span>
          </p></p> </p> 
          
          <p style="text-align: center; text-indent: 21.75pt" class="MsoNormal" align="center">
            <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image012.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image012" border="0" alt="clip_image012" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image012_thumb.jpg" width="504" height="386" v:shapes="_x0000_i1030" /></a> </span>
          </p></p> </p> 
          
          <p style="text-align: center; text-indent: 21.75pt" class="MsoNormal" align="center">
            <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span><span lang="EN-US">1.5</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">自定义安装对话框</span><span lang="EN-US"> </span>
          </p></p> </p> 
          
          <p style="text-indent: 21.75pt" class="MsoNormal">
            <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">在这个屏幕我们可以看到默认安装路径是到</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">c:\Program Files\Java\jdk1.x.x_xx</span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，然而，这个安装路径需要进行修改，点击<b style="mso-bidi-font-weight: normal">更改</b></span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">(A)…</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">按钮来修改</span><span lang="EN-US">JDK</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的安装目录，点击后输入类似于</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">C:\jdk<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">1.6.0</chsdate></span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">这样的不包含空格，也不包含中文路径的文件夹来安装。而这样的路径是不推荐的：</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">C:\Java</span></i><i style="mso-bidi-font-style: normal"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">学习</span><span lang="EN-US">\JDK 1.6</span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。之所以这样做是因为路径带空格后有时候会出现不必要的问题，导致某些</span><span lang="EN-US">Java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">程序运行失败，也会在以后设置</span><span lang="EN-US">PATH</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">和</span><span lang="EN-US">CLASSPATH</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">时出现一些问题。现在你需要记下来安装的路径例如</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">C:\jdk1.6.0</span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，然后接着点<b style="mso-bidi-font-weight: normal">下一步</b>按钮等待片刻就可以完成安装了。</span><span lang="EN-US"> </span>
          </p></p> </p> 
          
          <h3>
            <a name="_Toc201479541"></a><chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False"><span style="mso-bookmark: _toc201479541"><span lang="EN-US">1.2.3</span></span></chsdate><span style="mso-bookmark: _toc201479541"><span lang="EN-US"> </span></span><span style="mso-bookmark: _toc201479541"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">配置环境变量（可选）</span></span><span lang="EN-US"> </p> 
            
            <p>
              </span></h3> 
              
              <p class="MsoNormal">
                <span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">这一步呢，也不是必须的，如果打算使用</span><span lang="EN-US">MyEclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">来进行开发，而不是手工编译代码，可以完全忽略这一节的内容。</span><span lang="EN-US"> </span>
              </p>
            </p></p> 
            
            <p style="text-indent: 21.75pt" class="MsoNormal">
              <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">第一个需要配置的环境变量是</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">JAVA_HOME</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。在<b style="mso-bidi-font-weight: normal">我的电脑</b>上点击右键</span><span lang="EN-US">, </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">选择</span> <b style="mso-bidi-font-weight: normal"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">属性</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，在弹出的对话框中选择<b style="mso-bidi-font-weight: normal">高级</b>标签，然后点击<b style="mso-bidi-font-weight: normal">环境变量</b>按钮</span><span lang="EN-US">, </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">在出现的<b style="mso-bidi-font-weight: normal">环境变量</b>对话框的<b style="mso-bidi-font-weight: normal">系统变量</b></span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">(S)</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">栏目中点击<b style="mso-bidi-font-weight: normal">新建</b>按钮</span><span lang="EN-US">, </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">出现新建系统环境变量的对话框</span><span lang="EN-US">, </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">输入变量名为</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">JAVA_HOME</span></i><span lang="EN-US">, </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">值为</span><span lang="EN-US"> JDK </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">安装目录，例如：</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">C:\JDK<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">1.6.0</chsdate></span></i><span lang="EN-US">(</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">例如</span><span lang="EN-US">Tomcat</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">需要这个环境变量来查找</span><span lang="EN-US"> JDK)</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。</span> <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">如下图所示：</span><span lang="EN-US"> </span>
            </p></p> </p> 
            
            <p style="text-align: center; text-indent: 21.75pt" class="MsoNormal" align="center">
              <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image014.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image014" border="0" alt="clip_image014" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image014_thumb.jpg" width="331" height="391" v:shapes="_x0000_i1031" /></a> </span>
            </p></p> </p> 
            
            <p style="text-align: center; text-indent: 21.75pt" class="MsoNormal" align="center">
              <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image016.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image016" border="0" alt="clip_image016" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image016_thumb.jpg" width="418" height="495" v:shapes="_x0000_i1032" /></a> </span>
            </p></p> </p> 
            
            <p style="text-align: center; text-indent: 21.75pt" class="MsoNormal" align="center">
              <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span><span lang="EN-US">1.6 </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">新建系统变量</span><span lang="EN-US"> </span>
            </p></p> </p> 
            
            <p style="text-indent: 21.75pt" class="MsoNormal">
              <span lang="EN-US"><span style="mso-spacerun: yes">&#160;&#160;&#160; </span></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">接下来用类似的方法新建环境变量</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">CLASSPATH</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，取值为</span><span lang="EN-US"> .</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">（<b style="mso-bidi-font-weight: normal"><span style="color: red">注意：</span></b>是英文半角的字符点，表示当前目录），这个变量用来供</span><span lang="EN-US">Java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">虚拟机查找要加载的类。接下来需要把</span><span lang="EN-US">JDK</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的应用程序路径添加到系统的</span><span lang="EN-US">Path</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">变量中，点击滚动条找到列表中名为</span><span lang="EN-US">Path</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的变量，点击</span><span lang="EN-US">”</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">编辑</span><span lang="EN-US">(I)”</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">按钮，即可修改</span><span lang="EN-US">PATH</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的变量值。一般来说我们只需要在开头加</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">%JAVA_HOME%\bin;</span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">（注意不要用中文全角的；），然后点击两次<b style="mso-bidi-font-weight: normal">确定</b>按钮即可。如下图所示：</span><span lang="EN-US"> </span>
            </p></p> </p> 
            
            <p style="text-align: center; text-indent: 21.75pt" class="MsoNormal" align="center">
              <span style="font-family: 宋体; color: black; font-size: 10pt; mso-bidi-font-family: 宋体; mso-font-kerning: 0pt" lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image018.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image018" border="0" alt="clip_image018" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image018_thumb.jpg" width="347" height="139" v:shapes="_x0000_i1033" /></a> </span>
            </p></p> </p> 
            
            <p style="text-align: center; text-indent: 21.75pt" class="MsoNormal" align="center">
              <span style="font-family: 宋体; color: black; font-size: 10pt; mso-bidi-font-family: 宋体; mso-font-kerning: 0pt">图<span lang="EN-US">1.7 </span>修改<span lang="EN-US">Path</span>系统变量<span lang="EN-US"> </span></span>
            </p></p> </p> 
            
            <p style="text-indent: 21.75pt" class="MsoNormal">
              <b style="mso-bidi-font-weight: normal"><span style="font-family: 宋体; color: red; mso-ascii-font-family: arial; mso-hansi-font-family: arial">注意：</span></b><span style="font-family: 宋体; color: black; mso-bidi-font-family: 宋体; mso-font-kerning: 0pt">用户变量和系统变量的区别是用户变量只对<span lang="EN-US">Windows</span>的当前登录用户可用，而系统变量则是对所有的用户都有影响。<span lang="EN-US"> </span></span>
            </p></p> </p> 
            
            <p style="text-indent: 21.75pt" class="MsoNormal">
              <span style="font-family: 宋体; color: black; mso-bidi-font-family: 宋体; mso-font-kerning: 0pt">当这些变量设置完毕后，就可以在命令行里面检查是否设置成功。点击<span lang="EN-US">Windows</span>的<b style="mso-bidi-font-weight: normal">开始</b>按钮，选择<b style="mso-bidi-font-weight: normal">运行<span lang="EN-US">(R)&#8230;</span></b><span lang="EN-US">,</span>输入<i style="mso-bidi-font-style: normal"><span lang="EN-US">CMD</span></i>后按下回车，这时候会出现命令行窗口。输入<i style="mso-bidi-font-style: normal"><span lang="EN-US">javac</span></i>并按下回车（<span lang="EN-US">Enter</span>）键，如果能看到如下的输出，则环境变量已经配置成功：<span lang="EN-US"> </span></span>
            </p></p> </p> 
            
            <table style="width: 423pt; border-collapse: collapse; background: black; margin-left: 5.4pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt" class="MsoNormalTable" border="0" cellspacing="0" cellpadding="0" width="564">
              <tr style="height: 27.15pt; mso-yfti-irow: 0; mso-yfti-firstrow: yes; mso-yfti-lastrow: yes">
                <td style="padding-bottom: 0cm; padding-left: 5.4pt; width: 423pt; padding-right: 5.4pt; height: 27.15pt; padding-top: 0cm" valign="top" width="564">
                  <p class="MsoNormal">
                    <span style="font-family: 宋体; color: white; font-size: 10pt; mso-bidi-font-family: 宋体; mso-font-kerning: 0pt" lang="EN-US">C:\Documents and Settings\BeanSoft>javac </span>
                  </p></p> </p> 
                  
                  <p class="MsoNormal">
                    <span style="font-family: 宋体; color: white; font-size: 10pt; mso-bidi-font-family: 宋体; mso-font-kerning: 0pt">用法：<span lang="EN-US">javac <</span>选项<span lang="EN-US">> <</span>源文件<span lang="EN-US">> </span></span>
                  </p></p> </p> 
                  
                  <p class="MsoNormal">
                    <span style="font-family: 宋体; color: white; font-size: 10pt; mso-bidi-font-family: 宋体; mso-font-kerning: 0pt">其中，可能的选项包括：<span lang="EN-US"> </span></span>
                  </p></p> </p> 
                  
                  <p class="MsoNormal">
                    <span style="font-family: 宋体; color: white; font-size: 10pt; mso-bidi-font-family: 宋体; mso-font-kerning: 0pt" lang="EN-US"><span style="mso-spacerun: yes">&#160; </span>-g<span style="mso-spacerun: yes">&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; </span></span><span style="font-family: 宋体; color: white; font-size: 10pt; mso-bidi-font-family: 宋体; mso-font-kerning: 0pt">生成所有调试信息<span lang="EN-US"> </span></span>
                  </p></p> </p> 
                  
                  <p class="MsoNormal">
                    <span style="font-family: 宋体; color: white; font-size: 10pt; mso-bidi-font-family: 宋体; mso-font-kerning: 0pt" lang="EN-US"><span style="mso-spacerun: yes">&#160; </span>-g:none<span style="mso-spacerun: yes">&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; </span></span><span style="font-family: 宋体; color: white; font-size: 10pt; mso-bidi-font-family: 宋体; mso-font-kerning: 0pt">不生成任何调试信息<span lang="EN-US"> </span></span>
                  </p></p> </p> 
                  
                  <p class="MsoNormal">
                    <span style="font-family: 宋体; color: white; font-size: 10pt; mso-bidi-font-family: 宋体; mso-font-kerning: 0pt" lang="EN-US"><span style="mso-spacerun: yes">&#160; </span>-g:{lines,vars,source}<span style="mso-spacerun: yes">&#160;&#160;&#160;&#160; </span></span><span style="font-family: 宋体; color: white; font-size: 10pt; mso-bidi-font-family: 宋体; mso-font-kerning: 0pt">只生成某些调试信息<span lang="EN-US"> </span></span>
                  </p></p> </p> 
                  
                  <p class="MsoNormal">
                    <span style="font-family: 宋体; color: white; font-size: 10pt; mso-bidi-font-family: 宋体; mso-font-kerning: 0pt" lang="EN-US"><span style="mso-spacerun: yes">&#160; </span>-nowarn<span style="mso-spacerun: yes">&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; </span></span><span style="font-family: 宋体; color: white; font-size: 10pt; mso-bidi-font-family: 宋体; mso-font-kerning: 0pt">不生成任何警告<span lang="EN-US"> </span></span>
                  </p></p> </p> 
                  
                  <p class="MsoNormal">
                    <span style="font-family: 宋体; color: white; font-size: 10pt; mso-bidi-font-family: 宋体; mso-font-kerning: 0pt" lang="EN-US"><span style="mso-spacerun: yes">&#160; </span>-verbose<span style="mso-spacerun: yes">&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; </span></span><span style="font-family: 宋体; color: white; font-size: 10pt; mso-bidi-font-family: 宋体; mso-font-kerning: 0pt">输出有关编译器正在执行的操作的消息<span lang="EN-US"> </span></span>
                  </p></p> </p> 
                  
                  <p class="MsoNormal">
                    <span style="font-family: 宋体; color: white; font-size: 10pt; mso-bidi-font-family: 宋体; mso-font-kerning: 0pt" lang="EN-US"><span style="mso-spacerun: yes">&#160; </span>-deprecation<span style="mso-spacerun: yes">&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; </span></span><span style="font-family: 宋体; color: white; font-size: 10pt; mso-bidi-font-family: 宋体; mso-font-kerning: 0pt">输出使用已过时的<span lang="EN-US"> API </span>的源位置<span lang="EN-US"> </span></span>
                  </p></p> </p> 
                  
                  <p class="MsoNormal">
                    <span style="font-family: 宋体; color: white; font-size: 10pt; mso-bidi-font-family: 宋体; mso-font-kerning: 0pt" lang="EN-US"><span style="mso-spacerun: yes">&#160; </span>-classpath <</span><span style="font-family: 宋体; color: white; font-size: 10pt; mso-bidi-font-family: 宋体; mso-font-kerning: 0pt">路径<span lang="EN-US">><span style="mso-spacerun: yes">&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; </span></span>指定查找用户类文件和注释处理程序的位置<span lang="EN-US"> </span></span>
                  </p></p> </p> 
                  
                  <p class="MsoNormal">
                    <span style="font-family: 宋体; color: white; font-size: 10pt; mso-bidi-font-family: 宋体; mso-font-kerning: 0pt" lang="EN-US"><span style="mso-spacerun: yes">&#160; </span>-cp <</span><span style="font-family: 宋体; color: white; font-size: 10pt; mso-bidi-font-family: 宋体; mso-font-kerning: 0pt">路径<span lang="EN-US">><span style="mso-spacerun: yes">&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; </span></span>指定查找用户类文件和注释处理程序的位置<span lang="EN-US"> </span></span>
                  </p></p> </p> 
                  
                  <p class="MsoNormal">
                    <span style="font-family: 宋体; color: white; font-size: 10pt; mso-bidi-font-family: 宋体; mso-font-kerning: 0pt" lang="EN-US">&#8230; </span>
                  </p></p> </p>
                </td>
              </tr>
            </table>
            
            <p style="text-align: center; text-indent: 21.75pt" class="MsoNormal" align="center">
              <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span><span lang="EN-US">1.8 </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">配置成功后</span><span lang="EN-US">javac</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">命令的输出</span><span lang="EN-US"> </span>
            </p></p> </p> 
            
            <p style="text-indent: 21.75pt" class="MsoNormal">
              <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">反过来如果发现输出</span><span lang="EN-US"> </span>
            </p></p> </p> 
            
            <table style="border-bottom: medium none; border-left: medium none; border-collapse: collapse; border-top: medium none; border-right: medium none; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-border-alt: solid windowtext .5pt; mso-yfti-tbllook: 480" class="MsoTableGrid" border="1" cellspacing="0" cellpadding="0">
              <tr style="mso-yfti-irow: 0; mso-yfti-firstrow: yes; mso-yfti-lastrow: yes">
                <td style="border-bottom: windowtext 1pt solid; border-left: windowtext 1pt solid; padding-bottom: 0cm; padding-left: 5.4pt; width: 426.1pt; padding-right: 5.4pt; background: black; border-top: windowtext 1pt solid; border-right: windowtext 1pt solid; padding-top: 0cm; mso-border-alt: solid windowtext .5pt" valign="top" width="568">
                  <p class="MsoNormal">
                    <font color="#ffffff"><span lang="EN-US">&#8216;javac&#8217; </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">不是内部或外部命令，也不是可运行的程序或批处理文件。</span><span lang="EN-US"> </span></font>
                  </p></p> </p>
                </td>
              </tr>
            </table>
            
            <p style="text-indent: 21.75pt" class="MsoNormal">
              <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">这样的输出信息，则说明环境变量配置失败了，请仔细检查设置的步骤。</span><span lang="EN-US"> </span>
            </p></p> </p> 
            
            <p style="text-indent: 21.75pt" class="MsoNormal">
              <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">这之后你就可以用记事本来编写</span><span lang="EN-US">Java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">文件然后用命令行的方式来编译和运行了。</span><span lang="EN-US"> </span>
            </p></p> </p> 
            
            <h3>
              <a name="_Toc201479542"></a><chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False"><span style="mso-bookmark: _toc201479542"><span lang="EN-US">1.2.4</span></span></chsdate><span style="mso-bookmark: _toc201479542"><span lang="EN-US"> JDK 6 </span></span><span style="mso-bookmark: _toc201479542"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">中文文档下载地址</span><span lang="EN-US">(ZIP,HTML,CHM)</span></span><span style="mso-bookmark: _toc201479542"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">（可选）</span></span><span lang="EN-US"> </p> 
              
              <p>
                </span></h3> 
                
                <p style="text-indent: 21pt" class="MsoNormal">
                  <span lang="EN-US">JDK </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的中文</span><span lang="EN-US">API</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">文档有助于理解和学习</span><span lang="EN-US">Java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">语言的基础，但是从长远看还是希望读者能逐渐熟悉阅读英文的</span><span lang="EN-US">Javadoc</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。下载</span><span lang="EN-US">CHM</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">格式就可以了，阅读起来比较方便，还可以搜索。</span><span lang="EN-US"> </span>
                </p>
              </p></p> 
              
              <p style="text-indent: 21pt" class="MsoNormal">
                <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">目前在</span><span lang="EN-US"> http://developers.sun.com.cn </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">已正式宣布发布</span><span lang="EN-US">Java SE 6 API </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">中文版。</span><span lang="EN-US"> </span>
              </p></p> </p> 
              
              <p style="text-indent: 21pt" class="MsoNormal">
                <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">大家也可以从以下网址下载</span><span lang="EN-US">: </span>
              </p></p> </p> 
              
              <p style="text-indent: 21pt" class="MsoNormal">
                <span lang="EN-US">* HTML </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">格式</span><span lang="EN-US"> ( <a href="http://download.java.net/jdk/jdk-api-localizations/jdk-api-zh-cn/publish/1.6.0/html/zh_CN/api/index.html">http://download.java.net/jdk/jdk-api-localizations/jdk-api-zh-cn/publish/1.6.0/html/zh_CN/api/index.html</a> <span style="mso-spacerun: yes">&#160;</span><span style="mso-spacerun: yes">&#160;</span>) </span>
              </p></p> </p> 
              
              <p style="text-indent: 21pt" class="MsoNormal">
                <span style="mso-ansi-language: de" lang="DE">* zip </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">格式</span><span style="mso-ansi-language: de" lang="DE"> ( </span><span lang="EN-US"><a href="http://download.java.net/jdk/jdk-api-localizations/jdk-api-zh-cn/publish/1.6.0/html_zh_CN.zip"><span style="mso-ansi-language: de" lang="DE">http://download.java.net/jdk/jdk-api-localizations/jdk-api-zh-cn/publish/1.6.0/html_zh_CN.zip</span></a></span><span style="mso-ansi-language: de" lang="EN-US"> </span><span style="mso-ansi-language: de" lang="DE"><span style="mso-spacerun: yes">&#160; </span>) </span>
              </p></p> </p> 
              
              <p style="text-indent: 21pt" class="MsoNormal">
                <span style="mso-ansi-language: de" lang="DE">* CHM </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">格式</span><span style="mso-ansi-language: de" lang="DE"> ( </span><span lang="EN-US"><a href="http://download.java.net/jdk/jdk-api-localizations/jdk-api-zh-cn/publish/1.6.0/chm/JDK_API_1_6_zh_CN.CHM"><span style="mso-ansi-language: de" lang="DE">http://download.java.net/jdk/jdk-api-localizations/jdk-api-zh-cn/publish/1.6.0/chm/JDK_API_1_6_zh_CN.CHM</span></a></span><span style="mso-ansi-language: de" lang="EN-US"> </span><span style="mso-ansi-language: de" lang="DE"><span style="mso-spacerun: yes">&#160; </span>) </span>
              </p></p> </p> 
              
              <p style="text-indent: 21pt" class="MsoNormal">
                <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">官方论坛地址（</span><span lang="EN-US">Sun</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">中国社区）：</span><span lang="EN-US"> </span>
              </p></p> </p> 
              
              <p style="text-indent: 21pt" class="MsoNormal">
                <span lang="EN-US"><a href="http://gceclub.sun.com.cn/NASApp/sme/jive/thread.jsp?forum=35&thread=44422">http://gceclub.sun.com.cn/NASApp/sme/jive/thread.jsp?forum=35&thread=44422</a> </span>
              </p></p> </p> 
              
              <h2>
                <a name="_Toc201479543"><span lang="EN-US">1.3 Tomcat</span></a><span style="mso-bookmark: _toc201479543"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">服务器的下载，安装和运行</span><span lang="EN-US">(</span></span><span style="mso-bookmark: _toc201479543"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">可选</span><span lang="EN-US">)</span></span><span lang="EN-US"> </p> 
                
                <p>
                  </span></h2> 
                  
                  <p style="text-indent: 21pt; mso-char-indent-count: 2.0" class="MsoNormal">
                    <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">因为</span><span lang="EN-US">MyEclipse 6</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">已经内置了一个简易的</span><span lang="EN-US">Tomcat 6(MyEclipse Tomcat)</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，所以本节内容为可选操作，但是强烈推荐了解本节内容。</span><span lang="EN-US"> </span>
                  </p>
                </p></p> 
                
                <p style="text-indent: 21pt; mso-char-indent-count: 2.0" class="MsoNormal">
                  <span lang="EN-US">Tomcat</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">是一款开源免费的</span><span lang="EN-US">JSP</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">服务器，可以在</span> <span lang="EN-US"><a href="http://tomcat.apache.org/">http://tomcat.apache.org/</a> </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">下载并安装</span><span lang="EN-US"> Tomcat 5 </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">或者</span> <span lang="EN-US">6</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。</span><span lang="EN-US"> </span>
                </p></p> </p> 
                
                <p style="text-align: center" class="MsoNormal" align="center">
                  <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image020.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image020" border="0" alt="clip_image020" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image020_thumb.jpg" width="554" height="272" v:shapes="_x0000_i1034" /></a> </span>
                </p></p> </p> 
                
                <p style="text-align: center" class="MsoNormal" align="center">
                  <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span><span lang="EN-US">1.9 </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">下载</span><span lang="EN-US">Tomcat </span>
                </p></p> </p> 
                
                <p class="MsoNormal">
                  <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">建议下载压缩包版本（文件名是</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">apache-tomcat-<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">6.0.14</chsdate>.zip</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">），而不是</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">Windows Service Installer</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的</span><span lang="EN-US">EXE</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">安装文件。</span> <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">解压缩到磁盘目录</span><span lang="EN-US">, </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">记下安装路径例如</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">c:\apache-tomcat-<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">6.0.14</chsdate></span></i><span lang="EN-US">, </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">和</span><span lang="EN-US">JDK</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的安装一样，为了避免日后产生错误，解压缩的路径不要带有空格，如</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">Program Files</span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。用解压缩工具来解压缩下载下来的</span><span lang="EN-US">ZIP</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">格式的压缩包的时候（例如</span><span lang="EN-US">WinRAR</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">）千万不要解压缩成了</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">c:\apache-tomcat-6.0.14\apache-tomcat-6.0.14</span></i><span lang="EN-US"> </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">这样的安装路径。</span><span lang="EN-US"> </span>
                </p></p> </p> 
                
                <p style="text-indent: 21.75pt" class="MsoNormal">
                  <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">在</span><span lang="EN-US"> Windows </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">下面不需要设置</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">CATALINA_HOME</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">这个变量也可以运行</span><span lang="EN-US">Tomcat</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，如果你配置了这个变量，那么你的电脑上将永远只能启动设置了</span><span lang="EN-US">CATALINA_HOME</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的那个</span><span lang="EN-US">Tomcat</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，换句话说如果你想多个</span><span lang="EN-US">Tomcat</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">版本并存，就不能设置</span><span lang="EN-US">CATALINA_HOME</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。而使用</span><span lang="EN-US">MyEclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">进行开发的时候，也不需要这个变量。如果你想设置，就新建环境变量，名为</span><span lang="EN-US">CATALINA_HOME</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，取值为</span><span lang="EN-US">Tomcat</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的安装目录例如</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">c:\apache-tomcat-<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">6.0.14</chsdate></span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。</span><span lang="EN-US"> </span>
                </p></p> </p> 
                
                <p style="text-indent: 21.75pt" class="MsoNormal">
                  <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">进入</span><span lang="EN-US">Tomcat</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">安装目录下的</span><span lang="EN-US">bin</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">子目录，可以看到</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">startup.bat</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">和</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">shutdown.bat</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。双击</span><span lang="EN-US">starup.bat</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">启动</span><span lang="EN-US">Tomcat</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">服务器，将产生如下的输出信息：</span><span lang="EN-US"> </span>
                </p></p> </p> 
                
                <table style="width: 459.85pt; border-collapse: collapse; background: black; margin-left: 5.4pt; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt" class="MsoNormalTable" border="0" cellspacing="0" cellpadding="0" width="613">
                  <tr style="height: 27.15pt; mso-yfti-irow: 0; mso-yfti-firstrow: yes; mso-yfti-lastrow: yes">
                    <td style="padding-bottom: 0cm; padding-left: 5.4pt; width: 459.85pt; padding-right: 5.4pt; height: 27.15pt; padding-top: 0cm" valign="top" width="613">
                      <p style="text-indent: 21.75pt" class="MsoNormal">
                        <font color="#ffffff"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">信息</span><span lang="EN-US">: The Apache Tomcat Native library which allows optimal performance in produ </span></font>
                      </p></p> </p> 
                      
                      <p style="text-indent: 21.75pt" class="MsoNormal">
                        <span lang="EN-US"><font color="#ffffff">ction environments was not found on the java.library.path: D:\Java\jdk<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">1.7.0</chsdate>\bin; </font></span>
                      </p></p> </p> 
                      
                      <p style="text-indent: 21.75pt" class="MsoNormal">
                        <span lang="EN-US"><font color="#ffffff">.;C:\WINXP\Sun\Java\bin;C:\WINXP\system32;C:\WINXP;%JAVA_HOME%\bin;C:\oracle\ora </font></span>
                      </p></p> </p> 
                      
                      <p style="text-indent: 21.75pt" class="MsoNormal">
                        <span lang="EN-US"><font color="#ffffff">92\bin;C:\WINXP\system32;C:\WINXP;C:\WINXP\System32\Wbem;%JAVA_HOME%\bin;E:\_Por </font></span>
                      </p></p> </p> 
                      
                      <p style="text-indent: 21.75pt" class="MsoNormal">
                        <span lang="EN-US"><font color="#ffffff">tableJava\jdk<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">1.6.0</chsdate>\bin;C:\oracle\ora92\bin;C:\WINXP\system32;C:\WINXP;C:\WINXP\S </font></span>
                      </p></p> </p> 
                      
                      <p style="text-indent: 21.75pt" class="MsoNormal">
                        <span lang="EN-US"><font color="#ffffff">ystem32\Wbem;E:\_PortableJava\jdk<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">1.6.0</chsdate>\bin;C:\oracle\ora92\bin;C:\WINXP\system32 </font></span>
                      </p></p> </p> 
                      
                      <p style="text-indent: 21.75pt" class="MsoNormal">
                        <span lang="EN-US"><font color="#ffffff">;C:\WINXP;C:\WINXP\System32\Wbem;E:\_PortableJava\apache-ant-<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">1.6.2</chsdate>\bin;E:\_Porta </font></span>
                      </p></p> </p> 
                      
                      <p style="text-indent: 21.75pt" class="MsoNormal">
                        <span lang="EN-US"><font color="#ffffff">bleApps\SSH </font></span>
                      </p></p> </p> 
                      
                      <p style="text-indent: 21.75pt" class="MsoNormal">
                        <span lang="EN-US"><font color="#ffffff">2007-12-4 15:22:08 org.apache.coyote.http11.Http11Protocol init </font></span>
                      </p></p> </p> 
                      
                      <p style="text-indent: 21.75pt" class="MsoNormal">
                        <font color="#ffffff"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">信息</span><span lang="EN-US">: Initializing Coyote HTTP/1.1 on http-8080 </span></font>
                      </p></p> </p> 
                      
                      <p style="text-indent: 21.75pt" class="MsoNormal">
                        <span style="mso-ansi-language: es" lang="ES"><font color="#ffffff">2007-12-4 15:22:08 org.apache.catalina.startup.Catalina load </font></span>
                      </p></p> </p> 
                      
                      <p style="text-indent: 21.75pt" class="MsoNormal">
                        <font color="#ffffff"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">信息</span><span lang="EN-US">: Initialization processed in 2049 ms </span></font>
                      </p></p> </p> 
                      
                      <p style="text-indent: 21.75pt" class="MsoNormal">
                        <span lang="EN-US"><font color="#ffffff">2007-12-4 15:22:08 org.apache.catalina.core.StandardService start </font></span>
                      </p></p> </p> 
                      
                      <p style="text-indent: 21.75pt" class="MsoNormal">
                        <font color="#ffffff"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">信息</span><span lang="EN-US">: Starting service Catalina </span></font>
                      </p></p> </p> 
                      
                      <p style="text-indent: 21.75pt" class="MsoNormal">
                        <span lang="EN-US"><font color="#ffffff">2007-12-4 15:22:08 org.apache.catalina.core.StandardEngine start </font></span>
                      </p></p> </p> 
                      
                      <p style="text-indent: 21.75pt" class="MsoNormal">
                        <font color="#ffffff"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">信息</span><span lang="EN-US">: Starting Servlet Engine: Apache Tomcat/<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">6.0.14</chsdate> </span></font>
                      </p></p> </p> 
                      
                      <p style="text-indent: 21.75pt" class="MsoNormal">
                        <span lang="EN-US"><font color="#ffffff">2007-12-4 15:22:13 org.apache.coyote.http11.Http11Protocol start </font></span>
                      </p></p> </p> 
                      
                      <p style="text-indent: 21.75pt" class="MsoNormal">
                        <font color="#ffffff"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">信息</span><span lang="EN-US">: Starting Coyote HTTP/1.1 on http-8080 </span></font>
                      </p></p> </p> 
                      
                      <p style="text-indent: 21.75pt" class="MsoNormal">
                        <span lang="EN-US"><font color="#ffffff">2007-12-4 15:22:13 org.apache.jk.common.ChannelSocket init </font></span>
                      </p></p> </p> 
                      
                      <p style="text-indent: 21.75pt" class="MsoNormal">
                        <font color="#ffffff"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">信息</span><span lang="EN-US">: JK: ajp13 listening on /<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">0.0.0</chsdate>.0:8009 </span></font>
                      </p></p> </p> 
                      
                      <p style="text-indent: 21.75pt" class="MsoNormal">
                        <span lang="EN-US"><font color="#ffffff">2007-12-4 15:22:13 org.apache.jk.server.JkMain start </font></span>
                      </p></p> </p> 
                      
                      <p style="text-indent: 21.75pt" class="MsoNormal">
                        <font color="#ffffff"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">信息</span><span lang="EN-US">: Jk running ID=0 time=0/46<span style="mso-spacerun: yes">&#160; </span>config=null </span></font>
                      </p></p> </p> 
                      
                      <p style="text-indent: 21.75pt" class="MsoNormal">
                        <span lang="EN-US"><font color="#ffffff">2007-12-4 15:22:13 org.apache.catalina.startup.Catalina start </font></span>
                      </p></p> </p> 
                      
                      <p style="text-indent: 21.75pt" class="MsoNormal">
                        <font color="#ffffff"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">信息</span><span lang="EN-US">: Server startup in 4859 ms </span></font>
                      </p></p> </p> 
                      
                      <p class="MsoNormal">
                        <span style="font-family: 宋体; color: white; font-size: 10pt; mso-bidi-font-family: 宋体; mso-font-kerning: 0pt" lang="EN-US"></span>
                      </p>
                      
                      <p>
                        &#160;
                      </p></p>
                    </td>
                  </tr>
                </table>
                
                <p style="text-align: center; text-indent: 21.75pt" class="MsoNormal" align="center">
                  <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span><span lang="EN-US">1.10 </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">启动</span><span lang="EN-US">Tomcat</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">服务器</span><span lang="EN-US"> </span>
                </p></p> </p> 
                
                <p style="text-indent: 21.75pt" class="MsoNormal">
                  <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">当看到出现<i style="mso-bidi-font-style: normal">信息</i></span><i style="mso-bidi-font-style: normal"><span lang="EN-US">: Server startup in 4859 ms</span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的输出后，</span><span lang="EN-US">Tomcat</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">就启动完毕了。反之则可能出现错误，无法启动。要关闭</span><span lang="EN-US">Tomcat</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">服务器，可以关闭这个</span><span lang="EN-US">CMD</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">窗口，也可以双击运行</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">shutdown.bat</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。</span><span lang="EN-US"> </span>
                </p></p> </p> 
                
                <p style="text-align: center; text-indent: 21.75pt" class="MsoNormal" align="center">
                  <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">接着在浏览器中键入</span><span lang="EN-US"><a href="http://localhost:8080/">http://localhost:8080/</a> </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">来测试是否运行成功。如下图所示：</span>
                </p>
                
                <p style="text-align: center; text-indent: 21.75pt" class="MsoNormal" align="center">
                  <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial"></span><span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image022.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image022" border="0" alt="clip_image022" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image022_thumb.jpg" width="547" height="317" v:shapes="_x0000_i1035" /></a> </span>
                </p></p> </p> 
                
                <p style="text-align: center; text-indent: 21.75pt" class="MsoNormal" align="center">
                  <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span><span lang="EN-US">1.11 Tomcat </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的欢迎页面</span><span lang="EN-US"> </span>
                </p></p> </p> 
                
                <p style="text-indent: 21.75pt" class="MsoNormal">
                  <b style="mso-bidi-font-weight: normal"><span style="font-family: 宋体; color: red; mso-ascii-font-family: arial; mso-hansi-font-family: arial">注意：</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">有的时候您可能想修改</span><span lang="EN-US">Tomcat</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的默认监听端口，请用文本编辑器打开</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">Tomcat</span></i><i style="mso-bidi-font-style: normal"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">安装目录</span><span lang="EN-US">/conf/server.xml</span></i><span lang="EN-US">, </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">找到如下的定义：</span><span lang="EN-US"> </span>
                </p></p> </p> 
                
                <p style="text-indent: 21.75pt" class="MsoNormal">
                  <i style="mso-bidi-font-style: normal"><span lang="EN-US"><Connector port="8080" …</span></i><span lang="EN-US"> </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，替换</span><span lang="EN-US">8080</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">为你想要的端口即可。假设改成</span><span lang="EN-US">80</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，就可以省略端口这样访问：</span><span lang="EN-US"> </span>
                </p></p> </p> 
                
                <p style="text-indent: 21.75pt" class="MsoNormal">
                  <span lang="EN-US"><a href="http://localhost/">http://localhost/</a> </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">否则是</span> <span lang="EN-US"><a href="http://localhost:新端口/">http://localhost:<span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial" lang="EN-US"><span lang="EN-US">新端口</span></span>/</a> </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">或者</span> <span lang="EN-US"><a href="http://127.0.0.1:新端口/">http://127.0.0.1:<span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial" lang="EN-US"><span lang="EN-US">新端口</span></span>/</a> </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。</span><span lang="EN-US">Localhost</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">或者</span><span lang="EN-US"> 127.0.0.1 </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">是个特殊的网络地址，它就代表你本机的地址。</span><span lang="EN-US"> </span>
                </p></p> </p> 
                
                <p style="text-indent: 21.75pt" class="MsoNormal">
                  <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">另外，</span><span lang="EN-US">Tomcat</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">只能启动一次，如果一下启动两个</span><span lang="EN-US">Tomcat</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，会报这样的异常：</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">java.net.BindException: Address already in use: JVM_Bind</span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。除非是两个安装在不同端口的</span><span lang="EN-US">Tomcat</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">才能同时启动。</span><span lang="EN-US"> </span>
                </p></p> </p> 
                
                <h2>
                  <a name="_Toc201479544"><span lang="EN-US">1.4 JBoss </span></a><span style="mso-bookmark: _toc201479544"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">服务器的下载，安装和运行（可选）</span></span><span lang="EN-US"> </p> 
                  
                  <p>
                    </span></h2> 
                    
                    <p style="text-indent: 21.1pt; mso-char-indent-count: 2.0" class="MsoNormal">
                      <b style="mso-bidi-font-weight: normal"><span style="font-family: 宋体; color: red; mso-ascii-font-family: arial; mso-hansi-font-family: arial">注意：</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">如果你不想开发</span><span lang="EN-US">EJB</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">应用，本节内容不需要进行。</span><span lang="EN-US"> </span>
                    </p>
                  </p></p> 
                  
                  <p style="text-indent: 21pt; mso-char-indent-count: 2.0" class="MsoNormal">
                    <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">如果你没有安装</span><span lang="EN-US">JDK</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，</span><span lang="EN-US">JBoss </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">将无法单独启动，但可以在</span><span lang="EN-US">MyEclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">里面正常启动。</span><span lang="EN-US"> </span>
                  </p></p> </p> 
                  
                  <p style="text-indent: 21pt; mso-char-indent-count: 2.0" class="MsoNormal">
                    <span lang="EN-US">JBoss </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">是一款开源免费的支持</span><span lang="EN-US">EJB 3.0</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">和</span><span lang="EN-US">JSP</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，</span><span lang="EN-US">JMS</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">等的应用服务器。</span><span lang="EN-US"><a href="http://labs.jboss.com/jbossas/downloads">http://labs.jboss.com/jbossas/downloads</a> <span style="mso-spacerun: yes">&#160;</span></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">任何一个</span><span lang="EN-US"> 4.2 </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">或者</span><span lang="EN-US">5.0 </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">版本均可</span><span lang="EN-US">. </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">这里推荐您点击链接</span><span lang="EN-US"><a href="http://downloads.sourceforge.net/jboss/jboss-4.2.2.GA.zip">http://downloads.sourceforge.net/jboss/jboss-4.2.2.GA.zip</a> </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">直接下载。下载完毕后得到一个</span><span lang="EN-US">ZIP</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">文件，例如</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">jboss-4.2.2.GA.zip</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，解压缩到任何不含空格的目录即可，例如</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">c:\ jboss-4.2.2.GA</span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。在</span><span lang="EN-US">Windows</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">下不需要像某些文章所说的需要配置</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">JBOSS_HOME</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">变量。要启动</span><span lang="EN-US"> JBoss </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">进入</span><span lang="EN-US">JBoss</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">下面的</span><span lang="EN-US">bin</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">子目录双击</span><span lang="EN-US">run.bat</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">即可</span><span lang="EN-US">,</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">例如</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">c:\ jboss-4.2.2.GA\bin\run.bat</span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，启动后将会产生下面的输出日志：</span><span lang="EN-US"> </span>
                  </p></p> </p> 
                  
                  <table style="border-collapse: collapse; background: black; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 480" class="MsoFooter" border="0" cellspacing="0" cellpadding="0">
                    <tr style="mso-yfti-irow: 0; mso-yfti-firstrow: yes; mso-yfti-lastrow: yes">
                      <td style="padding-bottom: 0cm; padding-left: 5.4pt; width: 426.1pt; padding-right: 5.4pt; padding-top: 0cm" valign="top" width="568">
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">=================================================================== </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"></span>
                        </p>
                        
                        <p>
                          <font color="#ffffff">&#160;</font>
                        </p></p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff"><span style="mso-spacerun: yes">&#160; </span>JBoss Bootstrap Environment </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"></span>
                        </p>
                        
                        <p>
                          <font color="#ffffff">&#160;</font>
                        </p></p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff"><span style="mso-spacerun: yes">&#160; </span>JBOSS_HOME: C:\jboss-<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">4.2.2</chsdate>.GA </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"></span>
                        </p>
                        
                        <p>
                          <font color="#ffffff">&#160;</font>
                        </p></p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <font color="#ffffff"><span lang="EN-US"><span style="mso-spacerun: yes">&#160; </span></span><span style="mso-ansi-language: fr" lang="FR">JAVA: D:\Java\jdk<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">1.7.0</chsdate>\bin\java </span></font>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span style="mso-ansi-language: fr" lang="FR"></span>
                        </p>
                        
                        <p>
                          <font color="#ffffff">&#160;</font>
                        </p></p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span style="mso-ansi-language: fr" lang="FR"><font color="#ffffff"><span style="mso-spacerun: yes">&#160; </span>JAVA_OPTS:<span style="mso-spacerun: yes">&#160; </span>-Dprogram.name=run.bat -server -Xms<chmetcnv unitname="m" sourcevalue="128" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on">128m</chmetcnv> -Xmx<chmetcnv unitname="m" sourcevalue="512" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on">512m</chmetcnv> -Dsun.rmi.dgc.cli </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span style="mso-ansi-language: fr" lang="FR"><font color="#ffffff">ent.gcInterval=3600000 -Dsun.rmi.dgc.server.gcInterval=3600000 </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span style="mso-ansi-language: fr" lang="FR"></span>
                        </p>
                        
                        <p>
                          <font color="#ffffff">&#160;</font>
                        </p></p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span style="mso-ansi-language: fr" lang="FR"><font color="#ffffff"><span style="mso-spacerun: yes">&#160; </span>CLASSPATH: D:\Java\jdk<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">1.7.0</chsdate>\lib\tools.jar;C:\jboss-4.2.2.GA\bin\run.jar </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span style="mso-ansi-language: fr" lang="FR"></span>
                        </p>
                        
                        <p>
                          <font color="#ffffff">&#160;</font>
                        </p></p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">=============================================================================== </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"></span>
                        </p>
                        
                        <p>
                          <font color="#ffffff">&#160;</font>
                        </p></p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:13:48,015 INFO<span style="mso-spacerun: yes">&#160; </span>[Server] Starting JBoss (MX MicroKernel)&#8230; </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:13:48,015 INFO<span style="mso-spacerun: yes">&#160; </span>[Server] Release ID: JBoss [Trinity] <chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">4.2.2</chsdate>.GA (build: SVNTag= </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">JBoss_4_2_2_GA date=200710221139) </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:13:48,015 INFO<span style="mso-spacerun: yes">&#160; </span>[Server] Home Dir: C:\jboss-<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">4.2.2</chsdate>.GA </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:13:48,015 INFO<span style="mso-spacerun: yes">&#160; </span>[Server] Home URL: file:/C:/jboss-<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">4.2.2</chsdate>.GA/ </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:13:48,031 INFO<span style="mso-spacerun: yes">&#160; </span>[Server] Patch URL: null </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:13:48,031 INFO<span style="mso-spacerun: yes">&#160; </span>[Server] Server Name: default </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:13:48,031 INFO<span style="mso-spacerun: yes">&#160; </span>[Server] Server Home Dir: C:\jboss-<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">4.2.2</chsdate>.GA\server\default </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:13:48,031 INFO<span style="mso-spacerun: yes">&#160; </span>[Server] Server Home URL: file:/C:/jboss-<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">4.2.2</chsdate>.GA/server/defa </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span style="mso-ansi-language: no-bok" lang="NO-BOK"><font color="#ffffff">ult/ </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span style="mso-ansi-language: no-bok" lang="NO-BOK"><font color="#ffffff">09:13:48,031 INFO<span style="mso-spacerun: yes">&#160; </span>[Server] Server Log Dir: C:\jboss-<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">4.2.2</chsdate>.GA\server\default\log </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span style="mso-ansi-language: no-bok" lang="NO-BOK"></span>
                        </p>
                        
                        <p>
                          <font color="#ffffff">&#160;</font>
                        </p></p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span style="mso-ansi-language: no-bok" lang="NO-BOK"><font color="#ffffff">09:13:48,031 INFO<span style="mso-spacerun: yes">&#160; </span>[Server] Server Temp Dir: C:\jboss-<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">4.2.2</chsdate>.GA\server\default\tm </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">p </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:13:48,031 INFO<span style="mso-spacerun: yes">&#160; </span>[Server] Root Deployment Filename: jboss-service.xml </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:13:48,984 INFO<span style="mso-spacerun: yes">&#160; </span>[ServerInfo] Java version: <chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">1.7.0</chsdate>-ea,Sun Microsystems Inc. </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:13:48,984 INFO<span style="mso-spacerun: yes">&#160; </span>[ServerInfo] Java VM: Java HotSpot(TM) Server VM 11.0-b08,Sun </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff"><span style="mso-spacerun: yes">&#160;</span>Microsystems Inc. </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:13:48,984 INFO<span style="mso-spacerun: yes">&#160; </span>[ServerInfo] OS-System: Windows XP 5.1,x86 </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:13:49,703 INFO<span style="mso-spacerun: yes">&#160; </span>[Server] Core system initialized </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:13:52,359 INFO<span style="mso-spacerun: yes">&#160; </span>[WebService] Using RMI server codebase: http://127.0.0.1:8083 </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">/ </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:13:52,359 INFO<span style="mso-spacerun: yes">&#160; </span>[Log4jService$URLWatchTimerTask] Configuring from URL: resour </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span style="mso-ansi-language: fr" lang="FR"><font color="#ffffff">ce:jboss-log4j.xml </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span style="mso-ansi-language: fr" lang="FR"><font color="#ffffff">09:13:53,390 INFO<span style="mso-spacerun: yes">&#160; </span>[TransactionManagerService] JBossTS Transaction Service (JTA </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">version) &#8211; JBoss Inc. </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:13:53,390 INFO<span style="mso-spacerun: yes">&#160; </span>[TransactionManagerService] Setting up property manager MBean </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff"><span style="mso-spacerun: yes">&#160;</span>and JMX layer </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:13:53,937 INFO<span style="mso-spacerun: yes">&#160; </span>[TransactionManagerService] Starting recovery manager </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:13:54,031 INFO<span style="mso-spacerun: yes">&#160; </span>[TransactionManagerService] Recovery manager started </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:13:54,031 INFO<span style="mso-spacerun: yes">&#160; </span>[TransactionManagerService] Binding TransactionManager JNDI R </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">eference </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:13:57,281 INFO<span style="mso-spacerun: yes">&#160; </span>[EJB3Deployer] Starting java:comp multiplexer </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:13:57,593 INFO<span style="mso-spacerun: yes">&#160; </span>[STDOUT] no object for null </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:13:57,593 INFO<span style="mso-spacerun: yes">&#160; </span>[STDOUT] no object for null </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:13:57,609 INFO<span style="mso-spacerun: yes">&#160; </span>[STDOUT] no object for null </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:13:57,640 INFO<span style="mso-spacerun: yes">&#160; </span>[STDOUT] no object for {urn:jboss:bean-deployer}supplyType </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:13:57,640 INFO<span style="mso-spacerun: yes">&#160; </span>[STDOUT] no object for {urn:jboss:bean-deployer}dependsType </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:00,031 INFO<span style="mso-spacerun: yes">&#160; </span>[NativeServerConfig] JBoss Web Services &#8211; Native </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:00,031 INFO<span style="mso-spacerun: yes">&#160; </span>[NativeServerConfig] jbossws-native-<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">2.0.1</chsdate>.SP2 (build=20071021 </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">0837) </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:00,953 INFO<span style="mso-spacerun: yes">&#160; </span>[Embedded] Catalina naming disabled </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:01,156 INFO<span style="mso-spacerun: yes">&#160; </span>[AprLifecycleListener] The Apache Tomcat Native library which </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff"><span style="mso-spacerun: yes">&#160;</span>allows optimal performance in production environments was not found on the java </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">.library.path: D:\Java\jdk1.7.0\bin;.;C:\WINXP\Sun\Java\bin;C:\WINXP\system32;C: </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">\WINXP;%JAVA_HOME%\bin;C:\oracle\ora92\bin;C:\WINXP\system32;C:\WINXP;C:\WINXP\S </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">ystem32\Wbem;%JAVA_HOME%\bin;E:\_PortableJava\jdk<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">1.6.0</chsdate>\bin;C:\oracle\ora92\bin;C </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">:\WINXP\system32;C:\WINXP;C:\WINXP\System32\Wbem;E:\_PortableJava\jdk<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">1.6.0</chsdate>\bin;C </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">:\oracle\ora92\bin;C:\WINXP\system32;C:\WINXP;C:\WINXP\System32\Wbem;E:\_Portabl </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span style="mso-ansi-language: fr" lang="FR"><font color="#ffffff">eJava\apache-ant-<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">1.6.2</chsdate>\bin;E:\_PortableApps\SSH </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:01,234 INFO<span style="mso-spacerun: yes">&#160; </span>[Http11Protocol] Initializing Coyote HTTP/1.1 on http-127.0.0 </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">.1-8080 </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:01,234 INFO<span style="mso-spacerun: yes">&#160; </span>[AjpProtocol] Initializing Coyote AJP/1.3 on ajp-127.0.0.1-80 </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09 </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:01,250 INFO<span style="mso-spacerun: yes">&#160; </span>[Catalina] Initialization processed in 285 ms </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:01,250 INFO<span style="mso-spacerun: yes">&#160; </span>[StandardService] Starting service jboss.web </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:01,250 INFO<span style="mso-spacerun: yes">&#160; </span>[StandardEngine] Starting Servlet Engine: JBossWeb/<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">2.0.1</chsdate>.GA </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:01,312 INFO<span style="mso-spacerun: yes">&#160; </span>[Catalina] Server startup in 70 ms </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:01,453 INFO<span style="mso-spacerun: yes">&#160; </span>[TomcatDeployer] deploy, ctxPath=/, warUrl=&#8230;/deploy/jboss-w </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">eb.deployer/ROOT.war/ </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:02,296 INFO<span style="mso-spacerun: yes">&#160; </span>[TomcatDeployer] deploy, ctxPath=/invoker, warUrl=&#8230;/deploy/ </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">http-invoker.sar/invoker.war/ </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:02,421 INFO<span style="mso-spacerun: yes">&#160; </span>[TomcatDeployer] deploy, ctxPath=/jbossws, warUrl=&#8230;/deploy/ </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">jbossws.sar/jbossws-context.war/ </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:02,546 INFO<span style="mso-spacerun: yes">&#160; </span>[TomcatDeployer] deploy, ctxPath=/jbossmq-httpil, warUrl=&#8230;/ </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">deploy/jms/jbossmq-httpil.sar/jbossmq-httpil.war/ </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:03,359 INFO<span style="mso-spacerun: yes">&#160; </span>[TomcatDeployer] deploy, ctxPath=/web-console, warUrl=&#8230;/dep </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">loy/management/console-mgr.sar/web-console.war/ </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:03,781 INFO<span style="mso-spacerun: yes">&#160; </span>[MailService] Mail Service bound to java:/Mail </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:03,953 INFO<span style="mso-spacerun: yes">&#160; </span>[RARDeployment] Required license terms exist, view META-INF/r </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">a.xml in &#8230;/deploy/jboss-ha-local-jdbc.rar </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:04,000 INFO<span style="mso-spacerun: yes">&#160; </span>[RARDeployment] Required license terms exist, view META-INF/r </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">a.xml in &#8230;/deploy/jboss-ha-xa-jdbc.rar </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:04,062 INFO<span style="mso-spacerun: yes">&#160; </span>[RARDeployment] Required license terms exist, view META-INF/r </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">a.xml in &#8230;/deploy/jboss-local-jdbc.rar </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:04,109 INFO<span style="mso-spacerun: yes">&#160; </span>[RARDeployment] Required license terms exist, view META-INF/r </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">a.xml in &#8230;/deploy/jboss-xa-jdbc.rar </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:04,203 INFO<span style="mso-spacerun: yes">&#160; </span>[RARDeployment] Required license terms exist, view META-INF/r </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">a.xml in &#8230;/deploy/jms/jms-ra.rar </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:04,328 INFO<span style="mso-spacerun: yes">&#160; </span>[RARDeployment] Required license terms exist, view META-INF/r </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">a.xml in &#8230;/deploy/mail-ra.rar </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:04,390 INFO<span style="mso-spacerun: yes">&#160; </span>[RARDeployment] Required license terms exist, view META-INF/r </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">a.xml in &#8230;/deploy/quartz-ra.rar </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:04,390 INFO<span style="mso-spacerun: yes">&#160; </span>[QuartzResourceAdapter] start quartz!!! </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:04,484 INFO<span style="mso-spacerun: yes">&#160; </span>[SimpleThreadPool] Job execution threads will use class loade </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">r of thread: main </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:04,515 INFO<span style="mso-spacerun: yes">&#160; </span>[QuartzScheduler] Quartz Scheduler v.<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">1.5.2</chsdate> created. </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:04,515 INFO<span style="mso-spacerun: yes">&#160; </span>[RAMJobStore] RAMJobStore initialized. </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:04,515 INFO<span style="mso-spacerun: yes">&#160; </span>[StdSchedulerFactory] Quartz scheduler &#8216;DefaultQuartzSchedule </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">r&#8217; initialized from default resource file in Quartz package: &#8216;quartz.properties&#8217; </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"></span>
                        </p>
                        
                        <p>
                          <font color="#ffffff">&#160;</font>
                        </p></p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:04,515 INFO<span style="mso-spacerun: yes">&#160; </span>[StdSchedulerFactory] Quartz scheduler version: <chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">1.5.2</chsdate> </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:04,515 INFO<span style="mso-spacerun: yes">&#160; </span>[QuartzScheduler] Scheduler DefaultQuartzScheduler_$_NON_CLUS </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">TERED started. </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:05,968 INFO<span style="mso-spacerun: yes">&#160; </span>[ConnectionFactoryBindingService] Bound ConnectionManager &#8216;jb </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">oss.jca:service=DataSourceBinding,name=DefaultDS&#8217; to JNDI name &#8216;java:DefaultDS&#8217; </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:06,609 INFO<span style="mso-spacerun: yes">&#160; </span>[A] Bound to JNDI name: queue/A </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:06,625 INFO<span style="mso-spacerun: yes">&#160; </span>[B] Bound to JNDI name: queue/B </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:06,625 INFO<span style="mso-spacerun: yes">&#160; </span>[C] Bound to JNDI name: queue/C </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:06,625 INFO<span style="mso-spacerun: yes">&#160; </span>[D] Bound to JNDI name: queue/D </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:06,625 INFO<span style="mso-spacerun: yes">&#160; </span>[ex] Bound to JNDI name: queue/ex </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:06,656 INFO<span style="mso-spacerun: yes">&#160; </span>[testTopic] Bound to JNDI name: topic/testTopic </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:06,656 INFO<span style="mso-spacerun: yes">&#160; </span>[securedTopic] Bound to JNDI name: topic/securedTopic </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:06,656 INFO<span style="mso-spacerun: yes">&#160; </span>[testDurableTopic] Bound to JNDI name: topic/testDurableTopic </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"></span>
                        </p>
                        
                        <p>
                          <font color="#ffffff">&#160;</font>
                        </p></p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:06,656 INFO<span style="mso-spacerun: yes">&#160; </span>[testQueue] Bound to JNDI name: queue/testQueue </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:06,703 INFO<span style="mso-spacerun: yes">&#160; </span>[UILServerILService] JBossMQ UIL service available at : /127. </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <font color="#ffffff"><chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False"><span lang="EN-US">0.0.1</span></chsdate><span lang="EN-US">:8093 </span></font>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:06,750 INFO<span style="mso-spacerun: yes">&#160; </span>[DLQ] Bound to JNDI name: queue/DLQ </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:06,843 INFO<span style="mso-spacerun: yes">&#160; </span>[ConnectionFactoryBindingService] Bound ConnectionManager &#8216;jb </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">oss.jca:service=ConnectionFactoryBinding,name=JmsXA&#8217; to JNDI name &#8216;java:JmsXA&#8217; </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:06,875 INFO<span style="mso-spacerun: yes">&#160; </span>[TomcatDeployer] deploy, ctxPath=/jmx-console, warUrl=&#8230;/dep </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">loy/jmx-console.war/ </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:07,203 INFO<span style="mso-spacerun: yes">&#160; </span>[Http11Protocol] Starting Coyote HTTP/1.1 on http-127.0.0.1-8 </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">080 </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:07,375 INFO<span style="mso-spacerun: yes">&#160; </span>[AjpProtocol] Starting Coyote AJP/1.3 on ajp-127.0.0.1-8009 </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">09:14:07,390 INFO<span style="mso-spacerun: yes">&#160; </span>[Server] JBoss (MX MicroKernel) [<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">4.2.2</chsdate>.GA (build: SVNTag=JBos </font></span>
                        </p></p> </p> 
                        
                        <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                          <span lang="EN-US"><font color="#ffffff">s_4_2_2_GA date=200710221139)] Started in 19s:344ms </font></span>
                        </p></p> </p>
                      </td>
                    </tr>
                  </table>
                  
                  <p style="text-indent: 21.75pt" class="MsoNormal">
                    <span lang="EN-US"></span>
                  </p>
                  
                  <p>
                    &#160;
                  </p></p> 
                  
                  <p style="text-align: center; text-indent: 21.75pt" class="MsoNormal" align="center">
                    <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span><span lang="EN-US">1.12 </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">启动</span><span lang="EN-US">JBoss</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">服务器</span><span lang="EN-US"> </span>
                  </p></p> </p> 
                  
                  <p class="MsoNormal">
                    <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">当看到</span><span lang="EN-US"> Started in 33s:188ms </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">之类的信息后，服务器即启动完毕了，否则就是出错或者启动失败了。</span><span lang="EN-US"> </span>
                  </p></p> </p> 
                  
                  <p style="text-align: center; text-indent: 21.75pt" class="MsoNormal" align="center">
                    <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">接着在浏览器中键入</span><span lang="EN-US"><a href="http://localhost:8080/">http://localhost:8080/</a> </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">来测试是否运行成功。如下图所示：</span>
                  </p>
                  
                  <p style="text-align: center; text-indent: 21.75pt" class="MsoNormal" align="center">
                    <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial"></span><span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image024.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image024" border="0" alt="clip_image024" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image024_thumb.jpg" width="283" height="363" v:shapes="_x0000_i1036" /></a> </span>
                  </p></p> </p> 
                  
                  <p style="text-align: center; text-indent: 21.75pt" class="MsoNormal" align="center">
                    <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span> <span lang="EN-US">1.13 JBoss 4.2</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的欢迎页面</span><span lang="EN-US"> </span>
                  </p></p> </p> 
                  
                  <p style="text-indent: 21.75pt" class="MsoNormal">
                    <b style="mso-bidi-font-weight: normal"><span style="font-family: 宋体; color: red; mso-ascii-font-family: arial; mso-hansi-font-family: arial">注意：</span></b><span lang="EN-US">JBoss </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">中也已经包含了</span><span lang="EN-US">JSP</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">服务器功能，而且它监听的端口也是</span><span lang="EN-US">8080</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，所以</span><span lang="EN-US">Tomcat</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">和</span><span lang="EN-US">JBoss</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">是不能同时在一台电脑启动的。默认情况下</span><span lang="EN-US">JBoss</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">只监听</span><span lang="EN-US">localhost</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的请求，如果要让局域网的电脑访问</span><span lang="EN-US">JBoss</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">服务，请在命令行下用下面的参数来运行：</span><span lang="EN-US"> </span>
                  </p></p> </p> 
                  
                  <p style="text-indent: 21.75pt" class="MsoNormal">
                    <i style="mso-bidi-font-style: normal"><span lang="EN-US">run.bat –b <chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">0.0.0</chsdate>.0 </span></i>
                  </p></p> </p> 
                  
                  <h2>
                    <a name="_Toc201479545"></a><a name="_MySQL_5数据库服务器下载，安装和运行（可选）"></a><span style="mso-bookmark: _toc201479545"><span lang="EN-US">1.5 MySQL 5</span></span><span style="mso-bookmark: _toc201479545"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">数据库服务器下载，安装和运行（可选）</span></span><span lang="EN-US"> </p> 
                    
                    <p>
                      </span></h2> 
                      
                      <p class="MsoNormal">
                        <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">因为</span><span lang="EN-US">MyEclipse 6</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">自带了一款嵌入式</span><span lang="EN-US">Java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">数据库</span><span lang="EN-US">Derby(MyEclipse Derby)</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，足够开发使用，因此本节内容也是可选的。</span><span lang="EN-US"> </span>
                      </p>
                    </p></p> 
                    
                    <p class="MsoNormal">
                      <span lang="EN-US">MySQL </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">是一款用的比较广泛的轻量级的免费数据库服务器。</span><span lang="EN-US"> </span>
                    </p></p> </p> 
                    
                    <h3>
                      <a name="_Toc201479546"></a><chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False"><span style="mso-bookmark: _toc201479546"><span lang="EN-US">1.5.1</span></span></chsdate><span style="mso-bookmark: _toc201479546"><span lang="EN-US"> MySQL 5 </span></span><span style="mso-bookmark: _toc201479546"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">官方版本的下载和安装，运行</span></span><span lang="EN-US"> </p> 
                      
                      <p>
                        </span></h3> 
                        
                        <p class="MsoNormal">
                          <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">可以访问</span><span lang="EN-US"> MySQL </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">官方网站下载原版安装程序和</span><span lang="EN-US">JDBC</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">驱动，请访问：</span><span lang="EN-US"><a href="http://dev.mysql.com/downloads/mysql/5.0.html#win32">http://dev.mysql.com/downloads/mysql/5.0.html#win32</a><span style="mso-spacerun: yes">&#160; </span></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，如下所示：</span><span lang="EN-US"> </span>
                        </p>
                      </p></p> 
                      
                      <table style="width: 90%; mso-padding-alt: 1.5pt 1.5pt 1.5pt 1.5pt; mso-cellspacing: 0cm" class="MsoNormalTable" border="0" cellspacing="0" cellpadding="0" width="90%">
                        <tr style="mso-yfti-irow: 0; mso-yfti-firstrow: yes">
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: #dae6ea; padding-top: 1.5pt">
                            <p class="MsoNormal">
                              <span lang="EN-US">Windows Essentials (x86)</span><span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"> </span>
                            </p></p> </p>
                          </td>
                          
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: #dae6ea; padding-top: 1.5pt">
                            <p class="MsoNormal">
                              <span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"></span>
                            </p>
                            
                            <p>
                              &#160;
                            </p></p>
                          </td>
                          
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: #dae6ea; padding-top: 1.5pt">
                            <p class="MsoNormal">
                              <chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False"><span lang="EN-US">5.0.45</span></chsdate><span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"> </span>
                            </p></p> </p>
                          </td>
                          
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: #dae6ea; padding-top: 1.5pt">
                            <p class="MsoNormal">
                              <chmetcnv unitname="m" sourcevalue="22.9" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on"><span lang="EN-US">22.9M</span></chmetcnv><span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"> </span>
                            </p></p> </p>
                          </td>
                          
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: #dae6ea; padding-top: 1.5pt" nowrap="nowrap">
                            <p style="text-align: right" class="MsoNormal" align="right">
                              <span lang="EN-US"><a href="http://dev.mysql.com/get/Downloads/MySQL-5.0/mysql-essential-5.0.45-win32.msi/from/pick">Pick a mirror</a></span><span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"> </span>
                            </p></p> </p>
                          </td>
                        </tr>
                        
                        <tr style="mso-yfti-irow: 1">
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: #dae6ea; padding-top: 1.5pt" colspan="5">
                            <p style="text-align: right" class="MsoNormal" align="right">
                              <span style="color: #777777; font-size: 10pt" lang="EN-US">MD5: </span><code>&lt;span style="color: #777777; font-size: 12pt" lang="EN-US">9efd5d841174b&lt;chmetcnv unitname="a" sourcevalue="1476" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on">1476a&lt;/chmetcnv>317e94becf8786&lt;/span></code><span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"> </span>
                            </p></p> </p>
                          </td>
                        </tr>
                        
                        <tr style="mso-yfti-irow: 2">
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: white; padding-top: 1.5pt">
                            <p class="MsoNormal">
                              <span lang="EN-US">Windows ZIP/Setup.EXE (x86)</span><span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"> </span>
                            </p></p> </p>
                          </td>
                          
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: white; padding-top: 1.5pt">
                            <p class="MsoNormal">
                              <span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"></span>
                            </p>
                            
                            <p>
                              &#160;
                            </p></p>
                          </td>
                          
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: white; padding-top: 1.5pt">
                            <p class="MsoNormal">
                              <chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False"><span lang="EN-US">5.0.45</span></chsdate><span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"> </span>
                            </p></p> </p>
                          </td>
                          
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: white; padding-top: 1.5pt">
                            <p class="MsoNormal">
                              <chmetcnv unitname="m" sourcevalue="42.4" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on"><span lang="EN-US">42.4M</span></chmetcnv><span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"> </span>
                            </p></p> </p>
                          </td>
                          
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: white; padding-top: 1.5pt" nowrap="nowrap">
                            <p style="text-align: right" class="MsoNormal" align="right">
                              <span lang="EN-US"><a href="http://dev.mysql.com/get/Downloads/MySQL-5.0/mysql-5.0.45-win32.zip/from/pick">Pick a mirror</a></span><span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"> </span>
                            </p></p> </p>
                          </td>
                        </tr>
                        
                        <tr style="mso-yfti-irow: 3">
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: white; padding-top: 1.5pt" colspan="5">
                            <p style="text-align: right" class="MsoNormal" align="right">
                              <span style="color: #777777; font-size: 10pt" lang="EN-US">MD5: </span><code>&lt;span style="color: #777777; font-size: 12pt" lang="EN-US">1566ff960b22cda4903e03d&lt;chmetcnv unitname="F" sourcevalue="4" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on">4f&lt;/chmetcnv>6cfa205&lt;/span></code><span style="color: #777777; font-size: 10pt" lang="EN-US"> | <a href="http://dev.mysql.com/Downloads/MySQL-5.0/mysql-5.0.45-win32.zip.asc">Signature</a></span><span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"> </span>
                            </p></p> </p>
                          </td>
                        </tr>
                        
                        <tr style="mso-yfti-irow: 4">
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: #dae6ea; padding-top: 1.5pt">
                            <p class="MsoNormal">
                              <span lang="EN-US">Without installer (unzip in C:\)</span><span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"> </span>
                            </p></p> </p>
                          </td>
                          
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: #dae6ea; padding-top: 1.5pt">
                            <p class="MsoNormal">
                              <span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"></span>
                            </p>
                            
                            <p>
                              &#160;
                            </p></p>
                          </td>
                          
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: #dae6ea; padding-top: 1.5pt">
                            <p class="MsoNormal">
                              <chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False"><span lang="EN-US">5.0.45</span></chsdate><span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"> </span>
                            </p></p> </p>
                          </td>
                          
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: #dae6ea; padding-top: 1.5pt">
                            <p class="MsoNormal">
                              <chmetcnv unitname="m" sourcevalue="50" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on"><span lang="EN-US">50.0M</span></chmetcnv><span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"> </span>
                            </p></p> </p>
                          </td>
                          
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: #dae6ea; padding-top: 1.5pt" nowrap="nowrap">
                            <p style="text-align: right" class="MsoNormal" align="right">
                              <span lang="EN-US"><a href="http://dev.mysql.com/get/Downloads/MySQL-5.0/mysql-noinstall-5.0.45-win32.zip/from/pick">Pick a mirror</a></span><span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"> </span>
                            </p></p> </p>
                          </td>
                        </tr>
                        
                        <tr style="mso-yfti-irow: 5; mso-yfti-lastrow: yes">
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: #dae6ea; padding-top: 1.5pt" colspan="5">
                            <p style="text-align: right" class="MsoNormal" align="right">
                              <span style="color: #777777; font-size: 10pt" lang="EN-US">MD5: </span><code>&lt;span style="color: #777777; font-size: 12pt" lang="EN-US">c40ba57fe2ecb&lt;chmetcnv unitname="F" sourcevalue="965" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on">965f&lt;/chmetcnv>9ca88897b6e7d8b&lt;/span></code><span style="color: #777777; font-size: 10pt" lang="EN-US"> | <a href="http://dev.mysql.com/Downloads/MySQL-5.0/mysql-noinstall-5.0.45-win32.zip.asc">Signature</a></span><span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"> </span>
                            </p></p> </p>
                          </td>
                        </tr>
                      </table>
                      
                      <p class="MsoNormal">
                        <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">再这三个版本中选择第一个或者第二个，点击</span><span lang="EN-US">Pick a mirror</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">后即可下载，接着双击点击</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">Next</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">或者</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">Yes</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">按钮安装。安装完毕后服务器即会自动启动，无须每次手工启动。</span><span lang="EN-US"> </span>
                      </p></p> </p> 
                      
                      <p class="MsoNormal">
                        <span lang="EN-US">MySQL</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的</span><span lang="EN-US">JDBC </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">驱动下载地址位于</span><span lang="EN-US"><a href="http://dev.mysql.com/downloads/connector/j/5.1.html">http://dev.mysql.com/downloads/connector/j/5.1.html</a></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">：</span><span lang="EN-US"> </span>
                      </p></p> </p> 
                      
                      <table style="width: 90%; mso-padding-alt: 1.5pt 1.5pt 1.5pt 1.5pt; mso-cellspacing: 0cm" class="MsoNormalTable" border="0" cellspacing="0" cellpadding="0" width="90%">
                        <tr style="mso-yfti-irow: 0; mso-yfti-firstrow: yes">
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: #dae6ea; padding-top: 1.5pt">
                            <p class="MsoNormal">
                              <span lang="EN-US">Source and Binaries (tar.gz)</span><span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"> </span>
                            </p></p> </p>
                          </td>
                          
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: #dae6ea; padding-top: 1.5pt">
                            <p class="MsoNormal">
                              <span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"></span>
                            </p>
                            
                            <p>
                              &#160;
                            </p></p>
                          </td>
                          
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: #dae6ea; padding-top: 1.5pt">
                            <p class="MsoNormal">
                              <chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False"><span lang="EN-US">5.1.5</span></chsdate><span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"> </span>
                            </p></p> </p>
                          </td>
                          
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: #dae6ea; padding-top: 1.5pt">
                            <p class="MsoNormal">
                              <chmetcnv unitname="m" sourcevalue="7.8" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on"><span lang="EN-US">7.8M</span></chmetcnv><span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"> </span>
                            </p></p> </p>
                          </td>
                          
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: #dae6ea; padding-top: 1.5pt" nowrap="nowrap">
                            <p style="text-align: right" class="MsoNormal" align="right">
                              <span lang="EN-US"><a href="http://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-5.1.5.tar.gz/from/pick">Pick a mirror</a></span><span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"> </span>
                            </p></p> </p>
                          </td>
                        </tr>
                        
                        <tr style="mso-yfti-irow: 1">
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: #dae6ea; padding-top: 1.5pt" colspan="5">
                            <p style="text-align: right" class="MsoNormal" align="right">
                              <span style="color: #777777; font-size: 10pt" lang="EN-US">MD5: </span><chmetcnv unitname="F" sourcevalue="85289" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on"><code>&lt;span style="color: #777777; font-size: 12pt" lang="EN-US">85289f&lt;/span></code></chmetcnv><chmetcnv unitname="a" sourcevalue="74093" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on"><code>&lt;span style="color: #777777; font-size: 12pt" lang="EN-US">74093a&lt;/span></code></chmetcnv><code>&lt;span style="color: #777777; font-size: 12pt" lang="EN-US">2b165d&lt;chmetcnv unitname="F" sourcevalue="42" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on">42f&lt;/chmetcnv>&lt;chmetcnv unitname="ac" sourcevalue="5" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on">5ac&lt;/chmetcnv>38850d18&lt;/span></code><span style="color: #777777; font-size: 10pt" lang="EN-US"> | <a href="http://dev.mysql.com/Downloads/Connector-J/mysql-connector-java-5.1.5.tar.gz.asc">Signature</a></span><span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"> </span>
                            </p></p> </p>
                          </td>
                        </tr>
                        
                        <tr style="mso-yfti-irow: 2">
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: white; padding-top: 1.5pt">
                            <p class="MsoNormal">
                              <span lang="EN-US">Source and Binaries (zip)</span><span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"> </span>
                            </p></p> </p>
                          </td>
                          
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: white; padding-top: 1.5pt">
                            <p class="MsoNormal">
                              <span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"></span>
                            </p>
                            
                            <p>
                              &#160;
                            </p></p>
                          </td>
                          
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: white; padding-top: 1.5pt">
                            <p class="MsoNormal">
                              <chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False"><span lang="EN-US">5.1.5</span></chsdate><span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"> </span>
                            </p></p> </p>
                          </td>
                          
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: white; padding-top: 1.5pt">
                            <p class="MsoNormal">
                              <chmetcnv unitname="m" sourcevalue="8" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on"><span lang="EN-US">8.0M</span></chmetcnv><span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"> </span>
                            </p></p> </p>
                          </td>
                          
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: white; padding-top: 1.5pt" nowrap="nowrap">
                            <p style="text-align: right" class="MsoNormal" align="right">
                              <span lang="EN-US"><a href="http://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-5.1.5.zip/from/pick">Pick a mirror</a></span><span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"> </span>
                            </p></p> </p>
                          </td>
                        </tr>
                        
                        <tr style="mso-yfti-irow: 3; mso-yfti-lastrow: yes">
                          <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; background: white; padding-top: 1.5pt" colspan="5">
                            <p style="text-align: right" class="MsoNormal" align="right">
                              <span style="color: #777777; font-size: 10pt" lang="EN-US">MD5: </span><code>&lt;span style="color: #777777; font-size: 12pt" lang="EN-US">b207959597d8974545ef99d&lt;chmetcnv unitname="a" sourcevalue="5" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on">5a&lt;/chmetcnv>2cee662&lt;/span></code><span style="color: #777777; font-size: 10pt" lang="EN-US"> | <a href="http://dev.mysql.com/Downloads/Connector-J/mysql-connector-java-5.1.5.zip.asc">Signature</a></span><span style="font-family: 宋体; font-size: 12pt; mso-bidi-font-family: 宋体; mso-bidi-font-size: 10.5pt" lang="EN-US"> </span>
                            </p></p> </p>
                          </td>
                        </tr>
                      </table>
                      
                      <p class="MsoNormal">
                        <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">任选一个进行下载，解压缩后得到</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">mysql-connector-xxx.jar</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">就是驱动程序类库了。</span><span lang="EN-US"> </span>
                      </p></p> </p> 
                      
                      <p class="MsoNormal">
                        <span lang="EN-US"></span>
                      </p>
                      
                      <p>
                        &#160;
                      </p></p> 
                      
                      <h3>
                        <a name="_Toc201479547"></a><chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False"><span style="mso-bookmark: _toc201479547"><span lang="EN-US">1.5.2</span></span></chsdate><span style="mso-bookmark: _toc201479547"><span lang="EN-US"> MySQL 5</span></span><span style="mso-bookmark: _toc201479547"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">绿色版的下载安装和运行</span></span><span lang="EN-US"> </p> 
                        
                        <p>
                          </span></h3> 
                          
                          <p class="MsoNormal">
                            <span lang="EN-US">BeanSoft MySQL Java </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">开发套装包含</span><span lang="EN-US"> MySQL 5.0</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">服务器</span><span lang="EN-US">,</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">管理工具</span><span lang="EN-US">,JDBC</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">驱动和</span><span lang="EN-US">Java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">访问数据库的示例代码。</span><span lang="EN-US"> </span>
                          </p>
                        </p></p> 
                        
                        <h4>
                          <a name="_Toc201479548"></a><chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False"><span style="mso-bookmark: _toc201479548"><span lang="EN-US">1.5.2</span></span></chsdate><span style="mso-bookmark: _toc201479548"><span lang="EN-US">.1 </span></span><span style="mso-bookmark: _toc201479548"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">下载</span></span><span lang="EN-US"> </p> 
                          
                          <p>
                            </span></h4> 
                            
                            <p class="MsoNormal">
                              <span lang="EN-US"><a href="http://gro.clinux.org/frs/download.php/2103/portable_mysql.exe"></a><a href="http://gro.clinux.org/frs/download.php/2106/portable_mysql.exe">http://gro.clinux.org/frs/download.php/2106/portable_mysql.exe</a>&#160;&#160; 4.02MB (</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">自解压包</span><span lang="EN-US">) </span>
                            </p>
                          </p></p> 
                          
                          <p class="MsoNormal">
                            <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">用法</span><span lang="EN-US">: </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">下载后解压缩到硬盘的任意位置</span><span lang="EN-US">, </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">然后双击</span> <b style="mso-bidi-font-weight: normal"><span lang="EN-US">PStart.exe</span></b><span lang="EN-US"> </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">开始</span><span lang="EN-US">, </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">先启动</span><span lang="EN-US"> MySQL </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">服务器</span><span lang="EN-US">, </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">然后即可编译运行</span><span lang="EN-US"> JDBC </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">测试代码</span><span lang="EN-US">. </span>
                          </p></p> </p> 
                          
                          <p class="MsoNormal">
                            <b style="mso-bidi-font-weight: normal"><span style="font-family: 宋体; color: red; mso-ascii-font-family: arial; mso-hansi-font-family: arial">注意：</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">这个版本的</span><span lang="EN-US"> MySQL </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">绿色版默认采用的字符集是</span><span lang="EN-US"> GBK, </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">如果你修改成了别的字符集</span><span lang="EN-US">, MySQL-Front </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">将显示为乱码。</span><span lang="EN-US"> </span>
                          </p></p> </p> 
                          
                          <p class="MsoNormal">
                            <span lang="EN-US"></span>
                          </p>
                          
                          <p>
                            &#160;
                          </p></p> 
                          
                          <h4>
                            <a name="_Toc201479549"></a><chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False"><span style="mso-bookmark: _toc201479549"><span lang="EN-US">1.5.2</span></span></chsdate><span style="mso-bookmark: _toc201479549"><span lang="EN-US">.2 </span></span><span style="mso-bookmark: _toc201479549"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">用法图解</span></span><span lang="EN-US"> </p> 
                            
                            <p>
                              </span></h4> 
                              
                              <p style="text-align: center" class="MsoNormal" align="center">
                                <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image026.gif"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image026" border="0" alt="clip_image026" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image026_thumb.gif" width="526" height="429" v:shapes="_x0000_i1037" /></a> </span>
                              </p>
                            </p></p> 
                            
                            <p style="text-align: center" class="MsoNormal" align="center">
                              <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span><span lang="EN-US">1.14 MySQL </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">绿色版主界面</span><span lang="EN-US"> </span>
                            </p></p> </p> 
                            
                            <p class="MsoNormal">
                              <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">主界面</span><span lang="EN-US">, </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">双击</span> <b style="mso-bidi-font-weight: normal"><span lang="EN-US">mysql_start</span></b><span lang="EN-US"> </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">启动</span><span lang="EN-US"> MySQL </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">服务器</span><span lang="EN-US">, </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">双击</span> <b style="mso-bidi-font-weight: normal"><span lang="EN-US">mysql_stop</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">停止</span><span lang="EN-US">MySQL</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">服务器。详细用法双击</span> <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">网页</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">mysql</span></i><i style="mso-bidi-font-style: normal"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">绿色版</span></i> <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">来了解。</span><span lang="EN-US"> </span>
                            </p></p> </p> 
                            
                            <p style="text-align: center" class="MsoNormal" align="center">
                              <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image028.gif"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image028" border="0" alt="clip_image028" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image028_thumb.gif" width="602" height="444" v:shapes="_x0000_i1038" /></a> </span>
                            </p></p> </p> 
                            
                            <p style="text-align: center" class="MsoNormal" align="center">
                              <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span><span lang="EN-US">1.15</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">双击主界面的</span> <b style="mso-bidi-font-weight: normal"><span lang="EN-US">MySQL-Front</span></b><span lang="EN-US"> </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">启动管理工具</span><span lang="EN-US"> </span>
                            </p></p> </p> 
                            
                            <p style="text-indent: 21pt; mso-char-indent-count: 2.0" class="MsoNormal">
                              <span lang="EN-US">&#160; </span>
                            </p></p> </p> 
                            
                            <table style="border-collapse: collapse; background: black; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 480" class="MsoFooter" border="0" cellspacing="0" cellpadding="0">
                              <tr style="mso-yfti-irow: 0; mso-yfti-firstrow: yes; mso-yfti-lastrow: yes">
                                <td style="padding-bottom: 0cm; padding-left: 5.4pt; width: 426.1pt; padding-right: 5.4pt; padding-top: 0cm" valign="top" width="568">
                                  <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                                    <span lang="EN-US"><font color="#ffffff">E:\MyEclipse6_Video\software\jdbc>java -cp .;mysql-connector-java-<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">3.1.11</chsdate>-bin.jar </font></span>
                                  </p></p> </p> 
                                  
                                  <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                                    <span lang="EN-US"><font color="#ffffff"><span style="mso-spacerun: yes">&#160;</span>JDBCHelloWorld </font></span>
                                  </p></p> </p> 
                                  
                                  <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                                    <span lang="EN-US"><font color="#ffffff">5 </font></span>
                                  </p></p> </p> 
                                  
                                  <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                                    <font color="#ffffff"><span lang="EN-US">jpa test</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">洪文</span><span lang="EN-US"> </span></font>
                                  </p></p> </p> 
                                  
                                  <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                                    <span lang="EN-US"><font color="#ffffff">jpa password </font></span>
                                  </p></p> </p> 
                                  
                                  <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                                    <span lang="EN-US"></span>
                                  </p>
                                  
                                  <p>
                                    <font color="#ffffff">&#160;</font>
                                  </p></p> 
                                  
                                  <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                                    <span lang="EN-US"><font color="#ffffff">6 </font></span>
                                  </p></p> </p> 
                                  
                                  <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                                    <font color="#ffffff"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">北京</span> <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">首都</span><span lang="EN-US"> </span></font>
                                  </p></p> </p> 
                                  
                                  <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                                    <font color="#ffffff"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">哈哈</span><span lang="EN-US"> </span></font>
                                  </p></p> </p> 
                                  
                                  <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                                    <span lang="EN-US"></span>
                                  </p>
                                  
                                  <p>
                                    <font color="#ffffff">&#160;</font>
                                  </p></p> 
                                  
                                  <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                                    <span lang="EN-US"><font color="#ffffff">9 </font></span>
                                  </p></p> </p> 
                                  
                                  <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                                    <span lang="EN-US"><font color="#ffffff">user </font></span>
                                  </p></p> </p> 
                                  
                                  <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                                    <span lang="EN-US"><font color="#ffffff">password </font></span>
                                  </p></p> </p> 
                                  
                                  <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                                    <span lang="EN-US"></span>
                                  </p>
                                  
                                  <p>
                                    <font color="#ffffff">&#160;</font>
                                  </p></p> 
                                  
                                  <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                                    <span lang="EN-US"><font color="#ffffff">11 </font></span>
                                  </p></p> </p> 
                                  
                                  <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                                    <font color="#ffffff"><span lang="EN-US">JDBC </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">中文测试</span><span lang="EN-US"> </span></font>
                                  </p></p> </p> 
                                  
                                  <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                                    <font color="#ffffff"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">密码</span><span lang="EN-US"> </span></font>
                                  </p></p> </p> 
                                  
                                  <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                                    <span lang="EN-US"></span>
                                  </p>
                                  
                                  <p>
                                    <font color="#ffffff">&#160;</font>
                                  </p></p> 
                                  
                                  <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                                    <span lang="EN-US"><font color="#ffffff">E:\MyEclipse6_Video\software\jdbc>pause </font></span>
                                  </p></p> </p> 
                                  
                                  <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                                    <font color="#ffffff"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">请按任意键继续</span><span lang="EN-US">. . . </span></font>
                                  </p></p> </p>
                                </td>
                              </tr>
                            </table>
                            
                            <p style="text-indent: 21.75pt" class="MsoNormal">
                              <span lang="EN-US"></span>
                            </p>
                            
                            <p>
                              &#160;
                            </p></p> 
                            
                            <p style="text-align: center; text-indent: 21.75pt" class="MsoNormal" align="center">
                              <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span><span lang="EN-US">1.16</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">双击主界面的<b style="mso-bidi-font-weight: normal">运行</b></span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">JDBC</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">进行插入和读取数据测试</span><span lang="EN-US"> </span>
                            </p></p> </p> 
                            
                            <p class="MsoNormal">
                              <span lang="EN-US"></span>
                            </p>
                            
                            <p>
                              &#160;
                            </p></p> 
                            
                            <h2>
                              <a name="_Toc201479550"><span lang="EN-US">1.6 Eclipse 3.3</span></a><span style="mso-bookmark: _toc201479550"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的下载，安装和运行</span></span><span lang="EN-US"> </p> 
                              
                              <p>
                                </span></h2> 
                                
                                <p class="MsoNormal">
                                  <span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span>Eclipse </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">是一款基础的，开源免费的</span><span lang="EN-US">Java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">开发工具，目前比较流行。</span><span lang="EN-US">Eclipse 3.3 </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">可以在</span> <span lang="EN-US"><a href="http://www.eclipse.org/">http://www.eclipse.org/</a> </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">下载，进入首页后点击黄色的</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">Download</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">按钮，如下图所示：</span><span lang="EN-US"> </span>
                                </p>
                              </p></p> 
                              
                              <p style="text-align: center" class="MsoNormal" align="center">
                                <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image030.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image030" border="0" alt="clip_image030" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image030_thumb.jpg" width="222" height="297" v:shapes="_x0000_i1039" /></a> </span>
                              </p></p> </p> 
                              
                              <p style="text-align: center" class="MsoNormal" align="center">
                                <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span><span lang="EN-US">1.17 Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">首页面</span><span lang="EN-US"> </span>
                              </p></p> </p> 
                              
                              <p class="MsoNormal">
                                <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">点击后可以看到下载页面中的内容：</span><span lang="EN-US"> </span>
                              </p></p> </p> 
                              
                              <p style="text-align: center" class="MsoNormal" align="center">
                                <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image032.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image032" border="0" alt="clip_image032" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image032_thumb.jpg" width="554" height="247" v:shapes="_x0000_i1040" /></a> </span>
                              </p></p> </p> 
                              
                              <p style="text-align: center" class="MsoNormal" align="center">
                                <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span><span lang="EN-US">1.18 </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">下载</span><span lang="EN-US">Eclipse </span>
                              </p></p> </p> 
                              
                              <p class="MsoNormal">
                                <span lang="EN-US">Eclipse 3.3 </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">分出了几个类型的下载包，第一个是普通的</span><span lang="EN-US">Java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">开发包，我们下载它就可以了，点击</span><b><span lang="EN-US"><a href="http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/20071103/eclipse-java-europa-fall2-win32.zip">Eclipse IDE for Java Developers</a> </span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">就可以下载了。第二个是提供有限的</span><span lang="EN-US">Java EE</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">开发支持的，包括</span><span lang="EN-US">EJB</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，</span><span lang="EN-US">JSP, JSF</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的开发；第三个是</span><span lang="EN-US">C/C++</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的开发包；第四个是专门做插件和</span><span lang="EN-US">RCP</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">（</span><span lang="EN-US">Rich Client Platform, </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">富客户端平台，</span><span lang="EN-US">IBM</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">主推的基于</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的桌面应用开发平台，提供有限的系统底层调用和仿</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">外观的界面）开发的；第五个是传统的</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">下载包，包括</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">平台，</span><span lang="EN-US">Java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">开发工具和插件开发。</span><span lang="EN-US"> </span>
                              </p></p> </p> 
                              
                              <p style="text-indent: 21.75pt" class="MsoNormal">
                                <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">下载后得到一个压缩包</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">eclipse-java-europa-fall2-win32.zip</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，解压缩到</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">c:\</span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">后会自动得到</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">c:\eclipse</span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">这个目录，这样就算安装完毕了。</span><span lang="EN-US"> </span>
                              </p></p> </p> 
                              
                              <p style="text-indent: 21.75pt" class="MsoNormal">
                                <span lang="EN-US"><span style="mso-spacerun: yes">&#160;</span></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">要运行，进入目录</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">c:\eclipse</span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，双击</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">eclipse.exe</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，就可以启动并运行</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">了。启动过程中会提示你选择</span><span lang="EN-US">workspace</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，点击</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">OK</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">按钮就可以继续启动，如下图所示：</span><span lang="EN-US"> </span>
                              </p></p> </p> 
                              
                              <p style="text-align: center; text-indent: 21.75pt" class="MsoNormal" align="center">
                                <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image034.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image034" border="0" alt="clip_image034" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image034_thumb.jpg" width="525" height="225" v:shapes="_x0000_i1041" /></a> </span>
                              </p></p> </p> 
                              
                              <p style="text-align: center; text-indent: 21.75pt" class="MsoNormal" align="center">
                                <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span><span lang="EN-US">1.19 </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">启动时选择</span><span lang="EN-US">workspace </span>
                              </p></p> </p> 
                              
                              <p style="text-indent: 16.45pt; margin-left: 5.25pt; mso-char-indent-count: 1.56; mso-para-margin-left: .5gd" class="MsoNormal">
                                <b style="mso-bidi-font-weight: normal"><span style="font-family: 宋体; color: red; mso-ascii-font-family: arial; mso-hansi-font-family: arial">注意：</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">如果你不希望以后看到这个提示，选中复选框</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">Use this as the default and do not ask again</span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">即可。</span><span lang="EN-US"> </span>
                              </p></p> </p> 
                              
                              <p style="text-indent: 21.75pt" class="MsoNormal">
                                <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">第一次启动后主界面还显示一个欢迎页面（</span><span lang="EN-US">Welcome</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">），点击上面的</span><span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image036.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image036" border="0" alt="clip_image036" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image036_thumb.jpg" width="18" height="13" v:shapes="_x0000_i1042" /></a></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图标关闭欢迎页面，之后可以做一些基础的</span><span lang="EN-US">Java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">应用开发。这时界面如下所示：</span><span lang="EN-US"> </span>
                              </p></p> </p> 
                              
                              <p style="text-align: center; text-indent: 21.75pt" class="MsoNormal" align="center">
                                <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image038.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image038" border="0" alt="clip_image038" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image038_thumb.jpg" width="553" height="311" v:shapes="_x0000_i1043" /></a> </span>
                              </p></p> </p> 
                              
                              <p style="text-align: center; text-indent: 21.75pt" class="MsoNormal" align="center">
                                <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span><span lang="EN-US">1.20 Eclipse </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">主界面</span><span lang="EN-US"> </span>
                              </p></p> </p> 
                              
                              <p style="text-indent: 21.75pt" class="MsoNormal">
                                <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">至此</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">就算安装完毕了。</span><span lang="EN-US"> </span>
                              </p></p> </p> 
                              
                              <p style="text-indent: 21.75pt" class="MsoNormal">
                                <b style="mso-bidi-font-weight: normal"><span style="font-family: 宋体; color: red; mso-ascii-font-family: arial; mso-hansi-font-family: arial">注意：</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">为什么不介绍如何使用</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的中文语言包呢？这是因为</span><span lang="EN-US">MyEclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">没有中文语言包可以用，如果你下载了</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">中文语言包，将不得不面临不伦不类的界面上中英文混杂的局面。另外</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的中文语言包由</span><span lang="EN-US">IBM</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">捐助，很多术语由于众所周知的原因翻译的非常混乱，另外</span><span lang="EN-US">Java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的绝大多数第一手资料以及其它很多的商业开发工具（例如</span><span lang="EN-US">Jbuilder</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，</span><span lang="EN-US">IDEA</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">）都是只提供英文版的，因此使用英文版即是为了保持行文风格的一致，也有助于读者将来能够方便的学习</span><span lang="EN-US">Java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">和使用其它开发工具。作者并不能保证您的公司就一定会使用中文版的</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">进行开发。</span><span lang="EN-US"> </span>
                              </p></p> </p> 
                              
                              <p style="text-indent: 21.75pt" class="MsoNormal">
                                <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">在实际开发中不可避免会遇到一些奇怪的问题，导致解压缩安装的</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">无法运行。最典型的一种莫过于电脑上已经安装了正确版本的</span><span lang="EN-US">JDK</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">但是却在启动时报错的问题。遇到这种情况，首先您应该检查下载的</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">安装包是不是完整，压缩包有无损坏。最好是从官方站点下载一个。然后还有一种问题，那就是除了正确版本的</span><span lang="EN-US">JDK</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">外，还安装了一些别的低版本的</span><span lang="EN-US">JDK</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，例如安装</span><span lang="EN-US">Oracle</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">或者某些软件后，会自己安装一些</span><span lang="EN-US">JDK1.3</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">或者更低版本的</span><span lang="EN-US">JDK</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">启动的时候先从</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">所在目录的</span><span lang="EN-US">jre</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">目录下寻找</span><span lang="EN-US">java.exe</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，然后再从环境变量</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">PATH</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">中找，然后再从注册表中寻找。问题往往出现在从注册表中寻找时。那么不用着急，可以用两种方式来解决。第一种，将</span><span lang="EN-US">JDK</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">安装目录下的</span><span lang="EN-US">jre</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">子目录完整复制到</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">安装目录下，例如：从</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">C:\jdk<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">1.6.0</chsdate>\jre </span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">复制到</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">c:\eclipse\jre</span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，复制完成后应该能够找到</span><span lang="EN-US">java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">解释器程序</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">c:\eclipse\jre\bin\java.exe</span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，之后再启动</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，就好了。还有另一种方式，是在</span><span lang="EN-US">eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">目录下创建一个启动批处理文件</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">run.bat</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，内容写入：</span><span lang="EN-US"> </span>
                              </p></p> </p> 
                              
                              <p class="MsoNormal">
                                <i style="mso-bidi-font-style: normal"><span lang="EN-US">eclipse.exe –vm C:\jdk<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">1.6.0</chsdate>\bin\javaw.exe </span></i>
                              </p></p> </p> 
                              
                              <p class="MsoNormal">
                                <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。这个命令指定了</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">启动时应该使用哪个</span><span lang="EN-US">JVM</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，也就是用哪个</span><span lang="EN-US">javaw.exe</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。以后运行的时候双击这个批处理文件启动即可。</span><span lang="EN-US"> </span>
                              </p></p> </p> 
                              
                              <h2>
                                <a name="_Toc201479551"><span lang="EN-US">1.7 MyEclipse 6</span></a><span style="mso-bookmark: _toc201479551"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的下载，安装和运行</span></span><span lang="EN-US"> </p> 
                                
                                <p>
                                  </span></h2> 
                                  
                                  <p style="text-indent: 21pt; mso-char-indent-count: 2.0" class="MsoNormal">
                                    <span lang="EN-US">MyEclipse 6 </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">是一款商业的基于</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的</span><span lang="EN-US">Java EE</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">集成开发工具，换句话说不是免费产品。官方站点是</span><span lang="EN-US"><a href="http://www.myeclipseide.com/">http://www.myeclipseide.com/</a></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。</span><span lang="EN-US"> </span>
                                  </p>
                                </p></p> 
                                
                                <p class="MsoNormal">
                                  <span lang="EN-US">MyEclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的安装分为插件版本和</span><state w:st="on"><place w:st="on"><span lang="EN-US">AL</span></place></state><span lang="EN-US">L in ONE</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">版本，其中</span><state w:st="on"><place w:st="on"><span lang="EN-US">AL</span></place></state><span lang="EN-US">L in ONE</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">版本无需自己另外下载安装和配置</span><span lang="EN-US">JDK</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，</span><span lang="EN-US">Eclipse 3.3</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，因此如果你打算以最快的速度装好</span><span lang="EN-US">MyEclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，请选择</span><state w:st="on"><place w:st="on"><span lang="EN-US">AL</span></place></state><span lang="EN-US">L in ONE </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">版本。</span><span lang="EN-US"> </span>
                                </p></p> </p> 
                                
                                <h3>
                                  <a name="_Toc201479552"></a><chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False"><span style="mso-bookmark: _toc201479552"><span lang="EN-US">1.7.1</span></span></chsdate><span style="mso-bookmark: _toc201479552"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">下载</span></span><span lang="EN-US"> </p> 
                                  
                                  <p>
                                    </span></h3> 
                                    
                                    <p class="MsoNormal">
                                      <span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">打开首页后点击页面中的下载按钮：</span><span lang="EN-US"><a href="http://www.myeclipseide.com/module-htmlpages-display-pid-4.html"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image039" border="0" alt="clip_image039" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image039.gif" width="118" height="27" v:shapes="index_4_10" /></a></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，之后来到</span><span lang="EN-US">MyEclipse 6</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的下载页面，需要接受协议然后才能进行下载：</span><span lang="EN-US"> </span>
                                    </p>
                                  </p></p> 
                                  
                                  <p class="MsoNormal">
                                    <span lang="EN-US">MyEclipse challenges the misconception that good development tools have to be expensive by delivering the most cost-effective and full featured Eclipse-based J2EE IDE on the market today. </span>
                                  </p></p> </p> 
                                  
                                  <p class="MsoNormal">
                                    <span lang="EN-US">You can try MyEclipse free for a 30-day trial membership to test drive the full package and see if it is right for you.&#160;&#160; Want to learn more? <a title="MyEclipse Webinar" href="http://www.myeclipseide.com/module-htmlpages-display-pid-352.html">Register</a> for a FREE MyEclipse Webinar! </span>
                                  </p></p> </p> 
                                  
                                  <p style="text-align: center" class="MsoNormal" align="center">
                                    <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image041.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image041" border="0" alt="clip_image041" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image041_thumb.jpg" width="539" height="169" v:shapes="_x0000_i1045" /></a> </span>
                                  </p></p> </p> 
                                  
                                  <p style="text-align: center" class="MsoNormal" align="center">
                                    <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span> <span lang="EN-US">1.21 </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">接受</span><span lang="EN-US">MyEclipse 6</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的下载协议</span><span lang="EN-US"> </span>
                                  </p></p> </p> 
                                  
                                  <p class="MsoNormal">
                                    <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。点击</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">DOWNLOAD</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">按钮后来到真正的下载页面：</span><span lang="EN-US"> </span>
                                  </p></p> </p> 
                                  
                                  <div align="center">
                                    <table style="border-collapse: collapse; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-yfti-tbllook: 480" class="MsoFooter" border="0" cellspacing="0" cellpadding="0">
                                      <tr style="mso-yfti-irow: 0; mso-yfti-firstrow: yes; mso-yfti-lastrow: yes">
                                        <td style="padding-bottom: 0cm; padding-left: 5.4pt; width: 426.1pt; padding-right: 5.4pt; padding-top: 0cm" valign="top" width="568">
                                          <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                                            <b><span lang="EN-US">Downloads: Eclipse 3.3 Downloads </span></b>
                                          </p></p> </p> 
                                          
                                          <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                                            <span lang="EN-US"></span>
                                          </p>
                                          
                                          <p>
                                            &#160;
                                          </p></p> 
                                          
                                          <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                                            <b><span lang="EN-US">1. MyEclipse Enterprise Workbench <chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">6.0.1</chsdate> GA for Windows 98/2000/NT/XP/Vista (<chsdate w:st="on" year="2007" month="10" day="16" islunardate="False" isrocdate="False">10/16/2007</chsdate>)</span></b><span lang="EN-US">&#160; <a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image042.gif"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image042" border="0" alt="clip_image042" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image042_thumb.gif" width="13" height="12" v:shapes="_x0000_i1046" /></a>Description: </span>
                                          </p></p> </p> 
                                          
                                          <div align="center">
                                            <table style="width: 95%; mso-padding-alt: 0cm 1.5pt 1.5pt 1.5pt; mso-cellspacing: 1.5pt" class="MsoNormalTable" border="0" cellpadding="0" width="95%">
                                              <tr style="mso-yfti-irow: 0; mso-yfti-firstrow: yes">
                                                <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; padding-top: 1.5pt" valign="top">
                                                  <p class="MsoNormal">
                                                    <span lang="EN-US"> <br />&#160;&#160; <a href="http://www.myeclipseide.com/Downloads-index-req-getit-lid-65.html"></a></span>
                                                  </p></p> </p> 
                                                  
                                                  <table style="width: 100%; mso-padding-alt: 2.25pt 2.25pt 2.25pt 2.25pt; mso-cellspacing: 2.2pt" class="MsoNormalTable" border="0" cellspacing="3" cellpadding="0" width="100%">
                                                    <tr style="mso-yfti-irow: 0; mso-yfti-firstrow: yes; mso-yfti-lastrow: yes">
                                                      <td style="padding-bottom: 2.25pt; padding-left: 2.25pt; padding-right: 2.25pt; padding-top: 2.25pt">
                                                        <p class="MsoNormal">
                                                          <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image043.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image043" border="0" alt="clip_image043" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image043_thumb.jpg" width="50" height="50" v:shapes="_x0000_i1047" /></a> </span>
                                                        </p></p> </p>
                                                      </td>
                                                      
                                                      <td style="padding-bottom: 2.25pt; padding-left: 2.25pt; padding-right: 2.25pt; padding-top: 2.25pt">
                                                        <p class="MsoNormal">
                                                          <span lang="EN-US"><a href="http://www.myeclipseide.com/Downloads-index-req-getit-lid-95.html"><span style="color: windowtext; text-decoration: none; text-underline: none"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image044" border="0" alt="clip_image044" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image044.jpg" width="150" height="75" v:shapes="_x0000_i1048" /></span></a> <br style="mso-special-character: line-break" /> <br style="mso-special-character: line-break" /></span>
                                                        </p></p> </p>
                                                      </td>
                                                      
                                                      <td style="padding-bottom: 2.25pt; padding-left: 2.25pt; padding-right: 2.25pt; padding-top: 2.25pt">
                                                        <p class="MsoNormal">
                                                          <span lang="EN-US"><a href="http://www.myeclipseide.com/Downloads-index-req-getit-lid-96.html"><span style="color: windowtext; text-decoration: none; text-underline: none"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image045" border="0" alt="clip_image045" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image045.jpg" width="150" height="75" v:shapes="_x0000_i1049" /></span></a> </span>
                                                        </p></p> </p>
                                                      </td>
                                                      
                                                      <td style="padding-bottom: 2.25pt; padding-left: 2.25pt; padding-right: 2.25pt; padding-top: 2.25pt">
                                                        <p class="MsoNormal">
                                                          <span lang="EN-US"><a href="http://www.myeclipseide.com/Downloads-index-req-getit-lid-120.html"><span style="color: windowtext; text-decoration: none; text-underline: none"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image046" border="0" alt="clip_image046" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image046.gif" width="150" height="75" v:shapes="_x0000_i1050" /></span></a> <br style="mso-special-character: line-break" /> <br style="mso-special-character: line-break" /></span>
                                                        </p></p> </p>
                                                      </td>
                                                    </tr>
                                                  </table>
                                                  
                                                  <p class="MsoNormal">
                                                    <span lang="EN-US"></span>
                                                  </p></p> </p>
                                                </td>
                                              </tr>
                                              
                                              <tr style="mso-yfti-irow: 1; mso-yfti-lastrow: yes">
                                                <td style="padding-bottom: 1.5pt; padding-left: 1.5pt; padding-right: 1.5pt; padding-top: 0cm" valign="top">
                                                  <p class="MsoNormal">
                                                    <span lang="EN-US">MyEclipse Enterprise Workbench <chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">6.0.1</chsdate> &#8211; Windows Edition is now available for download. Make sure to review the <a href="http://www.myeclipseide.com/module-htmlpages-display-pid-351.html" target="new">release notes</a>. Also make sure Eclipse 3.3.x and JDK 1.5.0_08 or a later release are installed if downloading other than the All-in-one installer. The All-in-One installer is bundled with Eclipse and JRE, and also supplies users with MyEclipse <a title="MyEclipse SNAPs: Lock-in Free Tools!" href="http://www.myeclipseide.com/module-htmlpages-display-pid-310.html">SNAPs</a>. You can download Eclipse Directly from the <a href="http://www.myeclipseide.com/module-htmlpages-display-pid-342.html" target="new">Genuitec Mirror site</a> or at Eclipse.org <a href="http://www.eclipse.org/downloads/" target="new">here</a>. <br />MyEclipse is also available for download through <a href="http://www.poweredbypulse.com">Pulse</a> &#8211; the new and easy way to download and manage all of your Eclipse Installs. </span>
                                                  </p></p> </p>
                                                </td>
                                              </tr>
                                            </table>
                                          </div>
                                          
                                          <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                                            <span lang="EN-US"> <br />Version: <chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">6.0.1</chsdate> GA | File size: 176.33 MB <br />MD5 : For All-in-One : 1eba3b2521e<chmetcnv unitname="C" sourcevalue="66870" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on">66870c</chmetcnv>07b9db3d62addc2 | For Windows Plugin: 504fc0aaa1e9b<chmetcnv unitname="F" sourcevalue="1252773" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on">1252773f</chmetcnv>816e<chmetcnv unitname="F" sourcevalue="443" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on">443f</chmetcnv>9d8 <br />Added on: 16-Oct-2007 </span>
                                          </p></p> </p> 
                                          
                                          <p style="layout-grid-mode: char; tab-stops: center 207.65pt right 415.3pt" class="MsoNormal">
                                            <span lang="EN-US"></span>
                                          </p>
                                          
                                          <p>
                                            &#160;
                                          </p></p>
                                        </td>
                                      </tr>
                                    </table>
                                  </div>
                                  
                                  <p style="text-align: center" class="MsoNormal" align="center">
                                    <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span><span lang="EN-US">1.22</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">下载不同版本的</span><span lang="EN-US">MyEclipse 6 </span>
                                  </p></p> </p> 
                                  
                                  <p class="MsoNormal">
                                    <span lang="EN-US"><span style="mso-spacerun: yes">&#160; </span></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">那么编号为</span><span lang="EN-US">1</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的就是最容易安装的</span><span lang="EN-US">ALL in ONE</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">版本；编号为</span><span lang="EN-US">2</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的就是插件（</span><span lang="EN-US">PLUG-IN</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">）版本，这个版本的安装需要你按照前文的叙述分别下载和安装</span><span lang="EN-US">JDK</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">以及</span><span lang="EN-US">Eclipse 3.3</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">；编号为</span><span lang="EN-US">3</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的是</span><span lang="EN-US">MyEclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">新推出的基于点对点的自动下载和安装工具。对于初学者来说，我们推荐下载</span><span lang="EN-US">ALL in ONE</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，基本上不会出什么问题。分别点击您需要的版本（二者只选其一即可）后即可开始下载过程，因为文件比较大，大约有</span><span lang="EN-US">200 MB</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，所以需要耐心等待。而</span><span lang="EN-US">ALL in ONE</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">版本则个头更大。</span><span lang="EN-US"> </span>
                                  </p></p> </p> 
                                  
                                  <h3>
                                    <a name="_Toc201479553"></a><chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False"><span style="mso-bookmark: _toc201479553"><span lang="EN-US">1.7.2</span></span></chsdate><span style="mso-bookmark: _toc201479553"><span lang="EN-US"> </span></span><span style="mso-bookmark: _toc201479553"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">安装</span></span><span lang="EN-US"> </p> 
                                    
                                    <p>
                                      </span></h3> 
                                      
                                      <h4>
                                        <a name="_Toc201479554"></a><a name="_1.7.2.1_ALL_in_ONE 版本的安装"></a><chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False"><span style="mso-bookmark: _toc201479554"><span lang="EN-US">1.7.2</span></span></chsdate><span style="mso-bookmark: _toc201479554"><span lang="EN-US">.1 ALL in ONE </span></span><span style="mso-bookmark: _toc201479554"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">版本的安装</span></span><span lang="EN-US"> </p> 
                                        
                                        <p>
                                          </span></h4> 
                                          
                                          <p class="MsoNormal">
                                            <b style="mso-bidi-font-weight: normal"><span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span></span></b><span lang="EN-US">ALL in ONE </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">直接双击文件就可以运行，无需选择更多选项</span><span lang="EN-US">(</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">这个下载的文件名可能是</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">MyEclipse_<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">6.0.1</chsdate>GA_E3.3.1_FullStackInstaller.exe</span></b><span lang="EN-US">)</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。首先第一个屏幕是欢迎页面，点击</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">Next</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">按钮继续，这一页显示的是许可协议，点击</span><span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image048.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image048" border="0" alt="clip_image048" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image048_thumb.jpg" width="217" height="25" v:shapes="_x0000_i1051" /></a></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，然后点击</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">Next</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">按钮继续安装，接下来显示的是安装路径，默认是安装到</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">C:\Program Files\MyEclipse 6.0</span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，因为前面已经讲过</span><span lang="EN-US"> Java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">程序在这种路径下可能会出现不必要的问题，因此推荐在安装的时候选择一个不带空格的安装路径，如下图所示：</span><span lang="EN-US"> </span>
                                          </p>
                                        </p></p> 
                                        
                                        <p style="text-align: center" class="MsoNormal" align="center">
                                          <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image050.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image050" border="0" alt="clip_image050" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image050_thumb.jpg" width="616" height="458" v:shapes="_x0000_i1052" /></a> </span>
                                        </p></p> </p> 
                                        
                                        <p style="text-align: center" class="MsoNormal" align="center">
                                          <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span><span lang="EN-US">1.23</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">修改</span><span lang="EN-US">MyEclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的安装目录为不带空格的路径</span><span lang="EN-US"> </span>
                                        </p></p> </p> 
                                        
                                        <p class="MsoNormal">
                                          <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，接着一路点击</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">Next</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">按钮等待直到最后完成安装即可。</span><span lang="EN-US"> </span>
                                        </p></p> </p> 
                                        
                                        <h4>
                                          <a name="_Toc201479555"></a><chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False"><span style="mso-bookmark: _toc201479555"><span lang="EN-US">1.7.2</span></span></chsdate><span style="mso-bookmark: _toc201479555"><span lang="EN-US">.2 </span></span><span style="mso-bookmark: _toc201479555"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">插件（</span><span lang="EN-US">PLUG-IN</span></span><span style="mso-bookmark: _toc201479555"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">）</span> </span><span style="mso-bookmark: _toc201479555"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">版本的安装</span></span><span lang="EN-US"> </p> 
                                          
                                          <p>
                                            </span></h4> 
                                            
                                            <p style="text-indent: 10.5pt; mso-char-indent-count: 1.0" class="MsoNormal">
                                              <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">插件版本的安装基本上和上述一致，所不同的是在接受协议后将会出现一个选择现有</span><span lang="EN-US">Eclipse 3.3</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">安装目录的对话框，如下图所示：</span><span lang="EN-US"> </span>
                                            </p>
                                          </p></p> 
                                          
                                          <p style="text-align: center; text-indent: 10.5pt; mso-char-indent-count: 1.0" class="MsoNormal" align="center">
                                            <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image052.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image052" border="0" alt="clip_image052" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image052_thumb.jpg" width="553" height="219" v:shapes="_x0000_i1053" /></a> </span>
                                          </p></p> </p> 
                                          
                                          <p style="text-align: center; text-indent: 10.5pt; mso-char-indent-count: 1.0" class="MsoNormal" align="center">
                                            <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span> <span lang="EN-US">1.24 </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">选中现有</span><span lang="EN-US"> Eclipse 3.3 </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的安装目录</span><span lang="EN-US"> </span>
                                          </p></p> </p> 
                                          
                                          <p style="text-indent: 10.5pt; mso-char-indent-count: 1.0" class="MsoNormal">
                                            <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">点击</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">Choose…</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">按钮后选中安装好的</span><span lang="EN-US">Eclipse 3.3</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">所在目录例如</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">c:\eclipse</span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">然后一路点击</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">Next</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">按钮即可。</span><span lang="EN-US"> </span>
                                          </p></p> </p> 
                                          
                                          <p style="text-indent: 21pt; mso-char-indent-count: 1.99" class="MsoNormal">
                                            <b style="mso-bidi-font-weight: normal"><span style="font-family: 宋体; color: red; mso-ascii-font-family: arial; mso-hansi-font-family: arial">注意：</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">如果你这里选择了错误的</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">版本例如</span><span lang="EN-US">3.2</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">等等，安装能够继续，但是安装完毕后</span><span lang="EN-US">MyEclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">将无法正常启动和使用。</span><span lang="EN-US"> </span>
                                          </p></p> </p> 
                                          
                                          <h4>
                                            <a name="_Toc201479556"></a><chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False"><span style="mso-bookmark: _toc201479556"><span lang="EN-US">1.7.2</span></span></chsdate><span style="mso-bookmark: _toc201479556"><span lang="EN-US">.3 </span></span><span style="mso-bookmark: _toc201479556"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">使用</span><span lang="EN-US">ALL In ONE </span></span><span style="mso-bookmark: _toc201479556"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">版本制作</span><span lang="EN-US">MyEclipse</span></span><span style="mso-bookmark: _toc201479556"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">绿色版</span></span><span lang="EN-US"> </p> 
                                            
                                            <p>
                                              </span></h4> 
                                              
                                              <p class="MsoNormal">
                                                <span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span>MyEclipse ALL In ONE</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">版本虽然安装方便，但是也有其缺点，就是安装过程时间太长了，而且一旦装好后目录就不能移动位置。想想如果你想把它放到移动硬盘上，或是挪到其它的空间比较充裕的盘上，或者是给同事的系统上共享一个，这时候就需要试试绿色版了！</span><span lang="EN-US"> </span>
                                              </p>
                                            </p></p> 
                                            
                                            <p style="text-indent: 21pt" class="MsoNormal">
                                              <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">安装完毕后得到一个完整的目录</span><span lang="EN-US">, </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">那么我们要做的就是修改一个配置文件</span><span lang="EN-US">, </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">创建一个启动</span><span lang="EN-US"> BAT </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">文件后就可以实现</span><span lang="EN-US"> MyEclipse 6 </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的免安装运行了</span><span lang="EN-US">, </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">换句话说我们可以放在移动硬盘上启动</span><span lang="EN-US">(</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">当然注册码自己想办法搞定</span><span lang="EN-US">)</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。</span><span lang="EN-US"> </span>
                                            </p></p> </p> 
                                            
                                            <p style="text-indent: 21pt" class="MsoNormal">
                                              <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">首先看安装后的目录</span><span lang="EN-US">: </span>
                                            </p></p> </p> 
                                            
                                            <p style="text-align: center" class="MsoNormal" align="center">
                                              <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image054.gif"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image054" border="0" alt="clip_image054" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image054_thumb.gif" width="220" height="210" v:shapes="_x0000_i1054" /></a> </span>
                                            </p></p> </p> 
                                            
                                            <p class="MsoNormal">
                                              <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">我们先在这个目录下新建一个文件</span><span lang="EN-US">: <b style="mso-bidi-font-weight: normal">MyEclipse 6.0.bat</b> , </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">文件内容如下</span><span lang="EN-US">: </span>
                                            </p></p> </p> 
                                            
                                            <p style="text-align: left; background: #e1ebf4; word-break: break-all; mso-margin-bottom-alt: auto; mso-pagination: widow-orphan" class="MsoNormal" align="left">
                                              <i style="mso-bidi-font-style: normal"><span style="font-family: &quot;Verdana&quot;,&quot;sans-serif&quot;; color: black; font-size: 12pt; mso-bidi-font-family: 宋体; mso-font-kerning: 0pt; mso-bidi-font-size: 10.5pt" lang="EN-US">start eclipse\eclipse.exe -vm jre\bin\javaw.exe </span></i>
                                            </p></p> </p> 
                                            
                                            <p class="MsoNormal">
                                              <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">接下来只需要改一个</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">插件的配置文件就可以实现绿色版运行了</span><span lang="EN-US">, </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">我们用记事本等文本编辑器打开下面的这个文件</span> <b style="mso-bidi-font-weight: normal"><span lang="EN-US">com.genuitec.eclipse.MyEclipse.link</span></b><span lang="EN-US">: </span>
                                            </p></p> </p> 
                                            
                                            <p style="text-align: center" class="MsoNormal" align="center">
                                              <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image056.gif"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image056" border="0" alt="clip_image056" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image056_thumb.gif" width="284" height="66" v:shapes="_x0000_i1055" /></a> </span>
                                            </p></p> </p> 
                                            
                                            <p class="MsoNormal">
                                              <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">文件原始内容如下所示</span><span lang="EN-US">: </span>
                                            </p></p> </p> 
                                            
                                            <p class="MsoNormal">
                                              <i style="mso-bidi-font-style: normal"><span lang="EN-US">path=d:\\Java\\MyEclipse6.0\\myeclipse </span></i>
                                            </p></p> </p> 
                                            
                                            <p class="MsoNormal">
                                              <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">这个是指定</span><span lang="EN-US"> myeclipse </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">这个插件目录的位置的</span><span lang="EN-US">, </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">我们把它改成相对路径即可</span><span lang="EN-US">: </span>
                                            </p></p> </p> 
                                            
                                            <p class="MsoNormal">
                                              <i style="mso-bidi-font-style: normal"><span lang="EN-US">path=..\\myeclipse </span></i>
                                            </p></p> </p> 
                                            
                                            <p class="MsoNormal">
                                              <span lang="EN-US">OK, </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">完工了</span><span lang="EN-US">, </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">把</span><span lang="EN-US">MyEclipse 6.0 </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">整个目录复制到你的移动硬盘上或者刻成光盘。以后当你的系统重做后或者拿着移动硬盘到了一个根本没装过</span><span lang="EN-US"> Java </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">工具的电脑上后</span><span lang="EN-US">, </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">双击批处理文件</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">MyEclipse 6.0.bat</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">即可立即启动</span><span lang="EN-US"> MyEclipse </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">来工作</span><span lang="EN-US">! </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">复制到硬盘上的任何目录</span><span lang="EN-US">(</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">注意路径建议不要带空格或者汉字</span><span lang="EN-US">), </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">也可以同样启动</span><span lang="EN-US">, </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">免去我们安装和配置之苦。不过，注册码还是要重新输入的，自己去购买正版吧！</span><span lang="EN-US"> </span>
                                            </p></p> </p> 
                                            
                                            <h3>
                                              <a name="_Toc201479557"></a><chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False"><span style="mso-bookmark: _toc201479557"><span lang="EN-US">1.7.3</span></span></chsdate><span style="mso-bookmark: _toc201479557"><span lang="EN-US"> </span></span><span style="mso-bookmark: _toc201479557"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">运行</span></span><span lang="EN-US"> </p> 
                                              
                                              <p>
                                                </span></h3> 
                                                
                                                <p class="MsoNormal">
                                                  <span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">点击</span><span lang="EN-US">Windows</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">系统的<b style="mso-bidi-font-weight: normal">开始</b>菜单后选择<b style="mso-bidi-font-weight: normal">所有程序</b>，然后选择</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">MyEclipse 6.0</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的快捷方式组里面的</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">MyEclipse <chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">6.0.1</chsdate></span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">即可运行，如下图所示：</span><span lang="EN-US"> </span>
                                                </p>
                                              </p></p> 
                                              
                                              <p style="text-align: center" class="MsoNormal" align="center">
                                                <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image058.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image058" border="0" alt="clip_image058" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image058_thumb.jpg" width="434" height="161" v:shapes="_x0000_i1056" /></a> </span>
                                              </p></p> </p> 
                                              
                                              <p style="text-align: center" class="MsoNormal" align="center">
                                                <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span> <span lang="EN-US">1.25 </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">通过快捷方式运行</span><span lang="EN-US"> MyEclipse 6 </span>
                                              </p></p> </p> 
                                              
                                              <p style="text-indent: 21.75pt" class="MsoNormal">
                                                <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">启动过程中会提示你选择</span><span lang="EN-US">workspace</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，点击</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">OK</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">按钮就可以继续启动，如前图</span><span lang="EN-US">1.19</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">所示。第一次启动后主界面还显示一个欢迎页面（</span><span lang="EN-US">Welcome</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">）</span><span lang="EN-US">,</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">点击上面的</span><span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0361.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image036" border="0" alt="clip_image036" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image036_thumb1.jpg" width="18" height="13" v:shapes="_x0000_i1057" /></a></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图标关闭欢迎页面，之后就可以进行开发了。这时界面如下所示：</span><span lang="EN-US"> </span>
                                              </p></p> </p> 
                                              
                                              <p style="text-align: center; text-indent: 21.75pt" class="MsoNormal" align="center">
                                                <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image060.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image060" border="0" alt="clip_image060" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image060_thumb.jpg" width="553" height="308" v:shapes="_x0000_i1058" /></a> </span>
                                              </p></p> </p> 
                                              
                                              <p style="text-align: center; text-indent: 21.75pt" class="MsoNormal" align="center">
                                                <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span><span lang="EN-US">1.26 MyEclipse 6</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的工作界面</span><span lang="EN-US"> </span>
                                              </p></p> </p> 
                                              
                                              <p style="text-align: center; text-indent: 21.75pt" class="MsoNormal" align="center">
                                                <span lang="EN-US"></span>
                                              </p>
                                              
                                              <p>
                                                &#160;
                                              </p></p> 
                                              
                                              <p style="text-indent: 21pt; mso-char-indent-count: 2.0" class="MsoNormal">
                                                <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">如果你购买或者获得了</span><span lang="EN-US">MyEclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的注册码，可以选择菜单</span> <b style="mso-bidi-font-weight: normal"><span lang="EN-US">MyEclipse <span style="mso-spacerun: yes">&#160;</span>> <span style="mso-spacerun: yes">&#160;</span>Subscription Information…</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">来输入，这样你就可以没有时间和功能限制的使用</span><span lang="EN-US"> MyEclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的所有功能了。</span><span lang="EN-US"> </span>
                                              </p></p> </p> 
                                              
                                              <p style="text-indent: 21pt; mso-char-indent-count: 2.0" class="MsoNormal">
                                                <span lang="EN-US"></span>
                                              </p>
                                              
                                              <p>
                                                &#160;
                                              </p></p> 
                                              
                                              <p style="text-indent: 21pt; mso-char-indent-count: 2.0" class="MsoNormal">
                                                <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">如果要卸载</span><span lang="EN-US">MyEclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">则点击</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">Uninstall MyEclipse <chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">6.0.1</chsdate> </span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">后安装提示一步步点击</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">Next</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">按钮即可。</span><span lang="EN-US"> </span>
                                              </p></p> </p> 
                                              
                                              <h2>
                                                <a name="_Toc201479558"><span lang="EN-US">1.8 Eclipse</span></a><span style="mso-bookmark: _toc201479558"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">运行出错的疑难解答</span></span><span lang="EN-US"> </p> 
                                                
                                                <p>
                                                  </span></h2> 
                                                  
                                                  <p class="MsoNormal">
                                                    <span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span>Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">或者</span><span lang="EN-US">MyEclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">在运行时不可避免的会出现运行失败的问题（一般会出来对话框告诉你出错了，出错文件放在某</span><span lang="EN-US">.log</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">文件中云云，点击确定后却看不到</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">主界面），最常见的原因通常是由于</span><span lang="EN-US">JRE</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">问题引起的。一般来说，最低的</span><span lang="EN-US">JRE/JDK</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">版本要求是</span><chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False"><span lang="EN-US">1.4.2</span></chsdate><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">以上，而如果要进行</span><span lang="EN-US">Java EE </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">开发，一般则需要至少</span><span lang="EN-US"> JDK 1.5 </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">或者更高版本。按照本章所描述的内容正常按照</span><span lang="EN-US">JDK</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">或者</span><span lang="EN-US">JRE</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">后，一般不会出现什么问题。然而，有的时候可能出现下列情况：</span><span lang="EN-US"> </span>
                                                  </p>
                                                </p></p> 
                                                
                                                <p style="text-indent: -21pt; margin-left: 21pt; tab-stops: list 21.0pt; mso-list: l13 level1 lfo20" class="MsoNormal">
                                                  <span style="mso-bidi-font-family: arial; mso-fareast-font-family: arial" lang="EN-US"><span style="mso-list: ignore">1.<span style="font: 7pt &quot;Times New Roman&quot;">&#160;&#160;&#160;&#160;&#160; </span></span></span><span lang="EN-US">JDK/JRE</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">安装出现失败，导致部分文件不完整，致使</span><span lang="EN-US">java.exe</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">无法运行；</span><span lang="EN-US"> </span>
                                                </p></p> </p> 
                                                
                                                <p style="text-indent: -21pt; margin-left: 21pt; tab-stops: list 21.0pt; mso-list: l13 level1 lfo20" class="MsoNormal">
                                                  <span style="mso-bidi-font-family: arial; mso-fareast-font-family: arial" lang="EN-US"><span style="mso-list: ignore">2.<span style="font: 7pt &quot;Times New Roman&quot;">&#160;&#160;&#160;&#160;&#160; </span></span></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">安装了一些软件，这些软件自身带有低版本的</span><span lang="EN-US">JDK/JRE</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，致使</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">启动的时候无法找到正常的</span><span lang="EN-US">JRE</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，例如</span><span lang="EN-US">Oracle 9 </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">和</span><span lang="EN-US"> JBuilder 2005/2006 </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">等软件安装后，就会导致这种问题。</span><span lang="EN-US"> </span>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">这时候读者可以尝试用指定</span><span lang="EN-US">JVM</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的办法来启动</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">（</span><span lang="EN-US">MyEclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">也相同），假设您的</span><span lang="EN-US">JDK</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">安装在目录</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">c:\jdk<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">1.6.0</chsdate></span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">或者是</span><span lang="EN-US">JRE</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">安装在目录</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">c:\Program Files\Java\JRE1.6.0</span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">：进入</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">eclipse.exe</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">所在的目录，例如</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">c:\eclipse</span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">或者</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">c:\Program Files\MyEclipse\eclipse</span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，在目录下新建</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">run.bat</span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，文件内容如下所示：</span><span lang="EN-US"> </span>
                                                </p></p> </p> 
                                                
                                                <table style="border-bottom: medium none; border-left: medium none; border-collapse: collapse; border-top: medium none; border-right: medium none; mso-padding-alt: 0cm 5.4pt 0cm 5.4pt; mso-border-alt: solid windowtext .5pt; mso-yfti-tbllook: 480" class="MsoTableGrid" border="1" cellspacing="0" cellpadding="0">
                                                  <tr style="mso-yfti-irow: 0; mso-yfti-firstrow: yes; mso-yfti-lastrow: yes">
                                                    <td style="border-bottom: windowtext 1pt solid; border-left: windowtext 1pt solid; padding-bottom: 0cm; padding-left: 5.4pt; width: 426.1pt; padding-right: 5.4pt; border-top: windowtext 1pt solid; border-right: windowtext 1pt solid; padding-top: 0cm; mso-border-alt: solid windowtext .5pt" valign="top" width="568">
                                                      <p class="MsoNormal">
                                                        <span lang="EN-US">start eclipse.exe –vm <i style="mso-bidi-font-style: normal">c:\jdk<chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">1.6.0</chsdate>\bin\javaw.exe</i> </span>
                                                      </p></p> </p>
                                                    </td>
                                                  </tr>
                                                </table>
                                                
                                                <p class="MsoNormal">
                                                  <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。以后通过双击此</span><span lang="EN-US">run.bat</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">来启动</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">即可。</span><span lang="EN-US"> </span>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">还有的读者，使用</span><span lang="EN-US">MyEclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">开发项目后，随着项目文件的增多，以及运行时间的增加，实际上</span><span lang="EN-US">MyEclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">所消耗的内存是会一直增大的，有的时候会出现</span><span lang="EN-US">MyEclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">自身内存不足的情况，一般会出现下面的提示对话框：</span><span lang="EN-US"> </span>
                                                </p></p> </p> 
                                                
                                                <p style="text-align: center" class="MsoNormal" align="center">
                                                  <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image062.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image062" border="0" alt="clip_image062" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image062_thumb.jpg" width="564" height="182" v:shapes="_x0000_i1059" /></a> </span>
                                                </p></p> </p> 
                                                
                                                <p style="text-align: center" class="MsoNormal" align="center">
                                                  <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span><span lang="EN-US"> 1.27 </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">内存不足提示对话框</span><span lang="EN-US"> </span>
                                                </p></p> </p> 
                                                
                                                <p style="text-align: center" class="MsoNormal" align="center">
                                                  <span lang="EN-US"></span>
                                                </p>
                                                
                                                <p>
                                                  &#160;
                                                </p></p> 
                                                
                                                <p class="MsoNormal">
                                                  <span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">读者不要慌张，一般情况下这是因为</span><span lang="EN-US">MyEclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">占用到了它所能达到的最高内存。出于安全方面的考虑，</span><span lang="EN-US">Java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">本身不会把所有的系统内存都占为己有，而是会分配一个最大值，一旦到达此最大值，运行的程序就会出现</span><span lang="EN-US">OutOfMemery </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">错误。怎么修改它呢？同样的在刚刚提到的</span><span lang="EN-US">eclipse.exe</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">所在目录一般都有个文件叫</span><span lang="EN-US">eclipse.ini</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，用记事本啊，</span><span lang="EN-US">EditPlus</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">或者</span><span lang="EN-US">UltraEdit</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">或者免费的</span><span lang="EN-US">Notepad++</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，</span><span lang="EN-US">Notepad2</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">等软件都可以打开它，之后修改内容为如下所示：</span><span lang="EN-US"> </span>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <i style="mso-bidi-font-style: normal"><span lang="EN-US">-showsplash </span></i>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <i style="mso-bidi-font-style: normal"><span lang="EN-US">com.genuitec.myeclipse.product </span></i>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <i style="mso-bidi-font-style: normal"><span lang="EN-US">&#8211;launcher.XXMaxPermSize </span></i>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <chmetcnv unitname="m" sourcevalue="256" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on"><i style="mso-bidi-font-style: normal"><span style="mso-ansi-language: fr" lang="FR">256m</span></i></chmetcnv><i style="mso-bidi-font-style: normal"><span style="mso-ansi-language: fr" lang="FR"> </span></i>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <i style="mso-bidi-font-style: normal"><span style="mso-ansi-language: fr" lang="FR">-vmargs </span></i>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <i style="mso-bidi-font-style: normal"><span style="mso-ansi-language: fr" lang="FR">-Xms<chmetcnv unitname="m" sourcevalue="128" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on">128m</chmetcnv> </span></i>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <i style="mso-bidi-font-style: normal"><span style="mso-ansi-language: fr" lang="FR">-Xmx<chmetcnv unitname="m" sourcevalue="512" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on">512m</chmetcnv> </span></i>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <i style="mso-bidi-font-style: normal"><span style="mso-ansi-language: fr" lang="FR">-Duser.language=en </span></i>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <i style="mso-bidi-font-style: normal"><span lang="EN-US">-XX:PermSize=<chmetcnv unitname="m" sourcevalue="128" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on">128M</chmetcnv> </span></i>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <i style="mso-bidi-font-style: normal"><span lang="EN-US">-XX:MaxPermSize=<chmetcnv unitname="m" sourcevalue="256" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on">256M</chmetcnv> </span></i>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。主要需要修改的参数一般是</span><span lang="EN-US">-Xmx<chmetcnv unitname="m" sourcevalue="512" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on">512m</chmetcnv></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，它表示所能使用的最大内存为</span><span lang="EN-US">512MB</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。一般来说改成你电脑上能有的实际内存大小的</span><span lang="EN-US">80</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">％左右是没问题的，如果你电脑有</span><chmetcnv unitname="g" sourcevalue="2" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on"><span lang="EN-US">2G</span></chmetcnv><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">内存，你可以把它修改为</span><chmetcnv unitname="m" sourcevalue="1024" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on"><span lang="EN-US">1024M</span></chmetcnv><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。然而有趣的是，不要改成超过</span><chmetcnv unitname="g" sourcevalue="1.5" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on"><span lang="EN-US">1.5G</span></chmetcnv><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">大小的数值，否则反而会不稳定（</span><span lang="EN-US">Windows</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">下面的经验），容易莫名退出。</span><span lang="EN-US"> </span>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">读者还可以观察</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">所提供的内存指示器，操作方法是选择菜单</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">Window > Preferences</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，点中左侧的</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">General</span></b><span lang="EN-US"> </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">节点，然后选中复选框</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">Show heap status</span></b><span lang="EN-US"> </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，之后就可以在状态栏里面看到内存状态指示器了。如右图所示：</span><span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image064.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image064" border="0" alt="clip_image064" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image064_thumb.jpg" width="87" height="22" v:shapes="_x0000_i1060" /></a></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。</span><span lang="EN-US"> </span>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">下面给一些这些参数的解释供读者了解：</span><span lang="EN-US"> </span>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <span lang="EN-US">JVM </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">提供了各种用于调整内存分配和垃圾回收行为的标准开关和非标准开关。其中一些设置可以提高</span><span lang="EN-US"> JAVA IDE </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的性能。</span><span lang="EN-US"> </span>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">注意，由于</span><span lang="EN-US"> -X </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">（尤其是</span><span lang="EN-US"> -XX JVM</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">）开关通常是</span><span lang="EN-US"> JVM </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">或</span><span lang="EN-US"> JVM </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">供应商特定的，本部分介绍的开关可用于</span><span lang="EN-US"> Sun Microsystems J2SE <chsdate w:st="on" year="1899" month="12" day="30" islunardate="False" isrocdate="False">1.4.2</chsdate></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">以及</span><span lang="EN-US">JDK 1.5</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。</span><span lang="EN-US"> </span>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <span lang="EN-US"></span>
                                                </p>
                                                
                                                <p>
                                                  &#160;
                                                </p></p> 
                                                
                                                <p class="MsoNormal">
                                                  <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">以下设置在大多数系统上将产生比工厂更好的设置性能。</span><span lang="EN-US"> </span>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <b style="mso-bidi-font-weight: normal"><span lang="EN-US">-vmargs</span></b><span lang="EN-US"> &#8211; </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">表示将后面的所有参数直接传递到所指示的</span><span lang="EN-US"> Java VM</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。</span><span lang="EN-US"> </span>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <span lang="EN-US"></span>
                                                </p>
                                                
                                                <p>
                                                  &#160;
                                                </p></p> 
                                                
                                                <p class="MsoNormal">
                                                  <b style="mso-bidi-font-weight: normal"><span lang="EN-US">-Xverify:none</span></b><span lang="EN-US"> &#8211; </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">此开关关闭</span><span lang="EN-US">Java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">字节码验证，从而加快了类装入的速度，并使得在仅为验证目的而启动的过程中无需装入类。此开关缩短了启动时间，因此没有理由不使用它。</span><span lang="EN-US"> </span>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <span lang="EN-US"></span>
                                                </p>
                                                
                                                <p>
                                                  &#160;
                                                </p></p> 
                                                
                                                <p class="MsoNormal">
                                                  <b style="mso-bidi-font-weight: normal"><span lang="EN-US">-Xms<chmetcnv unitname="m" sourcevalue="24" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on">24m</chmetcnv> </span></b><span lang="EN-US">&#8211; </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">此设置指示</span><span lang="EN-US"> Java </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">虚拟机将其初始堆大小设置为</span><span lang="EN-US"> 24 MB</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。通过指示</span><span lang="EN-US"> JVM </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">最初应分配给堆的内存数量，可以使</span><span lang="EN-US"> JVM </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">不必在</span><span lang="EN-US"> IDE </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">占用较多内存时增加堆大小。</span><span lang="EN-US"> </span>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <span lang="EN-US"></span>
                                                </p>
                                                
                                                <p>
                                                  &#160;
                                                </p></p> 
                                                
                                                <p class="MsoNormal">
                                                  <b style="mso-bidi-font-weight: normal"><span lang="EN-US">-Xmx<chmetcnv unitname="m" sourcevalue="96" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on">96m</chmetcnv></span></b><span lang="EN-US"> &#8211; </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">此设置指定</span><span lang="EN-US"> Java </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">虚拟机应对堆使用的最大内存数量。为此数量设置上限表示</span><span lang="EN-US"> Java </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">进程消耗的内存数量不得超过可用的物理内存数量。对于具有更多内存的系统可以增加此限制，</span><span lang="EN-US">96 MB </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">设置有助于确保</span><span lang="EN-US"> IDE </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">在内存量为</span><span lang="EN-US"> 128MB </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">到</span><span lang="EN-US"> 256MB </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的系统上能够可靠地执行操作。注意：不要将该值设置为接近或大于系统的物理内存量，否则将在主要回收过程中导致频繁的交换操作。</span><span lang="EN-US"> </span>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <span lang="EN-US"></span>
                                                </p>
                                                
                                                <p>
                                                  &#160;
                                                </p></p> 
                                                
                                                <p class="MsoNormal">
                                                  <b style="mso-bidi-font-weight: normal"><span lang="EN-US">-XX:PermSize=<chmetcnv unitname="m" sourcevalue="20" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on">20m</chmetcnv></span></b><span lang="EN-US"> &#8211; </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">此</span><span lang="EN-US"> JVM </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">开关不仅功能更为强大，而且能够缩短启动时间。该设置用于调整内存</span><span lang="EN-US">"</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">永久区域</span><span lang="EN-US">"</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">（类保存在该区域中）的大小。因此我们向</span><span lang="EN-US"> JVM </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">提示它将需要的内存量。该设置消除了许多系统启动过程中的主要垃圾收集事件。</span><span lang="EN-US">SunONE Studio </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">或其它包含更多模块的</span><span lang="EN-US"> IDE </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的用户可能希望将该数值设置得更高。</span><span lang="EN-US"> </span>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">下面列出了其它一些可能对</span><span lang="EN-US"> ECLIPSE </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">在某些系统（不是所有系统）上的性能产生轻微或明显影响的</span><span lang="EN-US"> JVM </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">开关。尽管使用它们会产生一定的影响，但仍值得一试。</span><span lang="EN-US"> </span>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <span lang="EN-US"></span>
                                                </p>
                                                
                                                <p>
                                                  &#160;
                                                </p></p> 
                                                
                                                <p class="MsoNormal">
                                                  <b style="mso-bidi-font-weight: normal"><span lang="EN-US">-XX:CompileThreshold=100</span></b><span lang="EN-US"> &#8211; </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">此开关将降低启动速度，原因是与不使用此开关相比，</span><span lang="EN-US">HotSpot </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">能够更快地将更多的方法编译为本地代码。其结果是提高了</span><span lang="EN-US"> IDE </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">运行时的性能，这是因为更多的</span><span lang="EN-US"> UI </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">代码将被编译而不是被解释。该值表示方法在被编译前必须被调用的次数。</span><span lang="EN-US"> </span>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <span lang="EN-US"></span>
                                                </p>
                                                
                                                <p>
                                                  &#160;
                                                </p></p> 
                                                
                                                <p class="MsoNormal">
                                                  <b style="mso-bidi-font-weight: normal"><span lang="EN-US">-XX:+UseConcMarkSweepGC -XX:+UseParNewGC</span></b><span lang="EN-US"> &#8211; </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">如果垃圾回收频繁中断，则请尝试使用这些开关。此开关导致</span><span lang="EN-US"> JVM </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">对主要垃圾回收事件（如果在多处理器工作站上运行，则也适用于次要回收事件）使用不同的算法，这些算法不会影响整个垃圾回收进程。注意：目前尚不确定此收集器是提高还是降低单处理器计算机的性能。</span><span lang="EN-US"> </span>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <span lang="EN-US"></span>
                                                </p>
                                                
                                                <p>
                                                  &#160;
                                                </p></p> 
                                                
                                                <p class="MsoNormal">
                                                  <b style="mso-bidi-font-weight: normal"><span lang="EN-US">-XX:+UseParallelGC</span></b><span lang="EN-US"> &#8211; </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">某些测试表明，至少在内存配置相当良好的单处理器系统中，使用此回收算法可以将次要垃圾回收的持续时间减半。注意，这是一个矛盾的问题，事实上此回收器主要适用于具有千兆字节堆的多处理器。尚无可用数据表明它对主要垃圾回收的影响。注意：此回收器与</span><span lang="EN-US"> -XX:+UseConcMarkSweepGC </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">是互斥的。</span><span lang="EN-US"> </span>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <span lang="EN-US"></span>
                                                </p>
                                                
                                                <p>
                                                  &#160;
                                                </p></p> 
                                                
                                                <p class="MsoNormal">
                                                  <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">假设机器是</span><span lang="EN-US">512MB</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的内存，可以用这样的</span><span lang="EN-US">eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">启动参数：</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">eclipse.exe -vmargs -Xverify:none -Xms<chmetcnv unitname="m" sourcevalue="64" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on">64M</chmetcnv> -Xmx<chmetcnv unitname="m" sourcevalue="256" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on">256M</chmetcnv> -XX:PermSize=<chmetcnv unitname="m" sourcevalue="20" hasspace="False" negative="False" numbertype="1" tcsc="0" w:st="on">20M</chmetcnv><span style="mso-spacerun: yes">&#160; </span>-XX:+UseParallelGC</span></i><span lang="EN-US"> </span>
                                                </p></p> </p> 
                                                
                                                <p class="MsoNormal">
                                                  <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。</span><span lang="EN-US"> </span>
                                                </p></p> </p> 
                                                
                                                <h2>
                                                  <a name="_Toc201479559"><span lang="EN-US">1.9 </span></a><span style="mso-bookmark: _toc201479559"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">使用高级进程管理器来管理</span><span lang="EN-US">Java</span></span><span style="mso-bookmark: _toc201479559"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">进程</span></span><span lang="EN-US"> </p> 
                                                  
                                                  <p>
                                                    </span></h2> 
                                                    
                                                    <p class="MsoNormal">
                                                      <span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">由于</span><span lang="EN-US">Java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的进程，默认情况下使用</span><span lang="EN-US">Windows</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">自带的任务管理器（在</span><span lang="EN-US">Windows XP</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">下按下</span><b style="mso-bidi-font-weight: normal"><span lang="EN-US">Ctrl + Alt + Del</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">组合键，或者在任务栏空白处点右键然后选择菜单中的任务管理器），不管多少个</span><span lang="EN-US">java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">进程，只在进程的映像名称一栏统一显示一个</span><span lang="EN-US">java.exe</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，如果有多个进程，则无法区分，也看不到命令运行时的参数和启动路径。因为有时</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">会莫名崩溃，或者失去响应强行杀死后，原来启动的进程，包括服务器的和程序的，并不会跟随主进程而自行销毁，这时候就需要我们使用一款专业的微软收购不久的一个公司</span><span lang="EN-US">Sysinternals</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">提供的免费进程管理工具：</span><span lang="EN-US">Process Explorer</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">来查看并管理这些进程了。它的下载地址是</span><span lang="EN-US"><a href="http://download.sysinternals.com/Files/ProcessExplorer.zip">http://download.sysinternals.com/Files/ProcessExplorer.zip</a></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，下载说明页面是</span><span lang="EN-US"><a href="http://technet.microsoft.com/en-us/sysinternals/bb896653.aspx">http://technet.microsoft.com/en-us/sysinternals/bb896653.aspx</a> </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。下载后解压缩并运行其中的</span><span lang="EN-US">procexp.exe</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">即可看到系统进程列表，在图中启动了三个</span><span lang="EN-US">Java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">进程。参考图</span><span lang="EN-US">1.28</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。</span><span lang="EN-US"> </span>
                                                    </p>
                                                  </p></p> 
                                                  
                                                  <p style="text-align: center" class="MsoNormal" align="center">
                                                    <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image066.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image066" border="0" alt="clip_image066" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image066_thumb.jpg" width="553" height="405" v:shapes="_x0000_i1061" /></a> </span>
                                                  </p></p> </p> 
                                                  
                                                  <p style="text-align: center" class="MsoNormal" align="center">
                                                    <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image068.jpg"><img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="clip_image068" border="0" alt="clip_image068" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image068_thumb.jpg" width="439" height="515" v:shapes="_x0000_i1062" /></a> </span>
                                                  </p></p> </p> 
                                                  
                                                  <p style="text-align: center" class="MsoNormal" align="center">
                                                    <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span><span lang="EN-US">1.28 </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">高级进程管理器</span><span lang="EN-US"> </span>
                                                  </p></p> </p> 
                                                  
                                                  <p style="text-align: center" class="MsoNormal" align="center">
                                                    <span lang="EN-US"></span>
                                                  </p>
                                                  
                                                  <p>
                                                    &#160;
                                                  </p></p> 
                                                  
                                                  <p class="MsoNormal">
                                                    <span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">双击进程后，即可看到进程的启动参数，当前工作目录，进程所在目录，这样就可以明白新建文件时候它存放的相对路径，以及可以在电脑上安装了多个版本的</span><span lang="EN-US">JDK</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">时，区分到底用了哪个。还可以直接复制</span><span lang="EN-US">Command line</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">中的内容，修改为相对路径后制作进程的快速启动批处理文件（</span><span lang="EN-US">.cmd</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，</span><span lang="EN-US">.bat</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">），当然，选择性的杀死正确的进程就不用多介绍了。如果进行</span><span lang="EN-US">Web</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">开发时，发现</span><span lang="EN-US">Tomcat</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">老启动时报错</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">java.net.BindException: Address already in use: JVM_Bind</span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，就可以用这个工具看看是不是重复启动了多个</span><span lang="EN-US">Tomcat</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">了。</span><span lang="EN-US"> </span>
                                                  </p></p> </p> 
                                                  
                                                  <h2>
                                                    <a name="_Toc201479560"><span lang="EN-US">1.10 </span></a><span style="mso-bookmark: _toc201479560"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">小结</span></span><span lang="EN-US"> </p> 
                                                    
                                                    <p>
                                                      </span></h2> 
                                                      
                                                      <p style="text-indent: 21pt" class="MsoNormal">
                                                        <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">通过本章的介绍，您应该大致了解了本书所使用的</span><span lang="EN-US">Java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，数据库以及服务器软件的安装，设置和运行方式。再次强调如果使用</span><span lang="EN-US">MyEclipse 6.0 ALL in ONE</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">版本，将会最大限度的减少安装难度。</span><span lang="EN-US"> </span>
                                                      </p>
                                                    </p></p> 
                                                    
                                                    <p>
                                                      <span style="font-family: &quot;Arial&quot;,&quot;sans-serif&quot;; font-size: 10.5pt; mso-bidi-font-family: &#39;Times New Roman&#39;; mso-font-kerning: 1.0pt; mso-ansi-language: en-us; mso-fareast-font-family: 宋体; mso-fareast-language: zh-cn; mso-bidi-language: ar-sa" lang="EN-US"> <br style="page-break-before: always; mso-special-character: line-break" clear="all" /></span></span>
                                                    </p>
                                                    
                                                    <p>
                                                      转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2010/09/09/myeclipse-6-java-%e5%bc%80%e5%8f%91%e4%b8%ad%e6%96%87%e6%95%99%e7%a8%8b%e7%8b%ac%e5%ae%b6%e8%bf%9e%e8%bd%bd-%e7%ac%ac%e4%b8%80%e7%ab%a0-%e5%ae%89%e8%a3%85%e9%85%8d%e7%bd%ae%e5%bc%80%e5%8f%91/">MyEclipse 6 Java 开发中文教程独家连载 &#8211; 第一章 安装配置开发环境</a>
                                                    </p>