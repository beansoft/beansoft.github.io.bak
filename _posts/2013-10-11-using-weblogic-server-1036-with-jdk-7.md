---
id: 3440
title: Using WebLogic Server 1036 with JDK 7
date: 2013-10-11T20:22:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3440
permalink: /2013/10/11/using-weblogic-server-1036-with-jdk-7/
views:
  - "3692"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - Java7
  - WebLogic
---
From : [http://docs.oracle.com/cd/E23943_01/doc.1111/e14142/jdk7.htm](http://docs.oracle.com/cd/E23943_01/doc.1111/e14142/jdk7.htm "http://docs.oracle.com/cd/E23943_01/doc.1111/e14142/jdk7.htm"), with JDK 7, you can use the newly JMC(Java Misson Control) which introduced since JDK 7u40, the formal JRMC &#8211; JRockit Mission Control, now with JDK supoort.

&#160;

WebLogic Server does not ship with JDK 7. This appendix describes the steps you need to perform to use WebLogic Server with JDK 7. It also describes issues that you may encounter when using WebLogic Server with JDK 7.

Prior to installing JDK 7 for use with WebLogic Server, review the following issues that you may encounter when using JDK 7:

  * In some cases, the new JVM requires more PermGen space, which can cause PermGen errors. If this occurs, use one of the following two options to resolve the issue:
    
      * If you are using the `java` command to start WebLogic Server, include the following option in the command:
        
        `-XX:MaxPermSize=350m`
    
      * If you are using `startWebLogic.sh` (UNIX) or `startWebLogic.cmd` (Windows) to start WebLogic Server, prior to issuing the command, set the `MEM_ARGS` environment variable as follows:
        
        UNIX:
        
        `USER_MEM_ARGS="-Xms32m -Xmx200m -XX:MaxPermSize=350m"`
        
        `export MEM_ARGS`
        
        Windows:
        
        `set USER_MEM_ARGS=-Xms32m -Xmx200m -XX:MaxPermSize=350m`

  * In some cases, the new compiler generates larger byte code. It is possible that a large method may exceed the 64KB limit per method. In this situation, you may need to refactor the method.

  * Classes may have been removed that are from the internal package `sun.*`, or that have been marked as deprecated in a previous version of the JVM. If an application uses these removed methods, a `ClassNotFound` exception will occur.

  * JDBC 4.1 methods are not currently supported in WebLogic Server with JDK 7. Calls to these methods will result in an `SQLException` indicating that the method is not supported.

Before installing WebLogic Server, perform the following steps:

  1. Download the appropriate JDK 7 for your platform from the following URL:
    
    `<a href="http://www.oracle.com/technetwork/java/javase/downloads/java-se-jdk-7-download-432154.html">http://www.oracle.com/technetwork/java/javase/downloads/java-se-jdk-7-download-432154.html</a>`

  2. Install the JDK.

  3. Set `JAVA_HOME` to point to the installed JDK 7.

  4. Set `PATH` to point to `$JAVA_HOME/bin`.

  5. When installing WebLogic Server: select a Custom installation. For the JDK selection, deselect the bundled JDK entries and under the Local JDK section browse and select the JAVA_HOME directory.
    
      1. On the [Choose Install Type](http://docs.oracle.com/cd/E23943_01/doc.1111/e14142/install_screens.htm#CECHAIHH) screen, select the Custom option.
    
      2. On the [JDK Selection](http://docs.oracle.com/cd/E23943_01/doc.1111/e14142/install_screens.htm#CECIAFHE) screen, deselect the bundled JDK entries, and then under the Local JDK section, browse to and select the `JAVA_HOME` directory.

  6. After installing WebLogic Server, copy the following files from `WL_HOME/modules` to `JAVA_HOME/jre/lib/endorsed`, where `WL_HOME` is the WebLogic Server installation home directory:
    
    `javax.annotation_1.0.0.0_1-0.jar`
    
    `javax.xml.bind_2.1.1.jar`
    
    `javax.xml.ws_2.1.1.jar`

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Using WebLogic Server 1036 with JDK 7](http://www.beansoft.biz/2013/10/11/using-weblogic-server-1036-with-jdk-7/)