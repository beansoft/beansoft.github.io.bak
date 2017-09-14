---
id: 146
title: Portable Java IDE 搭建指南(原创)
date: 2006-11-21T18:51:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=146
permalink: '/2006/11/21/portable-java-ide-%e6%90%ad%e5%bb%ba%e6%8c%87%e5%8d%97%e5%8e%9f%e5%88%9b/'
views:
  - "3884"
original_post_id:
  - "146"
image: /wp-content/uploads/2012/09/o_portable_java.png
categories:
  - 其它
---
<div class="pagelayout">
  <div class="centercolumn">
    <div class="singlepost">
      <strong>Portable Java IDE 搭建指南(原创)</strong> </p> 
      
      <p>
        搭建一个可随身携带的 Java IDE, 让您随时随地用自己喜欢的工具开发, 甚至是重做系统之后也可以立即开发. 包括: MyEclipse, Intellij IDEA, Netbeans, Tomcat, Resin 等的 Portable 配置方法.
      </p>
      
      <ul class="entrylist">
        <li class="entrylistitem">
          <a id="CategoryEntryList1_EntryStoryList_Entries_ctl01_TitleUrl" class="entrylisttitle" href="http://www.blogjava.net/beansoft/archive/2006/11/27/83884.html"><strong><font color="#006bad" size="2">Portable Java IDE 2.1 打包下载</font></strong></a> (本文内容将逐渐更新到以 2.0 为准, 附带介绍使用方法) <p>
            首先像笔者这样的穷程序员, 买不起笔记本, 每日只能用移动硬盘来同步一下最新的工作成果或者新下载的软件, 有时候去帮人做 case, 这时候别人的电脑上可能一穷二白, 什么开发工具也没有. 如果这时候从头下载一套 IDE 再配置, 那不知道要有多少时间才能投入工作. 因此受 <a href="http://portableapps.com/">http://portableapps.com</a> 的可携带应用启发, 并在他们提供的工具的帮助下, 笔者经过努力, 终于搭建了一套集合数十种开发武器于一身的终极开发武器霸王: <strong>Portable Java IDE! </strong>这十种武器就是:&#160; Resin, Tomcat, Gel, IDEA, Mysql 5 绿色版, JProfiler, DJ Java Decompiler, DbVisualizer 5, MySql-Front, Portable Firefox, 每种都能要了你的命, 合起来就是要你命3000!
          </p>
          
          <p>
            <img border="0" hspace="0" alt="" src="http://www.blogjava.net/images/blogjava_net/beansoft/17524/o_portable_java.png" width="337" height="570" />
          </p>
          
          <p>
            这个软件, 启动后将会显示一个快捷方式面板, 可以建立分组, 点击相应的程序, 即可启动. 目录文件可以任意复制到硬盘, 移动硬盘, 新做的电脑上, 让您2分钟内投入工作(这两分钟可能需要您输入一下注册码&#8230;对某些软件来说).
          </p>
          
          <p>
            首先说目录结构: <br />/_PortableJavaIDE2.0 <br />&#160;&#160; jdk1.5.0 <br />&#160;&#160; eclipse3.2 <br />&#160;&#160; EclipsePlugins <br />&#160;&#160; MyEclipse5 <br />&#160;&#160; mysql5green <br />&#160;&#160; PortableFirefox <br />&#160;&#160; resin-pro-3.0 <br />&#160;&#160; jakarta-tomcat-5.0.30 <br />&#160;&#160; IntelliJ IDEA 5.1 <br />&#160;&#160; Gel <br />&#160;&#160; jprofiler4&#160; <br />&#160;&#160; netbeans-5.5 <br />&#8230;. <br />之所以这样布局, 就是为了启动的脚本能方便的找到相应的文件.
          </p>
          
          <p>
            然后根目录下放什么东西呢?根目录下放一个软件叫 Pstart, 它的作用就是能以相对路径的方式启动加在上面的快捷方式, 也能在不用的时候最小化到系统托盘. 该软件在这里下载: <a href="http://portableapps.com/apps/utilities/pstart">http://portableapps.com/apps/utilities/pstart</a> .启动后的界面如图所示: </li> </ul> 
            
            <p>
              <strong>PStart</strong>
            </p>
            
            <p class="info">
              &#160;
            </p>
            
            <p class="tagline" align="left">
              <img alt="pstart.png" align="right" src="http://portableapps.com/files/images/screenshots/pstart.png" width="150" height="224" />a handy application launcher that sits in your system tray
            </p>
            
            <p class="content">
              PStart is an application menu that allows you to easily launch your portable apps. When run, it sits in your system tray and brings up an icon menu of the apps you have on your portable device.
            </p>
            
            <p class="download-box">
              <a class="download-link" title="Get PStart" href="http://www.pegtop.de/start/"><span><strong>Get PStart</strong><em>for Windows, English 0.6MB</em></span></a><a href="http://portableapps.com/apps/utilities/application_menus/pstart#download_details">Download Details</a>
            </p>
            
            <p class="content">
              Features
            </p>
            
            <p class="content">
              PStart is a simple tray tool to start user defined applications. Designed to run portable applications (like Portable Firefox & Thunderbird), you can start anything runnable from USB key devices or removable disks.
            </p>
            
            <p>
              这下你明白我的用途了吧, 我们就是用它来做启动中心, 常用的目录也可以拖放到上面, 还可以加入二级, 三级甚至N级的应用分组.
            </p>
            
            <p>
              再介绍一下 2.0 中的 EXE 文件启动 BAT 文件的奥秘&#8230; 不知道大家用过 Together for Eclipse 没有, 它的启动文件 TogetherEC.exe, 很有意思, 你执行它的话, 它就自动执行同一个目录下面的 TogetherEC.bat,&#160; 而且, 你把这个 EXE 文件改名为不同的文件名, 它就会去启动不同的 BAT 文件名.
            </p>
            
            <p>
              接下来就有些老套了, 大部分的篇幅都是关于如何编写BAT文件或者配置文件来让应用能够使用相对路径来启动的方法了.
            </p>
            
            <p>
              <strong>JDK</strong>
            </p>
            
            <p>
              首先自然是下载然后安装一个 JDK 了, 这里我们建议您下载最新的 JDK 1.5, 从 <a href="http://java.sun.com/javase/downloads/index.jsp/,Tomcat"><font color="#002c99"><strong>http://java.sun.com/javase/downloads/index.jsp</strong></font></a>下载它. 安装完毕, 然后将安装时输入的安装路径(例如 c:jdk1.5.0_09)目录下的文件复制到/_PortableJava这里, 重命名为 jdk1.5.0, 记住这个路径.
            </p>
            
            <p>
              <strong>Eclipse</strong>
            </p>
            
            <p>
              接着下载 Eclipse, 从 <a href="http://www.eclipse.org/">http://www.eclipse.org</a> 下载它, 完了解压缩到/_PortableJava目录下, 将目录重命名为 eclipse3.2. 这还没完, 因为在没装 JRE 的电脑上, Eclipse 根本不能运行, 另外, Eclipse 的设置信息默认也是一个用户建立一个地方的, 因此我们要在这里改造到, 具体就是在 eclipse3.2 目录下新建这样一个文件:
            </p>
            
            <p>
              eclipse.bat
            </p>
            
            <div style="border-bottom:#cccccc 1px solid;border-left:#cccccc 1px solid;background-color:#eeeeee;width:98%;font-size:13px;border-top:#cccccc 1px solid;border-right:#cccccc 1px solid;padding:4px 5px 4px 4px;">
              <span style="color:#000000;">start eclipse -clean -vm ..JDK1</span><span style="color:#000000;">.5.0</span><span style="color:#000000;">binjavaw -data ./workspace</span>
            </div>
            
            <p>
              这个命令指定了JDK路径还有工作台(workspace)的路径, OK, 还差一步, 请启动 PStart.exe, 将这个 bat 文件拖放到它的 Items 面板下建立一个快捷方式. 这时候你会发现这个文件是 BAT 的图标, 怎么改它的图标呢? 在这个快捷方式上点击右键, 选择菜单"Properties", 完了出现一个属性对话框, 点击"Advanced"面板, 可以看到有个输入框"Replace icon (optional)", 点击框右边的"Browse"按钮, 选择 eclipse3.2 目录下面的那个eclipse.exe, OK, 你可以看到图标已经改变了. 双击这个快捷方式启动, 之后你就会发现每次在新的电脑上你的工作台设置都没有丢失! That&#8217;s IT! 因为你的 workspace 目录已经固定在当前目录下了.
            </p>
            
            <p>
              注: 如果你下载了 Portable Java IDE 2.0, 那么不需要建立这个启动文件了, 因为我们的 IDE 已经写好了这个启动脚本, 你所做的就是下载, 解压缩即可 具体: 解压缩 eclipse-xxx-win32.zip, 可以看到一个目录 eclipse, 把它重命名为<br /> eclipse3.2, 把这个目录复制到 _PortableJavaIDE2.0. <br /><strong>MyEclipse <br /></strong> <br />从 <span class="a"><font color="#008000" size="2"><a href="http://www.myeclipseide.com/">www.<b>myeclipse</b>ide.com</a></font><font color="#000000" size="3">下载 MyEclipse, 安装, 完毕后讲它单独的那个应用目录复制到/_PortableJava <br />下面, 重命名为MyEclipse5, 注意它下面一般会有两个子目录: eclipse, MyEclipse-UninstallerData. 接着在上文提到的 eclipse3.2 目录下面建立一个目录名字为 links, 然后在此目录下新建一个文件com.genuitec.eclipse.MyEclipse.link(当然这个名字也可以为其他), 内容如下: <br /></font></span> <br />path=..\MyEclipse5
            </p>
            
            <p>
              之后启动时候依然用上面的那个快捷方式即可, 同样的个人设置也不会丢失, 但是可能麻烦的是每次换电脑的时候都得输入注册码&#8230; 注册码自己购买, 呵呵, 偶不管这个.
            </p>
            
            <p>
              <strong>Gel <br /></strong> <br />Gel 是一款免费的 Java 开发工具, 有点像 JCreator, 但是它本身是支持国际化语言界面的(当然包括中文了), 基于 Delphi 开发的,&#160; 所以运行的速度很快, 也支持很漂亮的皮肤. 很不幸的是作者, 一个加拿大人, 于 2005年停止了对它的更新. 这是我2003年时候刚刚参加工作时候所遇到的最好的开发工具之一, 它的强大, 就在于它最早的对 JSP 文件支持鼠标指向动态提示 JavaDoc (根据源码解析生成) 的功能. 而且, 它也能和 class 文件关联, 双击即可反编译出来源码. 它的配置文件是基于 XML 的, 因此当您复制到别的地方的时候, 依然可以工作. 靠它, 我写了很多程序.呵呵.&#160; 所以, 我这里也集成了它作为一个最快速可以启动运行的 Java IDE.下载地址: <a href="http://memescape.co.uk/gexperts/download.html">http://memescape.co.uk/gexperts/download.html</a> <br />截图:
            </p>
            
            <p>
              <img style="border-bottom:black 2px solid;border-left:black 2px solid;width:640px;height:464px;border-top:black 2px solid;border-right:black 2px solid;" src="http://www.blogjava.net/images/blogjava_net/beansoft/17582/r_gel_screen.png" />
            </p>
            
            <p>
              下载后安装, 安装完毕将目录复制过来即可, 默认的目录名字是 Gel. 运行后会自动切换到中文并提示您设置 JDK.
            </p>
            
            <p>
              <strong>Mysql 5 绿色启动版</strong>
            </p>
            
            <p>
              首先请下载 <a href="http://www.blogjava.net/Files/beansoft/mysql5green.7z.zip"><font color="#002c99">mysql5green.7z.zip</font></a>(1.5MB压缩包), 解压缩后得到一个后缀为 .7z 的文件, 请用最新版的 WinRAR 或者去 <a href="http://www.7-zip.org/zh-cn/">http://www.7-zip.org/zh-cn/</a> 下载一个开源的 7zip 压缩管理器解开这个目录. 这个压缩包自带了一个 mysql5green 的目录. 启动mysql的时候只要运行程序APMXE.exe即可看到系统托盘中出现了 mysql 的管理图标, 点击右键选择启动, 即可启动 Mysql 程序. 对应的 mysql 版本是 5.0.19-nt.
            </p>
            
            <p>
              点击 IDE 2.0 中的启动菜单里的 Start Mysql 即可启动.
            </p>
            
            <p>
              <strong>Mysql-Front 2.5 绿色版</strong>
            </p>
            
            <p>
              Mysql-Front 是一款简单好用的 Mysql 管理工具, 它的2.5版本是免费的, 但是到了3.0之后就收费了. 下载, 解压缩即可. 目前它已经包含在 Portable Java IDE 2.0 中了, 目录是: _PortableJavaIDE2.0PortableAppsMySQL-Front.
            </p>
            
            <p>
              Dbvis <br />编写中&#8230;. </div>
            </p></div>
          </p></div> 
          
          <p>
            转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2006/11/21/portable-java-ide-%e6%90%ad%e5%bb%ba%e6%8c%87%e5%8d%97%e5%8e%9f%e5%88%9b/">Portable Java IDE 搭建指南(原创)</a>
          </p>