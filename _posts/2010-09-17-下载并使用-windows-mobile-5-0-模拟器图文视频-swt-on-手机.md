---
id: 1212
title: 下载并使用 Windows Mobile 5.0 模拟器(图文,视频) SWT on 手机
date: 2010-09-17T21:50:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1212
permalink: '/2010/09/17/%e4%b8%8b%e8%bd%bd%e5%b9%b6%e4%bd%bf%e7%94%a8-windows-mobile-5-0-%e6%a8%a1%e6%8b%9f%e5%99%a8%e5%9b%be%e6%96%87%e8%a7%86%e9%a2%91-swt-on-%e6%89%8b%e6%9c%ba/'
views:
  - "3333"
original_post_id:
  - "1212"
image: /wp-content/uploads/2012/09/clip_image0014.png
categories:
  - Windows
---
### 下载并使用 Windows Mobile 5.0 模拟器(图文,视频) SWT on 手机

2007-09-13 13:05:00 **BeanSoft** **整理: 2010-9-17**

首先是下载地址: Standalone Device Emulator 1.0 with Windows Mobile OS Images <http://www.microsoft.com/downloads/en/details.aspx?FamilyID=c62d54a5-183a-4a1e-a7e2-cc500ed1f19a&displaylang=en>

需要下载并安装页面所显示的两个包:&#160; 

<table border="0" cellspacing="0" cellpadding="0">
  <tr>
    <td valign="top" width="100%">
      <p>
        <b>Files in This Download</b>
      </p>
      
      <p>
        The links in this section correspond to separate files available in this download. Download the files most appropriate for you.
      </p>
      
      <table border="0" cellspacing="0" cellpadding="0">
        <tr>
          <td>
            <p>
              <b>File Name:</b>
            </p>
          </td>
          
          <td>
            <p>
              <b>File Size</b>
            </p>
          </td>
          
          <td>
            <p>
              <b></b>
            </p>
          </td>
        </tr>
        
        <tr>
          <td>
            <p>
              efp.msi
            </p>
          </td>
          
          <td>
            <p>
              57.0 MB
            </p>
          </td>
          
          <td>
            <p>
              Download
            </p>
          </td>
        </tr>
        
        <tr>
          <td>
            <p>
              V1Emulator.zip
            </p>
          </td>
          
          <td>
            <p>
              867 KB
            </p>
          </td>
          
          <td>
            <p>
              Download
            </p>
          </td>
        </tr>
      </table>
    </td>
  </tr>
</table>

第一个包是 Windows Mobile 5.0 的 Pocket PC 和 Smartphone 的模拟器文件, 第二个是模拟器. 安装的时候先安装 V1Emulator.zip, 然后再安装 efp.msi.&#160; 注意似乎 PPC 2003 并不能被这个模拟器支持, 要装对应的 SDK, 只有这个是不需要单独安装 VS Studio 和 SDK 的.

安装完毕后可以在开始菜单项里看到如下的程序组:

Windows Mobile 5.0 MSFP Emulator Images

<img style="border-bottom:0;border-left:0;display:inline;border-top:0;border-right:0;" title="clip_image001[4]" border="0" alt="clip_image001[4]" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0014.png" width="576" height="168" />

要启动 Pocket PC, 可以选择 Coldboot(干净的启动镜像) 和 Savestate(保存过的镜像状态). 这里我选择 Coldboot 来展示如何在 PC 和 模拟器之间共享文件, 这样你就可以安装程序并进行测试了. 注意的是这些 Mobile 版 Windows 5.0 都是英文版的.

点击 PocketPC &#8211; Coldboot 来启动模拟器. 启动后点选模拟器窗口的菜单项 文件 -> 配置 &#8230;, 选择共享文件夹右侧的浏览按钮来选择PC的一个目录作为和模拟器共享的外部存储器(Storage Card).

<img style="border-bottom:0;border-left:0;display:inline;border-top:0;border-right:0;" title="clip_image002[7]" border="0" alt="clip_image002[7]" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0027.png" width="702" height="442" />

然后选择PPC的 Start -> Programs 来打开程序快捷键, 

<img style="border-bottom:0;border-left:0;display:inline;border-top:0;border-right:0;" title="clip_image003[4]" border="0" alt="clip_image003[4]" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0034.png" width="297" height="458" />

接着选择 File Explorer 来启动资源管理器.

<img style="border-bottom:0;border-left:0;display:inline;border-top:0;border-right:0;" title="clip_image004[4]" border="0" alt="clip_image004[4]" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0044.png" width="242" height="324" />

选择 Storage Card, 就可以看到 PC 共享目录里的文件了, 你可以安装程序(PPC 的安装程序一般都是 CAB 格式), 复制文件等等. 也可以启动先前开发的 eswt 程序.

<img style="border-bottom:0;border-left:0;display:inline;border-top:0;border-right:0;" title="clip_image005[4]" border="0" alt="clip_image005[4]" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0054.png" width="244" height="322" />

本人已经制作了一个可以运行在 PPC 模拟器和手机上(WM5.0)的eswt程序包, 复制到/j9p即可运行, 有兴趣的欢迎索取压缩包.

<img style="border-bottom:0;border-left:0;display:inline;border-top:0;border-right:0;" title="clip_image006[4]" border="0" alt="clip_image006[4]" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0064.png" width="244" height="324" />

下面show一下操作 PPC 模拟器的视频:

<http://cid-519b3f7aa2172030.office.live.com/self.aspx/Public/WMobile/ppc%5E_emulator.swf> 464KB

手机开发 RCP/SWT 程序的项目首页在: embedded Rich Client Platform (eRCP) <http://www.eclipse.org/ercp/>

相关资料: [Windows Mobile 6 Localized Emulator Images](http://www.microsoft.com/downloads/en/details.aspx?FamilyID=38C46AA8-1DD7-426F-A913-4F370A65A582) (Windows Mobile 6 中文模拟器镜像文件, 需要 Visual Studio 2005)

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [下载并使用 Windows Mobile 5.0 模拟器(图文,视频) SWT on 手机](http://www.beansoft.biz/2010/09/17/%e4%b8%8b%e8%bd%bd%e5%b9%b6%e4%bd%bf%e7%94%a8-windows-mobile-5-0-%e6%a8%a1%e6%8b%9f%e5%99%a8%e5%9b%be%e6%96%87%e8%a7%86%e9%a2%91-swt-on-%e6%89%8b%e6%9c%ba/)