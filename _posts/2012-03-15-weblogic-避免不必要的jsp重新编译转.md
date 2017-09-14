---
id: 2713
title: 'WebLogic 避免不必要的JSP重新编译[转]'
date: 2012-03-15T21:35:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2713
permalink: '/2012/03/15/weblogic-%e9%81%bf%e5%85%8d%e4%b8%8d%e5%bf%85%e8%a6%81%e7%9a%84jsp%e9%87%8d%e6%96%b0%e7%bc%96%e8%af%91%e8%bd%ac/'
views:
  - "6160"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
关于JavaServer页面（JSP）新闻组的最常见的一个问题与重新编译有关。不想重新编译JSP，却又不得不这样做，这是许多开发人员所面对的烦恼。本文将描述造成重新编译的场景，并从解释WebLogic JSP容器的内部操作开始，介绍每个显然“不受欢迎的”场景，并应用容器的过期检查算法（Stale Checking Algorithm）。此外，本文还将讨论控制JSP和servlet类重载的参数。对以生产模式下运行的服务器，极力推荐这么做。

**JSP容器的过期检查机制**
  
在WebLogic中，JSP被编译成.class文件。我们使用的术语过期检查机制（Stale Checking Mechanism）指的是用来判断某一特殊JSP .class文件是否比当前JSP文件更旧（“过期”）的逻辑。WebLogic JSP容器确保任何JSP及其相关文件只在修改后才能被重新编译。查看生成的Java代码是了解JSP容器内部操作的一个好方法。我们将采用一个JSP作为例子，使用命令行JSP编译器编译它，并查看生成的源代码。JSP编译器（WebLogic.jspc）是随标准WebLogic 服务器安装工具箱一起提供的。

考虑一个称为foo.jsp的简单JSP页面：

A simple JSP page

现在使用命令行JSP编译器来编译这个JSP，指定一个称为keepgenerated的选项，顾名思义，该选项为JSP页面生成相应的Java代码，并将代码保存在磁盘上。

<pre>java weblogic.jspc -keepgenerated -d .\WEB-INF\classes foo.jsp
[jspc]warning: expected file /WEB-INF/web.xml not found,
tag libraries cannot be resolved.
&lt;Jul 11, 2004 7:29:26 PM PDT&gt; &lt;Warning&gt; &lt;HTTP&gt;
&lt;BEA-101181&gt; &lt;Could not find web.
xml under WEB-INF in the doc root: ..&gt;</pre>

编译器在作为上述选项指定的输出目录（-d）中生成.java文件及其对应的.class文件。它将生成的类文件放在称为jsp\_servlet的包中，这恰巧是默认的JSP包前缀（除非在weblogic.xml中覆盖），因此，生成的Java文件可在.\WEB-INF\classes\jsp\_servlet中找到，并且称为__foo.java。
  
请注意，我们可忽略编译器发出的关于未找到web.xml文件的警告，因为此时我们并没有真正使用标签库。
  
在生成代码(__foo.java)中，与我们的讨论最相关的部份就是staticIsStale()方法，如下所示。

**清单1. staticIsStale()方法**

<pre>public static boolean _staticIsStale(weblogic.servlet.jsp.StaleChecker sci) {
if (sci.isResourceStale("/foo.jsp", 1089594167518L, "8.1.2.0",
"America/Los_Angeles"))
return true;
return false;
}</pre>

从上面一小段代码中显然可以看出，调用weblogic.servlet.jsp.StaleChecker接口上的isResourceStale()方法是为了确定JSP是否已修改过。isResourceStale()方法的参数如下所示，这些参数是按以下顺序出现的：

1、 要检查的资源，比如，/foo.jsp。
  
2、 JSP页面的时间戳（长整型）。
  
3、 WebLogic Release Build版。
  
4、 当前机器的默认时区。

JSP容器通过实现StaleChecker接口调用_staticIsStale()方法。该实现接收一个带有清单1中所示参数的回调(isResourceStale())。有了这些参数，该实现可以仅接收所有必需的信息，以推断给定资源是否过期。当资源（参数1）/foo.jsp的时间戳（参数2）比存储在已编译类文件中的时间戳还要新（参数更大）时，或者当发行版本不同时，JSP容器认为JSP.class文件“过期”。
  
