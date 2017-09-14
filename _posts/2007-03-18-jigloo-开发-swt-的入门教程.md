---
id: 621
title: Jigloo 开发 SWT 的入门教程
date: 2007-03-18T17:59:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=621
permalink: '/2007/03/18/jigloo-%e5%bc%80%e5%8f%91-swt-%e7%9a%84%e5%85%a5%e9%97%a8%e6%95%99%e7%a8%8b/'
views:
  - "3847"
original_post_id:
  - "621"
image: /wp-content/uploads/2012/09/vis-example.png
categories:
  - Java SE
tags:
  - Jigloo
  - SWT
---
</p> 

**Jigloo 开发 SWT 的入门教程**

作者: [**BeanSoft@126.com**](mailto:BeanSoft@126.com)

日期: 2007.03.18

转载请注明出处 **<http://www.beansoft.biz/>** .

经常有朋友苦于自己做了一个转换工具算法, 想用图形界面封装一下给同事使用, 却不知道如何下手. 本文就介绍一下如何用 Jigloo 开发一个简单的 SWT 应用把自己编写的 public static String doConvert(String input) 方法封装成图形界面的版本. 本文适用于从未有过 GUI/SWT 开发经验但是熟悉 Eclipse IDE 的基本使用以及插件安装的读者, 读者同时应该对 Java 语言有了解和使用的经验. 本文不讲述 SWT/Swing 以及 GUI 设计的相关知识.

如果有读者希望用 Swing 来进行这个界面的设计, 那么请您留言发表建议, 如果需要的话我将讲述 Jigloo 开发 Swing 的入门教程, 要实现的目的和本文相同, 但是步骤相对简单, 因为不需要安装 Swing(JDK 自带了). 笔者的 Code Manager .SWT 即是用 Jigloo 完成了大部分的界面开发工作.

期望对如何使用 Jigloo 有深入了解的读者可以在安装 Jigloo 插件后阅读 Eclipse 帮助文档中的 **Jigloo GUI Builder Guide** 一节了解更多的技巧, 例如: 如何在大文件模式下使用 Jigloo, 如何避免解析某些代码, Jigloo 如何解析界面代码以及如何打开由其它界面设计器制作的界面文件等. 这些帮助文档可以通过菜单 Help -> Help Contents 来打开.

**一. 搭建开发环境**

> **1. SWT 类库的下载和安装**

