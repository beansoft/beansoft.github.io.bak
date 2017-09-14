---
id: 722
title: 'MyEclipse 6 Java 开发中文教程独家连载 &#8211; 介绍'
date: 2010-09-09T20:04:37+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=722
permalink: '/2010/09/09/myeclipse-6-java-%e5%bc%80%e5%8f%91%e4%b8%ad%e6%96%87%e6%95%99%e7%a8%8b%e7%8b%ac%e5%ae%b6%e8%bf%9e%e8%bd%bd-%e4%bb%8b%e7%bb%8d/'
views:
  - "4627"
original_post_id:
  - "722"
image: /wp-content/uploads/2012/09/clip_image002_thumb4.jpg
categories:
  - MyEclipse6中文教程
---
### **<font color="#ff0000">如果您需要转载本书内容, 请与本站联系! Email: </font>**[**<font color="#ff0000">wlsmon@qq.com</font>**](mailto:wlsmon@qq.com)**<font color="#ff0000">.</font>**

### <a name="_Toc201479530">介 </a>绍

Eclipse，日蚀也，日月无光是也！MyEclipse，吾之日月无光乎！此皆望文生义也。

吾幼时，乃有幸拜读李时珍先生之《本草纲目》，佩乎图文并盛，折服于李先生谦恭细致之态度也。东壁先生之作，必先亲恭乃告知于读者，己所不能验者，也必附其出处。不才乃想效仿李先生，草拟此图文书，以悼先生焉。

本书是讲解MyEclipse 6开发Java EE企业应用的入门图书。该书不但讲解了目前最流行的SSH（Spring、Struts、Hibernate）、JSF、JPA的开发，同时还对SOA实现的基石&#8211;Web Service的开发进行了探讨。缺点就是偏于实践操作，相关的理论详细介绍部分比较少，对于具有一定开发经验的读者没有吸引力，因此只适合作为初学者使用MyEclipse时的参考书，或者从事技术转型的开发人员，也可作为培训机构的辅助教材，或高校学生的自学教材，手把手的视频辅导方式可以确保入门。

本书的第一章介绍常见的Java软件以及数据库和MyEclipse开发工具的下载和安装方法；第二章则带领读者通过手工和开发工具对比的方式热身开发最简单的应用；第三章则对Eclipse开发环境进行介绍；第四章则介绍如何用MyEclipse管理数据库的；第五章开发基于JDBC的应用；第六章则介绍如何在管理应用服务器；第七章在四五章的基础上介绍Hibernate的快速开发；第八章在第六章基础上介绍基础的Web应用（JSP、Servlet）的开发；第九章则进一步介绍Struts 1的开发；第十章重点介绍Spring的IOC，AOP和整合Hibernate的开发；第十一章则介绍Spring整合Struts、Hibernate的开发过程；第十二章则介绍最新推出的JPA规范及其快速开发功能；第十三章介绍Java EE 5规范推出的Web层框架JSF的开发过程；第十四章则介绍SOA的基石：基于Xfire的Web Service的快速开发过程；第十五章讨论了EJB 3的开发；第十六章则探讨了如用进行UML建模。

为了确保读者能够在实际工作中能够灵活运用Myclipse，作者在使用大量插图介绍MyEclipse 6工具的同时，也结合从事培训的经验制作视频教程完整阐述开发过程，并配以完整清晰基于实际项目的源代码和相关软件包，确保初学者能够完整实践书中内容，快速入门。

目前网上和市场上Eclipse＋插件开发题材作品较多，写的也很深入。但全面介绍MyEclipse 6进行实际项目开发的还比较少，本书立足于初学者，重点关注快速开发开发功能，例如1分钟Hibernate生成，JPA开发等。作者还具有IT培训公司的实际培训经验，为初学者定制的MyEclipse学习视频深受学生和网上读者欢迎，本书将据此原则开发全部章节的视频讲解操作。

