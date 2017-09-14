---
id: 1267
title: 'How to Check Which Version of Microsoft .NET Framework is Installed in Windows?[转]'
date: 2010-09-28T12:30:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1267
permalink: '/2010/09/28/how-to-check-which-version-of-microsoft-net-framework-is-installed-in-windows%e8%bd%ac/'
views:
  - "3599"
original_post_id:
  - "1267"
categories:
  - Windows
---
### From <http://www.askvg.com/how-to-check-which-version-of-microsoft-net-framework-is-installed-in-windows/>

<span class="Apple-style-span" style="word-spacing:0;font:medium &#039;text-transform:none;color:rgb(0,0,0);text-indent:0;white-space:normal;letter-spacing:normal;border-collapse:separate;orphans:2;widows:2;"><span class="Apple-style-span" style="font-size:12px;"> </p> 

<p style="line-height:1.6em;font-family:&#039;margin:0 0 15px;padding:0;">
  Recently we posted a topic containing official download links for all<span class="Apple-converted-space">&#160;</span><strong>Microsoft .NET Framework</strong>versions:
</p>

<p style="line-height:1.6em;font-family:&#039;margin:0 0 15px;padding:0;">
  <span style="font-family:&#039;text-decoration:underline;margin:0;padding:0;"><strong><a title="Go to What is Microsoft .NET Framework? Download Links for All Versions Inside" style="color:rgb(0,66,118);font-family:&#039;text-decoration:none;margin:0;padding:0;" href="http://www.askvg.com/what-is-microsoft-net-framework-download-links-for-all-versions-inside/" rel="bookmark">What is Microsoft .NET Framework? Download Links for All Versions Inside</a></strong></span>
</p>

<p style="line-height:1.6em;font-family:&#039;margin:0 0 15px;padding:0;">
  One reader asked us how to determine which version of .NET Framework is installed in our system? So today in this topic, we&#8217;ll tell you the procedure to find out installed version of .NET Framework in your Windows.
</p>

<p style="line-height:1.6em;font-family:&#039;margin:0 0 15px;padding:0;">
  There are 2 easy way to find out the version of .NET Framework installed in your system:
</p>

<ul style="list-style-image:url('http://www.askvg.com/wp-content/themes/AskVG/images/b.png');font-family:&#039;margin:0;padding:0 0 8px 15px;">
  <li style="font-family:&#039;margin:0 0 12px;padding:0;">
    Using Windows Explorer
  </li>
  <li style="font-family:&#039;margin:0 0 12px;padding:0;">
    Using Registry Editor
  </li>
</ul>

<blockquote style="border-right:rgb(204,204,204) 1px dashed;border-top:rgb(204,204,204) 1px dashed;border-left:rgb(204,204,204) 1px dashed;border-bottom:rgb(204,204,204) 1px dashed;font-family:&#039;background-color:rgb(241,247,247);margin:0 0 14px;padding:10px 10px 0;">
  <p style="line-height:1.6em;font-family:&#039;text-align:center;margin:0 0 15px;padding:0;">
    <strong>Method 1: Using Windows Explorer</strong>
  </p>
</blockquote>

<p style="line-height:1.6em;font-family:&#039;margin:0 0 15px;padding:0;">
  All Microsoft .NET Framework versions are installed in following directory:
</p>

<blockquote style="border-right:rgb(204,204,204) 1px dashed;border-top:rgb(204,204,204) 1px dashed;border-left:rgb(204,204,204) 1px dashed;border-bottom:rgb(204,204,204) 1px dashed;font-family:&#039;background-color:rgb(241,247,247);margin:0 0 14px;padding:10px 10px 0;">
  <p style="line-height:1.6em;font-family:&#039;margin:0 0 15px;padding:0;">
    %windir%Microsoft.NETFramework
  </p>
</blockquote>

