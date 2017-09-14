---
id: 2724
title: 'BEA dev2dev WebLogic管理精华[转]'
date: 2012-03-15T22:26:37+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2724
permalink: '/2012/03/15/bea-dev2dev-weblogic%e7%ae%a1%e7%90%86%e7%b2%be%e5%8d%8e/'
views:
  - "8186"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
<div>
  <p align="center">
    BEA dev2dev WebLogic管理精华
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p align="right">
    sdj21 daijun@gmail.com
  </p>
  
  <p align="right">
    2005-3-12
  </p>
  
  <p>
    1     日常管理&#8230; 1
  </p>
  
  <p>
    1.1          WebLogic Platform 8.1 永不过期的开发版license. 1
  </p>
  
  <p>
    1.2          如何远程启动WebLogic服务?. 1
  </p>
  
  <p>
    1.3          控制台左边的树结构看不见？&#8230; 1
  </p>
  
  <p>
    1.4          WebLogic 配置出来的各种域有什么区别？&#8230; 2
  </p>
  
  <p>
    1.5          Too many open files错误的处理&#8230; 3
  </p>
  
  <p>
    1.6          Apache2和weblogic7实现虚拟主机&#8230; 4
  </p>
  
  <p>
    1.7          如何限制公网用户访问WebLogic的控制台呢？&#8230; 6
  </p>
  
  <p>
    1.8          开机自动启动oracle和weblogic. 6
  </p>
  
  <p>
    1.9          如何测试虚拟主机&#8230; 8
  </p>
  
  <p>
    1.10        WebLogic的Startup Class应该放在那个目录里&#8230; 8
  </p>
  
  <p>
    1.11        如何停止WebLogic服务？&#8230; 8
  </p>
  
  <p>
    2     应用管理&#8230; 9
  </p>
  
  <p>
    2.1          JNDI里面加和不加java:comp/env/前缀有什么区别？&#8230; 9
  </p>
  
  <p>
    2.2          如何更改默认打开主页？如何设置虚拟目录？&#8230; 9
  </p>
  
  <p>
    2.3          WebLogic Builder使用简介&#8230; 10
  </p>
  
  <p>
    2.4          WebLogic部署应用的方式简明列表&#8230; 10
  </p>
  
  <p>
    2.5          WebLogic如何设置session超时时间&#8230; 11
  </p>
  
  <p>
    3     监控调优&#8230; 13
  </p>
  
  <p>
    3.1          理解JVM的垃圾收集机制&#8230; 13
  </p>
  
  <p>
    3.1.1       简述&#8230; 13
  </p>
  
  <p>
    3.1.2       下面列举一些JVM使用的GC. 13
  </p>
  
  <p>
    3.1.3       Sun Hotspot 1.4.1 JVM堆大小的调整&#8230; 14
  </p>
  
  <p>
    3.1.4       从JVM中获取信息以助于调整方案&#8230; 15
  </p>
  
  <p>
    3.1.5       BEA JRockit JVM的使用&#8230; 15
  </p>
  
  <p>
    3.2          WebLogic Server Hang产生的一般原因&#8230; 16
  </p>
  
  <p>
    3.2.1       系统内存不足&#8230; 16
  </p>
  
  <p>
    3.2.2       系统CPU忙&#8230; 17
  </p>
  
  <p>
    3.2.3       系统文件描述符数目不足&#8230; 17
  </p>
  
  <p>
    3.2.4       线程死锁&#8230; 17
  </p>
  
  <p>
    3.3          &#8220;指定的网络名不再可用&#8221;错误&#8230; 18
  </p>
  
  <p>
    4     集群配置&#8230; 19
  </p>
  
  <p>
    4.1          集群简明配置过程&#8230; 19
  </p>
  
  <p>
    4.2          WebLogic应用在集群环境下的一些基本知识&#8230; 20
  </p>
  
  <p>
    4.2.1       基本概念&#8230; 20
  </p>
  
  <p>
    4.2.2       集群规划&#8230; 21
  </p>
  
  <p>
    4.2.3       服务器配置任务列表&#8230; 21
  </p>
  
  <p>
    5     安全管理&#8230; 25
  </p>
  
  <p>
    5.1          WebLogic AD ldap 配置方法&#8230; 25
  </p>
  
  <p>
    5.2          口令的保护&#8230; 26
  </p>
  
  <p>
    6     其它资源&#8230; 29
  </p>
  
  <p>
    6.1          dev2dev 学堂&#8230; 29
  </p>
  
  <p>
    6.2          WebLogic代码库和CodeShare. 29
  </p>
  
  <p>
    6.3          在线论坛Dev2dev. 30
  </p>
  
  <p>
    6.4          学习WebLogic起步过程&#8230; 30
  </p>
  
  <p>
    &nbsp;
  </p>
</div>

&nbsp;

