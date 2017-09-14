---
id: 14
title: 'Retrotranslator让你用JDK1.5的特性写出的代码能在JVM1.4中运行[转]'
date: 2010-04-07T11:48:30+00:00
author: 刘长炯
layout: post
guid: 'http://www.beansoft.biz/%e8%bd%ac%e8%bd%bd%e5%8c%ba/20100414/retrotranslator%e8%ae%a9%e4%bd%a0%e7%94%a8jdk1-5%e7%9a%84%e7%89%b9%e6%80%a7%e5%86%99%e5%87%ba%e7%9a%84%e4%bb%a3%e7%a0%81%e8%83%bd%e5%9c%a8jvm1-4%e4%b8%ad%e8%bf%90%e8%a1%8c.html'
permalink: '/2010/04/07/retrotranslator%e8%ae%a9%e4%bd%a0%e7%94%a8jdk1-5%e7%9a%84%e7%89%b9%e6%80%a7%e5%86%99%e5%87%ba%e7%9a%84%e4%bb%a3%e7%a0%81%e8%83%bd%e5%9c%a8jvm1-4%e4%b8%ad%e8%bf%90%e8%a1%8c/'
views:
  - "3052"
original_post_id:
  - "14"
categories:
  - 转载区
tags:
  - JDK 1.4 Retro
