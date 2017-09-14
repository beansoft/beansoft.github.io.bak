---
id: 588
title: Applet安全限制和签名Applet
date: 2010-08-20T19:28:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=588
permalink: '/2010/08/20/applet%e5%ae%89%e5%85%a8%e9%99%90%e5%88%b6%e5%92%8c%e7%ad%be%e5%90%8dapplet/'
views:
  - "4185"
original_post_id:
  - "588"
image: /wp-content/uploads/2012/09/clip_image002_thumb3.jpg
categories:
  - Java SE
tags:
  - Applet
  - Signer
---
作者: 刘长炯 整理日期 2008-05-11 10:44:00

<div class="posttitle">
  Applet安全限制和签名Applet
</div>

<p class="MsoNormal">
  <span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">因为</span><span lang="EN-US">Applet</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">在浏览器中运行，所以，并不是什么操作都能做，例如不能读写创建文件，不能任意连接网站等等，总之就是不可威胁用户电脑的信息安全。下面我们来试试看，新建一个文件操作的</span><span lang="EN-US">Applet</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，代码清单如下：</span>
</p>

<p class="MsoNormal">
  <b style="mso-bidi-font-weight: normal"><span lang="EN-US">applets.FileOperationApplet </span> </p> 
  
  <p>
    </b>
  </p></p> 
  
  <table style="border-bottom-style: none; border-right-style: none; border-collapse: collapse; border-top-style: none; border-left-style: none; mso-border-alt: solid windowtext .5pt; mso-yfti-tbllook: 480; mso-padding-alt: 0pt 5.4pt 0pt 5.4pt; mso-border-insideh: .5pt solid windowtext; mso-border-insidev: .5pt solid windowtext" class="MsoTableGrid" border="1" cellspacing="0" cellpadding="0">
    <tr style="mso-yfti-irow: 0; mso-yfti-firstrow: yes; mso-yfti-lastrow: yes">
      <td style="border-bottom: windowtext 1pt solid; border-left: windowtext 1pt solid; padding-bottom: 0pt; padding-left: 5.4pt; width: 426.1pt; padding-right: 5.4pt; border-top: windowtext 1pt solid; border-right: windowtext 1pt solid; padding-top: 0pt; mso-border-alt: solid windowtext .5pt" valign="top" width="568">
        <p style="text-align: left; mso-layout-grid-align: none" class="MsoNormal" align="left">
          <b><span style="font-family: &#39;Courier New&#39;; color: #7f0055; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">package</span></b><span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> applets;</span><span style="font-family: &#39;Courier New&#39;; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> </span>
        </p></p> 
        
        <p style="text-align: left; mso-layout-grid-align: none" class="MsoNormal" align="left">
          <span style="font-family: &#39;Courier New&#39;; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"></span>
        </p>
        
        <p>
          &#160;
        </p></p> 
        
        <p style="text-align: left; mso-layout-grid-align: none" class="MsoNormal" align="left">
          <b><span style="font-family: &#39;Courier New&#39;; color: #7f0055; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">import</span></b><span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> java.applet.Applet;</span><span style="font-family: &#39;Courier New&#39;; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> </span>
        </p></p> 
        
        <p style="text-align: left; mso-layout-grid-align: none" class="MsoNormal" align="left">
          <b><span style="font-family: &#39;Courier New&#39;; color: #7f0055; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">import</span></b><span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> java.awt.Label;</span><span style="font-family: &#39;Courier New&#39;; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> </span>
        </p></p> 
        
        <p style="text-align: left; mso-layout-grid-align: none" class="MsoNormal" align="left">
          <b><span style="font-family: &#39;Courier New&#39;; color: #7f0055; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">import</span></b><span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> java.io.*;</span><span style="font-family: &#39;Courier New&#39;; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> </span>
        </p></p> 
        
        <p style="text-align: left; mso-layout-grid-align: none" class="MsoNormal" align="left">
          <span style="font-family: &#39;Courier New&#39;; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"></span>
        </p>
        
        <p>
          &#160;
        </p></p> 
        
        <p style="text-align: left; mso-layout-grid-align: none" class="MsoNormal" align="left">
          <b><span style="font-family: &#39;Courier New&#39;; color: #7f0055; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">public</span></b><span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> </span><b><span style="font-family: &#39;Courier New&#39;; color: #7f0055; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">class</span></b><span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> FileOperationApplet </span><b><span style="font-family: &#39;Courier New&#39;; color: #7f0055; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">extends</span></b><span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> Applet {</span><span style="font-family: &#39;Courier New&#39;; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> </span>
        </p></p> 
        
        <p style="text-align: left; mso-layout-grid-align: none" class="MsoNormal" align="left">
          <span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160; </span></span><b><span style="font-family: &#39;Courier New&#39;; color: #7f0055; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">public</span></b><span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> </span><b><span style="font-family: &#39;Courier New&#39;; color: #7f0055; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">void</span></b><span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> start() {</span><span style="font-family: &#39;Courier New&#39;; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> </span>
        </p></p> 
        
        <p style="text-align: left; mso-layout-grid-align: none" class="MsoNormal" align="left">
          <span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"><span style="mso-tab-count: 2">&#160;&#160;&#160;&#160;&#160;&#160; </span></span><b><span style="font-family: &#39;Courier New&#39;; color: #7f0055; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">try</span></b><span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> {</span><span style="font-family: &#39;Courier New&#39;; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> </span>
        </p></p> 
        
        <p style="text-align: left; mso-layout-grid-align: none" class="MsoNormal" align="left">
          <span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"><span style="mso-tab-count: 3">&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; </span>FileWriter out = </span><b><span style="font-family: &#39;Courier New&#39;; color: #7f0055; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">new</span></b><span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> FileWriter(</span><span style="font-family: &#39;Courier New&#39;; color: #2a00ff; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">"c:\\test.txt"</span><span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">);</span><span style="font-family: &#39;Courier New&#39;; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> </span>
        </p></p> 
        
        <p style="text-align: left; mso-layout-grid-align: none" class="MsoNormal" align="left">
          <span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"><span style="mso-tab-count: 3">&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; </span>out.write(</span><span style="font-family: &#39;Courier New&#39;; color: #2a00ff; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">"</span><span style="font-family: 宋体; color: #2a00ff; font-size: 10pt; mso-ascii-font-family: &#39;Courier New&#39;; mso-hansi-font-family: &#39;Courier New&#39;; mso-font-kerning: 0pt; mso-bidi-font-family: &#39;Courier New&#39;">测试写入文件</span><span style="font-family: &#39;Courier New&#39;; color: #2a00ff; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">"</span><span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">);</span><span style="font-family: &#39;Courier New&#39;; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> </span>
        </p></p> 
        
        <p style="text-align: left; mso-layout-grid-align: none" class="MsoNormal" align="left">
          <span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"><span style="mso-tab-count: 3">&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; </span>out.close();</span><span style="font-family: &#39;Courier New&#39;; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> </span>
        </p></p> 
        
        <p style="text-align: left; mso-layout-grid-align: none" class="MsoNormal" align="left">
          <span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"><span style="mso-tab-count: 3">&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; </span>add(</span><b><span style="font-family: &#39;Courier New&#39;; color: #7f0055; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">new</span></b><span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> Label(</span><span style="font-family: &#39;Courier New&#39;; color: #2a00ff; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">"</span><span style="font-family: 宋体; color: #2a00ff; font-size: 10pt; mso-ascii-font-family: &#39;Courier New&#39;; mso-hansi-font-family: &#39;Courier New&#39;; mso-font-kerning: 0pt; mso-bidi-font-family: &#39;Courier New&#39;">文件写入成功</span><span style="font-family: &#39;Courier New&#39;; color: #2a00ff; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">"</span><span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">));</span><span style="font-family: &#39;Courier New&#39;; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> </span>
        </p></p> 
        
        <p style="text-align: left; mso-layout-grid-align: none" class="MsoNormal" align="left">
          <span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"><span style="mso-tab-count: 2">&#160;&#160;&#160;&#160;&#160;&#160; </span>} </span><b><span style="font-family: &#39;Courier New&#39;; color: #7f0055; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">catch</span></b><span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> (IOException e) {</span><span style="font-family: &#39;Courier New&#39;; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> </span>
        </p></p> 
        
        <p style="text-align: left; mso-layout-grid-align: none" class="MsoNormal" align="left">
          <span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"><span style="mso-tab-count: 3">&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; </span></span><span style="font-family: &#39;Courier New&#39;; color: #3f7f5f; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">// </span><b><span style="font-family: &#39;Courier New&#39;; color: #7f9fbf; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">TODO</span></b><span style="font-family: &#39;Courier New&#39;; color: #3f7f5f; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> Auto-generated catch block</span><span style="font-family: &#39;Courier New&#39;; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> </span>
        </p></p> 
        
        <p style="text-align: left; mso-layout-grid-align: none" class="MsoNormal" align="left">
          <span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"><span style="mso-tab-count: 3">&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; </span>e.printStackTrace();</span><span style="font-family: &#39;Courier New&#39;; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> </span>
        </p></p> 
        
        <p style="text-align: left; mso-layout-grid-align: none" class="MsoNormal" align="left">
          <span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"><span style="mso-tab-count: 3">&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; </span>add(</span><b><span style="font-family: &#39;Courier New&#39;; color: #7f0055; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">new</span></b><span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> Label(</span><span style="font-family: &#39;Courier New&#39;; color: #2a00ff; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">"</span><span style="font-family: 宋体; color: #2a00ff; font-size: 10pt; mso-ascii-font-family: &#39;Courier New&#39;; mso-hansi-font-family: &#39;Courier New&#39;; mso-font-kerning: 0pt; mso-bidi-font-family: &#39;Courier New&#39;">文件写入失败</span><span style="font-family: &#39;Courier New&#39;; color: #2a00ff; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">"</span><span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">));</span><span style="font-family: &#39;Courier New&#39;; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> </span>
        </p></p> 
        
        <p style="text-align: left; mso-layout-grid-align: none" class="MsoNormal" align="left">
          <span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"><span style="mso-tab-count: 2">&#160;&#160;&#160;&#160;&#160;&#160; </span>}</span><span style="font-family: &#39;Courier New&#39;; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> </span>
        </p></p> 
        
        <p style="text-align: left; mso-layout-grid-align: none" class="MsoNormal" align="left">
          <span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160; </span>}</span><span style="font-family: &#39;Courier New&#39;; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US"> </span>
        </p></p> 
        
        <p class="MsoNormal">
          <span style="font-family: &#39;Courier New&#39;; color: black; font-size: 10pt; mso-font-kerning: 0pt" lang="EN-US">}</span>
        </p>
      </td>
    </tr>
  </table>
  
  <p class="MsoNormal">
    <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。首先我们用</span><span lang="EN-US">Eclipse</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">来运行，当然没问题，因为模拟器为了调试方便，是运行所有的操作的，运行后，界面显示文件写入成功，并且在</span><span lang="EN-US">C</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">盘根目录下可以找到文件</span><span lang="EN-US">test.txt</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，并看到文件内容。随后我们创建</span><span lang="EN-US">HTML</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">文件，打算在网页文件中运行它，文件代码清单如下：</span>
  </p>
  
  <p class="MsoNormal">
    <b style="mso-bidi-font-weight: normal"><span lang="EN-US">FileOperationApplet.html </span> </p> 
    
    <p>
      </b>
    </p></p> 
    
    <table style="border-bottom-style: none; border-right-style: none; border-collapse: collapse; border-top-style: none; border-left-style: none; mso-border-alt: solid windowtext .5pt; mso-yfti-tbllook: 480; mso-padding-alt: 0pt 5.4pt 0pt 5.4pt; mso-border-insideh: .5pt solid windowtext; mso-border-insidev: .5pt solid windowtext" class="MsoTableGrid" border="1" cellspacing="0" cellpadding="0">
      <tr style="mso-yfti-irow: 0; mso-yfti-firstrow: yes; mso-yfti-lastrow: yes">
        <td style="border-bottom: windowtext 1pt solid; border-left: windowtext 1pt solid; padding-bottom: 0pt; padding-left: 5.4pt; width: 426.1pt; padding-right: 5.4pt; border-top: windowtext 1pt solid; border-right: windowtext 1pt solid; padding-top: 0pt; mso-border-alt: solid windowtext .5pt" valign="top" width="568">
          <p class="MsoNormal">
            <span lang="EN-US"><html></span>
          </p>
          
          <p class="MsoNormal">
            <span lang="EN-US"><body></span>
          </p>
          
          <p class="MsoNormal">
            <span lang="EN-US"><applet code=applets.FileOperationApplet.class width="200" height="200" ></span>
          </p>
          
          <p class="MsoNormal">
            <span lang="EN-US"></applet></span>
          </p>
          
          <p class="MsoNormal">
            <span lang="EN-US"></body></span>
          </p>
          
          <p class="MsoNormal">
            <span lang="EN-US"></html></span>
          </p>
        </td>
      </tr>
    </table>
    
    <p class="MsoNormal">
      <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，接着用浏览器打开这个网页，可以看到如图</span><span lang="EN-US">18.6</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">所示的出错界面和信息提示。这个出错信息完整的内容是：</span>
    </p>
    
    <p class="MsoNormal">
      <i style="mso-bidi-font-style: normal"><span lang="EN-US">java.security.AccessControlException: access denied (java.io.FilePermission c:\test.txt write) </span> </p> 
      
      <p>
        </i>
      </p></p> 
      
      <p class="MsoNormal">
        <i style="mso-bidi-font-style: normal"><span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span>at java.security.AccessControlContext.checkPermission(Unknown Source) </span> </p> 
        
        <p>
          </i>
        </p></p> 
        
        <p class="MsoNormal">
          <i style="mso-bidi-font-style: normal"><span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span>at java.security.AccessController.checkPermission(Unknown Source) </span> </p> 
          
          <p>
            </i>
          </p></p> 
          
          <p class="MsoNormal">
            <i style="mso-bidi-font-style: normal"><span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span>at java.lang.SecurityManager.checkPermission(Unknown Source) </span> </p> 
            
            <p>
              </i>
            </p></p> 
            
            <p class="MsoNormal">
              <i style="mso-bidi-font-style: normal"><span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span>at java.lang.SecurityManager.checkWrite(Unknown Source) </span> </p> 
              
              <p>
                </i>
              </p></p> 
              
              <p class="MsoNormal">
                <i style="mso-bidi-font-style: normal"><span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span>at java.io.FileOutputStream.<init>(Unknown Source) </span> </p> 
                
                <p>
                  </i>
                </p></p> 
                
                <p class="MsoNormal">
                  <i style="mso-bidi-font-style: normal"><span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span>at java.io.FileOutputStream.<init>(Unknown Source) </span> </p> 
                  
                  <p>
                    </i>
                  </p></p> 
                  
                  <p class="MsoNormal">
                    <i style="mso-bidi-font-style: normal"><span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span>at java.io.FileWriter.<init>(Unknown Source) </span> </p> 
                    
                    <p>
                      </i>
                    </p></p> 
                    
                    <p class="MsoNormal">
                      <i style="mso-bidi-font-style: normal"><span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span>at applets.FileOperationApplet.start(FileOperationApplet.java:10) </span> </p> 
                      
                      <p>
                        </i>
                      </p></p> 
                      
                      <p class="MsoNormal">
                        <i style="mso-bidi-font-style: normal"><span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span>at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Unknown Source) </span> </p> 
                        
                        <p>
                          </i>
                        </p></p> 
                        
                        <p class="MsoNormal">
                          <i style="mso-bidi-font-style: normal"><span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span>at java.lang.Thread.run(Unknown Source) </span> </p> 
                          
                          <p>
                            </i>
                          </p></p> 
                          
                          <p class="MsoNormal">
                            <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，即：访问拒绝，不能写入文件</span><span lang="EN-US">c:\test.txt</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。这很安全，不是吗？</span>
                          </p>
                          
                          <p style="text-align: center" class="MsoNormal" align="center">
                            <span lang="EN-US"><a href="http://www.blogjava.net/images/blogjava_net/beansoft/WindowsLiveWriter/AppletApplet_9712/clip_image002_2.jpg"><img border="0" alt="clip_image002" src="http://www.blogjava.net/images/blogjava_net/beansoft/WindowsLiveWriter/AppletApplet_9712/clip_image002_thumb.jpg" width="295" height="147" v:shapes="_x0000_i1025" /></a></span>
                          </p>
                          
                          <p style="text-align: center" class="MsoNormal" align="center">
                            <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">图</span><span lang="EN-US">18.6 Applet</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">安全限制错误</span>
                          </p>
                          
                          <p style="text-align: center" class="MsoNormal" align="center">
                            <span lang="EN-US"></span>
                          </p>
                          
                          <p>
                            &#160;
                          </p></p> 
                          
                          <p class="MsoNormal">
                            <span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">然而实话实说，</span><span lang="EN-US">Applet</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">在企业内部网上，还是很有用处的，它一般可以用来做一些复杂的操作，或者是大文件的上传下载，即时消息支持等等，笔者见过不少这样的解决方案（网络上也有人制作了</span><span lang="EN-US">Applet</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">批量文件上传的功能）。不过，这样的限制，虽然是安全了，但是却让</span><span lang="EN-US">Applet</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的功能大打折扣，那么有没有办法绕过这层安全限制呢？答案是肯定的，这就是</span><span lang="EN-US">Java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">中推出的签名</span><span lang="EN-US">JAR</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">功能，可以帮助我们在用户同意的情况下，绕过安全限制（当然在内部网没有问题，如果是外网，很容易发生恶意代码，例如恶意删除文件等等）。</span>
                          </p>
                          
                          <p class="MsoNormal">
                            <span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span></span><b style="mso-bidi-font-weight: normal"><span style="font-family: 宋体; color: red; mso-ascii-font-family: arial; mso-hansi-font-family: arial">注意：</span></b><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">由于</span><span lang="EN-US">Microsoft</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">也推出了一款</span><span lang="EN-US">JVM</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，导致了</span><span lang="EN-US">Java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">标准的分裂，微软格式的数字签名</span><span lang="EN-US">applet</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">打包格式为</span><span lang="EN-US">cab</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，签名方式也和我们下面描述的内容不同，有兴趣的读者可以去查找相关资料，总之是不通用的。</span>
                          </p>
                          
                          <p class="MsoNormal">
                            <span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">如果是正规的公司，数字证书都是需要购买的，像</span><span lang="EN-US">Verisign</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">之类的公司，提供这样的服务，它的好处就是确保证书是全球唯一的，能够在出现事故时，鉴定是否是有效的数字证书，其实就类似于一份全球唯一的身份证，带有你自己才知道的密码，缺点就是不免费。大家如果在线安装过软件，一般大公司的插件，例如</span><span lang="EN-US">Flash</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">播放器等等，都会带有数字证书。当然，在</span><span lang="EN-US">Java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">中，不需要这么麻烦，</span><span lang="EN-US">JDK</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">已经提供了一个工具</span><i style="mso-bidi-font-style: normal"><span lang="EN-US">keytool.exe</span></i><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">来让开发人员自己生成数字证书（至于安全，加密方面的话题，那就太繁杂了，读者可以自己去查找资料）。如果不想使用命令行版本的这个工具，还可以下载一个开源的软件</span><span lang="EN-US">KeyTool GUI</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，详见参考资料一节的内容。下面我们就快速进入主题，首先启动</span><span lang="EN-US">CMD</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">命令行工具，然后进入到当前的项目目录，运行下面的命令：</span>
                          </p>
                          
                          <p class="MsoNormal">
                            <i style="mso-bidi-font-style: normal"><span lang="EN-US">keytool -genkey -dname "cn=BeanSoft Studio, ou=Java Software, o=BeanSoft Studio, c=China" -alias beansoft -keypass beansoft -storepass beansoft -validity 365 -keystore .\beansoft </span> </p> 
                            
                            <p>
                              </i>
                            </p></p> 
                            
                            <p class="MsoNormal">
                              <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">这段命令将会创建一个数字文件放在当前目录的二进制文件</span><span lang="EN-US">beansoft</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">中。该证书的别名是</span><span lang="EN-US">beansoft</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">（通过</span><span lang="EN-US">-alias</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">指定），密钥的密码是</span><span lang="EN-US">beansoft</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">（</span><span lang="EN-US">-keypass</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">命令指定），存储密钥的文件密码也是</span><span lang="EN-US">beansoft</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">（</span><span lang="EN-US">&#8211; storepass</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">命令指定），证书的有效期是</span><span lang="EN-US">365</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">天（通过</span><span lang="EN-US">-validity</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">指定），</span>
                            </p>
                            
                            <p class="MsoNormal">
                              <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">并把它存储到密码文件</span><span lang="EN-US"> beansoft</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">中。这段命令执行后，没有出错信息的话即是创建成功。另外，如果是实际的项目的话，最好将两个密码设置成安全级别比较高的密码。除了这样来生成一个密钥文件外，还可以用</span><span lang="EN-US">KeyTool</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">以交互的方式来生成（比较推荐初学者使用这种方式）：</span>
                            </p>
                            
                            <p class="MsoNormal">
                              <i style="mso-bidi-font-style: normal"><span lang="EN-US">keytool –genkey </span> </p> 
                              
                              <p>
                                </i>
                              </p></p> 
                              
                              <p class="MsoNormal">
                                <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">随后，会提示您输入必须或者可选的内容。</span>
                              </p>
                              
                              <p class="MsoNormal">
                                <span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">随后我们可以检查下这份证书文件的内容，执行下面的命令：</span>
                              </p>
                              
                              <p class="MsoNormal">
                                <i style="mso-bidi-font-style: normal"><span lang="EN-US">keytool -list -keystore .\beansoft -storepass beansoft </span> </p> 
                                
                                <p>
                                  </i>
                                </p></p> 
                                
                                <p class="MsoNormal">
                                  <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">会输出信息：</span>
                                </p>
                                
                                <p class="MsoNormal">
                                  <i style="mso-bidi-font-style: normal"><span lang="EN-US">Keystore </span></i><i style="mso-bidi-font-style: normal"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">类型：</span><span lang="EN-US"> JKS </span> </p> 
                                  
                                  <p>
                                    </i>
                                  </p></p> 
                                  
                                  <p class="MsoNormal">
                                    <i style="mso-bidi-font-style: normal"><span lang="EN-US">Keystore </span></i><i style="mso-bidi-font-style: normal"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">提供者：</span><span lang="EN-US"> SUN </span> </p> 
                                    
                                    <p>
                                      </i>
                                    </p></p> 
                                    
                                    <p class="MsoNormal">
                                      <i style="mso-bidi-font-style: normal"><span lang="EN-US"></span> </p> 
                                      
                                      <p>
                                        &#160;
                                      </p>
                                      
                                      <p>
                                        </i>
                                      </p></p> 
                                      
                                      <p class="MsoNormal">
                                        <i style="mso-bidi-font-style: normal"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">您的</span><span lang="EN-US"> keystore </span></i><i style="mso-bidi-font-style: normal"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">包含</span><span lang="EN-US"> 1 </span></i><i style="mso-bidi-font-style: normal"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">输入</span><span lang="EN-US"> </span> </p> 
                                        
                                        <p>
                                          </i>
                                        </p></p> 
                                        
                                        <p class="MsoNormal">
                                          <i style="mso-bidi-font-style: normal"><span lang="EN-US"></span> </p> 
                                          
                                          <p>
                                            &#160;
                                          </p>
                                          
                                          <p>
                                            </i>
                                          </p></p> 
                                          
                                          <p class="MsoNormal">
                                            <i style="mso-bidi-font-style: normal"><span lang="EN-US">beansoft, 2008-5-7, PrivateKeyEntry, </span> </p> 
                                            
                                            <p>
                                              </i>
                                            </p></p> 
                                            
                                            <p class="MsoNormal">
                                              <i style="mso-bidi-font-style: normal"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">认证指纹</span><span lang="EN-US"> (MD5)</span></i><i style="mso-bidi-font-style: normal"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">：</span><span lang="EN-US"> 16:15:A0:47:92:96:29:96:93:5D:F0:76:F7:D0:2C:84 </span> </p> 
                                              
                                              <p>
                                                </i>
                                              </p></p> 
                                              
                                              <p class="MsoNormal">
                                                <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。这说明证书没有问题。</span>
                                              </p>
                                              
                                              <p class="MsoNormal">
                                                <span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">有时可能需要导出证书供人使用，可以执行下面的命令：</span>
                                              </p>
                                              
                                              <p class="MsoNormal">
                                                <i style="mso-bidi-font-style: normal"><span lang="EN-US">keytool -export -keystore .\beansoft -storepass beansoft -file beansoft.cer -alias beansoft </span> </p> 
                                                
                                                <p>
                                                  </i>
                                                </p></p> 
                                                
                                                <p class="MsoNormal">
                                                  <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">随后会生成一个</span><span lang="EN-US">beansoft.cer</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，不过在这里对</span><span lang="EN-US">Applet</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">签名是不需要这样做的，只有在做</span><span lang="EN-US">SSL</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">开发时，才能用得到它。</span>
                                                </p>
                                                
                                                <p class="MsoNormal">
                                                  <span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">随后，请读者按照</span><span lang="EN-US">16.1.3.1 JAR </span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">文件一节所介绍的内容，将</span><span lang="EN-US">Applet</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的类文件打包成</span><span lang="EN-US">jar</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">文件，名为</span><span lang="EN-US">applets.jar</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，放在项目的根目录下。接着就进入最关键的，对</span><span lang="EN-US">JAR</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">文件进行签名了，键入下列命令：</span>
                                                </p>
                                                
                                                <p class="MsoNormal">
                                                  <i style="mso-bidi-font-style: normal"><span lang="EN-US">jarsigner -verbose -keystore .\beansoft applets.jar beansoft </span> </p> 
                                                  
                                                  <p>
                                                    </i>
                                                  </p></p> 
                                                  
                                                  <p class="MsoNormal">
                                                    <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">接着提示信息为：</span>
                                                  </p>
                                                  
                                                  <p class="MsoNormal">
                                                    <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">输入密钥库的口令短语：</span><span lang="EN-US">beansoft</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">按下回车，即可看到签名过程：</span>
                                                  </p>
                                                  
                                                  <p class="MsoNormal">
                                                    <i style="mso-bidi-font-style: normal"><span lang="EN-US"><span style="mso-spacerun: yes">&#160;&#160; </span></span></i><i style="mso-bidi-font-style: normal"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">正在添加：</span><span lang="EN-US"> META-INF/MANIFEST.MF </span> </p> 
                                                    
                                                    <p>
                                                      </i>
                                                    </p></p> 
                                                    
                                                    <p class="MsoNormal">
                                                      <i style="mso-bidi-font-style: normal"><span lang="EN-US"><span style="mso-spacerun: yes">&#160;&#160; </span></span></i><i style="mso-bidi-font-style: normal"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">正在添加：</span><span lang="EN-US"> META-INF/BEANSOFT.SF </span> </p> 
                                                      
                                                      <p>
                                                        </i>
                                                      </p></p> 
                                                      
                                                      <p class="MsoNormal">
                                                        <i style="mso-bidi-font-style: normal"><span lang="EN-US"><span style="mso-spacerun: yes">&#160;&#160; </span></span></i><i style="mso-bidi-font-style: normal"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">正在添加：</span><span lang="EN-US"> META-INF/BEANSOFT.DSA </span> </p> 
                                                        
                                                        <p>
                                                          </i>
                                                        </p></p> 
                                                        
                                                        <p class="MsoNormal">
                                                          <i style="mso-bidi-font-style: normal"><span lang="EN-US"><span style="mso-spacerun: yes">&#160;&#160; </span></span></i><i style="mso-bidi-font-style: normal"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">正在添加：</span><span lang="EN-US"> applets/ </span> </p> 
                                                          
                                                          <p>
                                                            </i>
                                                          </p></p> 
                                                          
                                                          <p class="MsoNormal">
                                                            <i style="mso-bidi-font-style: normal"><span lang="EN-US"><span style="mso-spacerun: yes">&#160; </span></span></i><i style="mso-bidi-font-style: normal"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">正在签名：</span><span lang="EN-US"> applets/FileOperationApplet.class </span> </p> 
                                                            
                                                            <p>
                                                              </i>
                                                            </p></p> 
                                                            
                                                            <p class="MsoNormal">
                                                              <i style="mso-bidi-font-style: normal"><span lang="EN-US"><span style="mso-spacerun: yes">&#160; </span></span></i><i style="mso-bidi-font-style: normal"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">正在签名：</span><span lang="EN-US"> applets/LifeCycleApplet.class </span> </p> 
                                                              
                                                              <p>
                                                                </i>
                                                              </p></p> 
                                                              
                                                              <p class="MsoNormal">
                                                                <i style="mso-bidi-font-style: normal"><span lang="EN-US"><span style="mso-spacerun: yes">&#160; </span></span></i><i style="mso-bidi-font-style: normal"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">正在签名：</span><span lang="EN-US"> applets/MyApplet.class </span> </p> 
                                                                
                                                                <p>
                                                                  </i>
                                                                </p></p> 
                                                                
                                                                <p class="MsoNormal">
                                                                  <i style="mso-bidi-font-style: normal"><span lang="EN-US"><span style="mso-spacerun: yes">&#160; </span></span></i><i style="mso-bidi-font-style: normal"><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">正在签名：</span><span lang="EN-US"> applets/usb.jpg </span> </p> 
                                                                  
                                                                  <p>
                                                                    </i>
                                                                  </p></p> 
                                                                  
                                                                  <p class="MsoNormal">
                                                                    <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">可以看到</span><span lang="EN-US">META-INF</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">目录下将会多出两个数字指纹文件，运行的时候</span><span lang="EN-US">JVM</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">将会和类文件进行对比，确保文件没被人篡改过。</span>
                                                                  </p>
                                                                  
                                                                  <p class="MsoNormal">
                                                                    <span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">好了，现在的</span><span lang="EN-US">applets.jar</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">已经今非昔比了，它是个被签名过的</span><span lang="EN-US">JAR</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，怎么使用它呢？需要在它所在的同一目录下，即项目根目录下，新建一个</span><span lang="EN-US">HTML</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">文件，代码清单如下：</span>
                                                                  </p>
                                                                  
                                                                  <p class="MsoNormal">
                                                                    <b style="mso-bidi-font-weight: normal"><span lang="EN-US">FileOperationAppletSigned.html </span> </p> 
                                                                    
                                                                    <p>
                                                                      </b>
                                                                    </p></p> 
                                                                    
                                                                    <table style="border-bottom-style: none; border-right-style: none; border-collapse: collapse; border-top-style: none; border-left-style: none; mso-border-alt: solid windowtext .5pt; mso-yfti-tbllook: 480; mso-padding-alt: 0pt 5.4pt 0pt 5.4pt; mso-border-insideh: .5pt solid windowtext; mso-border-insidev: .5pt solid windowtext" class="MsoTableGrid" border="1" cellspacing="0" cellpadding="0">
                                                                      <tr style="mso-yfti-irow: 0; mso-yfti-firstrow: yes; mso-yfti-lastrow: yes">
                                                                        <td style="border-bottom: windowtext 1pt solid; border-left: windowtext 1pt solid; padding-bottom: 0pt; padding-left: 5.4pt; width: 426.1pt; padding-right: 5.4pt; border-top: windowtext 1pt solid; border-right: windowtext 1pt solid; padding-top: 0pt; mso-border-alt: solid windowtext .5pt" valign="top" width="568">
                                                                          <p class="MsoNormal">
                                                                            <span lang="EN-US"><html></span>
                                                                          </p>
                                                                          
                                                                          <p class="MsoNormal">
                                                                            <span lang="EN-US"><body></span>
                                                                          </p>
                                                                          
                                                                          <p class="MsoNormal">
                                                                            <span lang="EN-US"><applet code=applets.FileOperationApplet.class <b style="mso-bidi-font-weight: normal"><i style="mso-bidi-font-style: normal">archive="applets.jar"</i></b> width="200" height="200" ></span>
                                                                          </p>
                                                                          
                                                                          <p class="MsoNormal">
                                                                            <span lang="EN-US"></applet></span>
                                                                          </p>
                                                                          
                                                                          <p class="MsoNormal">
                                                                            <span lang="EN-US"></body></span>
                                                                          </p>
                                                                          
                                                                          <p class="MsoNormal">
                                                                            <span lang="EN-US"></html><b style="mso-bidi-font-weight: normal"> </b> </p> 
                                                                            
                                                                            <p>
                                                                              </span>
                                                                            </p></p> </td> </tr> </tbody> </table> 
                                                                            
                                                                            <p class="MsoNormal">
                                                                              <span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">唯一的不同，就是多了粗斜体的</span><span lang="EN-US">archive="applets.jar"</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">这句话。</span>
                                                                            </p>
                                                                            
                                                                            <p class="MsoNormal">
                                                                              <span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span></span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">好了，最激动人心的时刻到来了，请用浏览器打开这个网页，会看到一个安全提示，如图</span><span lang="EN-US">18.7</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">所示。点击<b style="mso-bidi-font-weight: normal">运行</b>按钮，即可看到正确的执行了操作，在用户的</span><span lang="EN-US">C</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">盘上创建了一个文件！很好，我们可以为所欲为了，像写普通</span><span lang="EN-US">Java</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">应用那样来写</span><span lang="EN-US">Applet</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">了！如果点击<b style="mso-bidi-font-weight: normal">取消</b>按钮，那很自然的无法创建文件，用户拥有选择权，当然，如果是企业的客户，自然都是让他们选择运行按钮。其实通过这里读者也可以注意到，现在好多网站（例如视频分享的网站等），都会提示您下载一些插件提供增强的功能，然而，他们的数字证书和这里的一样，都是自己造的（其实就是<b style="mso-bidi-font-weight: normal"><span style="color: red">伪造</span></b>），所以，装完后并不能保证是否夹杂了病毒或者恶意代码，所以读者上网时千万要谨慎识别，不要随意点击在线安装或者运行软件。</span>
                                                                            </p>
                                                                            
                                                                            <p style="text-align: center" class="MsoNormal" align="center">
                                                                              <span lang="EN-US"><a href="http://www.blogjava.net/images/blogjava_net/beansoft/WindowsLiveWriter/AppletApplet_9712/clip_image004_2.jpg"><img border="0" alt="clip_image004" src="http://www.blogjava.net/images/blogjava_net/beansoft/WindowsLiveWriter/AppletApplet_9712/clip_image004_thumb.jpg" width="295" height="197" v:shapes="_x0000_i1026" /></a></span>
                                                                            </p>
                                                                            
                                                                            <p style="text-align: center" class="MsoNormal" align="center">
                                                                              <span lang="EN-US">18.7 Applet</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">数字签名安全提示</span>
                                                                            </p>
                                                                            
                                                                            <p style="text-align: center" class="MsoNormal" align="center">
                                                                              <span lang="EN-US"></span>
                                                                            </p>
                                                                            
                                                                            <p>
                                                                              &#160;
                                                                            </p></p> 
                                                                            
                                                                            <p class="MsoNormal">
                                                                              <span lang="EN-US"><span style="mso-tab-count: 1">&#160;&#160;&#160;&#160;&#160;&#160; </span>OK</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，罗罗嗦嗦的讲了这么老半天，就是希望给那些使用</span><span lang="EN-US">Applet</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的用户提供一个相对完整的实践方案，也许现在能在项目中用到</span><span lang="EN-US">AWT</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">，</span><span lang="EN-US">Swing</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的地方，也就剩下</span><span lang="EN-US">Applet</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">了。接下来讨论在网页中使用</span><span lang="EN-US">Applet</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">的进一步功能：参数传递和调用</span><span lang="EN-US">JavaScript</span><span style="font-family: 宋体; mso-ascii-font-family: arial; mso-hansi-font-family: arial">。</span>
                                                                            </p>
                                                                            
                                                                            <p>
                                                                              posted on 2008-05-11 10:44:00 <b>BeanSoft</b> 评论总数 (0)
                                                                            </p>
                                                                            
                                                                            <hr color="#000000" size="1" />
                                                                            
                                                                            <p>
                                                                              转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2010/08/20/applet%e5%ae%89%e5%85%a8%e9%99%90%e5%88%b6%e5%92%8c%e7%ad%be%e5%90%8dapplet/">Applet安全限制和签名Applet</a>
                                                                            </p>