<p style="line-height:1.6em;font-family:&#039;margin:0 0 15px;padding:0;">
  Where "<strong>%windir%</strong>" represents "<strong>Windows</strong>" directory present in the system drive where Windows is installed in your system e.g.<span class="Apple-converted-space">&#160;</span><strong>C:Windows</strong>.
</p>

<p style="line-height:1.6em;font-family:&#039;margin:0 0 15px;padding:0;">
  So just type the above mentioned path in RUN dialog box or in Windows Explorer addressbar and press Enter. It&#8217;ll open the directory as shown in following screenshot:
</p>

<p style="line-height:1.6em;font-family:&#039;margin:0 0 15px;padding:0;">
  <img style="font-family:&#039;border-width:0;margin:0;padding:0;" alt="http://img.photobucket.com/albums/v374/vishaal_here/Check_NET_Framework_Version_Inst-1.png" src="http://img.photobucket.com/albums/v374/vishaal_here/Check_NET_Framework_Version_Inst-1.png" />
</p>

<p style="line-height:1.6em;font-family:&#039;margin:0 0 15px;padding:0;">
  Here in this folder, you can find out which versions are installed.
</p>

<blockquote style="border-right:rgb(204,204,204) 1px dashed;border-top:rgb(204,204,204) 1px dashed;border-left:rgb(204,204,204) 1px da shed;border-bottom:rgb(204,204,204) 1px dashed;font-family:&#039;background-color:rgb(241,247,247);margin:0 0 14px;padding:10px 10px 0;">
  <p style="line-height:1.6em;font-family:&#039;text-align:center;margin:0 0 15px;padding:0;">
    <strong>Method 2: Using Registry Editor</strong>
  </p>
</blockquote>

<p style="line-height:1.6em;font-family:&#039;margin:0 0 15px;padding:0;">
  You can also find out .NET Framework version using Registry Editor:
</p>

<p style="line-height:1.6em;font-family:&#039;margin:0 0 15px;padding:0;">
  <strong>1.</strong><span class="Apple-converted-space">&#160;</span>Type<span class="Apple-converted-space">&#160;</span><strong>regedit</strong><span class="Apple-converted-space">&#160;</span>in RUN or startmenu search box and press Enter. It&#8217;ll open Registry Editor.
</p>

<p style="line-height:1.6em;font-family:&#039;margin:0 0 15px;padding:0;">
  <strong>2.</strong><span class="Apple-converted-space">&#160;</span>Now go to:
</p>

<blockquote style="border-right:rgb(204,204,204) 1px dashed;border-top:rgb(204,204,204) 1px dashed;border-left:rgb(204,204,204) 1px dashed;border-bottom:rgb(204,204,204) 1px dashed;font-family:&#039;background-color:rgb(241,247,247);margin:0 0 14px;padding:10px 10px 0;">
  <p style="line-height:1.6em;font-family:&#039;margin:0 0 15px;padding:0;">
    HKEY_LOCAL_MACHINESOFTWAREMicrosoftNET Framework SetupNDP
  </p>
</blockquote>

<p style="line-height:1.6em;font-family:&#039;margin:0 0 15px;padding:0;">
  <strong>3.</strong><span class="Apple-converted-space">&#160;</span>Under this key, you&#8217;ll see separate keys for each .NET Framework version installed in your system.
</p>

<p style="line-height:1.6em;font-family:&#039;margin:0 0 15px;padding:0;">
  <img style="font-family:&#039;border-width:0;margin:0;padding:0;" alt="http://img.photobucket.com/albums/v374/vishaal_here/Check_NET_Framework_Version_Install.png" src="http://img.photobucket.com/albums/v374/vishaal_here/Check_NET_Framework_Version_Install.png" />
</p>

<p>
  </span></span>
</p>

<p>
  转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2010/09/28/how-to-check-which-version-of-microsoft-net-framework-is-installed-in-windows%e8%bd%ac/">How to Check Which Version of Microsoft .NET Framework is Installed in Windows?[转]</a>
</p>