让我们看它的一些重要结论：

  * 因为JSP页面的时间戳保存在类文件内部，并且是在编译时计算的，所以修改类文件的时间戳不会对过期检查过程产生影响。（这是一种很常见的荒谬说法，但愿上面的例子清楚地驳斥了它。）
  * 第4个参数，也就是时区，只在以存档格式（.war）进行部署时使用。
  * WebLogic发行版本随每个服务包改变，因此需要为每个服务包重新编译所有JSP。提出这个要求是为了确保JSP类可以利用较新服务包或发行版本中的所有编译器缺陷修复或所有JSP运行时更改。

**静态包含怎样？**
  
人们会问的下一个合乎逻辑的问题是：即使只修改了特定JSP页面的一个静态包含文件，JSP也会重新编译这个页面吗？回答是肯定的。即使是修改了像静态包含这样的相关文件，也要重新编译整个页面（称为“编译单元”更合适）。要了解容器如何处理这种依赖性，请考虑以下包含名为baz.inc的静态包含文件的JSP。

清单2. foo.jsp

<pre>A simple jsp page.
&lt;%@ include file="baz.inc"%&gt;</pre>

清单3. baz.inc

<pre>--
Simple Static Include
--</pre>

为JSP编译器对foo.jsp重运行上述命令行，现在会产生一个Java文件，它包含如下所示的一小段有趣代码。如您所见，每个从属物都是用_staticIsStale()方法处理的，这样，即使修改了一个从属物（这里是baz.inc），也要重新编译整个JSP或“编译单元”。JSP容器期望根JSP页面（foo.jsp）返回一个指示它是否过期的布尔值。因此，每个生成的类文件都会生成检验其所有相关文件的代码。

<pre>public static boolean _staticIsStale(weblogic.servlet.jsp.StaleChecker sci) {
if (sci.isResourceStale("/foo.jsp", 1089616972487L, "8.1.2.0", "America/Los_Angeles"))
return true;
if (sci.isResourceStale("/baz.inc", 1089616984268L, "8.1.2.0", "America/Los_Angeles"))
return true;
return false;
}</pre>

总之，WebLogic JSP容器让每个JSP .class维护自己的从属物列表，并根据这个列表来存储原始JSP（及其从属物）的状态（时间戳）。容器对JSP .class调用_staticIsStale()方法，然后JSP .class回调JSP容器，并通过weblogic.servlet.jsp.StaleChecker.isResourceStale()返回判断单个资源是否过期所需的所有信息。这大大简化了过期检查任务，而且消除了在单独某个位置上为每个JSP维护时间戳的需要。

**导致重新编译JSP的场景**
  
我们已经分析了JSP容器执行过期检查时要考虑的一些因素。现在，让我们来看看重新编译JSP的一些常见场景：

1. 使用构建脚本的文件副本可修改JSP的时间戳。这可导致重新编译所有JSP。
  
考虑一下所有JSP都位于名为src的目录中的场景。假定某一构建脚本复制了所有JSP，并将servlet Java文件编译到构建目录中。然后该脚本在src目录之上运行weblogic.jspc，并将所有已编译的JSP放入构建目录中。在这里，将JSP复制到构建目录中很可能改变了JSP的时间戳（除非构建脚本使用cp –p/-m保留文件时间戳）。当该Web应用程序从构建目录部署到服务器上时，要重新编译所有JSP，因为JSP类是用比已部署的JSP更旧的JSP（也就是这里复制到构建目录下的JSP）来编译的。这是最常见的重新编译的情况之一，它可通过确保执行复制操作时保留了文件时间戳来避免。
  
2. 修改weblogic.xml的packagePrefix参数将导致重新编译。过期检查机制负责查找特殊Web应用程序weblogic.xml文件中的packagePrefix，并为/foo.jsp搜索名为<packagePrefix>.\_\_foo.class的类。假定我们使用weblogic.jspc 预构建所有JSP，将它们放在Web应用程序的WEB-INF/classes目录中，然后我们将该Web应用程序归档（WAR）部署到服务器上。假定我们在这个Web应用程序中有一个名为foo.jsp的JSP。在weblogic.xml中缺乏“packagePrefix”的情况下，过期检查机制将查找jsp\_servlet.\\_\_foo.class类。现在假定我们修改weblogic.xml并添加一个包前缀，比如说com.bar，然后将同一WAR重新部署到服务器。此时访问foo.jsp将导致重新编译JSP，因为过期检查机制将查找名为“com.foo.__foo.class”的类。通过确保调用weblogic.jspc命令时使用了-package参数并使用了相同的包名称，可避免这个问题。