<div>
  <h2>
    1      日常管理
  </h2>
  
  <h3>
    1.1      WebLogic Platform 8.1 永不过期的开发版license
  </h3>
  
  <p>
    下载地址为：
  </p>
  
  <p>
    <a href="http://dev2dev.bea.com.cn/bbs/servlet/D2DServlet/download/81-8992-44196-240/license.bea">http://dev2dev.bea.com.cn/bbs/servlet/D2DServlet/download/81-8992-44196-240/license.bea</a>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    使用方式：
  </p>
  
  <p>
    替换c:\bea目录下的这个文件，这样就可以使WebLogic Platform用不过期
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    原文地址：
  </p>
  
  <p>
    <a href="http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=8992&tstart=0&quint=true">http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=8992&tstart=0&quint=true</a>
  </p>
  
  <h3>
    1.2      如何远程启动WebLogic服务?
  </h3>
  
  <p>
    用telnet远程控制服务器， 远程启动WEBLOGIC服务，启动后关闭telnet，WebLogic服务也跟着停止，这是因为使用telnet启动的进程会随着telnet进程的关闭而关闭。所以我们可以使用一些UNIX下的命令来做到不关闭。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    使用如下命令：
  </p>
  
  <p>
    nohup startWeblogic.sh&
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    如果想要监控标准输出可以使用：
  </p>
  
  <p>
    tail -f nohup.out
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    原文地址：
  </p>
  
  <p>
    <a href="http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=7709&tstart=0&quint=true">http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=7709&tstart=0&quint=true</a>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <h3>
    1.3      控制台左边的树结构看不见？
  </h3>
  
  <p>
    这是因为浏览器没有安装合适版本的JRE插件来支持Applet。
  </p>
  
  <p>
    可以到<a href="http://java.sun.com/products/plugin/%C2%A0" target="_blank">http://java.sun.com/products/plugin/ </a>下载相应浏览器的插件来解决这个问题。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    原文地址：
  </p>
  
  <p>
    <a href="http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=5233&tstart=0&quint=true">http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=5233&tstart=0&quint=true</a>
  </p>
  
  <h3>
    1.4      WebLogic 配置出来的各种域有什么区别？
  </h3>
  
  <p>
    请看这个链接中的Table 16-1 Configuration Template Summary ，说的很明白<br /> <a href="http://e-docs.bea.com/platform/docs81/confgwiz/tempref.html" target="_blank">http://e-docs.bea.com/platform/docs81/confgwiz/tempref.html</a>
  </p>
  
  <p>
    Table 16-1 Configuration Template Summary
  </p>
  
  <table width="556" border="1" cellspacing="0" cellpadding="0">
    <tr>
      <td valign="top">
        <strong>Template</strong>
      </td>
      
      <td valign="top">
        <strong>Required WebLogic Platform Component</strong>
      </td>
      
      <td valign="top">
        <strong>Filename</strong>
      </td>
      
      <td valign="top" width="207">
        <strong>Description</strong>
      </td>
    </tr>
    
    <tr>
      <td valign="top">
        <a href="http://e-docs.bea.com/platform/docs81/confgwiz/tempref.html#1087598">Avitek Medical Records Sample Domain</a>
      </td>
      
      <td valign="top">
        WebLogic Server
      </td>
      
      <td valign="top">
        <code>medrec.jar</code>
      </td>
      
      <td valign="top" width="207">
        Creates the Avitek Medical Records domain outside the installed kit. This domain is a WebLogic Server sample application suite that concisely demonstrates all aspects of the J2EE platform.
      </td>
    </tr>
    
    <tr>
      <td valign="top">
        <a href="http://e-docs.bea.com/platform/docs81/confgwiz/tempref.html#1092440">Basic WebLogic Integration Domain</a>
      </td>
      
      <td valign="top">
        WebLogic Integration,WebLogic Workshop,WebLogic Server
      </td>
      
      <td valign="top">
        <code>wli.jar</code>
      </td>
      
      <td valign="top" width="207">
        Creates a domain that supports the development of WebLogic Integration solutions.<strong>Note: </strong>To create a domain that supports the development of WebLogic Server Process Edition solutions, use the Basic WebLogic Integration Domain template. If you have an existing WebLogic Server-based domain, you can extend it to include the resources required for WebLogic Server Process Edition by using the <a href="http://e-docs.bea.com/platform/docs81/confgwiz/tempref.html#1098208">WebLogic Integration Extension Template</a>.
      </td>
    </tr>
    
    <tr>
      <td valign="top">
        <a href="http://e-docs.bea.com/platform/docs81/confgwiz/tempref.html#1092596">Basic WebLogic Platform Domain</a>
      </td>
      
      <td valign="top">
        WebLogic Platform (all components must be installed)
      </td>
      
      <td valign="top">
        <code>platform.jar</code>
      </td>
      
      <td valign="top" width="207">
        Creates a domain that supports the development of applications using all WebLogic Platform components.
      </td>
    </tr>
    
    <tr>
      <td valign="top">
        <a href="http://e-docs.bea.com/platform/docs81/confgwiz/tempref.html#1092774">Basic WebLogic Portal Domain</a>
      </td>
      
      <td valign="top">
        WebLogic Portal,WebLogic Workshop,WebLogic Server
      </td>
      
      <td valign="top">
        <code>wlp.jar</code>
      </td>
      
      <td valign="top" width="207">
        Creates a domain that supports the development of WebLogic Portal solutions.
      </td>
    </tr>
    
    <tr>
      <td valign="top">
        <a href="http://e-docs.bea.com/platform/docs81/confgwiz/tempref.html#1092546">Basic WebLogic Server Domain</a>
      </td>
      
      <td valign="top">
        WebLogic Server
      </td>
      
      <td valign="top">
        <code>wls.jar</code>
      </td>
      
      <td valign="top" width="207">
        Creates a simple WebLogic Server domain without any sample applications.
      </td>
    </tr>
    
    <tr>
      <td valign="top">
        <a href="http://e-docs.bea.com/platform/docs81/confgwiz/tempref.html#1085727">Basic WebLogic Workshop Domain</a>
      </td>
      
      <td valign="top">
        WebLogic Workshop,WebLogic Server
      </td>
      
      <td valign="top">
        <code>wlw.jar</code>
      </td>
      
      <td valign="top" width="207">
        Creates a domain that supports the development of WebLogic Workshop solutions.
      </td>
    </tr>
    
    <tr>
      <td valign="top">
        <a href="http://e-docs.bea.com/platform/docs81/confgwiz/tempref.html#1092278">WebLogic Server Examples Domain</a>
      </td>
      
      <td valign="top">
        WebLogic Server
      </td>
      
      <td valign="top">
        <code>examples.jar</code>
      </td>
      
      <td valign="top" width="207">
        Creates the WebLogic Server Examples domain outside the installed kit. This domain contains a collection of examples that illustrate best practices for coding individual J2EE APIs.
      </td>
    </tr>
  </table>
  
  <p>
    原文地址：
  </p>
  
  <p>
    <a href="http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=9188&tstart=0&quint=true">http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=9188&tstart=0&quint=true</a>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <h3>
    1.5      Too many open files错误的处理
  </h3>
  
  <p>
    在有些Linux下由于操作系统的限制，单一进程可以打开的文件数有限制，引起WebLogic报告错误，解决这问题需要编译内核并且调节一些限制参数。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    在Linux内核2.4.x中需要修改源代码，然后重新编译内核才生效。编辑Linux内核源代码中的 include/linux/fs.h文件，将 NR_FILE 由8192改为65536，将NR_RESERVED_FILES 由10 改为 128。编辑fs/inode.c 文件将MAX_INODE 由16384改为262144。一般情况下，系统最大打开文件数比较合理的设置为每4M物理内存256，比如256M内存可以设为16384，而最大的使用的i节点的数目应该是最大打开文件数目的3倍到4倍。另外，对每个进程的设置：
  </p>
  
  <p>
    ulimit -n 4096 将每个进程可以打开的文件数目加大到4096，缺省为1024
  </p>
  
  <p>
    ulimit -m 4096 限制每个进程使用的内存数。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    原文地址：
  </p>
  
  <p>
    <a href="http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=2461&tstart=0&quint=true">http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=2461&tstart=0&quint=true</a>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <h3>
    1.6      Apache2和weblogic7实现虚拟主机
  </h3>
  
  <p>
    选择apache2,是因为目前wls7只支持apache2的结合.
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    1.首先，正确安装apache2,这里我们假设安装在C:\apache group,安装完毕，需要测试apache2是否支持动态加载模块功能，这样测试，到命令
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    提示符下运行:
  </p>
  
  <p>
    c:\>apache group\apache2\bin\apache -l
  </p>
  
  <p>
    如果列出：
  </p>
  
  <p>
    mod_so.c
  </p>
  
  <p>
    则表示支持，然后将本篇文章附件中的mod_wl_20.so拷贝到apache group\apache2\modules下面，运行：
  </p>
  
  <p>
    c:\>apache group\apache2\bin\apache -t
  </p>
  
  <p>
    如果输出：
  </p>
  
  <p>
    Syntax Ok
  </p>
  
  <p>
    表示WebLogic Server plug-in安装成功。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    2.正确安装weblogic7.0。这里我们假设wls7的安装路径是：c:\bea。然后用域配置向导配置一个域，我们假设域
  </p>
  
  <p>
    的名称为amjn,路径是c:\bea\user_projects\amjn,然后在amjn下面分别建立两个站点web1,web2，修改
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    c:\bea\user_projects\amjn\config.xml文件，在
  </p>
  
  <p>
    <Application Deployed=&#8221;true&#8221; Name=&#8221;DefaultWebApp&#8221;
  </p>
  
  <p>
    Path=&#8221;.\applications&#8221; StagedTargets=&#8221;&#8221; TwoPhase=&#8221;false&#8221;>
  </p>
  
  <p>
    <WebAppComponent Name=&#8221;DefaultWebApp&#8221; Targets=&#8221;myserver&#8221; URI=&#8221;DefaultWebApp&#8221;/>
  </p>
  
  <p>
    </Application>
  </p>
  
  <p>
    下面添加：
  </p>
  
  <p>
    <Application Deployed=&#8221;true&#8221; Name=&#8221;web1&#8243; Path=&#8221;.\applications\web1&#8243;
  </p>
  
  <p>
    StagedTargets=&#8221;&#8221; TwoPhase=&#8221;false&#8221;>
  </p>
  
  <p>
    <WebAppComponent Name=&#8221;web1&#8243; URI=&#8221;web1&#8243; VirtualHosts=&#8221;web1_vh&#8221;/>
  </p>
  
  <p>
    </Application>
  </p>
  
  <p>
    <Application Deployed=&#8221;true&#8221; Name=&#8221;web2&#8243; Path=&#8221;.\applications\web2&#8243;
  </p>
  
  <p>
    StagedTargets=&#8221;&#8221; TwoPhase=&#8221;false&#8221;>
  </p>
  
  <p>
    <WebAppComponent Name=&#8221;web2&#8243; Targets=&#8221;myserver&#8221; URI=&#8221;web2&#8243; VirtualHosts=&#8221;web2_vh&#8221;/>
  </p>
  
  <p>
    </Application>
  </p>
  
  <p>
    在文件最下面的
  </p>
  
  <p>
    </Domain>
  </p>
  
  <p>
    的上面添加
  </p>
  
  <p>
    <VirtualHost DefaultWebApp=&#8221;web1&#8243; Name=&#8221;web1_vh&#8221; Targets=&#8221;myserver&#8221; VirtualHostNames=&#8221;www.web1.com&#8221;/>
  </p>
  
  <p>
    <VirtualHost DefaultWebApp=&#8221;web2&#8243; Name=&#8221;web2_vh&#8221; Targets=&#8221;myserver&#8221; VirtualHostNames=&#8221;www.web2.com&#8221;/>
  </p>
  
  <p>
    ,然后重新启动运行\amjn\startWebLogic.cmd,一定要运行正常。到这里，weblogic算是配置完成了。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    3.现在开始配置apache多个虚拟主机，首先我们先打开c:\winnt\system32\drivers\etc\hosts文件，在其中添加：
  </p>
  
  <p>
    10.1.3.30 www.web1.com
  </p>
  
  <p>
    10.1.3.30 www.web2.com
  </p>
  
  <p>
    这里面的10.1.3.30是你的weblogic服务器绑定的ip,然后打开apache2\conf\httpd.conf文件，在174行，注意是174行加入如下语句：
  </p>
  
  <p>
    #WebLogic Server Proxy Settings  &#8212;&#8212;-该行是174行
  </p>
  
  <p>
    LoadModule weblogic_module modules/mod_wl_20.so
  </p>
  
  <p>
    <IfModule mod_weblogic.c>
  </p>
  
  <p>
    WebLogicHost www.synnex-china.com
  </p>
  
  <p>
    WebLogicPort 7001
  </p>
  
  <p>
    MatchExpression *.jsp
  </p>
  
  <p>
    MatchExpression *.do
  </p>
  
  <p>
    </IfModule>
  </p>
  
  <p>
    然后修改httpd.conf文件中的Listen:80为Listen:10.1.3.30:80,在文件section 3部分添加:
  </p>
  
  <p>
    NameVirtualHost10.1.3.30
  </p>
  
  <p>
    <VirtualHost10.1.3.30>
  </p>
  
  <p>
    ServerName www.web1.com
  </p>
  
  <p>
    DocumentRoot &#8220;c:/bea/user_projects/amjn/applications/web1&#8221;
  </p>
  
  <p>
    ErrorLog logs/web1.com.log
  </p>
  
  <p>
    </VirtualHost>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    <VirtualHost10.1.3.30>
  </p>
  
  <p>
    ServerName www.web2.com
  </p>
  
  <p>
    DocumentRoot &#8220;c:/bea/user_projects/amjn/applications/web2&#8221;
  </p>
  
  <p>
    ErrorLog logs/web2.com.log
  </p>
  
  <p>
    </VirtualHost>
  </p>
  
  <p>
    启动apache,如果没有问题（可以通过logs/error.log查看），那就一切ok了
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    4.现在你可以分别敲入www.web1.com/index.jsp，访问的将是web1/index.jsp,敲入www.web2.com/index.jsp访问的将是web2/index.jsp
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    原文地址：
  </p>
  
  <p>
    <a href="http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=6326&tstart=0&quint=true">http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=6326&tstart=0&quint=true</a>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <h3>
    1.7      如何限制公网用户访问WebLogic的控制台呢？
  </h3>
  
  <p>
    我们的weblogic（版本6.1）应用部署在内部网上，通过防火墙映射到公网上，但公网用户通过键入域名：www.xxx.com/console，就可进入weblogic的登陆页面，用户可猜测管理员的密码，如何屏蔽公网用户对weblogic控制台的访问呢？
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    方法1：
  </p>
  
  <p>
    在控制台上点击左边的你那个domain，将Console Enabled这个选项去掉，这样就完全不能使用console了
  </p>
  
  <p>
    方法2：
  </p>
  
  <p>
    将“console”改名，改“Console Context Path”的“console”为一个希奇古怪的名字就可以了
  </p>
  
  <p>
    方法3：
  </p>
  
  <p>
    不要给WebLogic公网ip，通过一个有公网ip的apache等proxy来访问WebLogic
  </p>
  
  <p>
    方法4：
  </p>
  
  <p>
    启动Administration Port
  </p>
  
  <p>
    方法5：
  </p>
  
  <p>
    应用不发布在Admin Server上，Admin Serve在外网不可见
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    原文地址：
  </p>
  
  <p>
    <a href="http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=2230">http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=2230</a>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <h3>
    1.8      开机自动启动oracle和weblogic
  </h3>
  
  <p>
    我的机器是5L，oracle9i，weblogic6.1，HTTPServer<br /> 由于给别人装的机器，对方水平有限，为了省心，还是让系统起来自动运行各项应用比较好：）<br /> 首先自动启动oracle9i，9i装在oracle文件系统下，在/oracle下建立文件startdb，<br /> 文件内容<br /> echo &#8220;begin to start oracle&#8221;<br /> lsnrctl start<br /> sqlplus /nolog <<EOF<br /> connect /as sysdba<br /> startup<br /> exit<br /> exit<br /> echo &#8220;oracle have started&#8221;<br /> 给startdb执行权限<br /> 自动关闭oracle9i，在/oracle下建立文件stopdb<br /> sqlplus /nolog <<EOF<br /> connect /as sysdba<br /> shutdown immediate<br /> 好了启动和关闭oracle脚本完成还要加到系统的启动和关闭文件里，另外还要在启动oracle后启动weblogic<br /> 在/etc下建立文件rc.startdb，脚本如下
  </p>
  
  <p>
    su &#8211; oracle &#8220;-c /oracle/startdb&#8221;    ＃启动oracle<br /> cd /weblogic/wlserver6.1/config/mydomain  ＃转到weblogic启动目录，必须<br /> ./startWebLogic.sh  ＃启动weblogic<br /> 给文件执行权限<br /> 注 意由于weblogic在启动后如果用户退出telnet 就自动关闭，所以要把weblogic放在后台执行，所以在startWebLogic.sh文件中启动weblogic的命令行改为可以在后台运行，用 nohup （启动命令行） >/home/weblogic.log &<br /> 把weblogic的运行信息存到/home/weblogic.log文件中
  </p>
  
  <p>
    下面要把启动信息放到inittab中，加入一行<br /> startdb:2345678:wait:/etc/rc.startdb<br /> 这样系统启动后会自动启动oracle9i
  </p>
  
  <p>
    系统关机自动关闭oracle9i<br /> 在/etc下建立脚本文件rc.stopdb<br /> su &#8211; oracle &#8220;-c /oracle/stopdb&#8221;<br /> 给执行权限<br /> 由于5L中安装完成后没有/etc/rc.shutdown文件，需要手工创建一个<br /> 内容如下<br /> #!/bin/ksh<br /> rc.stopdb<br /> 给执行权限<br /> 这样当系统关机时会自动寻找rc.shutdown并执行，系统可以自动关闭oracle9i
  </p>
  
  <p>
    当然可以把一些命令行直接写入inittab或rc.shutdown中，看自己的喜好了：）
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    原文地址：
  </p>
  
  <p>
    <a href="http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=8415&tstart=25&quint=true">http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=8415&tstart=25&quint=true</a>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <h3>
    1.9      如何测试虚拟主机
  </h3>
  
  <p>
    在本机配置了虚拟主机，没有DNS Server，如何进行测试呢？
  </p>
  
  <p>
    C:\WINNT\system32\drivers\etc\hosts加入一行：127.0.0.1 test.project.com.cn
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    原文地址：
  </p>
  
  <p>
    <a href="http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=9776&tstart=25&quint=true">http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=9776&tstart=25&quint=true</a>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <h3>
    1.10WebLogic的Startup Class应该放在那个目录里
  </h3>
  
  <p>
    WebLogic在启动的时候可以指定Startup Class，它在任何一个应用的类被加载之前调用，所以应该加到启动时的系统类路径下，可以修改startWebLogic.cmd或commEnv.cmd文件相应的CLASSPATH部分，加入Startup Class的类路径。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    原文地址：
  </p>
  
  <p>
    <a href="http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=9119&tstart=25&quint=true">http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=9119&tstart=25&quint=true</a>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <h3>
    1.11如何停止WebLogic服务？
  </h3>
  
  <p>
    直接杀死进程不是标准的做法，应该使用如下Java命令：
  </p>
  
  <p>
    java -classpath weblogic.jar;%CLASSPATH% weblogic.Admin -url <host_name>:<port_number> SHUTDOWN -username <system_user_name> -password <system_user_password>
  </p>
  
  <p>
    例如：
  </p>
  
  <p>
    java -classpath weblogic.jar;%CLASSPATH% weblogic.Admin -url 192.168.0.1:7001
  </p>
  
  <p>
    SHUTDOWN -username system -password password
  </p>
  
  <p>
    其中如果SHUTDOWN管不掉，可以使用FORCESHUTDOWN代替SHUTDOWN来强制关掉服务器。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    另外也可以直接使用stopWebLogic.cmd。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    原文地址：
  </p>
  
  <p>
    <a href="http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=5519&tstart=25&quint=true">http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=5519&tstart=25&quint=true</a>
  </p>
  
  <p>
    &nbsp;
  </p>