---
转载自: [http://www.blogjava.net/Unmi/articles/124166.html](http://www.blogjava.net/Unmi/articles/124166.html "http://www.blogjava.net/Unmi/articles/124166.html") 作者:Unmi

JDK1.5出来多年了(2004年10月正式发行)，就连6.0正式版在 <http://java.sun.com>上已是赫然在目，紧跟着的各应用服务器和 Java IDE 厂商的都准备就绪. 可是相信很多开发者跟我一样却碍于公司用的是老版本的应用服务器，如WebSphere Application Server,，WebLogic等只能支持到1.4的JDK，要升级应用服务器成本和风险都有担心，所以项目中只能用1.4 的JDK，一直无法体验到 JDK 1.5 的新特性带来的便利．

有些同事机器里一直还是躺着 JDK 1.4，我可能比他们好一点就是直接装了一个 JDK 1.5，然后在 Java IDE 中设置编译器的 Compiler compliance level为 1.4（实质就是javac –target 1.4）．这样避免了用JDK1.5编译的Class 放在1.4的JVM中运行出现49.0的字节码版本太高的错误，这样做只不是50步和100步的差距，照例用不了JDK1.5 的新特性．
  
我一直在探索：能不能使用JDK1.5的特性，然后让生成的字节码能在1.4的JVM下运行．如是果是仅仅换掉应用服务所用的JDK恐怕是会出很多问题的．

也算是功夫不负有心人啊，时至今日终于在网上找着了一个叫做 Retrotranslator 的工具，开源的，在 SourceForge <http://sourceforge.net/projects/retrotranslator>，当前版本是1.2.1．这个工具正好能满足我的需求．进到那个下载页面，你只要下载 [Retrotranslator-1.2.1-bin.zip](http://downloads.sourceforge.net/retrotranslator/Retrotranslator-1.2.1-bin.zip?modtime=1170291482&big_mirror=0)，其中包含了
  
retrotranslator-runtime-1.1.1-bundle.jar 字节码转换之后，运行时需要这个包来支持
  
retrotranslator-transformer-1.2.1-bundle.jar 转换字节码用，如用命令转换或用ant来转换需要这个包
  
而且还有一个 backport-util-concurrent-3.0.jar 大概是用新的并发机制运行时需要依赖这个包
  
Retrotranslator实质上是一个基于ASM 框架的字节码转换工具，如果要看它详细的使用帮助，请见页面 <http://retrotranslator.sourceforge.net/>．
  
使用 Retrotranslator 可以让你使用的JDK1.5的特征有泛型、注解、泛型和注解的反射、枚举、自动装/拆箱、增强的循环、变参、协变式返回类型、格式化输出、静态引入、新的并发机制、增强的集合框架。（见[What Java 5 features are supported?](http://retrotranslator.sourceforge.net/#features)）
  
还能使用新的类和新的方法，如 StringBuilder 等，见[What Java 5 classes and methods are supported?](http://retrotranslator.sourceforge.net/#supported)
  
使用方式：
  
1． 命令行下转换用JDK1.5的编译的classes文件
  
2． 用Ant或Maven自动化转换用JDK1.5的编译的classes文件，Retrotranslator提供了对Ant和Maven的支持。
  
3． 运行程序时加载类时即时转换换用JDK1.5的编译的类打成的jar包
  
4． 作为 IntelliJ IDEA的一个插件使用，可惜现在还没有Eclipse的插件，只能是期盼着。

下面只介绍如何用ANT方式来转换用JDK1.5的编译的classes文件，让它们能运行在1.4的JVM中。步骤如下：
  
1． 用1.5的JDK编译好你的类，比如编译在c:workspaceunmiWEB-INFclasses下。用Ant或是IDE帮你编译好。
  
2． 把retrotranslator-transformer-1.2.1-bundle.jar拷入到 $ANT_HOME/lib中，如果是在Eclipse中运行Ant Build文件，你需要设置 Window->Preferences->Ant-Runtime然后Add External JARSs…把retrotranslator-transformer-1.2.1-bundle.jar加进来。
  
3． 上面准备做好了，就要开始用 Retrotranslator来转换你的字节码了。转换部分的Ant Build的target像下面这么写：

[view source](http://www.blogjava.net/#viewSource)

[print](http://www.blogjava.net/#printSource)[?](http://www.blogjava.net/#about)

`01.``<!-- 用 Retrotranslator 把上面编译的Class文件转换成JVM1.4的Class文件-->`

`02.``<``target` `name``=``"translate"``>` 

`03.` ```<``taskdef` `name``=``"retrotranslator"`

`04.` ```classname``=``"net.sf.retrotranslator.transformer.RetrotranslatorTask"` `/>` 

`05.` ```<``retrotranslator`

`06.` ```destdir``=``"c:workspaceunmiWEB-INFclasses"` `verify``=``"true"`

`07.` ```srcdir``=``"c:workspaceunmiWEB-INFclasses"``>` 

`08.` ```<!-- 项目中用到的包或类 -->`

`09.` ```<``classpath` `refid``=``"classpath"``/>` 

`10.` ``

`11.` ```<!-- 1.4JDK的运行时包 -->`

`12.` ```<``classpath` `location``=``"c:/jdk1.4/jre/lib/rt.jar"``/>` 

`13.` ```</``retrotranslator``>` 

`14.``</``target``>`

4． 注意到上面destdir和srcdir都写成了一样的，我是让转换后的类直接把原来的类覆盖了，你可已把destdir设置为别的目录。
  
5． 最后就是运行了，你需要事先把retrotranslator-runtime-1.1.1-bundle.jar和backport-util-concurrent-3.0.jar配置在你的classpath中，比如是WEB应用程序，把它们拷到WEB-INFlib中就行了。

比如，你写的是一个企业应用程序或者WEB程序，你只需要在打EAR或WAR包之前作以上的转换就行了。

另外，对于在JSP中用了JDK1.5的特性，就稍稍有点麻烦了，先要用特定于应用服务器的JSP编译器编译姛

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Retrotranslator让你用JDK1.5的特性写出的代码能在JVM1.4中运行[转]](http://www.beansoft.biz/2010/04/07/retrotranslator%e8%ae%a9%e4%bd%a0%e7%94%a8jdk1-5%e7%9a%84%e7%89%b9%e6%80%a7%e5%86%99%e5%87%ba%e7%9a%84%e4%bb%a3%e7%a0%81%e8%83%bd%e5%9c%a8jvm1-4%e4%b8%ad%e8%bf%90%e8%a1%8c/)