MyEclipse 6.0 是现今国内企业流行的基于Eclipse的商业开发工具 MyEclipse的当前最新版本。Eclipse（官方网站：[http://www.eclipse.org](http://www.eclipse.org/) ）是IBM公司主导下的一款开源免费的可以做基础Java项目开发的工具，然而大多数基于Eclipse二次开发的实用开发工具例如MyEclipse，IBM WSAD，BEA Workshop，Jbuilder 2007等等都是商业产品，有别于Eclipse自身开放免费的大旗，这些软件不能免费使用，例如MyEclipse 6.0只有30天的试用期，过期之后需要付费使用。因为Java开发工具领域的四分五裂，至今仍然没有一款IDE（Integrated Development Environment，集成开发环境）可以真正媲美微软的Visual Studio 系列。

MyEclipse 6.0 集中了开源和商业软件的开发支持的大多数框架，方便易用，功能强大，获得了广大开发人员的喜爱。用它来开发比自己下载Eclipse然后到处找插件安装要方便快捷的多，因此很多企业里面都用它进行实际的开发。它支持开发调试基于Spring, Hibernate, Struts, JSF, JPA, EJB, Web Service 等 Java EE 技术的项目，还支持建模例如UML。本书就如何使用MyEclipse开发Java EE应用进行简要的介绍，部分内容基于本人翻译的MyEclipse帮助文档。因为作者的水平有限，本书不可能涵盖MyEclipse或者Eclipse的方方面面，仅供初学者作为开发时的参考书来使用。

除此之外，也可以使用一些开源免费的或者商业的Java开发工具。包括Sun资助的开源免费的Netbeans 6，支持最新的Java EE 5技术，但是不支持Spring，Hibernate，它的Swing界面设计器和手机可视化开发工具以及JSF可视化工具目前来说处于领先的位置([www.netbeans.org](http://www.netbeans.org/))；免费小巧的Windows下的开发工具Gel（停止开发了，[www.gexperts.com](http://www.gexperts.com/)）；号称最聪明的Java开发工具――商业软件，比较贵：IntelliJ IDEA 7（[www.jetbrains.com/idea/](http://www.jetbrains.com/idea/)）；另外还有一款Windows下历史悠久的小开发工具，有商业和免费版本，在初学者中比较常见：JCreator（[www.jcreator.com](http://www.jcreator.com/)）；另外还有BEA Workshop，也就是原来的M7，后来被BEA收购了，有免费的JSP编辑器版本，商业版本支持Struts，Spring，Hibernate，说实话这个基于Eclipse的开发工具的可视化程度个人认为是最好的，可是售价也相当的高（[workshopstudio.bea.com](http://workshopstudio.bea.com/) ）；WSAD（IBM WebSphere® Studio Application Developer），现在的新名字是Rational Application Developer for WebSphere Software，因为Rational（能想起来的就是ROSE这个UML建模工具）被IBM收购了，商业软件([www-306.ibm.com/software/awdtools/developer/application/](http://www-306.ibm.com/software/awdtools/developer/application/))；Oracle则在早期购买了JBuilder的源码，后来推出了免费的JDeveloper，这款软件据说其JSF可视化开发功能和Oracle支持（[www.oracle.com/technology/global/cn/software/products/jdev/](http://www.oracle.com/technology/global/cn/software/products/jdev/)）都是非常的棒的。这么多开发工具，也在一个侧面印证了Java开发工具的混乱以及Java初学者面临的挑战。

考虑到每个人的时间都是很宝贵的，我已经尽量的去掉了很多无关紧要的内容来保持本书尽可能的少占用页面。节约时间就是延长生命。

名词解释：**SSH**，这是流行的Struts + Spring + Hibernate整合技术的简称。

#### <a name="_Toc201479531">文档说明</a>

<table cellspacing="0" cellpadding="0" border="1">
  <tr>
    <td valign="top" width="142">
      <p>
        版本
      </p>
    </td>
    
    <td valign="top" width="142">
      <p>
        日期
      </p>
    </td>
    
    <td valign="top" width="142">
      <p>
        作者
      </p>
    </td>
    
    <td valign="top" width="142">
      <p>
        说明
      </p>
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="142">
      <p>
        1.0
      </p>
    </td>
    
    <td valign="top" width="142">
      <p>
        2007.12至2008.6
      </p>
    </td>
    
    <td valign="top" width="142">
      <p>
        刘长炯
      </p>
    </td>
    
    <td valign="top" width="142">
      <p>
        第一版
      </p>
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="142">
      <p>
        1.1
      </p>
    </td>
    
    <td valign="top" width="142">
      <p>
        2008.8
      </p>
    </td>
    
    <td valign="top" width="142">
      <p>
        刘长炯
      </p>
    </td>
    
    <td valign="top" width="142">
      <p>
        提供了部分BUG修正，并免费发布
      </p>
    </td>
  </tr>
</table>

#### <a name="_Toc201479532">源码和视频下载地址</a>

本书的完整版，代码和视频下载均位于如下地址：[《MyEclipse 6 Java 开发中文教程》完整版书籍代码及配套超高清讲解视频免费下载(地址已修正)](http://www.beansoft.biz/?p=132)

视频文件的压缩后文件大小为: 459 MB (482,129,402 字节)，解压缩后文件内容为508MB。

#### 适用的读者

本书适用于希望了解如何使用MyEclipse 6.0进行Java企业应用开发的Java初学者。如果有一定Java语言基础或者Eclipse使用经验，对阅读本书有很大帮助。

由于MyEclipse更新非常快，作者在时间充裕的情况下，将推出最新版本的教程。

本书配有高清讲解视频500MB，几乎绝大多数章节均配有视频，特别适合于没有条件深造的在校学生，有一定编程基础但期望转向Java开发的技术人员使用，也可用于培训机构作为辅助教材。作者模拟培训课堂推出的专业手把手视频，深受广大读者欢迎。

本书虽然主要集中在MyEclipse自身使用，但是并非仅限于HelloWorld，而是让您切实接触到前沿的开源技术如SSH，Struts 2，EJB3，文件上传下载，乱码解决等实用案例，让您熟悉环境同时又能拥有一定的实战开发经验。

这本书理论与实践相结合。在你掌握理论的基础上，在结合具体的例子，使你掌握企业中最实用的技术。

衷心希望本书能对大家有所帮助！

#### <a name="_Toc201479533">如何购买DVD</a>光盘及技术支持

大家常说：开源软件的作者也是人，也要吃饭，所以人家提供付费服务是合理的。认真写一本书是很辛苦的，如果您认可并支持作者的辛勤劳动，可以购买本书的完整版，配套光盘或者捐款给作者。

如果你对本书内容有疑问，可以给作者发送邮件，但是我不保证除购书用户外的其他用户的问题可以得到回答，本人也不免费提供QQ形式的答疑服务。

本书源代码和讲解视频现提供免费下载。本书附带了配套DVD光盘，光盘内容包括全部源代码，讲解视频和配套软件（第一章提到的所有需要下载和安装的软件），让读者不需要上网就可以实践本书所有内容。光盘和完整版电子书价格为50元（如果为学生或者贫困或者不需要光盘，可打折），付费用户可以享受最新的源代码和网上技术支持以及获得最新电子版服务。

由于现在是非常时期（2008.8～2008.10），邮局及快递公司均无法邮寄自刻光盘，因此您现在订购后不能立刻得到光盘，为免纠纷，目前作者**暂不接受任何订购请求**。

如果您需要了解更多信息，请发邮件至 **wlsmon@qq.com**。

#### <a name="_Toc201479534">关于作者</a>

刘长炯，目前居住中国北京，西安电子科技大学通信工程学士。曾任Synnex China公司系统架构师和Java讲师。从2001年起一直专注于Java方向的学习和开发。所维护的Java博客 <http://www.blogjava.net/beansoft/> 曾获得2007年12月《程序员》杂志的编辑推荐。

作者目前就职于Oracle(甲骨文)公司(<http://www.oracle.com/>)。

电子邮件：**wlsmon@qq.com**

作者同时也是2008年6月博文视点公司出版发行的**《开源技术选型手册》**的作者之一

[<img title="clip_image002" style="border-right:0;border-top:0;display:inline;border-left:0;border-bottom:0;" height="240" alt="clip_image002" hspace="12" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image002_thumb.jpg" width="194" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image002.jpg)。《开源技术选型手册》是一本面向CTO、项目经理、团队Leader和高级软件开发人员的一本参考书，供他们在做技术选型的时候使用。我们期望通过各个领域专家对自己所涉及领域的流行开源软件的整理分析，让读者能够阅览此书后对这些软件有一个大体的认识，并客观地了解它们的优缺点，进而做出有价值的判断。

#### <a name="_Toc201479535">版权声明</a>

本书版权（包含电子版、源代码及配套光盘）归作者刘长炯个人完全所有，仅限购买者/下载者本人阅读使用，不得以任何形式出版、篡改、编辑、抄袭，不得用于任何商业目的。**如需通过网络等途径传播，则不得向第三方用户收取任何附加费用（如果除作者外的第三方刻录光盘或提供付费下载用于牟利，则属于侵权）**。

**本书目前未委托任何出版社进行出版，如有发现侵权，欢迎举报。**

未经作者书面许可，任何商业培训机构不得使用本书**电子版、代码及配套视频**作为培训教程，否则将依法追究其法律责任。

如需部分或者全文引用，请事先征求作者意见。

如果发现文中有错误的地方，欢迎将页码和出错的地方反馈给我；欢迎反馈修改建议。

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [MyEclipse 6 Java 开发中文教程独家连载 &#8211; 介绍](http://www.beansoft.biz/2010/09/09/myeclipse-6-java-%e5%bc%80%e5%8f%91%e4%b8%ad%e6%96%87%e6%95%99%e7%a8%8b%e7%8b%ac%e5%ae%b6%e8%bf%9e%e8%bd%bd-%e4%bb%8b%e7%bb%8d/)