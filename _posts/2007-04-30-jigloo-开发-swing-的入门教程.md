---
id: 622
title: Jigloo 开发 Swing 的入门教程
date: 2007-04-30T14:15:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=622
permalink: '/2007/04/30/jigloo-%e5%bc%80%e5%8f%91-swing-%e7%9a%84%e5%85%a5%e9%97%a8%e6%95%99%e7%a8%8b/'
views:
  - "3312"
original_post_id:
  - "622"
categories:
  - Java SE
tags:
  - GUI Designer
  - Jigloo
  - Swing
---
   <span class="wenzhang_con" id="articlecontent" style="width:740px;"></p> 

<div class="posttitle">
  Jigloo 开发 Swing 的入门教程
</div>

<p>
  参考文章: <a href="http://www.beansoft.biz/?p=621">Jigloo 开发 SWT 的入门教程</a><font color="#1a8bc8"></font><font color="#1a8bc8"></font>
</p>

<p>
  作者: <a href="mailto:BeanSoft@126.com"><u><font color="#0000ff">BeanSoft@126.com</font></u></a>
</p>

<p>
  日期: 2007.04.30
</p>

<p>
  转载请注明出处 <a href="http://beansoft.biz/">http://beansoft.biz/</a>
</p>

<p>
  下载本文操作视频: <a href="http://cid-519b3f7aa2172030.office.live.com/self.aspx/Public/beansoft%5E_java-cn%5E_org/jigloo%5E_swing.swf">jigloo_swing.swf</a><u><font color="#0000ff"> </font></u>1.86 MB
</p>

<p>
  经常有朋友苦于自己做了一个转换工具算法, 想用图形界面封装一下给同事使用, 却不知道如何下手. 本文就介绍一下如何用 Jigloo 开发一个简单的 Swing 桌面应用把自己编写的 <span class="STYLE1"><strong><em><font color="#0066ff">public static String doConvert(String input)</font></em></strong></span> 方法封装成图形界面的版本. 本文适用于从未有过 GUI/SWT 开发经验但是熟悉 Eclipse IDE 的基本使用以及插件安装的读者, 读者同时应该对 Java 语言有了解和使用的经验. 本文不讲述 SWT/Swing 以及 GUI 设计的相关知识.
</p>

<p>
  这里用 Swing 来进行这个界面的设计, 步骤相对于基于 SWT 来得简单, 因为不需要安装 Swing(JDK/JRE 自带了). 笔者的 Tomcat Server Monitor 即是用 Jigloo 完成了大部分的界面开发工作.
</p>

<p>
  题外话: 目前 Swing 界面开发做的最好的界面设计器是 Netbeans 的界面设计器, 基本上不用再考虑布局的问题.
</p>

<p>
  期望对如何使用 Jigloo 有深入了解的读者可以在安装 Jigloo 插件后阅读 Eclipse 帮助文档中的 <strong>Jigloo GUI Builder Guide</strong> 一节了解更多的技巧, 例如: 如何在大文件模式下使用 Jigloo, 如何避免解析某些代码, Jigloo 如何解析界面代码以及如何打开由其它界面设计器制作的界面文件等. 这些帮助文档可以通过菜单 Help -> Help Contents 来打开.
</p>

<p>
  <strong>一. 搭建开发环境</strong>
</p>

<blockquote>
  <p>
    <strong>1. JDK/JRE 的下载和安装 </strong>
  </p>
</blockquote>

<p>
  JDK 可以从 <a href="http://java.sun.com/j2se/"><u><font color="#0000ff">http://java.sun.com/j2se/</font></u></a> 进行下载和安装, 这里就不再赘述了. 安装完的 JDK 就可以用来开发和运行 Swing .
</p>

<p>
  &#160;
</p>

<blockquote>
  <p>
    <strong>2. Jigloo 的下载和安装</strong>
  </p>
</blockquote>