3. 修改weblogic.xml的workingDir参数也会导致重新编译。在这种情况下，除了通常的Web应用程序类路径之外，JSP容器还将在新的“workingDir”中查找JSP类。因为在部署新版本之前，原先使用的目录中有JSP类，但JSP容器无法找到它们，因此将重新编译请求的JSP。
  
注意：场景2和场景3清楚地解释了即使在修改weblogic.xml时，也需要重构建或预编译Web应用程序。在完成所有修改后部署预编译的WAR，确保不用重新编译JSP。

4. 将预构建的WAR部属到一个更新版本的WebLogic服务器会导致重新编译所有JSP。正如描述过期检查机制那一节所解释的，在将JSP部署到不同版本的服务器时，JSP容器会重新编译所有JSP。这么做是为了确保特定版本或服务包中的所有JSP编译器/运行时增强或缺陷修复在生成的代码中可用（没有这一限制，可能会以一些类在JSP运行时引用不存在的方法而结束操作）。在理想情况下，预编译JSP 的构建脚本必须使用与正在部署的服务器使用同一版本的weblogic.jar。建议将服务器使用的所有补丁和周期性修复添加到构建脚本使用的类路径下。总之，构建和部署环境必须完全一致。这可以避免部署后遇到任何不必要重新编译的问题。

**进一步控制过期检查**
  
在容器执行过期检查时进行控制可以让我们调优容器，使它运行得更好，因此为JSP和servlet提供了更好的响应时间。每次过期检查都要求JSP容器转到磁盘并为那个特定的JSP重新读取最后修改时间。当调用太频繁时，该过程可导致性能下降，因为它影响JSP的响应时间。在理想情况下，需要过期检查开发期间表现得非常活跃，特别是在应用程序经常改变时。通过单击浏览器上的刷新/重载，并让JSP容器重新编译和重载新页面，可很好地测试出对特殊JSP所做的修改。但在生产模式下，同样的做法可能导致性能降低。
  
以下参数的默认值最适合开发模式。建议你们在生产环境下进行部署时相应地修改这些值。

**PageCheckSeconds**
  
对已经编译好的JSP的每个新请求，容器都会从其配置文件（这里是weblogic.xm）检查pageCheckSeconds的值，如果上次过期检查与当前时间之间的间隔大于pageCheckSeconds，那么还要执行过期检查操作。例如，假设pageCheckSeconds的值设为10秒。对于针对foo.jsp的请求，容器执行检查操作，以了解当前时间与最后过期检查之间的间隔是否大于pageCheckSeconds。这里假定页面在10秒以前被重新编译和访问过；容器将检查该类是否过期。在此间隔中，不会对foo.jsp的任何请求进行过期检查。
  
如果不是处于开发模式下，而且无需要每隔1秒（默认值）就检查一次JSP页面，那么强烈推荐您将参数值更改为-1（永远不进行过期检查）或者更改为像60秒这样的值。这避免了每次访问JSP时都调用File.lastModified()、重载JSP类和检查时间戳。
  
**清单4. 来自weblogic.xml的代码片段，展示了可如何设置该这个参数**

<pre>&lt;!DOCTYPE weblogic-web-app PUBLIC "-//BEA Systems, Inc.//DTD Web Application 8.1//EN"
"http://www.bea.com/servers/wls810/dtd/weblogic810-web-jar.dtd"&gt;
&lt;weblogic-web-app&gt;
&lt;jsp-descriptor&gt;
&lt;jsp-param&gt;
&lt;param-name&gt;pageCheckSeconds&lt;/param-name&gt;
&lt;param-value&gt;10&lt;/param-value&gt;
&lt;/jsp-param&gt;
&lt;/jsp-descriptor&gt;
&lt;/weblogic-web-app&gt;</pre>

请注意，对于Web应用程序中的JSP从不个别改变的生产环境，最好配置容器永不对servlets和JSP执行过期检查。

**servlet-reload-check-secs**
  
在开发模式中，当servlet被修改和重新编译到，比方说，迅速增长的WAR的WEB-INF/classes目录中时，我们期望从浏览器执行请求时，容器调用它的最新版本的servlet。为了处理该问题，WebLogic 的Web容器每隔servlet-reload-check-secs间隔就会检查WEB-INF/classes中是否有文件被修改过。这个参数的默认值是1秒。对于希望看到对servlet类的最新修改但又不必重新部署应用程序的开发模式而言，这是一个很好的默认值。但在进入生产之前，必须将这个值更改为-1（永不重载servlet文件）。在生产模式下，个别类不会改变，将servlet-reload-check-secs的值设为-1总是最好的选择。

