---
id: 1308
title: Picasa Portable
date: 2010-10-13T21:29:33+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1308
permalink: /2010/10/13/picasa-portable/
views:
  - "2818"
original_post_id:
  - "1308"
tagazine-media:
  - 'a:7:{s:7:"primary";s:0:"";s:6:"images";a:0:{}s:6:"videos";a:0:{}s:11:"image_count";s:1:"0";s:6:"author";s:8:"27534716";s:7:"blog_id";s:8:"27979815";s:9:"mod_stamp";s:19:"2010-10-13 13:29:33";}'
categories:
  - 软件使用与下载
---
Picasa’s default settings is stored in the folder of **C:…..Local SettingsApplication DataGoogle** , so sometimes after reinstall the system, all settings will gone, especially the faces category of the photo. So can we move it to other place? Sure, we can!

&#160;

Create one batch file in the picasa install directory(might be named **PicasaPortable.cmd**), the content is:

<div id="codeSnippetWrapper">
  <div style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;padding:0;" id="codeSnippet">
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">mkdir <span style="color:#006080;">"D:Google_DatasGoogleLocal SettingsApplication DataGoogle"</span></pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#0000ff;">set</span> USERPROFILE=D:Google_DatasGoogle</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">start Picasa3.exe</pre>
    
    <p>
      <!--CRLF--></div> </div> 
      
      <p>
        Then everyting is done!
      </p>
      
      <p>
        转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2010/10/13/picasa-portable/">Picasa Portable</a>
      </p>