</div>

** <br clear="all" />**

<div>
  <h2>
    2      应用管理
  </h2>
  
  <h3>
    2.1      JNDI里面加和不加java:comp/env/前缀有什么区别？
  </h3>
  
  <p>
    java:comp/env是标准的J2EE环境查找规则，使用这种方式必须做一次环境名到JNDI名的映射，这种隔离使得在写程序时不必关注真正的JNDI名字，其实说白了跟把JNDI名放到配置文件里是一样的，用法如下：
  </p>
  
  <p>
    如把java:comp/env/my/datasource映射到my.ora.dataource
  </p>
  
  <p>
    web.xml<br /> <resource-ref><br /> <res-ref-name>my/datasource</res-ref-name><br /> <res-type>javax.sql.DataSource</res-type><br /> <res-auth>CONTAINER<res-auth><br /> </resource-ref>
  </p>
  
  <p>
    weblogic.xml<br /> <reference-descriptor><br /> <resource-description><br /> <res-ref-name>my/datasource</res-ref-name><br /> <jndi-name>my.ora.dataource</jndi-name>
  </p>
  
  <p>
    ………………….
  </p>
  
  <p>
    而不使用这个前缀的，其实就是直接的JNDI名
  </p>
  
  <p>
    原文地址：
  </p>
  
  <p>
    <a href="http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=17074&tstart=0&quint=true">http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=17074&tstart=0&quint=true</a>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <h3>
    2.2      如何更改默认打开主页？如何设置虚拟目录？
  </h3>
  
  <p>
    设置默认打开主页：
  </p>
  
  <p>
    web.xml增加<br /> <welcome-file-list><br /> <welcome-file>yourfile</welcome-file><br /> </welcome-file-list>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    虚拟目录的配置方法：<br /> 在weblogic.xml中添加如下的类似配置<br /> <virtual-directory-mapping><br /> <local-path>c:/usr/common_jsps.jar</local-path><br /> <url-pattern>*.jsp</url-pattern><br /> </virtual-directory-mapping>
  </p>
  
  <p>
    原文地址：
  </p>
  
  <p>
    <a href="http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=16333&tstart=0&quint=true">http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=16333&tstart=0&quint=true</a>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <h3>
    2.3      WebLogic Builder使用简介
  </h3>
  
  <p>
    在DEV2DEV论坛上有网友会问类似于这样的问题“如何为EJB写那些部署描述文件如ejb-jar.xml以及WebLogic-ejb- jar.xml呢？”，对初学EJB的朋友来说，是一个比较困难的问题，如果不想手写的话，可以采用BEA提供的WebLogic Builder工具或是JBuilder等工具来自动生成。本文就WebLogic Builder的使用进行一个简单的介绍，权且当一个入门的指引，同时欢迎各位朋友就你的经验对这篇文章进行补充完善。使用步骤如下：
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    一、准备。<br /> 例子就用WebLogic安装完后的example中statelessSession EJB的例子，给个路径参考<br /> C: \bea\weblogic700\samples\server\src\examples\ejb20\basic\statelessSession 　将这个目录下的.java文件全部拷贝出来放到一个临时目录中比如C:\temp\WebLogic_Builder_Test来做这个实验，拷贝的文 件有Client.java，Trader.java，TraderBean.java，TradeResult.java， TraderHome.java。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    二、对java原文件进行编译<br /> 命令行中进入C:\temp\WebLogic_Builder_Test，键入　javac -d . *.java，
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    三、打jar包<br /> 命令行中，C:\temp\WebLogic_Builder_Test目录下，键入jar -cvf test.jar *.*，生成test.jar包。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    四、 打开WebLogic Builder工具，选择并打开我们在步骤三中创建的test.jar包，这时WebLogic Builder给出一个提示“Unable to locate deployment descriptors. C:\temp\WebLogic_Builder_Test\test.jar. Would you like new descriptors created for you?”，这意思明白了吧，WebLogic Builder要为你创建基本的部署描述符文件了，当然点击是咯，然后选择保存，这样你的C:\temp\WebLogic_Builder_Test目录下的test.jar文件就有那两个部署描述文件了，可以通过WebLogic Builder工具中的View&#8211;>XML Source进行查看。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    恭喜你，对WebLogic Builder这个工具的使用入门了，至于该工具的其它的一些使用功能比如BEAN属性配置、server部署什么的，就请大家自己研究吧！^Q^
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    原文地址：
  </p>
  
  <p>
    <a href="http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=2683">http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=2683</a>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <h3>
    2.4      WebLogic部署应用的方式简明列表
  </h3>
  
  <p>
    1、WebLogic中应用可分三种，分别对应不同的描述文件及扩展名或目录结构：
  </p>
  
  <p>
    （1）*.JAR: 是EJB的压缩包(有3个描述文件ejb-jar.xml，WEBLOGIC*.0-ejb-jar.xml，WEBLOGIC*.0-cmp-rdbms-jar.xml)
  </p>
  
  <p>
    （2）*.WAR: 是只包含JSP和SERVLET的WEB APPLICATION压缩包(有2个描述文件web.xml，weblogic.xml)
  </p>
  
  <p>
    （3）*.EAR: 是包含EJB和WEB APPLICATION 的J2EE Enterprise Application压缩包(有1 个描述文件，application.xml)
  </p>
  
  <p>
    注意：它们不能混用，如WEB APPLICATOIN不能打包成.EAR文件。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    2、WebLogic的应用用两种发布方式:
  </p>
  
  <p>
    （1）以目录形式存放在WEBLOGIC的APPLICATIONS目录下，适用于开发阶段
  </p>
  
  <p>
    （2）以一个压缩包形式存放在WEBLOGIC的APPLICATIONS目录下，适用于运行阶段，可用JAR 打包，如D:\test >jar cf testwar.war *
  </p>
  
  <p>
    把TEST目录下的所有文件打包成一个testwar.war文件。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    3、WebLogic应用的布置方式有2种
  </p>
  
  <p>
    （1）静态布置:即把应用在CONFIG.XML中登记，可通过WEBLOGIC的控制台进行添加，WEBLOGIC会自动把该应用对应的压缩包拷到APPLICAITONS目录下，如果对该应用修改，需要重新布置才行。
  </p>
  
  <p>
    （2）动态布置:没有在config.xml中登记，可直接把压缩包或目录拷到APPLICATIONS目录下，WebLogic会自动检测到. WebLogic每次启动时会自动对APPLICATIONS目录下没有进行静态布置的应用，进行动态布置。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    4、一个例子:
  </p>
  
  <p>
    如果一个应用中有EJB，JSP，SERVLET，其布置步骤如下:
  </p>
  
  <p>
    （1）生成EJB的JAR文件，最好一个JAR文件对应一个EJB
  </p>
  
  <p>
    （2）生成WEB APPLICATION的WAR文件，在web.xml，weblogic.xml中登记，配置SERVLET，JSP等。
  </p>
  
  <p>
    （3）创建一个application.xml文件，设置该应用的属性.把application.xml，*.JAR， *.WAR，打包成一个*.EAR
  </p>
  
  <p>
    （4）WebLogic的控制台中登记该应用或把该EAR文件拷到application目录下。到此处就完成了部署。
  </p>
  
  <p>
    原文地址：
  </p>
  
  <p>
    <a href="http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=8766&tstart=25&quint=true">http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=8766&tstart=25&quint=true</a>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <h3>
    2.5      WebLogic如何设置session超时时间
  </h3>
  
  <p>
    1 web.xml
  </p>
  
  <p>
    设置WEB应用程序描述符web.xml里的<session-timeout>元素。这个值以分钟为<br /> 单位，并覆盖weblogic.xml中的TimeoutSecs属性<br /> <session-config><br /> <session-timeout>54</session-timeout><br /> </session-config><br /> 此例表示Session将在54分钟后过期<br /> 当<session-timeout>设置为－2，表示将使用在weblogic.xml中设置的<br /> TimeoutSecs这个属性值。<br /> 当<session-timeout>设置为－1，表示Session将永不过期，而忽略在<br /> weblogic.xml中设置的TimeoutSecs属性值。<br /> 该属性值可以通过console控制台来设置
  </p>
  
  <p>
    2 weblogic.xml
  </p>
  
  <p>
    设置WebLogic特有部署描述符weblogic.xml的<session-descriptor>元素的<br /> TimeoutSecs属性。这个值以秒为单位<br /> <session-descriptor><br /> <session-param><br /> <param-name>TimeoutSecs</param-name><br /> <param-value>3600</param-value><br /> </session-param><br /> </session-descriptor><br /> 默认值是3600秒
  </p>
  
  <p>
    原文地址：
  </p>
  
  <p>
    <a href="http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=1972&tstart=25&quint=true">http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=1972&tstart=25&quint=true</a>
  </p>
