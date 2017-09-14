---
id: 1213
title: SWT 在微软 Pocket PC 上运行成功
date: 2007-07-03T12:51:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1213
permalink: '/2007/07/03/swt-%e5%9c%a8%e5%be%ae%e8%bd%af-pocket-pc-%e4%b8%8a%e8%bf%90%e8%a1%8c%e6%88%90%e5%8a%9f/'
views:
  - "3308"
original_post_id:
  - "1213"
image: /wp-content/uploads/2012/09/r_swt_ppc_dev.png
categories:
  - Windows
tags:
  - Mobile
  - PocketPC
  - Windows
---
看 SWT 源码的时候注意到他们的一些地方写着支持 Mobile Device, 后来看了 SWT 的下载包的确有相关的 PPC 版本. 于是经过一番折腾和查找资料, 终于让简单的 SWT 应用在我的 多普达838(Windows Mobile 5.0) 和 Pocket PC 模拟器上运行成功了(开发的时候用模拟器还是很方便的). 先放一下截图, 遗憾的是好像只支持 IBM J9 虚拟机(手机版), 而且还是试用版90天的. 以后有空把步骤和资料整理一下:

在 Eclipse 3.3 下开发:

    <img style="border-bottom:0;border-left:0;border-top:0;border-right:0;" border="0" alt="swt_ppc Dev" src="http://www.blogjava.net/images/blogjava_net/beansoft/20752/r_swt_ppc_dev.png" />

在手机上运行:

![http://www.blogjava.net/images/blogjava_net/beansoft/20752/o_swt_ppc.gif](http://www.blogjava.net/images/blogjava_net/beansoft/20752/o_swt_ppc.gif)

看来以后可以研究研究给自己的多普达写点小应用了, 不过访问注册表这些东西还是没法做. 这就是 Java 的缺陷之一, 不论号称多么强大的 UI 组件库, 最后也不能和能提供本机 FileView, ListView, FolderView, Registry 的 Windows 组件库相比. RCP 的应用大部分集中在画图, IDE, 简单的多页视图这些方面, 国外的算法集中的多一些. 如果真要做像 Lotus 8 那样的定制 SWT 组件界面的应用, 有不是一般公司做的了, 自己画组件的代码, 还是挺复杂的. 所以个人一直对 RCP 不太看好, 因为现在的 .NET 实在太厉害了, 不管是 Windows 版还是手机版, 不过这些都是一家之言了, 哈哈.

源码和普通的 SWT 没什么两样, 唯一的限制: 1) 类文件应该是 1.4 版本; 2) 不能用自定义组件(C开头的).

&#160;

import org.eclipse.swt.*;   
import org.eclipse.swt.events.SelectionAdapter;   
import org.eclipse.swt.events.SelectionEvent;   
import org.eclipse.swt.widgets.*;   
import org.eclipse.swt.layout.*; 

public class HelloWorld {   
static private Button button1;   
static private Button button2;   
static private TreeItem treeItem2;   
static private TreeItem treeItem1;   
static private Tree tree1;   
static private Label label1;   
static private Text text1;   
static private Label label2;   
static private Slider slider1;   
static private ProgressBar progressBar1; 

public static void main(String[] args) {   
Display display = new Display(); 

/*   
* Create a Shell with the default style i.e. full screen, no decoration   
* on PocketPC. Alternative: &#8216;new Shell(display, SWT.CLOSE)&#8217; to get the   
* Pocket PC &#8216;Ok&#8217; button.   
*/   
Shell shell = new Shell(display);   
RowLayout shellLayout = new RowLayout(org.eclipse.swt.SWT.VERTICAL);   
shellLayout.fill = true;   
shellLayout.type = SWT.VERTICAL; 

/*   
* Set a text so that the top level Shell also appears in the Pocket PC   
* task list   
*/   
shell   
.setText("u5faeu8f6f PocketPC u624bu673a SWT HelloWorld u793au4f8b By BeanSoft"); 

/*   
* Set a menu bar to follow UI guidelines on Pocket PC   
*/   
Menu mb = new Menu(shell, SWT.BAR);   
shell.setMenuBar(mb); 

/*   
* Add widgets   
*/   
shell.setLayout(shellLayout);   
shell.setSize(358, 208);   
{   
button1 = new Button(shell, SWT.PUSH | SWT.CENTER);   
button1.setText("u9000u51fa!");   
button1.setBounds(0, 0, 126, 28);   
button1.addSelectionListener(new SelectionAdapter() {   
public void widgetSelected(SelectionEvent evt) {   
button1WidgetSelected(evt);   
}   
});   
}   
{   
button2 = new Button(shell, SWT.RADIO | SWT.LEFT);   
button2.setText("Radio");   
button2.setBounds(147, 0, 63, 28);   
}   
{   
tree1 = new Tree(shell, SWT.NONE);   
tree1.setBounds(0, 28, 126, 56);   
{   
treeItem1 = new TreeItem(tree1, SWT.NONE);   
treeItem1.setText("treeItem1");   
{   
treeItem2 = new TreeItem(treeItem1, SWT.NONE);   
treeItem2.setText("treeItem2");   
}   
}   
}   
{   
progressBar1 = new ProgressBar(shell, SWT.NONE);   
progressBar1.setSelection(50);   
}   
{   
label1 = new Label(shell, SWT.NONE);   
label1.setText("Code Manager .SWT u624bu673au7248");   
}   
{   
slider1 = new Slider(shell, SWT.NONE);   
slider1.setSelection(20);   
}   
{   
label2 = new Label(shell, SWT.NONE);   
label2.setText("<http://www.blogjava.net/beansoft");>   
}   
{   
text1 = new Text(shell, SWT.MULTI | SWT.WRAP);   
text1   
.setText("SWT u7ec8u4e8eu5728 Pocket PC u4e0au8fd0u884cu6210u529fu4e86!nVM: IBM J9nu4f5cu8005: u5218u957fu70af");   
} 

shell.open();   
while (!shell.isDisposed()) {   
if (!display.readAndDispatch())   
display.sleep();   
}   
} 

private static void button1WidgetSelected(SelectionEvent evt) {   
System.out.println("button1.widgetSelected, event=" + evt);   
System.exit(0);   
}   
}

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [SWT 在微软 Pocket PC 上运行成功](http://www.beansoft.biz/2007/07/03/swt-%e5%9c%a8%e5%be%ae%e8%bd%af-pocket-pc-%e4%b8%8a%e8%bf%90%e8%a1%8c%e6%88%90%e5%8a%9f/)