---
id: 3432
title: Jar Class File Searcher Tool(Free!)
date: 2013-09-12T23:05:36+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3432
permalink: /2013/09/12/jar-class-file-searcher-toolfree/
views:
  - "3439"
categories:
  - Java SE
  - OpenSource
tags:
  - Class
  - jar
  - Search
---
Requires: Java 1.6+, Platform: Windows, Linux(Gnome), Mac OS(not yet tested, if you&#8217;d tested, please do mail me and leave a screenshot).

Download: [www.beansoft.biz/weblogic/JarSearch.jar](http://www.beansoft.biz/weblogic/JarSearch.jar) (Cross platform)/ [www.beansoft.biz/weblogic/JarSearch.exe](http://www.beansoft.biz/weblogic/JarSearch.exe)

Working as a Java Developer and working across multiple projects there is one frequent error which I have encountered is : <tt>Exception in thread "main" java.lang.NoClassDefFound Error</tt>, or just got a tons of errors in your Eclipse Java code sait the class can&#8217;t be found, but there are hundreds jars there, I don’t really know where it is! The reason for this error is missing class file from the CLASSPATH, but it’s hard to get them one by one.

This sometimes becomes very frustrating when you have to search for missing class in a set of JAR files. For resolving this error quickly I have mod a JAVA utility based on [http://code.google.com/p/classjarsearch/](http://code.google.com/p/classjarsearch/ "http://code.google.com/p/classjarsearch/") and <https://github.com/samsonw/OpenExplorer>, one pure Swing project developed with Netbeans yet another one is a Eclipse plugin created by Eclipse,

which searches for class file in all jar files present in a particular directory.

This tool is very simple and it only has 2 inputs. First text input should be class name that we want to search. Class Name can be either full or partial. It can also be &#8216;.&#8217; or &#8216;/&#8217; seperated. Second text input is directory location in which search should be conducted. This can be provided using Browse button which displys a basic file browser or just paste the path in the text box. Hit Search button and any jar file which has class that matches input would be displayed.

The new features come here is a copy button and a locate button, the first one is used for copy path to your clipboard while the latter could bring up the system file browser and locate or select the jar file you have selected in the search result table.

**Download jar to a local directory. Switch to extracted directory and execute: java -jar <tt>JarSearch.jar</tt>**

**I have added <tt>JarSearch.exe</tt> which is single download for windows, created with [http://sourceforge.net/projects/launch4j](http://sourceforge.net/projects/launch4j "http://sourceforge.net/projects/launch4j").**

Screenshots:

Windows:

[<img style="background-image: none; border-right-width: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="image" border="0" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2013/09/image_thumb.png" width="1028" height="332" />](http://www.beansoft.biz/wp-content/uploads/2013/09/image.png)

Linux:

[<img style="background-image: none; border-right-width: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="$RUU7[6@YYPFT~WQ~{F)72U" border="0" alt="$RUU7[6@YYPFT~WQ~{F)72U" src="http://www.beansoft.biz/wp-content/uploads/2013/09/RUU76YYPFTWQF72U_thumb.jpg" width="1024" height="292" />](http://www.beansoft.biz/wp-content/uploads/2013/09/RUU76YYPFTWQF72U.jpg)

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Jar Class File Searcher Tool(Free!)](http://www.beansoft.biz/2013/09/12/jar-class-file-searcher-toolfree/)