</div>

** <br clear="all" />**

<div>
  <h2>
    3      监控调优
  </h2>
  
  <h3>
    3.1      理解JVM的垃圾收集机制
  </h3>
  
  <h4>
    3.1.1  简述
  </h4>
  
  <p>
    GC即垃圾收集机制是指JVM用于释放那些不再使用的对象所占用的内存。java语言并不要求JVM有GC，也没有规定GC如何工作。不过常用的JVM都有GC，而且大多数GC都使用类似的算法管理内存和执行收集操作。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    在充分理解了垃圾收集算法和执行过程后，才能有效的优化它的性能。有些垃圾收集专用于特殊的应用程序。比如，实时应用程序主要是为了避免垃圾收集中断，而 大多数OLTP应用程序则注重整体效率。理解了应用程序的工作负荷和JVM支持的垃圾收集算法，便可以进行优化配置垃圾收集器。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    垃圾收集的目的在于清除不再使用的对象。GC通过确定对象是否被活动对象引用来确定是否收集该对象。GC首先要判断该对象时候可以收集。两种常用的方法是 引用计数和对象引用遍历。引用计数存储对特定对象的所有引用数，也就是说，当应用程序创建引用以及引用超出范围时，JVM必须适当增减引用数。当某对象的 引用数为0时，便可以进行垃圾收集。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    早期的JVM使用引用计数，现在大多数JVM采用对象引用遍历。对象引用遍历从一组对象开始，沿着整个对象图上的每条链接，递归确定可到达 （reachable）的对象。如果某对象不能从这些根对象的一个（至少一个）到达，则将它作为垃圾收集。在对象遍历阶段，GC必须记住哪些对象可以到 达，以便删除不可到达的对象，这称为标记（marking）对象。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    下一步，GC要删除不可到达的对象。删除时，有些GC只是简单的扫描堆栈，删除未标记的对象，并释放它们的内存以生成新的对象，这叫做清除 （sweeping）。这种方法的问题在于内存会分成好多小段，而它们不足以用于新的对象，但是组合起来却很大。因此，许多GC可以重新组织内存中的对象，并进行压缩（compact），形成可利用的空间。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    为此，GC需要停止其他的活动活动。这种方法意味着所有与应用程序相关的工作停止，只有GC运行。结果，在响应期间增减了许多混杂请求。另外，更复杂的 GC不断增加或同时运行以减少或者清除应用程序的中断。有的GC使用单线程完成这项工作，有的则采用多线程以增加效率。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <h4>
    3.1.2  下面列举一些JVM使用的GC
  </h4>
  
  <p>
    标记－清除收集器：这种收集器首先遍历对象图并标记可到达的对象，然后扫描堆栈以寻找未标记对象并释放它们的内存。这种收集器一般使用单线程工作并停止其他操作。
  </p>
  
  <p>
    标记－压缩收集器：有时也叫标记－清除－压缩收集器，与标记－清除收集器有相同的标记阶段。在第二阶段，则把标记对象复制到堆栈的新域中以便压缩堆栈。这种收集器也停止其他操作。
  </p>
  
  <p>
    复制收集器 这种收集器将堆栈分为两个域，常称为半空间。每次仅使用一半的空间，JVM生成的新对象则放在另一半空间中。GC运行时，它把可到达对象复制到另一半空 间，从而压缩了堆栈。这种方法适用于短生存期的对象，持续复制长生存期的对象则导致效率降低。
  </p>
  
  <p>
    增量收集器 增量收集器把堆栈分为多个域，每次仅从一个域收集垃圾。这会造成较小的应用程序中断。有多种方法可以定义实际的GC。
  </p>
  
  <p>
    分代收集器  这种收集器把堆栈分为两个或多个域，用以存放不同寿命的对象。JVM生成的新对象一般放在其中的某个域中。过一段时间，继续存在的对象将获得使用期并转入更长寿命的域中。分代收集器对不同的域使用不同的算法以优化性能。
  </p>
  
  <p>
    并发收集器  并发收集器与应用程序同时运行。这些收集器在某点上一般都不得不停止其他操作以完成特定的任务，但是因为其他应用程序可进行其他的后台操作，所以中断其他处理的实际时间大大降低。
  </p>
  
  <p>
    并行收集器  并行收集器使用某种传统的算法并使用多线程并行的执行它们的工作。在多cpu机器上使用多线程技术可以显著的提高java应用程序的可扩展性。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <h4>
    3.1.3  Sun Hotspot1.4.1JVM堆大小的调整
  </h4>
  
  <p>
    Sun Hotspot1.4.1使用分代收集器，它把堆分为三个主要的域：新域、旧域以及永久域。JVM生成的所有新对象放在新域中。一旦对象经历了一定数量的垃圾收集循环 后，便获得使用期并进入旧域。在永久域中JVM则存储class和method对象。就配置而言，永久域是一个独立域并且不认为是堆的一部分。下面介绍如 何控制这些域的大小。
  </p>
  
  <p>
    可使用-Xms和-Xmx控制整个堆的原始大小或最大值。比如，下面的命令是把初始大小设置为128M：
  </p>
  
  <p>
    java –Xms128m–Xmx256m
  </p>
  
  <p>
    为控制新域的大小，可使用-XX:NewRatio设置新域在堆中所占的比例。比如下面的命令把整个堆设置成128m，新域比率设置成3，即新域与旧域比例为1：3，新域为堆的1/4或32M：
  </p>
  
  <p>
    java –Xms128m–Xmx128m–XX:NewRatio =3
  </p>
  
  <p>
    可使用-XX:NewSize和-XX:MaxNewsize设置新域的初始值和最大值。比如，下面的命令把新域的初始值和最大值设置成64m:
  </p>
  
  <p>
    java –Xms256m–Xmx256m–Xmn64m
  </p>
  
  <p>
    一般不把永久域当作堆的一部分。永久域默认大小为4m。运行程序时，JVM会调整永久域的大小以满足需要。每次调整时，JVM会对堆进行一次完全的垃圾收 集。使用-XX:MaxPerSize标志来增加永久域搭大小。在WebLogic Server应用程序加载较多类时，经常需要增加永久域的最大值。当JVM加载类时，永久域中的对象急剧增加，从而使JVM不断调整永久域大小。为了避免 调整，可使用-XX:PerSize标志设置初始值。比如，下面把永久域初始值设置成32m，最大值设置成64m。
  </p>
  
  <p>
    java –Xms512m–Xmx512m–Xmn128m–XX:PermSize=32m–XX:MaxPermSize=64m
  </p>
  
  <p>
    默认状态下，HotSpot在新域中使用复制收集器。该域一般分为三个部分。第一部分为Eden，用于生成新的对象。另两部分称为救助空间，当Eden充满 时，收集器停止应用程序，把所有可到达对象复制到当前的from救助空间，一旦当前的from救助空间充满，收集器则把可到达对象复制到当前的to救助空 间。From和to救助空间互换角色。维持活动的对象将在救助空间不断复制，直到它们获得使用期并转入旧域。
  </p>
  
  <p>
    使用-XX:SurvivorRatio可控制新域子空间的大小。同NewRation一样，SurvivorRation规定某救助域与Eden空间的比值。比如，以下命令把新域设置成64m，Eden占32m，每个救助域各占16m：
  </p>
  
  <p>
    java –Xms256m–Xmx256m–Xmn64m–XX:SurvivorRation=2
  </p>
  
  <p>
    如前所述，默认状态下HotSpot对新域使用复制收集器，对旧域使用标记－清除－压缩收集器。在新域中使用复制收集器有很多意义，因为应用程序生成的大 部分对象是短寿命的。理想状态下，所有过渡对象在移出Eden空间时将被收集。如果能够这样的话，并且移出Eden空间的对象是长寿命的，那么理论上可以 立即把它们移进旧域，避免在救助空间反复复制。<br /> 但是，应用程序不能适合这种理想状态，因为它们有一小部分中长寿命的对象。最好是保持这些中长寿命的对象并放在新域中，因为复制小部分的对象总比压缩旧域廉价。
  </p>
  
  <p>
    为控制新域中对象的复制，可用-XX:TargetSurvivorRatio控制救助空间的比例。该值是一个百分比，默认值是50。当较大的堆栈使用较低的sruvivorratio时，应增加该值到80至90，以更好利用救助空间。
  </p>
  
  <p>
    用-XX:maxtenuring threshold可控制上限。为放置所有的复制全部发生以及希望对象从eden扩展到旧域，可以把MaxTenuring Threshold设置成0。设置完成后，实际上就不再使用救助空间了，因此应把SurvivorRatio设成最大值以最大化Eden空间，设置如下：
  </p>
  
  <p>
    java … -XX:MaxTenuringThreshold=0 –XX:SurvivorRatio＝5000
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <h4>
    3.1.4  从JVM中获取信息以助于调整方案
  </h4>
  
  <p>
    -verbose.gc开关可显示GC的操作内容。打开它，可以显示最忙和最空闲收集行为发生的时间、收集前后的内存大小、收集需要的时间等。
  </p>
  
  <p>
    打开-xx:+ printgcdetails开关，可以详细了解GC中的变化。
  </p>
  
  <p>
    打开-XX: + PrintGCTimeStamps开关，可以了解这些垃圾收集发生的时间，自JVM启动以后以秒计量。
  </p>
  
  <p>
    最后，通过-xx: + PrintHeapAtGC开关了解堆的更详细的信息。
  </p>
  
  <p>
    为了了解新域的情况，可以通过-XX:=PrintTenuringDistribution开关了解获得使用期的对象权。
  </p>
  
  <h4>
    3.1.5  BEA JRockit JVM的使用
  </h4>
  
  <p>
    Bea WebLogic 8.1使用的新的JVM用于Intel平台。在Bea安装完毕的目录下可以看到有一个类似于jrockit81sp1_141_03的文件夹。这就是Bea新JVM所在目录。
  </p>
  
  <p>
    不同于HotSpot把Java字节码编译成本地码，它预先编译成类。JRockit还提供了更细致的功能用以观察JVM的运行状态，主要是独立的GUI控制台或者WebLogic Server控制台。Bea JRockit JVM支持4种垃圾收集器：
  </p>
  
  <p>
    分代复制收集器：它与默认的分代收集器工作策略类似。对象在新域中分配，即JRockit文档中的nursery。这种收集器最适合单CPU机上小型堆操作。
  </p>
  
  <p>
    单空间并发收集器：该收集器使用完整堆，并与背景线程共同工作。尽管这种收集器可以消除中断，但是收集器需花费较长的时间寻找死对象，而且处理应用程序时收集器经常运行。如果处理器不能应付应用程序产生的垃圾，它会中断应用程序并关闭收集。
  </p>
  
  <p>
    分代并发收集器：这种收集器在护理域使用排它复制收集器，在旧域中则使用并发收集器。由于它比单空间共同发生收集器中断频繁，因此它需要较少的内存，应用程序的运行效率也 较高，注意，过小的护理域可以导致大量的临时对象被扩展到旧域中。这会造成收集器超负荷运作，甚至采用排它性工作方式完成收集。
  </p>
  
  <p>
    并行收集器：该收集器也停止其他进程的工作，但使用多线程以加速收集进程。尽管它比其他的收集器易于引起长时间的中断，但一般能更好的利用内存，程序效率也较高。<br /> 默 认状态下，JRockit使用分代并发收集器。要改变收集器，可使用-Xgc:<gc_name>，对应四个收集器分别为gencopy， singlecon，gencon以及parallel。可使用-Xms和-Xmx设置堆的初始大小和最大值。要设置护理域，则使用-Xns:
  </p>
  
  <p>
    java –jrockit –Xms512m–Xmx512m–Xgc:gencon –Xns128m…
  </p>
  
  <p>
    尽管JRockit支持-verbose:gc开关，但它输出的信息会因收集器的不同而异。JRockit还支持memory、load和codegen的输出。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    原文地址：
  </p>
  
  <p>
    <a href="http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=124&threadID=19031&tstart=0">http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=124&threadID=19031&tstart=0</a>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <h3>
    3.2      WebLogic Server Hang产生的一般原因
  </h3>
  
  <h4>
    3.2.1  系统内存不足
  </h4>
  
  <p>
    l  系统CPU忙，系统文件描述符数目不足，线程死锁，JVM有GC方面的bug，对于一些特定的情况可以使用truss命令跟踪系统调用来进行分析。可以打开JVM的gc log,在java命令行上加上-verbose:gc,GC的log输出在java进程的标准输出里,在hp的JVM上，可以通过在java命令行上加-Xverbosegc:file=gcfilename来将gc log写到指定的文件其输出类似：[GC 15639K->13700K(65280K), 0.0068439 secs]。解决办法是调整JVM的内存设置和gc算法,升级jvm或是os patch。
  </p>
  
  <p>
    l  出现OutOfMemoryError或是观察到内存吃紧，操作系统本身的剩余内存，通过top或是vmstat观察，操作系统的swap区，Swap区太小可能导致编译jsp时报“Not enough space”的错，操作系统kernel参数中maxsize的大小，如果观测到数据库连接池里的连接泄漏，极可能是内存泄漏的先兆
  </p>
  
  <p>
    l  JVM的heap区大小，通过java命令行中的-Xms,-Xmx指定，建议最小值和最大值设成一样，可以通过WebLogic console上server/monitor/performance来观察其使用情况，建议生产系统最256M，一般情况下可以设置为系统剩余物理内存的80％，Heap size太大在一些JVM上会有问题，对于sun和hp的JVM，permanent size太小也会出OutOfMemoryError，在java命令行上加-XX:MaxPermSize=128m
  </p>
  
  <p>
    l  尽量减少内存消耗，Session中不要放大的数据，并尽量在不再需要的时候remove掉，如果可以调整session timeout到较小的值，避免在J2EE server端应用里边调用AWT/swing作图，调整ejb的cache/pool设置
  </p>
  
  <p>
    l  内存泄漏，可以通过WebLogic console来观察JVM的heap memory使用情况来获知是否有内存泄漏情况，采用第三方辅助工具来获取更详细信息，如Jprobe/OptimizeIt；有可能是weblogic的bug，但绝大部分情况是由用户的应用引起的，最常见的代码问题是数据库连接没正常关闭。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <h4>
    3.2.2  系统CPU忙
  </h4>
  
  <p>
    l  如果用户访问量很大，CPU占用很高（user态）并不是异常
  </p>
  
  <p>
    l  如果是kernel态很多，需要OS厂商调整操作系统
  </p>
  
  <p>
    l  采用top找到占用CPU很多的进程，如果是非weblogic进程，应该考虑将其移到另外的server上运行，如果是运行weblogic的java进程，通过做thread dump（详细信息后边会介绍到）来确认是那段代码导致了这么高的CPU使用（也有可能是os/jvm本身不正常）
  </p>
  
  <h4>
    3.2.3  系统文件描述符数目不足
  </h4>
  
  <p>
    Log中有“too many open files”的错误，表示达到了系统对一个进程能同时打开的文件数的限制：
  </p>
  
  <p>
    l  ulimit –a –H 可以查看当前限制
  </p>
  
  <p>
    l  ulimit –n number可以来更改当前环境的设置，建议至少设到4096
  </p>
  
  <p>
    l  Solaris上可以通过/usr/proc/bin/pfiles pid来查看指定进程的限制和当前使用的file descriptor数目
  </p>
  
  <p>
    l  Solaris上root用户可以通过/usr/proc/bin/plimit -n soft,hard pid 来动态更改进程的文件描述符的限制
  </p>
  
  <h4>
    3.2.4  线程死锁
  </h4>
  
  <p>
    对于原因不明的hang或是响应慢，最根本的方法就是获取thread dump信息，对于windows系统，在运行java的窗口按Ctrl＋Break，对于UNIX系统，首先用ps找到运行weblogic的java进程的pid，然后执行kill –3 pid，JVM将负责将所有java进程的状态、执行堆栈dump到其标准输出，为了方便获取thread dump信息，在weblogic启动的时候，最好将其标准输出重定向到一个文件，为了反映线程状态的动态变化，需要接连多次做thread dump，每次间隔10-20s。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    对于thread dump信息，主要关注的是线程的状态和其执行堆栈，线程的状态一般为三类
  </p>
  
  <p>
    l  Runnable（R）：当前可以运行的线程
  </p>
  
  <p>
    l  Waiting on monitor（CW）：线程主动wait
  </p>
  
  <p>
    l  Waiting for monitor entry（MW）：线程等锁
  </p>
  
  <p>
    一般关注的都是第一和第三种状态的线程<br /> CPU很忙则关注runnable的线程<br /> CPU闲则关注waiting for monitor entry的线程<br /> 一种典型的死锁是由于在server端应用（比如servlet）中请求由同一weblogic实例serve的资源，解决办法就是将该servlet放到另外的执行队列里去执行。
  </p>
  
  <p>
    原文地址：
  </p>
  
  <p>
    <a href="http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=4525&tstart=0&quint=true">http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=4525&tstart=0&quint=true</a>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <h3>
    3.3      &#8220;指定的网络名不再可用&#8221;错误
  </h3>
  
  <p>
    wl6.1和wl7.0部署应用后都在后台抛出“java.net.SocketException: ReadFile failed: 指定的网络名不再可用”,这不是一个致命的错误，只会在中文Window上。如Hilaser和linstone提出了办法：
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    l  如果你是自己随便玩玩，将你的JDK升级到jdk1.3.1_06
  </p>
  
  <p>
    l  用wls6.1 sp4，到如下位置下载<br /> <a href="http://commerce.bea.com/SoftwareProductDetailWLS?SWName=WebLogic+Server+Evaluation+Software&SWVersion=Version+6.1+SP4&SWPlatform=Microsoft+Windows+NT%2F2000">http://commerce.bea.com/SoftwareProductDetailWLS?SWName=WebLogic+Server+Evaluation+Software&SWVersion=Version+6.1+SP4&SWPlatform=Microsoft+Windows+NT%2F2000</a>
  </p>
  
  <p>
    l  运行cmd，打开窗口菜单（点击左上角窗口图标），选择 默认值，将默认代码页改为437。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    原文地址：
  </p>
  
  <p>
    <a href="http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=9393&tstart=0">http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=9393&tstart=0</a>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    &nbsp;
  </p>