<p>
  <a href="http://cloudgarden.com/jigloo/index.html"><u><font color="#0000ff">Jigloo</font></u></a> <br />能识别大多数的 FormBuilder 创建的 GUI, 例如 JBuilder 等, 运行速度比较快, 比 Visual Editor 好用. 可以编辑 AWT,Swing/SWT 的界面. 个人用免费, 商用需收费.
</p>

<p>
  Note: Jigloo is free for non-commercial use, but purchase of a Professional License is required for commercial use (after successfully evaluating Jigloo).
</p>

<p>
  注: 3.95 版本上笔者测试运行过的 Eclipse 版本有 2.1, 3.2, 3.3. 为了便于讲述, 本文所使用的 Eclipse 版本是 3.3.0, Jigloo 3.95, JDK 1.5.
</p>

<p>
  Eclipse: <br />2.1.*, 3.0*, 3.1*, 3.2, 3.3
</p>

<p>
  Java: <br />1.3, 1.4 or 5.0
</p>

<p>
  Platforms:
</p>

<p>
  Windows, Linux (gtk) and Mac OSX. (On a Mac, only SWT GUIs can be built).
</p>

<p>
  下载地址: <a title="here" href="http://cloudgarden1.com/jigloo_395.zip"><u><font color="#0000ff">jigloo_395.zip</font></u></a>
</p>

<p>
  <strong>二. Jigloo 简单使用 </strong>
</p>

<p>
  <strong>1. 初识 Jigloo</strong>
</p>

<p>
  首先我们要如上所示新建一个名为 jiglooSwing 的 Java 工程:
</p>

<p>
  选择菜单 File -> New -> Project&#8230;, 然后选择在第一个分类中选择 Java Project, 点击 Next, 然后输入 jiglooSwing, 点击"<u>F</u>inish"按钮. 然后请复制下列代码到剪贴板然后在 MyProject 的 src 目录上点击右键, 选择"Paste", 这样这个转换类就出现在了工程中:
</p>

<pre>public class Converter {<br />	public static String doConvert(String input) {<br />		return input + " is converted.";<br />	}<br />}</pre>

<p>
  然后我们选择菜单 File -> New -> Other&#8230;, 在所出现的 New 对话框中打开分类 GUI Forms -> Swing, 选中 JFrame, 如下图所示:
</p>

<p>
  <img height="400" alt="" src="http://image4.360doc.com/DownloadImg/2009/11/11/59141_8792079_1.png" width="593" border="0" />
</p>

<p>
  在接下来的向导对话框中保持默认的输入值不变, 然后删除 src 这个包名即可:
</p>

<p>
  <img height="503" alt="" src="http://image4.360doc.com/DownloadImg/2009/11/11/59141_8792079_2.png" width="596" border="0" />
</p>

<p>
  接着将会自动用 Jigloo 界面设计器打开新生成的文件, 显示如下:<br /> <br /><img height="738" alt="" src="http://image4.360doc.com/DownloadImg/2009/11/11/59141_8792079_3.png" width="724" border="0" />
</p>

<p>
  在 Outline(大纲) 页面中显示如下内容:
</p>

<p>
  (1) 按钮切换是否显示栅格;
</p>

<p>
  (2) 按钮弹出一个窗口预览当前设计界面(不经过编译);
</p>

<p>
  (3) 按钮编译并运行生成的代码;
</p>

<p>
  (4) 按钮启动/停止分析代码改动(由代码生成设计界面);
</p>

<p>
  (5) 按钮切换是否显示继承的组件;
</p>

<p>
  (6) 按钮切换界面从 SWT 到 Swing 或者反向转换(注意会有代码错误出现, 并非 100% 准确);
</p>

<p>
  (7) 列出了界面中的组件层次大纲, 单击可以选中相应的组件.
</p>

<p>
  在编辑器页面中显示如下内容:
</p>

<p>
  (8) 正在设计中的界面, 点击红色控制(handle)点并拖拉可以调整组件的大小, 位置;
</p>

