---
id: 2284
title: 'Remote Debugging with Eclipse[FW]'
date: 2011-09-30T22:49:28+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2284
permalink: /2011/09/30/remote-debugging-with-eclipsefw/
views:
  - "7591"
original_post_id:
  - "2284"
categories:
  - MyEclipse/Eclipse
tags:
  - Debug
  - Eclipse
  - Remote
  - WebLogic
---
This old article discussed how to remote debug WebLogic, Tomcat, JBoss. Relatived: <http://www.ibm.com/developerworks/opensource/library/os-eclipse-javadebug/index.html>

From: <http://www.eclipsezone.com/eclipse/forums/t53459.html>&#160;

###### At 8:22 PM on Nov 1, 2005, [Levent Gurses](http://www.eclipsezone.com/forums/profile.jspa?userID=185068)

ow many times trying to fix a server-side Java problem appeared trivial, but getting to the source of the problem took all the time? A remote debugger attached to a Java application can shorten the defect-discovery times significantly and make the process more enjoyable.

Table of Contents

  * [The Java Debugger](http://www.eclipsezone.com/eclipse/forums/t53459.html#jdebugger)
  * [Debugging WebLogic](http://www.eclipsezone.com/eclipse/forums/t53459.html#weblogic)
  * [Debugging JBoss](http://www.eclipsezone.com/eclipse/forums/t53459.html#jboss)
  * [Debugging Tomcat](http://www.eclipsezone.com/eclipse/forums/t53459.html#tomcat)
  * [Debugger Verification](http://www.eclipsezone.com/eclipse/forums/t53459.html#verify)
  * [The Eclipse Connection](http://www.eclipsezone.com/eclipse/forums/t53459.html#eclipse)
  * [References](http://www.eclipsezone.com/eclipse/forums/t53459.html#references)
  * [System Info](http://www.eclipsezone.com/eclipse/forums/t53459.html#systeminfo)
  * [About the Author](http://www.eclipsezone.com/eclipse/forums/t53459.html#about)

<!&#8211; What is it &#8211;>

<a name="jdebugger"></a>

### The Java Debugger

The Java Debugger (jdb) is a dynamic, controlled, assignment-based debugging tool. It helps find and fix bugs in the Java language programs both locally and on the server. To use jdb in a J2EE application server you must first launch it with debugging enabled and attach to the server from the debugger through a JPDA port (Default port is 1044).

The default JPDA options for J2EE servers are as follows:

<pre>-Xdebug -Xrunjdwp:transport=dt_socket,server=y,suspend=n,address=1044</pre>

The jdb parameters specify the way debugger will operate. For instance **transport=dt_socket** instructs the JVM that the debugger connections will be made through a socket while the **address=1044** parameter informs it that the port number will be 1044. Similarly, if you substitute **suspend=y** , the JVM starts in suspended mode and stays suspended until a debugger is attached to it. This may be helpful if you want to start debugging as soon as the JVM starts.

<a name="weblogic"></a>

### Debugging WebLogic

Debugging WebLogic is no different than debugging any other Java remote application. You need to make sure to launch it with the required debugging arguments and attach a debugger. In the case of WebLogic 8.1, you need to add these arguments to the startup script. WebLogic comes with several launch scripts (\*.sh and \*.cmd) under BEA_HOME/weblogic81/server/bin.

  1. Locate startWSL.cmd and add the following variable DEBUG_OPTS: 
    <pre>set DEBUG_OPTS = -Xdebug -Xrunjdwp:transport= dt_socket,address=1044,server=y,suspend=n</pre>

  2. Next, insert the new variable to the WebLogic startup command, after "%JAVA_HOME%binjava" and preferably before the other options. 
  3. Your startup script should look like: 
    "%JAVA\_HOME%binjava" %DEBUG\_OPTS% %JAVA\_VM% %MEM\_ARGS% %JAVA\_OPTIONS%-Dweblogic.Name=%SERVER\_NAME% -Dweblogic.management.username= %WLS\_USER%-Dweblogic.management.password= %WLS\_PW% -Dweblogic.management.server= %ADMIN\_URL%-Dweblogic.ProductionModeEnabled= %PRODUCTION\_MODE%-Djava.security.policy= "%WL_HOME%serverlibweblogic.policy" weblogic.Server

<a name="jboss"></a>

### Debugging JBoss

Same as WebLogic, except that you need to change run.bat/run.sh located under JBOSS_HOME/bin.

Linux users should see something similar to this:

<pre>$ cd /var/jboss4/bin
 $ sh ./run.sh
 =========================================================================

 JBoss Bootstrap Environment

 JBOSS_HOME: /var/jboss4

 JAVA: /usr/java/j2sdk1.4.2_06/bin/java

 JAVA_OPTS: -server -Xms128m -Xmx128m -Dprogram.name=run.sh

 DEBUG_OPTS = -Xdebug -Xrunjdwp:transport= dt_socket,address=1044,server=y,suspend=n

 CLASSPATH: /var/jboss4/bin/run.jar:/usr/java/j2sdk1.4.2_06/lib/tools.jar

 =========================================================================</pre>

<a name="tomcat"></a>

### Debugging Tomcat

Again, very much similar to WebLogic and JBoss, except that you need to change catalina.bat/catalina.sh located under TOMCAT_HOME/bin.

<a name="verify"></a>

### Debugger Verification

Now you can launch your application in debug mode. Just to make sure that the server is listening to port 1044 you can run netstat /a. You should see port 1044 in the list of open ports (See Figure 1: List of open ports: netstat -a).
    
  
![](http://www.jacoozi.com/uploadfiles/blog/debug_image002.png)

Figure 1 List of open ports: netstat -a

<a name="eclipse"></a>

### The Eclipse Connection

After making sure WebLogic is listening for incoming connections on port 1044, what is left is to tell Eclipse to connect to this port and you are ready to debug.

  1. In Eclipse, navigate to **Run | Debug** (See **Figure 2: Create new Remote Java Application configuration in Eclipse** ). 
  2. Select **Remote Java Application** , on the left column. Click **New** , on the bottom of the same column. 
  3. In the **Create configuration** screen you&#8217;ll be prompted to enter some values. Start with a meaningful name. In my case that&#8217;s **WebLogic Instance** . For Project, select the Java project that contains the source code you want to debug. Leave **Connection Type** in default, i.e. **Standard (Socket Attach)** . For **Host** , enter localhost. If you want to debug a remote server, enter its hostname or IP address. For port, enter **1044** or the port you defined in your WebLogic startup script. 
  4. Click **Apply**
  5. Make sure WebLogic instance is running in debug mode. In the same screen click **Debug** . Eclipse should automatically take you to the **Debug**perspective and you should see a stack trace in the **Debug** view. 
  6. If you are not automatically taken to the **Debug** perspective, select **Window | Open Perspective | Other** and then click **Debug.**

![](http://www.jacoozi.com/uploadfiles/blog/debug_image004.png)

**Figure 2 Create new Remote Java Application configuration in Eclipse
      
  
** 

****

![](http://www.jacoozi.com/uploadfiles/blog/debug_image008.png)

Figure 3 Breakpoint hit in Eclipse debugger</p> 

<span [http://](http://www.eclipsezone.com)

Eclipse Debug window should automatically pop-up with the stack pointer on your first breakpoint (See Figure 3: Breakpoint hit in Eclipse&#8217;s debugger ). After that, you can use all the various functions that the debugger has to offer, namely variable assignments, step-into, drop to frame, etc.

<a name="references"></a>

### References

  * [Debugging J2EE Applications](http://java.sun.com/j2ee/1.4/docs/devguide/dgdebug.html)
  * [Connecting to a Remote VM with the Java Remote Application Launcher](http://help.eclipse.org/help31/index.jsp?topic=/org.eclipse.jdt.doc.user/tasks/tasks-141.htm)
  * [Debugging with the Eclipse Platform](http://www-106.ibm.com/developerworks/opensource/library/os-ecbug)

<a name="systeminfo"></a>

### System Information

  * Windows 2000 
  * JDK 1.4.2_03 
  * Eclipse 3.0 
  * BEA WebLogic 8.1 
  * JBoss 4.0.2 
  * Tomcat 5.0.26

<a name="about"></a>

### About the Author

<img hspace="6" src="http://www.jacoozi.com/images/stories/levent_portrait.jpg" align="left" />

Levent Gurses is a Washington, DC-based technology consultant. He is also one of the co-founders of [Jacoozi](http://www.jacoozi.com/) , an integrated solutions provider based in Alexandria, VA. In his professional life Levent helps clients overcome their J2EE challenges and develop leaner and meaner software development practices. Most of his free time goes in reading and motorcycle racing.

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Remote Debugging with Eclipse[FW]](http://www.beansoft.biz/2011/09/30/remote-debugging-with-eclipsefw/)