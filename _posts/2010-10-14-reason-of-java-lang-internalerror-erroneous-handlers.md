---
id: 1315
title: 'Reason of java.lang.InternalError: erroneous handlers'
date: 2010-10-14T23:18:05+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1315
permalink: /2010/10/14/reason-of-java-lang-internalerror-erroneous-handlers/
views:
  - "4856"
original_post_id:
  - "1315"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
<font color="#ff0000"><strong>This article is not allowed to copy/paste to other web sites without my written permission. It’s written by BeanSoft(</strong><strong>wlsmon@qq.com </strong><strong>), posted at </strong></font>[**<font color="#ff0000">http://www.beansoft.biz/</font>**](http://www.beansoft.biz/) 

Well, a lot of guys might encounter this strange errors when do dev on the WebLogic Server along with JRockit VM, well, I don’t care what other guys do with this error, but one case I found is that the real reason is ClassNotFound. This is a big app on WLS 10.3.0 with JRockit 1.6, and it running under the dev mode, after upload one jar file to the WEB-INF/lib folder, then update the app through console, it’s still not work,&#160; and produced a strange error message as following:

[<img style="border-bottom:0;border-left:0;display:inline;border-top:0;border-right:0;" title="image" border="0" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2010/10/image_thumb.png" width="708" height="226" />](http://www.beansoft.biz/wp-content/uploads/2010/10/image1.png) 

Well, it’s said java.lang.InternalError: erroneous handlers. After checking the class loading status var my private used tool, I found one jar file is not loaded into the JVM as expected, but it’s need by another jar who hold this class: DefaultXPath. Finally, reboot the wls server will fix this issue. Well, still I don’t know exactly the reason why it’s failed to update.

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Reason of java.lang.InternalError: erroneous handlers](http://www.beansoft.biz/2010/10/14/reason-of-java-lang-internalerror-erroneous-handlers/)