<p>
  (9) SWT/Swing 组件选择面板, 单击一个组件, 然后再单击一次(8), 即可将组件放到界面中, 同样也可以继续调节大小,位置;
</p>

<p>
  (12) 显示的是代码视图, 这是生成的代码, 也可以再下面修改代码, 完毕后上面将会重新解析绘制设计中的界面;
</p>

<p>
  在 GUI Properties 页面中显示如下内容:
</p>

<p>
  (10) 按钮切换属性列表显示为拖拉面板(SashForm)或者多页面板(TabbedPane);
</p>

<p>
  (11) 属性列表, 依次为: 属性(Properties), 布局(Layout), 事件(Event).
</p>

<p>
  <strong>2. 拖拉快速搭建界面 </strong>
</p>

<p>
  拖放, 预览.<br /> <br />首先我们在(7)中选择 <em>this &#8211; JFrame, Border </em>, 然后在(11)中选择 Layout 面板, 点击树节点 Layout(*), 在右侧下拉列表框中选择其值为 Absolute( 绝对布局).
</p>

<p>
  我们选择这个布局主要是为了快速开发的关系, 虽然这不是一个很好的选择. 详细信息可以自行浏览 Swing 开发相关的资料.
</p>

<p>
  好了, 接下来在(9)中选择面板 Components, 然后点击两次 JTextField 控件, 放到设计面板上, 拖拉使其不要重叠并放置在合适的位置上, 这两个组件按照默认值即可, 分别为 jTextField1, jTextField2.
</p>

<p>
  最后我们把一个 JButton 添加上去, 在添加对话框中修改 Text 值为 OK.
</p>

<p>
  拖放各个组件来布局到合适的大小和位置, 如下图所示:<br /> <br /><img height="441" alt="" src="http://image4.360doc.com/DownloadImg/2009/11/11/59141_8792079_4.png" width="257" border="0" />
</p>

<p>
  这时候可以点击工具栏按钮 (2) 或者 (3) 预览设计成的界面. Jigloo 已经帮你写好了大部分的代码, 因此无需担心界面无法显示.
</p>

<p>
  <strong>3. 加入事件响应代码 </strong>
</p>

<p>
  首先点击一下界面上的 "OK" 按钮, 然后选择(11)中的 Event 面板, 然后展开ActionListener , 单击 actionPerformed 节点右侧的not handled 下拉框, 然后选择 handler method, 这样将会生成一个点击 OK 后触发的事件调用方法, 如下图所示:<br /> <br /><img height="222" alt="" src="http://image4.360doc.com/DownloadImg/2009/11/11/59141_8792079_5.png" width="256" border="0" />
</p>

<p>
  接着编辑器中的鼠标将会定位到刚才生成的事件方法中, 默认生成的代码如下所示:
</p>

