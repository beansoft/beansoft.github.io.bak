---
id: 1183
title: 'Eclipse 配置显示中文 javadoc 的视频[整理]'
date: 2007-06-15T12:06:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1183
permalink: '/2007/06/15/eclipse-%e9%85%8d%e7%bd%ae%e6%98%be%e7%a4%ba%e4%b8%ad%e6%96%87-javadoc-%e7%9a%84%e8%a7%86%e9%a2%91%e6%95%b4%e7%90%86/'
views:
  - "3114"
original_post_id:
  - "1183"
categories:
  - Java SE
---
BeanSoft@2007-06-15

1 Sun 官方的中文版 Java API 文档发布了，地址为：[Oracle JDK 5/6 中文文档下载地址(ZIP,HTML,CHM) 2010年版](http://www.beansoft.biz/?p=555), 下载后请参考如下步骤配合 Eclipse 使用   
2. 点击菜单 <窗口> >－> <首选项>   
3. 点击左边项目列表中的 <Java> -> <已安装的 JRE>,选中你已经安装好的 JRE5.0   
4 单击右边的编辑,点击对话框下边的库列表中的 rt.jar 左边的加号 “+”，展开 rt.jar 的配置, 选中第二项，JavaDoc 位置   
5 单击右边的编辑（如果右边的编辑是灰色的，将库列表上边的“使用默认的系统库”复选框取消选择），在弹出的对象框中，上边是使用解压后的文件来进行帮助，下面使用未解压的压缩包帮助。   
6 使用未解压的压缩包，选择下面归档中的javaDoc，（需要输入两个内容，一个是压缩包所在的位置, 可以选择右边的浏览选择，第二个是压缩包里面的路径，也可以使用右边的浏览进行选择，一直到 api 文件夹为止，就是包含index.htm的文件夹。完成后，在浏览的下面有一个检验的按钮可以进行检查）。   
7 完成后，确定，完成配置，   
在eclipse中选择系统的方法，按 F1 即可在帮助窗口中看到对应的 JavaDoc 的帮助入口，点击后，就可以直接看到对应的 JavaAPI 的 Doc 了

不过可惜, 我的blogjava附件空间也快被用完了&#8230; 郁闷. 视频下载地址: http://www.blogjava.net/Files/beansoft/eclipse\_cn\_javadoc.zip 516KB, 下载后把后缀改成 .swf 就能看了.

点击观看视频： [http://www.beansoft.biz/wp-content/uploads/2010/09/eclipse\_cn\_javadoc.swf](http://www.beansoft.biz/wp-content/uploads/2010/09/eclipse_cn_javadoc.swf)

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Eclipse 配置显示中文 javadoc 的视频[整理]](http://www.beansoft.biz/2007/06/15/eclipse-%e9%85%8d%e7%bd%ae%e6%98%be%e7%a4%ba%e4%b8%ad%e6%96%87-javadoc-%e7%9a%84%e8%a7%86%e9%a2%91%e6%95%b4%e7%90%86/)