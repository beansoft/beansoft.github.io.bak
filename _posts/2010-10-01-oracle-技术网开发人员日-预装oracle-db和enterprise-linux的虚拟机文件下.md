---
id: 1290
title: 'Oracle 技术网开发人员日-预装Oracle DB和Enterprise Linux的虚拟机文件下载[Virtualbox][转]'
date: 2010-10-01T12:05:49+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1290
permalink: '/2010/10/01/oracle-%e6%8a%80%e6%9c%af%e7%bd%91%e5%bc%80%e5%8f%91%e4%ba%ba%e5%91%98%e6%97%a5-%e9%a2%84%e8%a3%85oracle-db%e5%92%8centerprise-linux%e7%9a%84%e8%99%9a%e6%8b%9f%e6%9c%ba%e6%96%87%e4%bb%b6%e4%b8%8b/'
views:
  - "5081"
original_post_id:
  - "1290"
image: /wp-content/uploads/2012/09/tux.gif
categories:
  - Oracle
---
本文内容转自: [http://www.oracle.com/technology/global/cn/software/products/virtualbox/appliances/index.html](http://www.oracle.com/technology/global/cn/software/products/virtualbox/appliances/index.html "http://www.oracle.com/technology/global/cn/software/products/virtualbox/appliances/index.html")&#160;

English edition: [http://www.oracle.com/technetwork/database/enterprise-edition/databaseappdev-vm-161299.html](http://www.oracle.com/technetwork/database/enterprise-edition/databaseappdev-vm-161299.html "http://www.oracle.com/technetwork/database/enterprise-edition/databaseappdev-vm-161299.html")

站长BeanSoft即将对此虚拟机的用法及相关疑难问题进行进一步的介绍.

提示: 下载文件需要有OTN帐号, 可免费注册. 此Linux未安装中文字体和输入法.

&#160;![http://oss.oracle.com/images/tux.gif](http://oss.oracle.com/images/tux.gif)[http://oss.oracle.com/images/tux.gif](http://oss.oracle.com/images/tux.gif "http://oss.oracle.com/images/tux.gif")

## 研讨会前安装说明 — 动手实践

欢迎阅读 **Oracle 技术网开发人员日 — 数据库应用程序开发动手实践**的动手实践 (HOL) 安装说明。这是一个需要您自带笔记本电脑参与的研讨会；本文档介绍如何安装为该动手实践研讨会提供了预先配置的所需 Oracle 软件的虚拟来宾软件设备。 

此数据库开发软件设备是完成 Java、Apex 和数据库开发系列动手实践主题所必需的 — 如果您进行的是 .Net 开发主题，则不需要该软件设备。

请注意，本软件设备**仅用于测试**，因此**不受生产环境支持**，因而不应在生产环境中使用。 该虚拟机包括以下内容：

<ul type="square">
  <li>
    Oracle Enterprise Linux 5
  </li>
  <li>
    Oracle Database 11<em>g</em> 第 2 版企业版
  </li>
  <li>
    Oracle TimesTen In-Memory Database Cach
  </li>
  <li>
    Oracle XML DB
  </li>
  <li>
    Oracle SQL Developer
  </li>
  <li>
    Oracle SQL Developer Data Modeler
  </li>
  <li>
    Oracle Application Express
  </li>
  <li>
    Oracle JDeveloper
  </li>
  <li>
    动手实践（在 Firefox 中通过工具栏菜单访问）
  </li>
</ul>

* * *

## 要求

<div align="left">
</div>

<ul class="bodycopy" type="square">
  <li>
    最少 2GB RAM
  </li>
  <li>
    最少 15 GB 的可用硬盘空间（注意：实施虚拟化最好使用连续磁盘空间，因此最好在 Windows 上运行一次磁盘碎片整理程序，并确保在 Windows 上使用 NTFS 文件管理系统处理大文件。 )
  </li>
  <li>
    <div align="left">
      2GHz 处理器（主频较低的处理器也可以，但速度会较慢）
    </div>
  </li>
  
  <li>
    <div align="left">
      Mozilla Firefox 2.0 或更高版本、Internet Explorer 7 或更高版本、Safari 3.0 或更高版本、Google Chrome 1.0 或更高版本
    </div>
  </li>
  
  <li>
    <div align="left">
      Adobe Acrobat reader
    </div>
  </li>
</ul>

* * *

## 安装

**第 1 步.** 将 [Oracle VM VirtualBox](http://www.sun.com/software/products/virtualbox/get.jsp){.bodylink} 下载并安装到您的主机系统中。

**第 2 步.** 下载以下文件： 

 <img style="display:inline;border-width:0;" title="image" border="0" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2010/10/image.png" width="13" height="13" />[Oracle Developer Days.mf](http://download.oracle.com/otn/other/Oracle%20Developer%20Days.mf){.bodylink}<span class="textA">（212 字节，md5sum：93f7aa6238d02a1f6bd867b77a744737）</span>   
 <img style="display:inline;border-width:0;" title="image" border="0" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2010/10/image.png" width="13" height="13" />[Oracle Developer Days.ovf](http://download.oracle.com/otn/other/Oracle%20Developer%20Days.ovf){.bodylink}<span class="textA">（93,496 字节，md5sum：45007ccf025fba1c3597161796200781）</span>   
 <img style="display:inline;border-width:0;" title="image" border="0" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2010/10/image.png" width="13" height="13" />[OTN\_DD\_ROOT.vmdk](http://download.oracle.com/otn/other/OTN_DD_ROOT.vmdk){.bodylink}<span class="textA">（1,258,071,040 字节，md5sum：0afed725e7605a3fbcae6aa1c32a20c8）</span>

**第 3 步.** 下载并重新组装以下文件： 

 <img style="display:inline;border-width:0;" title="image" border="0" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2010/10/image.png" width="13" height="13" />[OTN\_DD\_ORACLE.vmdk.001](http://download.oracle.com/otn/other/OTN_DD_ORACLE.vmdk.001){.bodylink}<span class="textA">（1,468,006,400 字节，md5sum：66dac174bdb1ae835750f40c09550dd0）</span>   
 <img style="display:inline;border-width:0;" title="image" border="0" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2010/10/image.png" width="13" height="13" />[OTN\_DD\_ORACLE.vmdk.002](http://download.oracle.com/otn/other/OTN_DD_ORACLE.vmdk.002){.bodylink}<span class="textA">（1,290,919,424 字节，md5sum：15920705ec65827b306f10efec3f22f5）</span>

> Linux：   
> &#8211; 下载这两个文件，保持文件名不变   
> &#8211; 下载 [.sh 文件](http://download.oracle.com/otn/other/combine.sh)并执行 或者运行以下命令：
> 
> <pre>cat OTN_DD_ORACLE.vmdk.001  OTN_DD_ORACLE.vmdk.002 &gt; OTN_DD_ORACLE.vmdk<br /></pre>
> 
> Windows：
> 
> &#8211; 下载这两个文件，保持文件名不变
> 
> &#8211; 下载 [.bat 文件](http://download.oracle.com/otn/other/combine.bat)并从命令行执行 ，或者运行以下命令：
> 
> <pre>copy /B OTN_DD_ORACLE.vmdk.001 + OTN_DD_ORACLE.vmdk.002 OTN_DD_ORACLE.vmdk </pre>

**第 4 步.** 导入您的 VM：**File > Import Appliance** 启动 Appliance Import Wizard。单击 **Choose&#8230;** 找到您刚才在其中重新组装两个文件的目录，选择 **OTN Developer Days.ovf**，然后单击 **Next>** 开始导入虚拟机。导入时，系统将提示您接受相应的开发人员许可。导入完成后，您将看到“Oracle Developer Days （Powered Off)”。

**第 5 步.** 测试您的 VM：导入完成后，双击 OTN Developer Days VM。单击 **OK** 关闭 Virtualbox Information 对话框。进入 Enterprise Linux 5 屏幕后即可进行登录。（用户名和口令均为 **oracle**。）完成该登录过程；看到终端窗口后说明登录成功，您可以关闭该窗口。一旦完成了客户 VM 中的工作，就可以使用 **System > Shut Down** 关闭该虚拟机；这一操作将客户 VM 恢复为 Powered Off 状态。

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Oracle 技术网开发人员日-预装Oracle DB和Enterprise Linux的虚拟机文件下载\[Virtualbox\]\[转\]](http://www.beansoft.biz/2010/10/01/oracle-%e6%8a%80%e6%9c%af%e7%bd%91%e5%bc%80%e5%8f%91%e4%ba%ba%e5%91%98%e6%97%a5-%e9%a2%84%e8%a3%85oracle-db%e5%92%8centerprise-linux%e7%9a%84%e8%99%9a%e6%8b%9f%e6%9c%ba%e6%96%87%e4%bb%b6%e4%b8%8b/)