<pre>	private void jButton1ActionPerformed(ActionEvent evt) {<br />		System.out.println("jButton1.actionPerformed, event=" + evt);<br />		//TODO add your code for jButton1.actionPerformed<br />	}</pre>

<p>
  我们在 TODO 后面加入下列代码即可完成我们所需要的功能了:
</p>

<p>
  jTextField2.setText(Converter.doConvert(jTextField1.getText()));
</p>

<p>
  这段代码将会设置文本框2中的文本内容为先前编写的转换代码所处理过的内容, 输入的内容是 jTextField1 中显示的文本. 相当于调用如下一段代码:
</p>

<p>
  String input = jTextField1.getText();<br /> <br />String output = Converter.doConvert(input);
</p>

<p>
  jTextField2.setText(output);
</p>

<p>
  setText(String) 和 getText() 方法分别对组件显示的文本内容进行读写操作.
</p>

<p>
  <strong>4. 测试</strong>
</p>

<p>
  点击 (3) 按钮,运行, 修改 jTextField1 中的值, 然后点击 OK 按钮, 可以看到运行结果正常. 如下图所示:<br /> <br /><img height="175" alt="" src="http://image4.360doc.com/DownloadImg/2009/11/11/59141_8792079_6.png" width="400" border="0" />
</p>

<p>
  <strong>三. 打包发布应用 </strong>
</p>

<p>
  <strong>1. 目录布局以及复制依赖文件 </strong>
</p>

<p>
  我们这个项目不依赖任何第三方包, 最后的文件目录结构如下示:
</p>

<p>
  jiglooSwing<br /> <br />├─classes
</p>

<p>
  └─src
</p>

<p>
  <strong>2. 编写启动脚本</strong>
</p>

<p>
  在根目录下编写 运行.bat, 内容如下所示:
</p>

<pre>java -cp classes NewJFrame</pre>

<p>
  双击运行此批处理文件可以看到主窗口.
</p>

<p>
  <strong>四. FAQ </strong>
</p>

<blockquote>
  <p>
    欢迎提问, 并来 <a href="http://beansoft.java-cn.org/"><u><font color="#800080">Wiki</font></u></a> 留言交流.
  </p>
</blockquote>

<p>
  一些常见小问题.
</p>

<p>
  Q: 我编辑下面的代码后发现 GUI Properties 面板和组件层次大纲消失了?
</p>

<p>
  A: 点击一下界面设计器中的按钮后 GUI Properties 面板将会再次出现.
</p>

<p>
  Q: 我想给窗口设置一个标题, 并且给两个文本框设置默认的值为空, 怎么办?
</p>

<p>
  A: 修改 Properties 属性中的 text 即可, 文本框的可以先在界面设计器中选中组件, 然后在GUI属性页修改即可. 主窗口的稍微复杂一点, 如下图所示需要先选中 JFrame, 然后再修改:<br /> <br /><img height="443" alt="" src="http://image4.360doc.com/DownloadImg/2009/11/11/59141_8792079_7.png" width="258" border="0" />
</p>

<p>
  Q: 我想使用多行文本编辑器(TextArea), 而文中的例子是单行文本框, 怎么办?
</p>

<p>
  A: 将这段操作改为 " 接下来在(9)中选择面板 Components, 然后点击两次 <strong>JTextArea</strong> 控件, 放到设计面板上, 拖拉使其不要重叠并放置在合适的位置上, 这两个组件按照默认值即可, 分别为 jTextArea1, jTextArea2. 如果发现放 jTextArea2 的时候无法添加上去, 请把它放到 Outline 中的 (7) 的 <em>this &#8211; JFrame, Absolute </em>即可".
</p>

<p>
  同时事件处理代码根据变量名的改动修改为如下代码:
</p>

<p>
  jTextArea2.setText(Converter.doConvert(jTextArea1.getText()));
</p>

<p>
  Q: 发现关闭 Eclipse 再打开刚才设计的代码的时候没有出现 Jigloo 界面设计器, 我如何才能打开它进行编辑?
</p>

<p>
  A: 有时候 Eclipse 不能记住上次打开某文件的时候所用的编辑器, 因此首先确保这个类没有被 Eclipse 的其它编辑器打开, 然后右键点击文件选择 "Open with->Form Editor". 如下图所示:<br /> <br /><img height="390" alt="" src="http://image4.360doc.com/DownloadImg/2009/11/11/59141_8792079_8.png" width="515" border="0" />
</p>

<p>
  &#160;
</p>

<p>
  <strong>五: 下载本文所使用的 jiglooSwing 源码</strong>
</p>

<p>
  下载后解开文件, 将项目导入 Eclipse 即可编译.
</p>

<p>
  <a href="http://www.blogjava.net/Files/beansoft/jiglooSwing.zip"><u><font color="#800080">jiglooSwing.zip</font></u></a> 5 KB
</p>

<p>
  </span>
</p>

<p>
  转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2007/04/30/jigloo-%e5%bc%80%e5%8f%91-swing-%e7%9a%84%e5%85%a5%e9%97%a8%e6%95%99%e7%a8%8b/">Jigloo 开发 Swing 的入门教程</a>
</p>