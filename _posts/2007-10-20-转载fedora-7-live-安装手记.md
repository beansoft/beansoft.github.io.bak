---
id: 595
title: (转载)Fedora 7 Live 安装手记
date: 2007-10-20T10:27:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=595
permalink: '/2007/10/20/%e8%bd%ac%e8%bd%bdfedora-7-live-%e5%ae%89%e8%a3%85%e6%89%8b%e8%ae%b0/'
views:
  - "2876"
original_post_id:
  - "595"
image: /wp-content/uploads/2012/09/image13.png
categories:
  - Linux/Unix
---
### 注: 昨天用 VMWare 试了试 Fedora Live, 下载地址: [ftp://download.fedora.redhat.com/pub/fedora/linux/releases/7/Live/i386/](ftp://download.fedora.redhat.com/pub/fedora/linux/releases/7/Live/i386/ "ftp://download.fedora.redhat.com/pub/fedora/linux/releases/7/Live/i386/") 里面的两个 ISO 随便下一个就行了, 还不错, 安装后登录选择语言, 竟然支持中文和中文输入法, 要知道现在想找个安装包为700MB 的 Linux 还能支持中文的还真不多啊. 不过感觉有点吃内存, 响应上不如 RedHat 快. 安装后占用了 2.54 G 的空间.

 <img style="border-right:0;border-top:0;border-left:0;border-bottom:0;" height="600" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2010/08/image13.png" width="800" border="0" />

### June 5th, 2007

# <a title="Fedora 7 Live 安装手记" href="http://www.osxcn.com/ubuntu/fedora-7-installation-notes.html" rel="bookmark">Fedora 7 Live 安装手记</a>

<small>Category: <a title="View all posts in Ubuntu" href="http://www.osxcn.com/category/ubuntu" rel="category tag">Ubuntu</a>, Author: Nicky, Popularity: 30% </small> 

