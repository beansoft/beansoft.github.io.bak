---
id: 716
title: 'Portable JSPWiki 1.1 简体中文版下载[整理]'
date: 2010-09-09T19:49:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=716
permalink: '/2010/09/09/portable-jspwiki-1-1-%e7%ae%80%e4%bd%93%e4%b8%ad%e6%96%87%e7%89%88%e4%b8%8b%e8%bd%bd/'
views:
  - "4708"
original_post_id:
  - "716"
image: /wp-content/uploads/2012/09/o_pjspwiki_1.1_zh_cn.png
categories:
  - JSPWiki
---
**Portable** **JSPWiki** 1.1 简体中文版   
BeanSoft(beansoft@126.com)   
2007-02-02   
有 很多朋友询问 **JSPWiki** 的配置问题, 很多人无法运行. 这里给一份解压缩就能跑的**JSPWiki** (支持中文页面,附件和中文界面), 已经内置了 Apache Tomcat 5.5.20, 预装好了默认的页面编辑器以及 WikiWizard 中文版编辑器(此编辑器为 Applet, 需要安装 JRE 1.4 或者 1.5).   
用法:   
1. 首先请**下载** [http://cid-519b3f7aa2172030.office.live.com/self.aspx/Public/beansoft^\_java-cn^\_org/^_PortableJSPWiki1.1.7z](http://cid-519b3f7aa2172030.office.live.com/self.aspx/Public/beansoft^_java-cn^_org/^_PortableJSPWiki1.1.7z "http://cid-519b3f7aa2172030.office.live.com/self.aspx/Public/beansoft^_java-cn^_org/^_PortableJSPWiki1.1.7z")(9MB);   
&#160;&#160; 如果解不开 .7Z 格式的压缩包, 请**下载**一份最新版的 WinRAR: http://www.winrar.com.cn/index2.htm 或者 7Z 文件管理器 http://www.7-zip.org/zh-cn/.   
2. 新建一个目录 PortableJSPWiki(别的目录名也可, 但是路径不要带空格), 然后解压缩 _PortableJSPWiki1.1.7z 到该目录下;   
3. 如果已经设置好了 JAVA\_HOME 系统变量的路径到 JDK 1.5.0 的安装目录, 请直接执行第5步, 启动脚本已经更新, 会自动使用已有的 JAVA\_HOME;   
4. 您可以手工设置 JAVA_HOME 系统变量的路径到 JDK 1.5.0 的安装目录; 或者将 JDK 1.5 目录下的内容复制到目录 "jdk1.5.0" 下面;   
5. 双击 StartPortableApps.exe ,可以看到任务栏托盘出多处了一个图标, 点击此图标, 将弹出一个类似开始菜单的窗口, 它是&#160; **Portable** App Menu 窗口, 然后点击第一个菜单项: Apache Tomcat 5.5.20 启动 Tomcat;   
6. 点击 **Portable** App Menu 窗口上的 "localhost 8080 **jspwiki**" 菜单项目, 将会在浏览器中打开 Wiki 的首页面并有中文内容出现, 网址应该是 http://localhost:8080/**JSPWiki**/ ;   
7. 登录可以输入 admin/admin (用户名密码都是admin), 这是系统唯一的管理员权限账户;   
8. 退出可以关闭所有新打开的窗口即可, 包括托盘的图标;   
9. 卸载删除所有页面即可.   
这个版本都包含了什么?   
1. 修改了 Tomcat 的 Connector 参数可以支持中文附件和页面名称; 参考 http://beansoft.java-cn.org/Wiki.jsp?page=JSPWikiI18N, 您可以看到本页面和附件都是中文的.   
2. 修改页面存储路径为 ../../jspwiki_pages, 这样 **JSPWiki** 的页面存放在和 Tomcat 平级的目录中;   
3. 增加了3种内联图片格式:   
**jspwiki**.translatorReader.inlinePattern.1 = *.jpg   
**jspwiki**.translatorReader.inlinePattern.2 = *.png   
**jspwiki**.translatorReader.inlinePattern.3 = *.gif   
4. 基于最新版本 2.4.91 构建;   
5. 使用了本站开发的 http://beansoft.java-cn.org/Wiki.jsp?page=VistaTemplate 简体中文作为默认模版;   
6. 内置了管理员账户 admin/admin, 可以登录后修改密码;   
7. 采用 **Portable** Java IDE 的框架来启动此 Tomcat;   
8. 修正了 WikiWizard 编辑器显示中文为方框的问题, WikiWizard 使用的是中文版(汉化者也是本人); 参考 http://beansoft.java-cn.org/Wiki.jsp?page=JSPWikiFAQ.   
9. 修正了搜索框搜索中文为乱码的问题;   
10. 2007-03-14 修改了 log4j 日志文件使用绝对路径导致启动时报错的问题;   
您可以键入 http://localhost:8080/**JSPWiki**/Install.jsp 重新设置安装参数.   
别的都是原样提供, 完了.   
最后, 不可避免的有些 Bug, 请各位反馈建议.   
目录结构说明:   
[PortableApps] 启动菜单   
StartPortableApps.exe&#160; 菜单启动中心   
[apache-tomcat-5.5.20]&#160;&#160;&#160; Tomcat 5.5.20 预装了 **JSPWiki**   
[jdk1.5.0] JDK 1.5 的目录(默认为空)   
[Documents] 一些文件目录, 默认为空   
[jspwiki_pages]&#160; **JSPWiki** 的页面内容存放在这个目录下   
readme.txt&#160; 说明文件   
更多信息请访问 http://beansoft.java-cn.org/ 以及 Java Blog http://www.blogjava.net/beansoft/.   
![http://www.blogjava.net/images/blogjava_net/beansoft/17524/o_pjspwiki_1.1_zh_cn.png](http://www.blogjava.net/images/blogjava_net/beansoft/17524/o_pjspwiki_1.1_zh_cn.png)

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Portable JSPWiki 1.1 简体中文版下载[整理]](http://www.beansoft.biz/2010/09/09/portable-jspwiki-1-1-%e7%ae%80%e4%bd%93%e4%b8%ad%e6%96%87%e7%89%88%e4%b8%8b%e8%bd%bd/)