</div>

&nbsp;

<div>
  <h2>
    4      集群配置
  </h2>
  
  <h3>
    4.1      集群简明配置过程
  </h3>
  
  <p>
    在wls7中，集群的受管服务器无需使用相同的端口，这使在一个主机上实现集群成为可能。下面的例子是在一个主机（172.30.94.60）上的 wls7里创建一个集群（mycluster）DEMO，包括管理服务器（myserver:7001）、集群（两个受管服务器serverA: 8001、serverB:8003）、代理服务器（ProxyServer:80）。应用WebApp是部署在集群上的web应用，而 DefaultWebApp是部署在代理服务器上用来代理集群应用WebApp的。具体步骤如下：
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    1．创建集群域clusterdomainnew，管理服务器myserver（7001:7003）；
  </p>
  
  <p>
    2．创建Machine：admin（myserver,ProxyServer），cluster(serverA,serverB)；
  </p>
  
  <p>
    3．创建受管服务器serverA(8001)，serverB(8003)；
  </p>
  
  <p>
    4．创建集群mycluster；
  </p>
  
  <p>
    Choose Servers for this Cluster: serverA，serverB
  </p>
  
  <p>
    config.xml:
  </p>
  
  <p>
    <Cluster ClusterAddress=&#8221;172.30.94.60:8001,172.30.94.60:8003&#8243;
  </p>
  
  <p>
    MulticastAddress=&#8221;237.0.0.1&#8243; MulticastPort=&#8221;7777&#8243; Name=&#8221;mycluster&#8221;/>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    5．部署WebApp应用，targets mucluster；
  </p>
  
  <p>
    6．创建代理服务器ProxyServer（80），将DefaultWebApp  targets ProxyServer；
  </p>
  
  <p>
    7．编辑DefaultWebApp应用，注册HttpClusterServlet：
  </p>
  
  <p>
    <servlet>
  </p>
  
  <p>
    <servlet-name>HttpClusterServlet</servlet-name>
  </p>
  
  <p>
    <servlet-class>weblogic.servlet.proxy.HttpClusterServlet</servlet-class>
  </p>
  
  <p>
    <init-param>
  </p>
  
  <p>
    <param-name>WebLogicCluster</param-name>
  </p>
  
  <p>
    <param-value>172.30.94.60:8001:8002|172.30.94.60:8003:8004</param-value>
  </p>
  
  <p>
    </init-param>
  </p>
  
  <p>
    <init-param>
  </p>
  
  <p>
    <param-name>DebugConfigInfo</param-name>
  </p>
  
  <p>
    <param-value>ON</param-value>
  </p>
  
  <p>
    </init-param>
  </p>
  
  <p>
    </servlet>
  </p>
  
  <p>
    <servlet-mapping>
  </p>
  
  <p>
    <servlet-name>HttpClusterServlet</servlet-name>
  </p>
  
  <p>
    <url-pattern>/</url-pattern></servlet-mapping>
  </p>
  
  <p>
    <servlet-mapping>
  </p>
  
  <p>
    <servlet-name>HttpClusterServlet</servlet-name>
  </p>
  
  <p>
    <url-pattern>*.jsp</url-pattern> </servlet-mapping>
  </p>
  
  <p>
    <servlet-mapping>
  </p>
  
  <p>
    <servlet-name>HttpClusterServlet</servlet-name>
  </p>
  
  <p>
    <url-pattern>*.htm</url-pattern> </servlet-mapping>
  </p>
  
  <p>
    <servlet-mapping>
  </p>
  
  <p>
    <servlet-name>HttpClusterServlet</servlet-name>
  </p>
  
  <p>
    <url-pattern>*.html</url-pattern>
  </p>
  
  <p>
    </servlet-mapping>
  </p>
  
  <p>
    8．重启myserver；
  </p>
  
  <p>
    9．启动serverA：startManagedWeblogic  serverA  http://172.30.94.60:7001;
  </p>
  
  <p>
    启动成功后，访问http://172.30.94.60:8001/WebApp/ 验证一下！
  </p>
  
  <p>
    10.启动serverB：startManagedWeblogic  serverB  http://172.30.94.60:7001;
  </p>
  
  <p>
    启动成功后，访问http://172.30.94.60:8003/WebApp/ 验证一下！
  </p>
  
  <p>
    11. 启动ProxyServer：startManagedWeblogic ProxyServer  http://172.30.94.60:7001。
  </p>
  
  <p>
    访问http://172.30.94.60/WebApp，是不是大功告成了：）
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    原文地址：
  </p>
  
  <p>
    <a href="http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=3257&tstart=25&quint=true">http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=3257&tstart=25&quint=true</a>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <h3>
    4.2      WebLogic应用在集群环境下的一些基本知识
  </h3>
  
  <h4>
    4.2.1  基本概念
  </h4>
  
  <p>
    1．硬件的cluster和WebLogic的cluster不是一回事，硬件做的是冷备份，对用户的session，用户请求的负载均衡等的处理是做不到 的，而且一般硬件的双机热备也不是时时的备份，而是间隔一段时间再将主机上的数据copy过来，而WebLogic Server的cluster就不是这样，其session的数据是时时的复制的，对不经常更改的jndi等的复制虽然也是定期完成的，但update的 时间间隔很短
  </p>
  
  <p>
    2．WebLogic Server的cluster配置非常方便，请参考dev2dev学堂
  </p>
  
  <p>
    <a href="http://dev2dev.bea.com.cn/bbs/school/guide/webser/20030627.html" target="_blank">http://dev2dev.bea.com.cn/bbs/school/guide/webser/20030627.html</a>
  </p>
  
  <p>
    如果你要对集群做扩展，操作也非常方便，你只需要启动一个指向这个集群的Admin Server的managed server就可以了，由这个集群中的唯一的Admin Server往这个managed server上部署应用<br /> 3．http状态会话复制就是session的复制，例如你登陆了系统，如果一个服务器坏了，cluster会将你的请求转发集群中的另外一个server，由其继续处理你的这个请求，而不要重新登陆。<br /> 4．EJB集群中有状态，无状态EJB的意义和区别请看J2EE中EJB的相关知识<br /> 5．对EJB的集群，也是非常简单的，直接把EJB应用target到cluster的server上！<br /> 6．对WebLogic Server来说，它的cluster做session的in memory的时时复制，这适用于web application及stateful session BEA的session内容的复制<br /> 7．对非stateful的EJB，WebLogic Server的cluster做其负载均衡及failover的工作（failover只针对EJB的stateless BEAN
  </p>
  
  <h4>
    4.2.2  集群规划
  </h4>
  
  <p>
    在规划集群配置时，应该牢记以下关于网络环境与集群配置的限制。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    1． 首先，集群中的WebLogic主机必须使用永久的静态IP地址。动态IP地址分配不能用于集群环境。如果服务器位于防火墙后面，而客户机位于防火墙外面，那么服务器必须有公共的静态IP地址，只有这样，客户端才能访问服务器。<br /> 2．集群中的所有WebLogic服务器必须位于同一个局域网，并且必须是IP广播可到达的。<br /> 3．集群中的所有WebLogic服务器必须使用相同的版本。配置集群中的服务器，使它们支持所提供的服务。对于使用了JDBC连接的EJB，所有部署了某EJB的服务器必须具有相同的部署与持久化配置。也就是说所有服务器都应该有相同的JDBC配置。所有部署了servlet的主机必须维护一组具有相同ACL的servlet。
  </p>
  
  <p>
    如果客户端应用直接使用JDBC连接池，那么你必须为每个WebLogic服务器创建相同的连接池（并具有相同的ACL）。这意味着集群所使用的连接池应该 可以在所有的机器上创建。例如，一台运行WebLogic的NT服务器配置了连接Microsoft SQL Server数据库的连接池，那么一个包含非Windows机器（即不支持Microsoft SQL Server连接的机器）的集群不能使用这个连接池。
  </p>
  
  <p>
    其它配置细节可能会因不同的集群成员而不同。例如，一台Solaris服务器可以比一台小的 NT工作站处理更多的登录请求。这种差异是可以接受的。因此，正如这里所给出的例子，对于那些与性能相关的属性，你可以根据每个集群成员的特点来配置不同 的值，只要所有成员的服务配置相同即可。因此，集群中的WebLogic服务器在所有与WebLogic服务、类文件以及外部资源（例如数据库）相关的方 面具有相同的配置。
  </p>
  
  <p>
    <strong> </strong>
  </p>
  
  <h4>
    4.2.3  服务器配置任务列表
  </h4>
  
  <p>
    可以通过管理控制台进行以下服务器配置：
  </p>
  
  <p>
    l  Server节点配置单独的服务器可以配置的属性包括名字：监听端口与IP地址。
  </p>
  
  <p>
    l  Server节点克隆一个服务器：克隆的服务器保存了原来服务器的属性值，你可以使用Server节点中的Configuration配置新服务器的名字。
  </p>
  
  <p>
    l  使用管理控制台的Server节点来删除一个服务器：点击要删除的服务器的图标，将弹出一个删除服务器的确认对话框，点击对话框中的Yes按钮将删除服务器。
  </p>
  
  <p>
    l  使用管理控制台的Server节点查看一个服务器的日志：点击要查看的服务器，点击Monitoring标签页，点击View Server Log连结，便可以在管理控制台的右窗格查看服务器日志。
  </p>
  
  <p>
    l  使用管理控制台的Server节点查看一个服务器的JNDI树：点击所要查看的服务器，然后点击Monitoring标签页，点击该页面上View JNDI Tree连接，该服务器JNDI树的信息便显示在管理控制台的右窗格中。
  </p>
  
  <p>
    l  使用管理控制台的Server节点查看服务器的执行队列：点击所要查看的服务器，然后点击Execute Queue 链接，然后查看管理控制台右边窗格里的表格中的内容。
  </p>
  
  <p>
    l  使用管理控制台的Server节点查看服务器的执行线程：点击所要查看的服务器，然后点击Execute Queue 链接，然后查看管理控制台右边窗格里的表格中的内容：
  </p>
  
  <p>
    l  使用管理控制台的Server节点查看server sockets：点击所要查看的服务器,点击View Sockets连接，然后查看管理控制台右边窗格里的表格中的内容。
  </p>
  
  <p>
    l  使用管理控制台的Server节点查看服务器连接：点击所要查看的服务器，点击View Connections连接，然后查看管理控制台右边窗格里的表格中的内容。
  </p>
  
  <p>
    l  使用管理控制台的Server节点进行强制垃圾收集，点击要监控的服务器，点击JVM标签页，点击页面上的Force Garbage Collection连接，将弹出是否要进行垃圾收集的确认对话框。
  </p>
  
  <p>
    l  Server节点监视服务器的安全：点击要监控的服务器，点击Monitoring标签页，点击Security标签页，将显示安全信息。
  </p>
  
  <p>
    l  Server节点查看服务器的版本：点击要查看的服务器，点击Version标签页，将显示服务器的版本信息。
  </p>
  
  <p>
    l  Server节点监控服务器集群：点击要监控的服务器，点击Cluster标签页，将显示该服务器的集群数据。
  </p>
  
  <p>
    l  Server节点来部署EJB：点击需要部署EJB的服务器，点击需要分发的EJB并使用移动控件将它移到被选列中，点击Apply来保存你的选择。
  </p>
  
  <p>
    l  Server节点来监视部署在某一服务器上的所有EJB：点击需要监视的服务器，点击Monitor All EJB Deployments连接来显示EJB的部署列表。
  </p>
  
  <p>
    l  Server节点将web应用组件部署在某一服务器上：选择要部署web应用的服务器：选择需要部署的web应用，然后通过移动控件将它移到被选列中，点击Apply来保存你的选择。
  </p>
  
  <p>
    l  Server节点来监控某一服务器上的所有web应用组件：点击web应用所在的服务器，然后点击Monitor All Web Applications连接来显示Web Application 的部署列表。
  </p>
  
  <p>
    l  Server节点在服务器上部署启动与终止类：点击需要部署启动类的服务器，然后点击需要部署的启动类并将它移到被选列中，点击Apply来保存你的选择，使用终止类控件来部署终止类的过程与此相同。
  </p>
  
  <p>
    l  Server节点为服务器分配JDBC连接池：点击web server分配表中的一个服务器，在Available列中点击一到多个JDBC连接池，并通过移动控件将所选择的JDBC连接池移到Chosen列，点击Apply来保存你所做的分配。
  </p>
  
  <p>
    l  Server节点为一个服务器分配WLEC连接池：点击需要分配WLEC连接池的服务器：在Available列中选择一个或多个要分配的WLEC连接池，使用移动控件将所选择的WLEC连接池移动到Chosen列。
  </p>
  
  <p>
    l  通 过管理控制台的Server节点监视某一服务器上的所有WLEC连接池：选择一个需要监视连接池的服务器，点Monitor All WLEC Connection Pools on This Server链接，所有分配给这台服务器的连接池会显示在右窗格中的WLEC Connection Pools列表中。
  </p>
  
  <p>
    l  Server节点为一台服务器分配XML 注册表，选择要分配XML 注册表的服务器，从XML 注册表的下拉列表中选择一个注册表，点Apply保存设置。
  </p>
  
  <p>
    l  Server节点分配邮件会话：选择一个要分配邮件会话的服务器，从Available列中选择要分配给服务器的邮件会话，使用移动控件把所选择的移动会话移动到Chosen列中，点Apply按钮保存设置。
  </p>
  
  <p>
    l  通过管理控制台为服务器分配文件T3s：选择一个要分配文件T3的服务器，从Available列中选择要分配给服务器的文件T3s，使用移动控件把所选择的文件T3s移动到Chosen列，点Apply按钮保存设置。
  </p>
  
  <p>
    l  Connection连接，然后查看管理控制台右边窗格里的表格中的内容。
  </p>
  
  <p>
    l  使用管理控制台的Server节点进行强制垃圾收集：点击要监控的服务器，点击JVM标签页，点击页面上的Force Garbage Collection连接，将弹出是否要进行垃圾收集的确认对话框。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    原文地址：
  </p>
  
  <p>
    <a href="http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=4800&tstart=0&quint=true">http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=4800&tstart=0&quint=true</a>
  </p>
  
  <p>
    &nbsp;
  </p>