<div class="entry">
  <p>
    <img alt="fedora-logo.png" src="http://www.osxcn.com/wp-content/uploads/2007/06/fedora-logo.png" /><br />这次 <a href="http://fedoraproject.org/">Fedora 7</a> <a href="http://torrent.fedoraproject.org/">提供的 CD 镜像</a>分为两大版本，Fedora 7 Live 和 Fedora 7 KDE Live，前者默认采用 GNOME 桌面环境，后者集成 KDE 环境，只有在 DVD 版中才同时提供 GNOME 和 KDE 这两个供选择。用过 Redhat Linux 的都知道，在安装的时候可以选择一个桌面环境，也可以同时选择它们，现在 Fedora 7 真有点 Ubuntu 和 Kubuntu 的意思。我下载的是 Fedora 7 Live i686 来尝试，整个安装过程分为两方面，安装和配置，共 16 大步骤，花了我 30 张截图，不过绝大多数设置默认就行，重点还是在分区上。
  </p>
  
  <p>
    下面是安装全过程。<span id="more-1127"></span>
  </p>
  
  <p>
    <strong>一、进入 Live 桌面</strong>
  </p>
  
  <p>
    1、下载 <a href="http://fedoraproject.org/get-fedora.html">Fedora 7 Live</a>，设置为光盘启动后，选择第一个从光盘镜像启动。<br /><a href="http://photo7.yupoo.com/20070603/204304_2020707713_zmhdjspe.jpg"><img alt="" src="http://photo7.yupoo.com/20070603/204304_2020707713.jpg" /></a>
  </p>
  
  <p>
    2、直接回车进入<br /><a href="http://photo8.yupoo.com/20070603/204305_862139803_doemtvli.jpg"><img alt="" src="http://photo8.yupoo.com/20070603/204305_862139803.jpg" /></a>
  </p>
  
  <p>
    3、进入到 Live 桌面<br /><a href="http://photo7.yupoo.com/20070603/204306_2055378006_xjafmche.jpg"><img alt="" src="http://photo7.yupoo.com/20070603/204306_2055378006.jpg" /></a><br />这种 Live 安装方式，对桌面用户来说是最爽的。
  </p>
  
  <p>
    <strong>二、进行安装</strong>
  </p>
  
  <p>
    1、双击桌面 install to fedora 图标开始安装。<br /><a href="http://photo7.yupoo.com/20070603/204306_300286132_btgikojv.jpg"><img alt="" src="http://photo7.yupoo.com/20070603/204306_300286132.jpg" /></a>
  </p>
  
  <p>
    2、选择键盘布局。<br /><a href="http://photo7.yupoo.com/20070603/204307_907963165_aefdiido.jpg"><img alt="" src="http://photo7.yupoo.com/20070603/204307_907963165.jpg" /></a>
  </p>
  
  <p>
    3、问你是否初始化这个驱动器，选择 Yes，否则无法继续。<br /><a href="http://photo8.yupoo.com/20070603/204308_1887007985_qymvtbss.jpg"><img alt="" src="http://photo8.yupoo.com/20070603/204308_1887007985.jpg" /></a>
  </p>
  
  <p>
    4、开始分区，选择 Create custom layout，自定义分区。<br /><a href="http://photo6.yupoo.com/20070603/204309_1086473308_hzmgrcfy.jpg"><img alt="" src="http://photo6.yupoo.com/20070603/204309_1086473308.jpg" /></a><br />Linux 分区和文件系统的选择可以<a href="http://www.osxcn.com/ubuntu/linux-partition-and-file-system.html">参考这篇文章</a>。
  </p>
  
  <p>
    可惜不提供 ReiserFS 文件系统的选择。<br /><a href="http://photo6.yupoo.com/20070603/204310_1514825198_haunhrsa.jpg"><img alt="" src="http://photo6.yupoo.com/20070603/204310_1514825198.jpg" /></a>
  </p>
  
  <p>
    分区结束，点击 Next。<br /><a href="http://photo8.yupoo.com/20070603/204311_2036594160_nkcerdvc.jpg"><img alt="" src="http://photo8.yupoo.com/20070603/204311_2036594160.jpg" /></a>
  </p>
  
  <p>
    如果提示 Low Memory，选择 Yes。<br /><a href="http://photo8.yupoo.com/20070603/204312_676350344_gmhoovfo.jpg"><img alt="" src="http://photo8.yupoo.com/20070603/204312_676350344.jpg" /></a>
  </p>
  
  <p>
    5、选择 GRUB 安装位置，点击 Next。<br /><a href="http://photo7.yupoo.com/20070603/204312_302714869_roqdnhdh.jpg"><img alt="" src="http://photo7.yupoo.com/20070603/204312_302714869.jpg" /></a>
  </p>
  
  <p>
    6、网络设备配置，可以让它默认，点击 Next。<br /><a href="http://photo8.yupoo.com/20070603/204313_1304258053_jzyhfwuh.jpg"><img alt="" src="http://photo8.yupoo.com/20070603/204313_1304258053.jpg" /></a>
  </p>
  
  <p>
    7、选择时区，可以在下拉菜单中选择，建议直接在地图上点击。<br /><a href="http://photo7.yupoo.com/20070603/204314_1460303475_wflarbds.jpg"><img alt="" src="http://photo7.yupoo.com/20070603/204314_1460303475.jpg" /></a>
  </p>
  
  <p>
    8、设置超级用户 root 的口令。<br /><a href="http://photo6.yupoo.com/20070603/204315_1194655274_nayhwpep.jpg"><img alt="" src="http://photo6.yupoo.com/20070603/204315_1194655274.jpg" /></a>
  </p>
  
  <p>
    9、安装配置结束，点击 Next 开始进行安装。<br /><a href="http://photo6.yupoo.com/20070603/204316_1707277464_rqpmmiox.jpg"><img alt="" src="http://photo6.yupoo.com/20070603/204316_1707277464.jpg" /></a>
  </p>
  
  <p>
    自动安装过程<br /><a href="http://photo7.yupoo.com/20070603/204318_456716711_oupbscwo.jpg"><img alt="" src="http://photo7.yupoo.com/20070603/204318_456716711.jpg" /></a>
  </p>
  
  <p>
    10、安装结束，点击 Close 重新引导系统。<br /><a href="http://photo6.yupoo.com/20070603/204319_800279568_klboevah.jpg"><img alt="" src="http://photo6.yupoo.com/20070603/204319_800279568.jpg" /></a>
  </p>
  
  <p>
    <strong>三、安装后的设置</strong>
  </p>
  
  <p>
    1、重新引导，进入 GRUB 画面。<br /><a href="http://photo8.yupoo.com/20070603/204320_2006264815_ziiovjfi.jpg"><img alt="" src="http://photo8.yupoo.com/20070603/204320_2006264815.jpg" /></a>
  </p>
  
  <p>
    可以看到核心是 2.6.21，比 Ubuntu 7.04 稍高一点。<br /><a href="http://photo6.yupoo.com/20070603/204320_317133761_fftfufst.jpg"><img alt="" src="http://photo6.yupoo.com/20070603/204320_317133761.jpg" /></a>
  </p>
  
  <p>
    启动画面很漂亮。<br /><a href="http://photo8.yupoo.com/20070603/204321_534810815_yjsqnltv.jpg"><img alt="" src="http://photo8.yupoo.com/20070603/204321_534810815.jpg" /></a>
  </p>
  
  <p>
    2、开始进行设置，这里面大多数都可以默认，直接 Forward 就是。<br /><a href="http://photo7.yupoo.com/20070603/204322_612363250_xlhxzkle.jpg"><img alt="" src="http://photo7.yupoo.com/20070603/204322_612363250.jpg" /></a>
  </p>
  
  <p>
    3、直接 Forward。<br /><a href="http://photo7.yupoo.com/20070603/204323_1346005643_ailwrrsq.jpg"><img alt="" src="http://photo7.yupoo.com/20070603/204323_1346005643.jpg" /></a>
  </p>
  
  <p>
    4、选择在哪些服务上启用防火墙，可以都不选择。<br /><a href="http://photo8.yupoo.com/20070603/204323_1626043052_xcrncnwc.jpg"><img alt="" src="http://photo8.yupoo.com/20070603/204323_1626043052.jpg" /></a>
  </p>
  
  <p>
    5、直接 Forward。<br /><a href="http://photo8.yupoo.com/20070603/204324_1124315462_kehsopck.jpg"><img alt="" src="http://photo8.yupoo.com/20070603/204324_1124315462.jpg" /><br /></a>
  </p>
  
  <p>
    6、设置时间。<br /><a href="http://photo8.yupoo.com/20070603/204325_65594093_vpoyhhdz.jpg"><img alt="" src="http://photo8.yupoo.com/20070603/204325_65594093.jpg" /></a>
  </p>
  
  <p>
    7、发送硬件信息到服务器，选 Do not send profile，点击 Forward。<br /><a href="http://photo8.yupoo.com/20070603/204326_595827399_hissplqi.jpg"><img alt="" src="http://photo8.yupoo.com/20070603/204326_595827399.jpg" /></a>
  </p>
  
  <p>
    再说一次 No, do not send。<br /><a href="http://photo8.yupoo.com/20070603/204327_283926644_avqqxgac.jpg"><img alt="" src="http://photo8.yupoo.com/20070603/204327_283926644.jpg" /></a>
  </p>
  
  <p>
    8、建立个人帐户信息<br /><a href="http://photo8.yupoo.com/20070603/204327_507196592_ekjbxloq.jpg"><img alt="" src="http://photo8.yupoo.com/20070603/204327_507196592.jpg" /></a>
  </p>
  
  <p>
    如果提示口令太弱，不管它，点击 Yes。<br /><a href="http://photo8.yupoo.com/20070603/204328_1131572422_cwmhcxkt.jpg"><img alt="" src="http://photo8.yupoo.com/20070603/204328_1131572422.jpg" /></a>
  </p>
  
  <p>
    9、声卡设置，完成点击 Finish。<br /><a href="http://photo8.yupoo.com/20070603/204329_2146088263_hfkdpxwk.jpg"><img alt="" src="http://photo8.yupoo.com/20070603/204329_2146088263.jpg" /></a>
  </p>
  
  <p>
    到这里 Fedora 7 Live 的安装才算彻底完成了，虽然很多步骤可以默认，直接点击下一步，但相比 <a href="http://www.osxcn.com/ubuntu/ubuntu-installation-manual.html">Ubuntu 7 步加 15 分钟安装的过程</a>，说不繁琐那是骗人的。
  </p>
</div>

来自: <http://www.osxcn.com/ubuntu/fedora-7-installation-notes.html>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [(转载)Fedora 7 Live 安装手记](http://www.beansoft.biz/2007/10/20/%e8%bd%ac%e8%bd%bdfedora-7-live-%e5%ae%89%e8%a3%85%e6%89%8b%e8%ae%b0/)