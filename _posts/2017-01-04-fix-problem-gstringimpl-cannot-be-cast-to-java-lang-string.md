---
id: 3869
title: 'Fix problem: GStringImpl cannot be cast to java.lang.String'
date: 2017-01-04T13:58:04+00:00
author: 刘长炯
excerpt: 'I have this code in my Android Studio’s gradle file:'
layout: post
guid: http://www.beansoft.biz/?p=3869
permalink: /2017/01/04/fix-problem-gstringimpl-cannot-be-cast-to-java-lang-string/
views:
  - "1479"
categories:
  - Android
---
</p> 

I have this code in my Android Studio’s gradle file:

<img src="http://www.beansoft.biz/wp-content/uploads/2017/01/1ED60E35-D493-4257-B0C3-087F7BA2F7B7-24778-000016D683A58187_file.png" style="" />

</p> 

<pre>javaCompileOptions {<br />&nbsp;&nbsp;&nbsp; annotationProcessorOptions {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; arguments = [ targetModuleName : 'Base',<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; assetsDir : "$projectDir/src/main/assets"<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ]<br />&nbsp;&nbsp;&nbsp; }<br />}
</pre>

Then the IDE throws this error message to me when I sync the project:

Error:Cause: org.codehaus.groovy.runtime.GStringImpl cannot be cast to java.lang.String

Possible causes for this unexpected error include:<ul><li>Gradle&#8217;s dependency cache may be corrupt (this sometimes occurs after a network connection timeout.)

Why? As “” will product a GStringImpl, but not a String object.

How to fix it? Follow a workaround in this bug:&nbsp;<https://github.com/flyway/flyway/issues/690>, then finally code is this:</p> 

<pre>javaCompileOptions {<br />&nbsp;&nbsp;&nbsp; annotationProcessorOptions {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; arguments = [ targetModuleName : 'Base',<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; assetsDir : "$projectDir/src/main/assets".toString()<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ]<br />&nbsp;&nbsp;&nbsp; }<br />}
</pre></p> 

</body></html>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Fix problem: GStringImpl cannot be cast to java.lang.String](http://www.beansoft.biz/2017/01/04/fix-problem-gstringimpl-cannot-be-cast-to-java-lang-string/)