</div>

** <br clear="all" />**

<div>
  <h2>
    5      安全管理
  </h2>
  
  <h3>
    5.1      WebLogic AD ldap 配置方法
  </h3>
  
  <p>
    Weblogic AD ldap 配置方法
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    一 创建并配置windows端AD.
  </p>
  
  <p>
    1 在AD中加入新的OU,myOrg.
  </p>
  
  <p>
    2 在myOrg中加入两个ou ,groups 和people。在groups中加入两个组group1,group2,在people中加入两个用户user1,user2.
  </p>
  
  <p>
    3配置user1用户属于组group1，user2用户属于组group2。
  </p>
  
  <p>
    windows Active Directory 端配置完毕。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    二 得到配置参数
  </p>
  
  <p>
    1 下载ldap brSofterra LDAP Browser 2.5 (可用google搜索)
  </p>
  
  <p>
    2 配置ldap browser。
  </p>
  
  <p>
    打开ldap browser应用程序。创建新的profile。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    填入参数：
  </p>
  
  <p>
    单击fetch DNs (only ldap v.3) 得到自动配置的ldap 基础配置
  </p>
  
  <p>
    在DC=www 前面加入AD中配置的OU=myOrg。
  </p>
  
  <p>
    完成后如下图。表示连接AD 成功
  </p>
  
  <p>
    得到base DN 参数为 OU=myOrg,DC=www,DC=test,DC=com, (DC=www,DC=test,DC=com视您的windows域而定，本例域为<a href="http://www.test.com/">www.test.com</a>)。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    三 配置weblogic server
  </p>
  
  <p>
    启动域，打开控制器http://localhost:7001/console。
  </p>
  
  <p>
    配置新的authentication。
  </p>
  
  <p>
    点击authentication 。在右边选择configure a new active directory authenticator
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    1 General 中的配置
  </p>
  
  <p>
    2 Active Directory栏配置
  </p>
  
  <p>
    3 user栏配置
  </p>
  
  <p>
    user栏只需要修改User Base DN 为自己的user base DN,这里填入ldap browser 中得到的数据OU=myOrg,DC=www,DC=test,DC=com,不过我们要得到的是用户所以在前面在加入我们创建的OU=people。
  </p>
  
  <p>
    4 group 栏配置。
  </p>
  
  <p>
    group 栏只需要修改group Base DN 为自己的group base DN,这里填入ldap browser 中得到的数据OU=myOrg,DC=www,DC=test,DC=com,不过我们要得到的是组所以在前面在加入我们创建的OU=groups。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    保存后其余的都不用在修改了。
  </p>
  
  <p>
    我们再次点击user时，ldap中的用户和组就加入到weblogic server 的用户中了
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    原文地址：
  </p>
  
  <p>
    <a href="http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=8194&tstart=25&quint=true">http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=8194&tstart=25&quint=true</a>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <h3>
    5.2      口令的保护
  </h3>
  
  <p>
    保护用来访问WebLogic服务器资源的口令是很重要的。在过去，用户名与口令以明文的形式存储在WebLogic服务器的安全域中。现在 WebLogic服务器对所有口令进行散列化。当WebLogic服务器获得一个客户端请求时，客户端所输入的口令也被散列化，然后把散列化结果与所保存的散列化口令进行比较，看它们是否相互匹配。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    每个filerealm.properties文件都有一个与它关联的SerializedSystemIni.dat文件，这个文件被用来散列化口令。在安装时，SerializedSystemIni.dat文件保存在\wlserver6.1\config\mydomain目录下，如果该文件被破坏，那么就需要重新配置WebLogic服务器。
  </p>
  
  <p>
    我们建议你采用以下预防措施：
  </p>
  
  <p>
    备份SerializedSystemIni.dat文件，并将其与filerealm.properties文件的备份存放于同一目录下。设置SerializedSystemIni.dat文件的访问权限，例如只允许WebLogic服务器的管理员有读写这个文件的权限，其它用户没有这个文件的任何权限。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    如果你使用的是weblogic.properties文件，并且想散列化这个文件中的口令，你可以用管理控制台主窗口的Convert weblogic.properties选项将weblogic.properties文件转换为config.xml文件。一旦文件被转换，则所有现存的口令就已经被保护了。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    Config.xml文件中的不在含有明文的口令，若在其中保存明文的口令，config.xml会对其进行加密并被散列化该口令。被加密的口令不能从一个域复制到另一个域，而是应该使用明文口令替换config.xml中被加密的散列化口令，然后再将文件复制到另外一个域中。管理控制台在下一次写文件时会加密并散列化口令。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    要保护WebLogic服务器的口令，执行以下操作：
  </p>
  
  <p>
    1. 打开管理控制台
  </p>
  
  <p>
    2. 点击Security节点
  </p>
  
  <p>
    3. 在管理控制台右侧窗格中选择Passwords标签页。
  </p>
  
  <p>
    4. 定义该标签页中需要配置的属性，按照相应的提示输入值，并选中必须选择的复选框（详细信息，参见下表）。
  </p>
  
  <p>
    5. 点Apply按钮保存所做的设置
  </p>
  
  <p>
    6. 重启WebLogic服务器。
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    如下详细描述了Security Configuration窗口的Password标签页上的各个属性。
  </p>
  
  <p>
    l  Minimum Password Length: 口令所需的长度，至少为8个字符。缺省为8个字符
  </p>
  
  <p>
    l  Lockout Enabled: 在超过Lockout Threshold次尝试后，是否需要锁住某个登录无效的帐号。缺省情况下，该属性被启用。
  </p>
  
  <p>
    l  Lockout Threshold： 当一个用户试图登录到一个用户帐户，因口令不对而失败，那么多少次这样的失败登录后将锁住这个帐号。以后对该帐号的访问（即使是username/password是正确）也将引发Security异常；在管理员对该帐号进行解锁前，或在锁住期限内，该帐号一直处于锁住的状态。注意非法登录必须在Lockout Reset Duration属性所定义范围内。默认为5
  </p>
  
  <p>
    l  Lockout Duration：该属性定义了当某一帐户因为在Lockout Reset Duration期限内发生非法登录而被锁住后，多长时间范围内该用户帐号不能被使用。要解开一个被锁住的用户帐号，你必须拥有 weblogic.passwordpolicy中的unlockuser权限。默认为30分钟。
  </p>
  
  <p>
    l  Lockout Reset Duration：该属性定义了在多长时间里，非法登录某一帐号将导致该帐号被锁住。在本属性定义的时间范围内，当非法登录的次数超过了Lockout Threshold属性所定义的值，那么该帐号将被锁住，例如，该属性被设置为5分钟，当帐号在6分钟内被非法登录了3次，那么该帐号不会被锁住，但是，如果在5分钟内，发生了5次非法登录，那么该帐号将被锁住。缺省为5分钟。
  </p>
  
  <p>
    l  Lockout Cache Size：指定无效的或非法的登录意图的缓存大小。缺省为5
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    注：本文针对weblogic6，其他版本请参考
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p>
    原文地址
  </p>
  
  <p>
    <a href="http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=930&tstart=50&quint=true">http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=930&tstart=50&quint=true</a>
  </p>
  
  <p>
    &nbsp;
  </p>
