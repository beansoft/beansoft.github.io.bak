---
id: 1197
title: '用开源软件搭建企业内部协作平台, Kill QQ MSN[原创]'
date: 2007-02-03T13:44:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1197
permalink: '/2007/02/03/%e7%94%a8%e5%bc%80%e6%ba%90%e8%bd%af%e4%bb%b6%e6%90%ad%e5%bb%ba%e4%bc%81%e4%b8%9a%e5%86%85%e9%83%a8%e5%8d%8f%e4%bd%9c%e5%b9%b3%e5%8f%b0-kill-qq-msn%e5%8e%9f%e5%88%9b/'
views:
  - "5221"
original_post_id:
  - "1197"
categories:
  - IM
---
2007-02-03 <BeanSoft@126.com> 原创作品, 转载请注明出处

下载本文完整图文版(右键另存为): <a href="http://www.beansoft.biz/wp-content/uploads/2011/02/killqqmsn.swf" target="_blank">http://www.beansoft.biz/wp-content/uploads/2011/02/killqqmsn.swf</a> 238KB

提示: 点击最右上角的 **回** 按钮全屏阅读

<http://www.beansoft.biz/wp-content/uploads/2011/02/killqqmsn.swf>

作为公司的一分子, 您可能忧心忡忡于通过 MSN, QQ 流入的各种名目繁多的病毒, 木马, 例如熊猫烧香, 以及通过 MSN 传播的导致公司网络瘫痪的蠕虫病毒. 换句话说, 我们需要企业内部协作平台, 来保证信息安全和减少依赖外网办公所带来的高风险. 例如: 地震了, 外网断了, 同事们再也不能通过MSN/QQ交流了. 自然, QQ/MSN 有它的用途, 但是主要用途就是和私人的朋友交流, 很多同事也不希望有关自己隐私的QQ/MSN被公司知道. 在这种种的需求之下, 搭建企业内部 collaboration platform 很有必要性. 本文就介绍如何通过整合几种基于 Java 的开源软件来搭建企业内部协作平台, 包括知识库, 内部 IM 和能够方便的交流的在线 Web IM.

首先就是文档库和知识库, 这个基本上通过安装 Wiki, 例如 JSPWiki, 通过它, 同事们可以方便的共同的编辑同一个需求页面, 设计文档, 也可以将已经写好的文档上传, 加上简短的说明, 这些说明都可以通过全文索引被搜索到. JSPWiki 的中文版本搭建可以阅读这里: [Tomcat 下最简单的不改源码让 JSPWiki 支持中文文件/附件的方法](http://www.blogjava.net/beansoft/archive/2007/02/03/97756.html).

其次就是企业内部的 IM, 有人推荐 Tencent RTX, 但是请看: 第一: 其服务端是搭建于 Windows 的 Server, 而我希望在类 Linux 平台使用它; 第二: 商业软件, 需要掏钱; 第三: 客户端和 QQ 一样, 有诸多安全隐患, 而且还可以直接连接 QQ 好友, 不利于彻底封杀 QQ; 第四: 传输协议是不公开的, 如果我想日后升级到其它厂商的服务器, 很明显这是痴人说梦. 在此我的目光集中到了 Jabber 协议的服务器上, 而且重点考察基于 Java 构建的. 最后, 我看到了 Jive Software 的开源版本的服务器和客户端(Jabber 协议的), : WildFire 和 Spark, 他们的网站是 <http://www.igniterealtime.org/>. 从他们的首页可以看到他们的下一个版本即将推出语音聊天/会议支持. 然后我还找到了 [JWChat](http://jwchat.sourceforge.net), 它可以解决我们的 Web IM 问题. 虽然眼前来讲 Spark 和 JWChat 都没有中文版本的界面, 但是可以看到他们已经留下了资源文件, 等着汉化. 如果真的要使用, 这些都不是大问题, 汉化很容易解决.

这套系统很好用, 历史也很悠久了, 服务器有管理界面, 支持文件传送, 离线消息, 屏幕截图, 联系人查找, 个性头像, 用户自己注册, 改密码, 创建聊天室(ChatRoom)等等. 而且按照他们网站的许可协议是可以商用的. 也有 Windows, Linux, Mac 的版本, 基于 Java 构建.

Spark 这个客户端的安装很简单, 下载相应版本的(如果不熟悉 Java, 直接下载带 JRE 的即可), 一路 next 下去, 就 OK了. 然后启动它. 注意下面的 IP 是我们部署在局域网的 WildFire Jabber 服务器的地址.

注册:   
在登录界面点击&#8221;Account&#8221;按钮进行注册. 

截图:

服务器端叫 WildFire, 管理界面是基于 Web 的, 有简体中文的语言界面支持. 它的安装也很简单, 下载完全版本, 一路 next 下去, 需要注意的是: 启动后必须先设置一下方可开始使用. 点击WildFire 主窗口的 Launch Admin 按钮, 然后进入管理控制台, 语言选择 Simplified Chinese (zh_CN), 不要忘了给 admin 设置一个密码, 数据库选择默认的 HSQL Database Engine 1.8.0, 这样就完工了. 服务器的功能非常的强大, 包括禁止注册, 管理用户等等.

<img src="http://www.beansoft.biz/wp-content/uploads/2012/04/zrclip_001p3abd1757.png" height="616" width="617" />

客户端下载:   
<http://www.igniterealtime.org/downloads/index.jsp#spark>

服务器端下载:   
<http://www.igniterealtime.org/downloads/index.jsp#wildfire>

最后我们可以在刚才的 JSPWiki 服务器上搭建一个 Web 版本的 Jabber 客户端, 支持 IE 和 Firefox 浏览器, 这样如果有人不方便通过客户端来交流的话, 也没有问题, 只不过一些功能, 例如文件传输, 就不可用了. JWChat 下载 war 版本, 然后重命名为 chat.war, 放到 Tomcat 的应用目录下, 然后修改配置文件 config.js 即可工作, 只要修改下面几行即可:

var SITENAME = &#8220;192.168.83.107&#8221;;// 把这个改成 Jabber 服务器的地址

var DEFAULTCONFERENCEROOM = &#8220;talks&#8221;;// 默认的聊天室名字   
var DEFAULTCONFERENCESERVER = &#8220;conference.192.168.83.107&#8221;;// 默认的聊天室服务器地址

然后键入 <http://localhost:8080/chat>, 即可开始聊天了!

最后, 在 JSPWiki 的左菜单(Edit.jsp?page=LeftMenu)上加入这个连接, 例如: <http://jabber.mybiz.com:8080/chat/> , 然后同事们就可以边修改文档边在线进行交流了.

看看最后的效果:

<img src="http://www.beansoft.biz/wp-content/uploads/2012/04/zrclip_002p7902ad92.png" height="654" width="400" />

准备好了嘛? 立即 Kill QQ MSN , 从此让同事们的沟通更安全, 更便捷.

BeanSoft 2007-02-03

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [用开源软件搭建企业内部协作平台, Kill QQ MSN[原创]](http://www.beansoft.biz/2007/02/03/%e7%94%a8%e5%bc%80%e6%ba%90%e8%bd%af%e4%bb%b6%e6%90%ad%e5%bb%ba%e4%bc%81%e4%b8%9a%e5%86%85%e9%83%a8%e5%8d%8f%e4%bd%9c%e5%b9%b3%e5%8f%b0-kill-qq-msn%e5%8e%9f%e5%88%9b/)