SWT 是 IBM 出品的类似于 AWT 的组件包, 基于 OS 组件封装模拟而成, 由 C 代码和 Java 代码混合而成. 首页: [**http://www.eclipse.org/swt/**](http://www.eclipse.org/swt/). 详细介绍可以 Google. 本文以 Windows 版本为例进行讲解. 需要注意的是并非所有平台都能运行 SWT, 详情请参考 SWT 项目主页的介绍. 并且不同的平台需要对应平台的 SWT 运行库.

截图:

 <img height="225" alt="Vista" src="http://www.eclipse.org/swt/images/vis-example.png" width="225" /> <img height="204" alt="Windows" src="http://www.eclipse.org/swt/images/win-example.png" width="216" /><img height="224" alt="Linux" src="http://www.eclipse.org/swt/images/lin-example.png" width="212" />

下载 SWT 3.3 M5 swt-3.3M5-win32-win32-x86.zip:

Download from: [**[China] Actuate Shanghai (http)**](http://www.eclipse.org/downloads/download.php?file=/eclipse/downloads/drops/S-3.3M5-200702091006/swt-3.3M5-win32-win32-x86.zip&url=http://download.actuatechina.com/eclipse/eclipse/downloads/drops/S-3.3M5-200702091006/swt-3.3M5-win32-win32-x86.zip&mirror_id=385) Windows 版本. 用 3.3 的好处是它运行的时候不需要再指定 library 路径了.

然后参考 [**http://www.eclipse.org/swt/eclipse.php**](http://www.eclipse.org/swt/eclipse.php) **Developing SWT applications using Eclipse** 一文中的说明搭好基于 Eclipse 的开发环境.

以下为文章内容的中文翻译:

因为 SWT 被集成为 Eclipse plug-in API 的一部分, 独立运行的应用程序开发最好基于 SWT 独立版的下载. 这个文档讲帮助你安装.

首先, 从[**SWT homepage**](http://www.eclipse.org/swt/) 下载适于您的平台的 SWT 的.zip 文件.

SWT .zip 文件可以导入到你的工作区. 选择 _File_ 菜单, 然后选择 _Import_ , 选中 _Existing Projects Into Workspace_ 向导. (新版本的 eclipse 中, 你可以在 _General_ 分类下找到 _Existing Projects Into Workspace_).

![Existing Projects Into Workspace Wizard](http://www.eclipse.org/swt/images/existing.png)

定位向导里面的路径到你下载的 .zip 文件所在的目录. 这将会在工作区里创建一个名为 _org.eclipse.swt_ 的工程.

![Import Projects Wizard](http://www.eclipse.org/swt/images/%20-projects.png)

您自己的 Java 项目可以将 SWT 项目作为依赖添加进来. 打开Java 项目的 Properties 对话框, 在 _Java Build Path_ 设置页中, 包含 org.eclipse.swt 项目.

![Project Properties](http://www.eclipse.org/swt/images/add-project.png)

将 SWT 项目作为依赖项, 你可以使用 Eclipse 的一些方便的功能例如 Javadoc 视图和代码提示(code assist).

![SWT Eclipse Example](http://www.eclipse.org/swt/images/swt-example.png)

现在你可以在你的项目中运行任何的主类, 通过选中类然后选择菜单 _Run > Run As > Java Application._

> **2. Jigloo 的下载和安装**

[**Jigloo**](http://cloudgarden.com/jigloo/index.html)   
能识别大多数的 FormBuilder 创建的 GUI, 例如 JBuilder 等, 运行速度比较快, 比 Visual Editor 好用. 可以编辑 AWT,Swing/SWT 的界面. 个人用免费, 商用需收费.

Note: Jigloo is free for non-commercial use, but purchase of a Professional License is required for commercial use (after successfully evaluating Jigloo).

注: 3.95 版本上笔者测试运行过的 Eclipse 版本有 3.2, 3.3. 为了便于讲述, 本文所使用的 Eclipse 版本是 3.3.0, Jigloo 3.95, JDK 1.5.

Eclipse:   
2.1.\*, 3.0\*, 3.1*, 3.2, 3.3

Java:   
1.3, 1.4 or 5.0

Platforms:

Windows, Linux (gtk) and Mac OSX. (On a Mac, only SWT GUIs can be built).

下载地址: [**jigloo_395.zip**](http://cloudgarden1.com/jigloo_395.zip)

**二. Jigloo 简单使用**

**1. 初识 Jigloo**

首先我们要如上所示新建一个名为 MyProject 的 Java 工程:

选择菜单 File -> New -> Project&#8230;, 然后选择在第一个分类中选择 Java Project, 点击 Next, 然后输入 MyProject, 并按照上节所讲设置好依赖关系. 然后请复制下列代码然后在 MyProject 的 src 目录上点击右键, 选择"Paste", 这样这个转换类就出现在了工程中:

<pre>public class Converter {<br /> public static String doConvert(String input) {<br />  return input + " is converted.";<br /> }<br />}</pre>

然后我们选择菜单 File -> New -> Other&#8230;, 在所出现的 New 对话框中打开分类 GUI Forms -> SWT, 选中 SWT Composite, 如下图所示:

<img height="500" src="http://www.blogjava.net/images/blogjava_net/beansoft/20752/o_jigloo_new_1.png" width="525" />

在接下来的向导对话框中保持默认的输入值不变即可:

<img height="288" src="http://www.blogjava.net/images/blogjava_net/beansoft/20752/o_jigloo_new_2.png" width="525" />

接着将会自动用 Jigloo 界面设计器打开新生成的文件, 显示如下:
    
  
<img height="738" src="http://www.blogjava.net/images/blogjava_net/beansoft/20752/o_jigloo_main.png" width="724" />

在 Outline(大纲) 页面中显示如下内容:

(1) 按钮切换是否显示栅格;

(2) 按钮弹出一个窗口预览当前设计界面(不经过编译);

(3) 按钮编译并运行生成的代码;

(4) 按钮启动/停止分析代码改动(由代码生成设计界面);

(5) 按钮切换是否显示继承的组件;

(6) 按钮切换界面从 SWT 到 Swing 或者反向转换(注意会有代码错误出现, 并非 100% 准确);

(7) 列出了界面中的组件层次大纲, 单击可以选中相应的组件.

在编辑器页面中显示如下内容:

(8) 正在设计中的界面, 点击红色控制(handle)点并拖拉可以调整组件的大小, 位置;

(9) SWT/Swing 组件选择面板, 单击一个组件, 然后再单击一次(8), 即可将组件放到界面中, 同样也可以继续调节大小,位置;

(12) 显示的是代码视图, 这是生成的代码, 也可以再下面修改代码, 完毕后上面将会重新解析绘制设计中的界面;

在 GUI Properties 页面中显示如下内容:

(10) 按钮切换属性列表显示为拖拉面板(SashForm)或者多页面板(TabbedPane);

(11) 属性列表, 依次为: 属性(Properties), 布局(Layout), 事件(Event).

**2. 拖拉快速搭建界面**

拖放, 预览.
    
  
首先我们在(7)中选择 _this &#8211; Composite, Grid_, 然后在(11)中选择 Layout 面板, 点击树节点 Layout(*), 在右侧下拉列表框中选择其值为 Absolute( 绝对布局).

我们选择这个布局主要是为了快速开发的关系, 虽然这不是一个很好的选择. 详细信息可以自行浏览 SWT 开发相关的资料.
    
  
好了, 接下来在(9)中选择面板 Controls, 然后点击两次 Text 控件, 放到设计面板上, 拖拉使其不要重叠并放置在合适的位置上, 这两个组件按照默认值即可, 分别为 text1, text2. 如果发现放 Text2 的时候无法添加上去, 请把它放到 Outline 中的 (7) 的 _this &#8211; Composite, Grid_ 即可.

最后我们把一个 Button 添加上去, 在添加对话框中修改 Text 值为 OK.

拖放各个组件(包括 Composite)来布局到合适的大小和位置, 如下图所示:
    
  
<img height="247" src="http://www.blogjava.net/images/blogjava_net/beansoft/20752/o_jigloo_design_main.png" width="609" />

这时候可以点击工具栏按钮 (2) 或者 (3) 预览设计成的界面. Jigloo 已经帮你写好了大部分的代码, 因此无需担心界面无法显示.

**3. 加入事件响应代码**

首先点击一下界面上的 "OK" 按钮, 然后选择(11)中的 Event 面板, 然后展开SelectionListener , 单击 widgetSelected 节点右侧的not handled 下拉框, 然后选择 handler method, 这样将会生成一个点击 OK 后触发的事件调用方法, 如下图所示:
    
  
<img height="312" src="http://www.blogjava.net/images/blogjava_net/beansoft/20752/o_jigloo_event.png" width="281" />

接着编辑器中的鼠标将会定位到刚才生成的事件方法中, 默认生成的代码如下所示:

<pre>private void button1WidgetSelected(SelectionEvent evt) {<br />  System.out.println("button1.widgetSelected, event=" + evt);<br />  //TODO add your code for button1.widgetSelected<br /> }</pre>

我们在 TODO 后面加入下列代码即可完成我们所需要的功能了:

text2.setText(Converter.doConvert(text1.getText()));

这段代码将会设置文本框2中的文本内容为先前编写的转换代码所处理过的内容, 输入的内容是 text1 中显示的文本. 相当于调用如下一段代码:

String input = text1.getText();
    
  
String output = Converter.doConvert(input);

text2.setText(output);

setText(String) 和 getText() 方法分别对组件显示的文本内容进行读写操作.

**4. 测试**

点击 (3) 按钮,运行, 修改 text1 中的值, 然后点击 OK 按钮, 可以看到运行结果正常. 如下图所示:
    
  
<img height="153" src="http://www.blogjava.net/images/blogjava_net/beansoft/20752/o_jigloo_result.png" width="183" />

**三. 打包发布应用**

**1. 目录布局以及复制依赖文件**

我们这个项目仅仅依赖 swt.jar, 首先在 MyProject 下新建一个文件夹 lib, 然后从项目 org.eclipse.swt 下将swt.jar复制到当前项目的 lib 下, 即可, 最后的文件目录结构如下示:

MyProject
    
  
├─classes

├─lib

└─src

**2. 编写启动脚本**

在根目录下编写 运行.bat, 内容如下所示:

<pre>java -cp classes;libswt.jar NewComposite</pre>

双击运行此批处理文件可以看到主窗口.

**3. 用 pack200 打包发布(可以大大减小个头)**

如果使用的是 JDK 1.5, 可以用 pack200 来减小 swt.jar 的大小, 注意用户下载后必须先解压才能运行程序.pack200用法以及批处理文件语法请自行查找相关资料.

压缩所用的两个批处理文件如下:

压缩.bat 发布的时候运行一次

<pre>pack200 libswt.jar.gz libswt.jar
del libswt.jar</pre>

解压缩.bat 用户下载后需要运行一次

<pre>unpack200 libswt.jar.gz libswt.jar
del libswt.jar.gz</pre>

**四. FAQ**

> 欢迎提问, 并来 [**Wiki**](http://beansoft.java-cn.org/) 留言交流.

一些常见小问题.

Q: 我编辑下面的代码后发现 GUI Properties 面板和组件层次大纲消失了?

A: 点击一下界面设计器中的按钮后 GUI Properties 面板将会再次出现.

Q: 我想给窗口设置一个标题, 并且给两个文本框设置默认的值为空, 怎么办?

A: 修改 Properties 属性中的 text 即可, 文本框的可以先在界面设计器中选中组件, 然后在GUI属性页修改即可. 主窗口的稍微复杂一点, 如下图所示需要先选中 Shell, 然后再修改:
    
  
<img height="541" src="http://www.blogjava.net/images/blogjava_net/beansoft/20752/o_jigloo_change_text.png" width="259" />

Q: 我想使用多行文本编辑器(TextArea), 而文中的例子是单行文本框, 怎么办?

A: 将这段操作改为 " 接下来在(9)中选择面板 Controls, 然后点击两次 **TextArea** 控件, 放到设计面板上, 拖拉使其不要重叠并放置在合适的位置上, 这两个组件按照默认值即可, 分别为 text1, text2. 如果发现放 Text2 的时候无法添加上去, 请把它放到 Outline 中的 (7) 的 _this &#8211; Composite, Grid_ 即可", 而不是使用原来的 Text 控件.

Q: 发现关闭 Eclipse 再打开刚才设计的代码的时候没有出现 Jigloo 界面设计器, 我如何才能打开它进行编辑?

A: 有时候 Eclipse 不能记住上次打开某文件的时候所用的编辑器, 因此首先确保这个类没有被 Eclipse 的其它编辑器打开, 然后右键点击文件选择 "Open with->Form Editor". 如下图所示:
    
  
<img height="390" src="http://www.blogjava.net/images/blogjava_net/beansoft/20752/o_jigloo_open_existing.png" width="515" />

**五: 下载本文所使用的 MyProject 源码**

下载后解开文件, 然后需要运行一次 解压缩.bat, 将项目导入 Eclipse 即可编译.

[**MyProject.zip**](http://www.blogjava.net/Files/beansoft/MyProject.zip) 741KB

算是我对使用 Jigloo 写的一份个人备忘录.

刚刚在官方网站上看到了如何在 Eclipse 2 上运行 Jigloo 的方法, 试了一下成功了:

\# If you are using Jigloo with WebSphere or Eclipse 2, then you need to modify Jigloo&#8217;s plugin.xml file to remove the following line: from the section of the file. Then restart Eclipse.

\# If you are using Java version 1.3 (eg, with WebSphere or on Mac OSX) then you need to download this xml.jar file and place it in the jigloo plugin folder, then restart Eclipse.

参考: Jigloo 的 KeyGen 研究http://www.blogjava.net/beansoft/archive/2007/03/18/104580.html

SWT 和 JFace，第 1 ~ 4 部分

http://www.ibm.com/developerworks/cn/opensource/os-jface1/

http://www.ibm.com/developerworks/cn/opensource/os-jface2/

http://www.ibm.com/developerworks/cn/opensource/os-jface3/

http://www.ibm.com/developerworks/cn/opensource/os-jface4/

posted on 2007-03-18 17:59 [BeanSoft](http://www.beansoft.biz/)

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Jigloo 开发 SWT 的入门教程](http://www.beansoft.biz/2007/03/18/jigloo-%e5%bc%80%e5%8f%91-swt-%e7%9a%84%e5%85%a5%e9%97%a8%e6%95%99%e7%a8%8b/)