</div>

** <br clear="all" />**

## 6      其它资源

本文前面部分删除了许多重复的文章，也没有包括一些比较复杂的文章，大家可以到Dev2dev WebLogic管理板块

<http://dev2dev.bea.com.cn/bbs/forum.jspa?forumID=81&start=0>

和本版精华

<http://dev2dev.bea.com.cn/bbs/forum!quint.jspa?forumID=81>

下查看。

本文随同本论坛其它板块的资料，也保留在社会书签<http://del.icio.us/dev2dev.cn>处，大家可以也尝试使用这种书签，来共同维护我们的资源，人多力量大。以下我说说其他有用资料。

### 6.1      dev2dev 学堂

这里的资料十分的丰富。

l  实战集锦非常实用，里面主要包括了一些WebLogic出现的问题以及解决方案，其中你不仅可以学到WebLogic的许多知识，也可以知道许多Java与操作系统的基础知识，也可以发现许多排错和调优的好工具以及使用方法。

l  WebLogic Server里面包括了大量的基础教程，既有图文并茂的教程，也有许多动画教程。你可以学到WebLogic的在Windows和Linux/UNIX下的安装，可以学到如何配置SSL和集群，如何发布简单应用程序，如何使用JMS，如何调用你的第一个JSP文件。

l  WebLogic常见问题包括经常遇到了简单问题以及快捷的回答。

