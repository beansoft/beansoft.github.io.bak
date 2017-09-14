---
id: 297
title: WLST on Weblogic 8.1下载地址(转)
date: 2010-07-15T14:07:02+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=297
permalink: '/2010/07/15/wlst-on-weblogic-8-1%e4%b8%8b%e8%bd%bd%e5%9c%b0%e5%9d%80%e8%bd%ac/'
views:
  - "9161"
original_post_id:
  - "297"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - WebLogic8
  - WLST
---
</p> 

<div class="post-body entry-content">
  <div>
    <span class="Apple-style-span" style="font-size:13px;color:rgb(51,51,51);line-height:19px;font-family:verdana;"> </p> 
    
    <div>
      <span class="Apple-style-span" style="font-weight:bold;"><span class="Apple-style-span" style="font-size:10px;"><span class="Apple-style-span" style="font-family:&#039;"><span class="Apple-style-span" style="color:rgb(51,102,255);">另一处下载地址: <a title="http://www.alagorn.net/weblogic/20100214/wlst-for-weblogic81-download.html" href="http://www.alagorn.net/weblogic/20100214/wlst-for-weblogic81-download.html">http://www.alagorn.net/weblogic/20100214/wlst-for-weblogic81-download.html</a>&#160;</span></span></span></span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="font-weight:bold;"><span class="Apple-style-span" style="font-size:10px;"><span class="Apple-style-span" style="font-family:&#039;"><span class="Apple-style-span" style="color:rgb(51,102,255);">From: <a title="http://unni-at-work.blogspot.com/2009/07/wlst-on-weblogic-81_08.html" href="http://unni-at-work.blogspot.com/2009/07/wlst-on-weblogic-81_08.html">http://unni-at-work.blogspot.com/2009/07/wlst-on-weblogic-81_08.html</a></span></span></span></span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="font-weight:bold;"><span class="Apple-style-span" style="font-size:10px;"><span class="Apple-style-span" style="font-family:&#039;"><span class="Apple-style-span" style="color:rgb(51,102,255);">This posting is a reply to the below query which was asked to me sometime back by one of my virtual friends (Karoly Nador).</span></span></span></span><span class="Apple-style-span" style="font-family:&#039;"> <br /></span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="font-family:&#039;">In WLS 9.0 onwards WLST in inbuild with weblogc.jar, but for WLS 8.1 you would need use the jython.jar and wlst.jar files in order to run WLST.</span>
    </div>
    
    <div>
    </div>
    
    <div>
      <span class="Apple-style-span" style="font-family:&#039;">Download link : <a href="http://www.4shared.com/file/116721496/8c3533ea/WLST_WLS_81.html">http://www.4shared.com/file/116721496/8c3533ea/WLST_WLS_81.html</a></span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="font-family:&#039;"> <br /></span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="font-family:&#039;">You will have to add both these files in the beginning of the CLASSPATH varibale in setWLSenv.cmd/.sh <br /></span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="font-family:&#039;"> <br /></span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="font-family:&#039;">Eg: set CLASSPATH=C:Installerwlst_v62jython.jar;C:Installerwlst_v62wlst.jar;C:InstallerwlstExplorerwlstExplorer.jar;%WEBLOGIC_CLASSPATH%;%CLASSPATH%</span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="font-family:&#039;"> <br /></span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="font-family:&#039;">How to run:</span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="font-family:&#039;">1. Open a new command window</span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="font-family:&#039;">2. Run the &#8216;setWLSenv.cmd/.sh&#8217; script to set the enviroment variables</span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="font-family:&#039;">3. invoke WLST in interavtive mode using the follwowing command : &#8216;java weblogic.WLST&#8217;</span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="font-family:&#039;"> <br /></span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="color:rgb(51,102,255);"><span class="Apple-style-span" style="font-size:10px;"><span class="Apple-style-span" style="font-family:&#039;">&#8212;&#8212;&#8212;- Forwarded message &#8212;&#8212;&#8212;-</span></span></span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="color:rgb(51,102,255);"><span class="Apple-style-span" style="font-size:10px;"><span class="Apple-style-span" style="font-family:&#039;">From: Karoly Nador(xxx@googlemail.com);</span></span></span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="color:rgb(51,102,255);"><span class="Apple-style-span" style="font-size:10px;"><span class="Apple-style-span" style="font-family:&#039;">Date: Wed, Jul 8, 2009 at 2:04 PM</span></span></span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="color:rgb(51,102,255);"><span class="Apple-style-span" style="font-size:10px;"><span class="Apple-style-span" style="font-family:&#039;">Subject: Wlst.jar for Weblogic 8.1</span></span></span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="color:rgb(51,102,255);"><span class="Apple-style-span" style="font-size:10px;"><span class="Apple-style-span" style="font-family:&#039;">To: unni@unnikrishnanpillai.tk</span></span></span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="color:rgb(51,102,255);"><span class="Apple-style-span" style="font-size:10px;"><span class="Apple-style-span" style="font-family:&#039;"> <br /></span></span></span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="color:rgb(51,102,255);"><span class="Apple-style-span" style="font-size:10px;"><span class="Apple-style-span" style="font-family:&#039;">Hi Unni,</span></span></span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="color:rgb(51,102,255);"><span class="Apple-style-span" style="font-size:10px;"><span class="Apple-style-span" style="font-family:&#039;">i read your blog, and you make a really good job. </span></span></span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="color:rgb(51,102,255);"><span class="Apple-style-span" style="font-size:10px;"><span class="Apple-style-span" style="font-family:&#039;">We would solve many of our problems, if we would use the wlst utility, but i can&#8217;t find it for the Weblogic 8.1</span></span></span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="color:rgb(51,102,255);"><span class="Apple-style-span" style="font-size:10px;"><span class="Apple-style-span" style="font-family:&#039;">We use PeopleSoft 8.48, and with this is weblogic 8.1 delivered. The old bea-Sites are down, from there i can&#8217;t download it.</span></span></span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="color:rgb(51,102,255);"><span class="Apple-style-span" style="font-size:10px;"><span class="Apple-style-span" style="font-family:&#039;">Do you have any idea, where can i download it? </span></span></span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="color:rgb(51,102,255);"><span class="Apple-style-span" style="font-size:10px;"><span class="Apple-style-span" style="font-family:&#039;">Thanks in advance.</span></span></span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="font-size:10px;color:rgb(51,102,255);"><span class="Apple-style-span" style="font-family:&#039;"> <br /></span></span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="font-size:10px;color:rgb(51,102,255);"><span class="Apple-style-span" style="font-family:&#039;">Best regards from Germany</span></span><span class="Apple-style-span" style="font-family:&#039;"> <br /></span>
    </div>
    
    <div>
      <span class="Apple-style-span" style="font-size:10px;color:rgb(51,102,255);"><span class="Apple-style-span" style="font-family:&#039;">Karoly Nador</span></span>
    </div>
    
    <p>
      </span></div> 
      
      <div style="clear:both;">
      </div>
    </p></div> 
    
    <div class="post-footer">
      <div class="post-footer-line post-footer-line-1">
        <span class="post-author vcard">Posted by <span class="fn">Unnikrishnan Pillai</span> </span><span class="post-timestamp">at <a class="timestamp-link" title="permanent link" href="http://unni-at-work.blogspot.com/2009/07/wlst-on-weblogic-81_08.html" rel="bookmark"><abbr class="published" title="2009-07-08T18:09:00+05:30">7/08/2009 06:09:00 PM</abbr></a> </span>
      </div></p>
    </div>
    
    <p>
      转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2010/07/15/wlst-on-weblogic-8-1%e4%b8%8b%e8%bd%bd%e5%9c%b0%e5%9d%80%e8%bd%ac/">WLST on Weblogic 8.1下载地址(转)</a>
    </p>