**清单5. servlet-reload-check-secs值设为-1的weblogic.xml示例**

<pre>&lt;!DOCTYPE weblogic-web-app PUBLIC "-//BEA Systems, Inc.//DTD Web Application 8.1//EN"
"http://www.bea.com/servers/wls810/dtd/weblogic810-web-jar.dtd"&gt;
&lt;weblogic-web-app&gt;
&lt;container-descriptor&gt;
&lt;servlet-reload-check-secs&gt;-1&lt;/servlet-reload-check-secs&gt;
&lt;/container-descriptor&gt;
&lt;/weblogic-web-app&gt;</pre>

**JSP类加载器**
  
我们将通过查看WebLogic服务器如何加载JSP类来结束我们的讨论。每个JSP都是在自己的类加载器（通常称为一次性类加载器）中加载的。该类加载器是Web应用程序类加载器的子加载器，负责加载有关的JSP类及其内部类（如果有的话）。好奇的读者可能会觉得奇怪，为什么WebLogic在每个JSP自己的类加载器中加载JSP。真的需要这么复杂吗？WebLogic不能只用应用程序类加载器而使得生活更轻松吗？所有这些问题都是有根据的，而且每个寻求WebLogic类加载器天堂的人都应该问自己这些问题。为了解决这些问题，让我们设想我们的Web应用程序有几个JSP、少数servlet、一个过滤器以及几百个还包含标签处理器类的实用类。现在，假设所有这些类都被加载到单个类加载器中。如果修改单个JSP，然后单击浏览器上的重载，那么下面的事情将不得不发生：

  * JSP容器将不得不重新编译页面。
  * 将不得不丢弃用来加载较早类版本的整个Web应用程序类加载器。
  * 不得不创建一个新的Web应用程序类加载器，而且要重载和重新初始化所有servlet和JSP（包括刚才修改的那个）。

Java不允许重用类加载器来重载类的新版本。相反，您不得不放弃类加载器并创建一个新的。基于这个原因，上面的场景非常不合时宜；即使只更改了一个类，应用服务器也不得不重载大量的类。
  
现在，让我们看看WebLogic是如何实现其类加载器方案的。考虑一下前面提及的那个场景。如果我们修改JSP，并碰巧在浏览器上进行重载，那么服务器将执行以下任务：

  * JSP容器重新编译页面。
  * 它丢弃用来加载这个JSP类的旧版本的那个JSP类加载器。
  * 它创建一个将Web应用程序类加载器作为父加载器的新JSP类加载器，并为该页面提供服务。

如您所见，只有一个JSP类必须重载，整个Web应用程序类加载器保持不动，并且不受我们对JSP所做小小改动的影响。因此，在修改单个JSP时，容器会丢弃旧的类加载器、重新编译并只重载为这个JSP生成的类。这避免了重载或抛弃整个Web应用程序类加载器。当只有某一特殊Web应用程序中的某些JSP经常改变时，这是一个很大的胜利。

**结束语
  
** 有了这些关于JSP容器内部组织的知识，不但可以避免遭遇令人不快的、不必要的JSP重新编译的状况，而且还可以通过使用pageCheckSeconds和servlet-reload-checks-secs参数改进页面响应时间自身。

**原文出处：**
  
<http://dev2dev.bea.com/pub/a/2005/01/jsp_reloaded.html>

<img src="http://dev2dev.bea.com.cn/images/_.gif" alt="" width="100%" height="1" />

作者简介

Nagesh Susarla是BEA Systems的WebLogic服务器开发小组的一名高级软件工程师。他致力于为WebLogic服务器设计和实现Servlet/JSP容器，而且还是ANTLR (分析器/生成器)的超级爱好者。

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [WebLogic 避免不必要的JSP重新编译[转]](http://www.beansoft.biz/2012/03/15/weblogic-%e9%81%bf%e5%85%8d%e4%b8%8d%e5%bf%85%e8%a6%81%e7%9a%84jsp%e9%87%8d%e6%96%b0%e7%bc%96%e8%af%91%e8%bd%ac/)