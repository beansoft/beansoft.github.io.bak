---
id: 636
title: Java 技巧 105：利用 JWhich 掌握类路径(ZZ附War版本)
date: 2007-01-10T14:13:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=636
permalink: '/2007/01/10/java-%e6%8a%80%e5%b7%a7-105%ef%bc%9a%e5%88%a9%e7%94%a8-jwhich-%e6%8e%8c%e6%8f%a1%e7%b1%bb%e8%b7%af%e5%be%84zz%e9%99%84war%e7%89%88%e6%9c%ac/'
views:
  - "2944"
original_post_id:
  - "636"
categories:
  - Java SE
---
昨天遇到 Weblogic 的 classpath 问题, 一个类死活加载不进来, 后来就根据以前存的这个资料做了个 web 版本的工具.

[](http://www.blogjava.net/Files/ajaxjava/jwhich.zip)

[jwhich.zip](http://www.blogjava.net/Files/beansoft/jwhich.zip) 7KB 

运行以后的一个输出如下:

&#160;

<font size="1">Please input classname or resource path(eg: /): </font>

<pre><font size="1">Class 'synnex.classpath.JWhich' found in
'/E:/_PortableJava/apache-tomcat-5.5.20/webapps/jwhich/WEB-INF/classes/synnex/classpath/JWhich.class'



<b>Current classpath:</b>

Classpath:
....JDK1.6.0libtools.jar
E:_PortableJavaapache-tomcat-5.5.20binbootstrap.jar



<b>Validate classpath:</b>

Classpath element '....JDK1.6.0libtools.jar'  exist.

Classpath element 'E:_PortableJavaapache-tomcat-5.5.20binbootstrap.jar'  exist.



<b>Boot classpath:</b>

Classpath:
E:_PortableJavaJDK1.6.0jrelibresources.jar
E:_PortableJavaJDK1.6.0jrelibrt.jar
E:_PortableJavaJDK1.6.0jrelibsunrsasign.jar
E:_PortableJavaJDK1.6.0jrelibjsse.jar
E:_PortableJavaJDK1.6.0jrelibjce.jar
E:_PortableJavaJDK1.6.0jrelibcharsets.jar
E:_PortableJavaJDK1.6.0jreclasses



<b>Validate boot classpath:</b>

Classpath element 'E:_PortableJavaJDK1.6.0jrelibresources.jar'  exist.

Classpath element 'E:_PortableJavaJDK1.6.0jrelibrt.jar'  exist.

!!! Classpath element 'E:_PortableJavaJDK1.6.0jrelibsunrsasign.jar' does not exist.

Classpath element 'E:_PortableJavaJDK1.6.0jrelibjsse.jar'  exist.

Classpath element 'E:_PortableJavaJDK1.6.0jrelibjce.jar'  exist.

Classpath element 'E:_PortableJavaJDK1.6.0jrelibcharsets.jar'  exist.

!!! Classpath element 'E:_PortableJavaJDK1.6.0jreclasses' does not exist.



<b>All System Properties:</b>
java.runtime.name=Java(TM) SE Runtime Environment
sun.boot.library.path=E:_PortableJavaJDK1.6.0jrebin
java.vm.version=1.6.0-b105
shared.loader=${catalina.base}/shared/classes,${catalina.base}/shared/lib/*.jar
java.vm.vendor=Sun Microsystems Inc.
java.vendor.url=http://java.sun.com/
java.rmi.server.randomIDs=true
path.separator=;
tomcat.util.buf.StringCache.byte.enabled=true
java.util.logging.config.file=E:_PortableJavaapache-tomcat-5.5.20conflogging.properties
java.vm.name=Java HotSpot(TM) Client VM
file.encoding.pkg=sun.io
sun.java.launcher=SUN_STANDARD
user.country=CN
sun.os.patch.level=Service Pack 1
java.vm.specification.name=Java Virtual Machine Specification
user.dir=E:_PortableJavaapache-tomcat-5.5.20bin
java.runtime.version=1.6.0-b105
java.awt.graphicsenv=sun.awt.Win32GraphicsEnvironment
java.endorsed.dirs=E:_PortableJavaapache-tomcat-5.5.20commonendorsed
os.arch=x86
java.io.tmpdir=E:_PortableJavaapache-tomcat-5.5.20temp
line.separator=

java.vm.specification.vendor=Sun Microsystems Inc.
java.naming.factory.url.pkgs=org.apache.naming
java.util.logging.manager=org.apache.juli.ClassLoaderLogManager
user.variant=
os.name=Windows 2003
sun.jnu.encoding=GBK
java.library.path=E:_PortableJavaJDK1.6.0bin;.;D:WINDOWSSunJavabin;D:WINDOWSsystem32;D:WINDOWS;E:_PortableJavajdk1.5.0bin;D:WINDOWSsystem32;D:WINDOWS;D:WINDOWSSystem32Wbem;F:AdminAppsSecureCRT;D:Program FilesMicrosoft SQL Server80ToolsBINN;f:Program FilesZipGenius 6;f:Program FilesUniversal Extractorbin;d:SYBASEDLL;
java.specification.name=Java Platform API Specification
java.class.version=50.0
sun.management.compiler=HotSpot Client Compiler
os.version=5.2
user.home=D:Documents and SettingsAdministrator.JACKYLIU
java.security.policy=file:/E:/_PortableJava/apache-tomcat-5.5.20/webapps/JSPWiki/WEB-INF/jspwiki.policy
catalina.useNaming=true
user.timezone=Asia/Shanghai
java.awt.printerjob=sun.awt.windows.WPrinterJob
file.encoding=GBK
java.specification.version=1.6
catalina.home=E:_PortableJavaapache-tomcat-5.5.20
java.class.path=....JDK1.6.0libtools.jar;E:_PortableJavaapache-tomcat-5.5.20binbootstrap.jar
user.name=Administrator
java.naming.factory.initial=org.apache.naming.java.javaURLContextFactory
com.sun.management.jmxremote=
package.definition=sun.,java.,org.apache.catalina.,org.apache.coyote.,org.apache.tomcat.,org.apache.jasper.
java.vm.specification.version=1.0
java.home=E:_PortableJavaJDK1.6.0jre
sun.arch.data.model=32
user.language=zh
java.specification.vendor=Sun Microsystems Inc.
awt.toolkit=sun.awt.windows.WToolkit
java.vm.info=mixed mode, sharing
java.version=1.6.0
java.ext.dirs=E:_PortableJavaJDK1.6.0jrelibext;D:WINDOWSSunJavalibext
sun.boot.class.path=E:_PortableJavaJDK1.6.0jrelibresources.jar;E:_PortableJavaJDK1.6.0jrelibrt.jar;E:_PortableJavaJDK1.6.0jrelibsunrsasign.jar;E:_PortableJavaJDK1.6.0jrelibjsse.jar;E:_PortableJavaJDK1.6.0jrelibjce.jar;E:_PortableJavaJDK1.6.0jrelibcharsets.jar;E:_PortableJavaJDK1.6.0jreclasses
server.loader=${catalina.home}/server/classes,${catalina.home}/server/lib/*.jar
java.vendor=Sun Microsystems Inc.
java.security.auth.login.config=file:/E:/_PortableJava/apache-tomcat-5.5.20/webapps/JSPWiki/WEB-INF/jspwiki.jaas
catalina.base=E:_PortableJavaapache-tomcat-5.5.20
file.separator=
java.vendor.url.bug=http://java.sun.com/cgi-bin/bugreport.cgi
common.loader=${catalina.home}/common/classes,${catalina.home}/common/i18n/*.jar,${catalina.home}/common/endorsed/*.jar,${catalina.home}/common/lib/*.jar
sun.io.unicode.encoding=UnicodeLittle
sun.cpu.endian=little
package.access=sun.,org.apache.catalina.,org.apache.coyote.,org.apache.tomcat.,org.apache.jasper.,sun.beans.
sun.desktop=windows
sun.cpu.isalist=</font></pre>

下面是原载 IBM Dev 社区的文章:

&#160;

**Java 技巧 105：利用 JWhich 掌握类路径**

**确定类路径中的什么类将被载入**

作者 [Mike Clark](mailto:mike.clark@javaworld.com) 

> **摘要**
> 
> 尽管 Java 类路径看上去是个很简单的概念，但它也经常是困惑和麻烦的源泉。本文将向您展示一个简单的工具，它可以清楚地确定类装载器从您的类路径中载入了什么 Java 类。（_1,000_ 字）

开发人员在处理 Java 类路径时经常会遇到一些尴尬：他们不总是很清楚类装载器将要载入什么类，尤其是在应用程序的类路径被大量的路径和文件充斥的情况下更是如此。在本文中，我将介绍一个工具，它可以显示被载入的类文件的绝对路径。

**类路径简介**

Java 虚拟机（JVM）使用一个类装载器根据应用程序的需要载入所需的类。`CLASSPATH` 环境变量告诉类装载器去哪里找第三方和用户自定义的类。您也可以利用 `-classpath` JVM 命令行参数为每个应用程序指定类路径，这个路径将重载 `CLASSPATH` 环境变量指定的类路径。 

类路径的内容可以是各种目录，例如没有包含在包中的类文件所在的目录，某个包的根目录，或者包含类的压缩文件（.zip 或 .jar 文件等）。类路径中的各个路径在 Unix 类型的系统中用冒号分隔，在 MS Windows 系统中用分号分隔。 

类装载器按照一种委托树的形式组织，其中每个类装载器都有一个父类装载器。当系统要求某个类装载器查找一个类时，它在查找类之前首先把该请求委托给它的父类装载器。您系统中的 JDK 或 JRE 提供的默认类装载器是系统类装载器，它利用 `CLASSPATH` 环境变量或 `-classpath` JVM 命令行参数载入第三方和用户自定义的类。系统类装载器委托扩展类装载器载入使用 Java 扩展机制的类。扩展类装载器委托自引导类装载器（委托到此为止）载入 JDK 的核心类。 

您可以开发特定的类装载器指导 JVM 如何动态地载入类。例如，大多数 Servlet 引擎使用自定义的类装载器，当指定的类路径中的类发生改变后，它可以动态地重新调入这些 servlet 类。 

这里，十分重要而且很让人吃惊的一点是，类装载器根据类在类路径中的存放顺序进行载入。从第一个路径开始，类装载器访问每个指定的目录或压缩文件来查找要载入的类。它载入第一个名字匹配的类，而剩下的路径将被忽略。 

听起来很简单，是吗？ 

**类路径中的圈套**

无论那些 Java 开发人员承认与否，他们中的新手和老手都时常（通常是最糟糕的时候）被麻烦的类路径所愚弄。随着应用程序中的第三方和用户自定义类的增加，类路径变得拥挤不堪，所以类装载器首先载入哪个类并不总是那么显而易见的，这一点在类路径中包含路径双重拷贝的情况下尤为突出。请记住，类装载器载入第一个名字匹配的类，并将其他同名而优先级较低的类“有效”地隐藏起来。 

这一切看上去都太简单，以至于我们好像不可能落入类路径的这个圈套。那么，就让我们看一看。在经过了一整天繁重的键盘操作后，您想在类路径中添加一个目录，以便应用程序可以调入某个类的最新版本。然而，您没有注意到这个类的另一个版本已经位于某个优先级较高的目录中。就这样，您中招了！ 

**JWhich：一个简单的类路径工具**

扁平型路径声明中的优先级问题并不是 Java 类路径所独有的。要解决这一问题，您只需站在传说中的软件巨人的肩膀上即可。Unix 操作系统的 `which` 命令接受一个名字做为参数，只要这个名字是一个命令，它就显示与之相关的可执行文件的路径。这个命令首先扫描 `PATH` 环境变量，确定要查找的命令出现的第一个位置。这听起来也是一个管理 Java 类路径的强有力的工具。受这个思路的启发，我开始编写一个 Java 程序。这个程序可以根据一个 Java 类名显示需要载入的类文件的绝对路径，它和类路径中指定的路径一致。 

下面的 `JWhich` 示例显示了类 `com.clarkware.ejb.ShoppingCartBean` 的绝对路径，它是类装载器载入该类时遇到的第一个路径，属于目录： 

`> java JWhich com.clarkware.ejb.ShoppingCartBean<br />
    <br />Class 'com.clarkware.ejb.ShoppingCartBean' found in</p>
<p>'/home/mclark/classes/com/clarkware/ejb/ShoppingCartBean.class'</p>
<p>`

下面的 `JWhich` 示例显示了类 `javax.servlet.http.HttpServlet` 的绝对路径，它是类装载器载入该类时遇到的第一个路径，属于压缩文件： 

`> java JWhich javax.servlet.http.HttpServlet<br />
    <br />Class 'javax.servlet.http.HttpServlet' found in</p>
<p>'file:/home/mclark/lib/servlet.jar!/javax/servlet/http/HttpServlet.class'</p>
<p>`

**JWhich 如何工作**

如果要完全确定类路径中的哪个类会被载入，您就必须搞清楚类装载器的“想法”。这并不像听上去那么难－－直接问它就可以了！下面是与 `JWhich` 相关的代码。有关全部代码，请参见[资源](http://www-900.ibm.com/developerWorks/cn/java/jw-tips/tip105/index.shtml#resources)。

<pre>1:   public class JWhich {
2:
3:     /**
4:      * Prints the absolute pathname of the class file
5:      * containing the specified class name, as prescribed
6:      * by the current classpath.
7:      *
8:      * @param className Name of the class.
9:      */
10:     public static void which(String className) {
11:
12:      if (!className.startsWith("/")) {
13:        className = "/" + className;
14:      }
15:      className = className.replace('.', '/');
16:      className = className + ".class";
17:
18:      java.net.URL classUrl =
19:        new JWhich().getClass().getResource(className);
20:
21:      if (classUrl != null) {
22:        System.out.println("nClass '" + className +
23:          "' found in n'" + classUrl.getFile() + "'");
24:      } else {
25:        System.out.println("nClass '" + className +
26:          "' not found in n'" +
27:          System.getProperty("java.class.path") + "'");
28:      }
29:    }
30:
31:    public static void main(String args[]) {
32:      if (args.length &gt; 0) {
33:        JWhich.which(args[0]);
34:      } else {
35:        System.err.println("Usage: java JWhich &lt;classname&gt;");
36:      }
37:    }
38:  }
   </pre>

首先，您需要稍微调整一下类的名字，以便类装载器可以接受它（第 12－16 行）。在类名前加上“/”而不是载入该类的包的名称，这样可以指示类装载器在类路径中逐字核对这个类名。将每个“.”换成“/”可以将类的名称转变为一个有效的 URL 地址，类装载器需要使用这种格式的地址。 

接下来，系统向类装载器查询与给定格式的类名称相符的资源（第 18－19 行）。每个 `Class` 对象都有对它进行载入的 `ClassLoader` 对象的引用，所以系统会查询载入 `JWhich` 类的类装载器对象。`Class.getResource()` 方法实际上委托载入该类的类装载器执行操作，它会返回类文件资源的 URL 地址。如果带有指定类名称的类文件资源不在当前类路径中，它将返回 `null`。 

最后，如果带有指定类名称的类文件资源在当前的类路径中，那么系统将显示它的绝对路径（第 21－24 行）。做为调试手段，如果类文件不在当前类路径中，那么您将获得 `java.class.path` 系统属性的值，即显示当前的类路径（第 24－28 行）。 

在使用 servlet 引擎类路径的 Java servlet 或使用 EJB 服务器类路径的 Engerprise JavaBean （EJB）中，我们可以很容易地想象出上面这些简单代码是如何被载入的。例如在 servlet 引擎中，如果一个自定义的类装载器载入 `JWhich` 类，那么系统将使用 servlet 引擎的类装载器查找类。如果 servlet 引擎的类装载器不能找到某个类，那么它将委托给它的父类装载器。通常来说，当某个类装载器载入 `JWhich` 时，它的类装载器或某个父类装载器需要载入的类都可以被找到。 

**结论**

如果需求是发明之母，那么帮助管理 Java 类路径的工具就来得太迟了。与 Java 相关的新闻组和邮件列表中充满了有关类路径的问题。我们需要降低新的开发人员进入这个领域所面临的障碍，以便我们都可以继续工作在一个更高的层次上。 `JWhich` 是一个简单而功能强大的工具，它可以帮助您掌握任何环境下的 Java 类路径。 

<a></a>

**关于作者**

[Mike Clark](mailto:mike.clark@javaworld.com) 是 [Clarkware Consulting](http://www.clarkware.com/) 公司的独立顾问，专门负责使用 J2EE 技术进行基于 Java 的结构设计和开发。他最近完成了一个 B2B XML exchange 服务器的开发和发布，目前是一个项目的顾问，该项目要构建一个 J2EE 性能管理产品。 

<a><strong>资源</strong></a> 

  * 下载文章中的代码：
      
      
    <http://www.javaworld.com/javatips/javatip105/jwhich.zip> 
  * 带有类路径校验器的全版 JWhich 可以在下面的网址中获得：
      
      
    <http://www.clarkware.com/software/jwhich.zip> 
  * 有关 Sun JDK 的官方文档，以及它如何处理不同平台上的类路径，请参见下面的文档：
      
      
    <http://java.sun.com/j2se/1.3/docs/tooldocs/findingclasses.html> 
  * 有关如何在 Unix 和 Windows 平台上设置类路径的详细内容，请参见下面的“设置类路径”：
      
      
    [](http://www-900.ibm.com/developerWorks/cn/java/jw-tips/tip105/index.shtml)</p> 
      * Unix：
          
          
        <http://java.sun.com/j2se/1.3/docs/tooldocs/solaris/classpath.html> 
      * Windows：
          
          
        <http://java.sun.com/j2se/1.3/docs/tooldocs/win32/classpath.html>
  * 查看以往所有的 **Java 技巧**并提交您自己的技巧： 
    <http://www.javaworld.com/javatips/jw-javatips.index.html> </li> 
    
      * 要获得更多的 Java 技巧，请订阅 ITworld.com 的免费 _Java Tutor_ 简讯： 
        <http://www.itworld.com/cgi-bin/subcontent12.cgi> </li> 
        
          * 在 _Java 世界_的作者 Geoff Friesen 主持的 Java 初学者论坛中发表意见： 
            [http://www.itworld.com/jump/jw-javatip105/forums.itworld.com/webx?14@@.ee6b804/1195!skip=1125](http://www.itworld.com/jump/jw-javatip105/forums.itworld.com/webx?14@@.ee6b804/1195%21skip=1125)</li> </ul> 
            
            转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Java 技巧 105：利用 JWhich 掌握类路径(ZZ附War版本)](http://www.beansoft.biz/2007/01/10/java-%e6%8a%80%e5%b7%a7-105%ef%bc%9a%e5%88%a9%e7%94%a8-jwhich-%e6%8e%8c%e6%8f%a1%e7%b1%bb%e8%b7%af%e5%be%84zz%e9%99%84war%e7%89%88%e6%9c%ac/)