&nbsp;

dev2dev 学堂：<http://dev2dev.bea.com.cn/bbs/school/index.jsp>

实战指南：<http://www.bea.com.cn/support_pattern/index.htm>

WebLogic Server学堂：<http://dev2dev.bea.com.cn/bbs/school/guide/webser/index1.jsp>

常见问题：[http://www.bea.com.cn/services/custsupp/techresor/faq/faq\_weblogic\_list.jsp](http://www.bea.com.cn/services/custsupp/techresor/faq/faq_weblogic_list.jsp)

### 6.2      WebLogic代码库和CodeShare

代码库是以前WebLogic为大家提供的一些代码实例，CodeShare是最近发起的一个项目，代码库的许多代码会转移到CodeShare下，但是现在还没有完全做到，许多代码还只能在代码库里找到。如果想学习某些比较复杂的技术，看实例代码是最好的方式，而且这些代码通常会附有非常详细的文档来帮助使用。

&nbsp;

代码库：<http://dev2dev.bea.com.cn/code/codelib/index.jsp>

代码库Weblogic部分：<http://dev2dev.bea.com/code/wls.jsp>

CodeShare：<http://dev2dev.bea.com.cn/code/CodeShare/index.jsp>

&nbsp;

### 6.3      在线论坛Dev2dev

有一些文章没有收录到这里，主要是因为篇幅太长，或者内容与网站的其他地方有些重复，可是还是很精彩的文章。

l  BLOGIC 8.1下集群配置实例
  
<http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=19302>

l  一个Domain里的机器可以是不同的平台吗？
  
<http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=1692>

l  Weblogic的access.log详细说明
  
<http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=8669>

l  OutOfMemoryError错误的调节，JVM的一个参数
  
<http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=9779>

l  在FreeBSD下安装Linux版本的WebLogic
  
<http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=9554>

l  axman与zghr对JDBC Connection的讨论
  
<http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=121&threadID=9121>

l  WebLogic Server管理指南
  
<http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=81&threadID=8387>

&nbsp;

### 6.4      学习WebLogic起步过程

经常有人问WebLogic如何起步，这里列下大体的过程，具体可以参考dev2dev学堂和论坛精华。

l  下载
  
到<http://dev2dev.bea.com.cn/download/index.jsp>下载相应的版本

l  安装
  
只以windows为例，直接运行下载的安装程序就然后根据步骤一路默认就好。

l  配置最基本的domain
  
WebLogic安装好后应该在运行“开始-所有程序-Bea WebLogic Platform-Configuration  Wizard”或者是&#8221;C:\bea\weblogic81\common\bin\config.cmd&#8221;，就可以配置一个Domain，也就是一组服务器单元。

l  使用console
  
配置好了一个domain，就可以启动Admin Server，可以使用“开始 &#8211; 所有程序 &#8211; Bea WebLogic Platform &#8211; Configuration  Wizard &#8211; User Projects – mydomain – Start Server”, 或者是到了mydomain目录调用startWebLogic.cmd,就可以启动Server，然后在浏览器中进入<http://localhot:7001/conole>就进入了管理界面，通常的管理都在这里进行。

l  发布应用
  
可以到console的Deployment部分发布

&nbsp;

&nbsp;

&nbsp;

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [BEA dev2dev WebLogic管理精华[转]](http://www.beansoft.biz/2012/03/15/bea-dev2dev-weblogic%e7%ae%a1%e7%90%86%e7%b2%be%e5%8d%8e/)