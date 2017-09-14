---
id: 659
title: JIDE的开源Swing组件
date: 2008-03-17T19:15:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=659
permalink: '/2008/03/17/jide%e7%9a%84%e5%bc%80%e6%ba%90swing%e7%bb%84%e4%bb%b6/'
views:
  - "5260"
original_post_id:
  - "659"
image: /wp-content/uploads/2012/09/scr_oss.png
categories:
  - Java SE
---
虽然它们早就开源了（去年吧），我也是今天才看到，虽然目前也用不上，但是也许有人会需要吧。官方地址：[http://www.jidesoft.com/products/oss.htm](http://www.jidesoft.com/products/oss.htm "http://www.jidesoft.com/products/oss.htm") JIDE是一款做的非常棒的提供专业的开发工具级别Swing组件的类库（仿.NET，Office等），商业版本是收费的。

这个开源版本提供了大概30多个专业的组件。用法可以点击Run It，然后左边是示例，右侧是示例对应的代码。下面内容是引用：

JIDE Common Layer (Open Source Project) 

As of April 2007, we decided to open source the **JIDE Common Layer** &#8211; the foundation of all JIDE other products. You can get the JIDE Common Layer release or access subversion repository from <https://jide-oss.dev.java.net>. If you are paid JIDE customers, the source code for JIDE Common Layer is always included in the release under src subfolder. 

JIDE Common Layer has nearly 100k lines of code and over 30 components and utilities. It has been part of JIDE commercial products since 2002 so the quality and stability are quite high. You can run a webstart demo from the link below to see it in action. 

 <img height="289" src="http://www.jidesoft.com/imgs/scr_oss.png" width="469" border="0" />

[<img height="25" src="http://www.jidesoft.com/imgs/btn_run_it.png" width="95" border="0" />](http://www.jidesoft.com/1.4/jide_demo.jnlp)[<img height="25" src="http://www.jidesoft.com/imgs/btn_get_it.png" width="95" border="0" />](https://jide-oss.dev.java.net) 

Licensing 

JIDE Common Layer is **dual-licensed**. The two licenses are **[GPL](http://www.gnu.org/licenses/gpl.txt) with [classpath exception](http://www.gnu.org/software/classpath/license.html)** and **free [commercial license](http://www.jidesoft.com/purchase/SLA.htm)**. You can click on the links to see more information. The first license is the most widely used license among open source community. It is also the same license under which Java platform is open sourced. The second license is the original commercial license under which all other JIDE products are released, except it is free of charge in this case. We released under this license so that all existing paid JIDE customers don&#8217;t have to switch to the open source license. 

Technical Support 

One of main issues in open source project is the lack of technical support. To address this issue, here is our support policy: 

  * Documentation: All source codes are javadoc’ed. A developer guide is provided to describe how to use each component. A lot of examples can be downloaded to show you how to use components and classes in JIDE Common Layer. 

  * Bug reports: We will have dedicated resource to work on the bugs based on the priority we decide. We also accept bug fixes from the community after reviewed by our staff. 

  * Free community support: We provide a special [forum](http://www.jidesoft.com/forum/viewforum.php?f=18) so that you can get help from other people in the community. In order to encourage community, we will give away JIDE Developer License for those who actively participate in the discussion. 

  * Paid technical support: If you think it’s critical to get the high quality support in a timely fashion, you can always purchase the Annual Maintenance Renewal for JIDE Common Layer #2090 from [online store](http://www.jidesoft.com/store). For those who purchased JIDE commercial products, technical support for JIDE Common Layer is always included. Here is the JIDE Common Layer [forum](http://www.jidesoft.com/forum/viewforum.php?f=19) for paid customers. 

Contribution 

We are very flexible in accepting contributions from you as long as your own the copyright of the contribution. If you found a bug in our code, or would like to add a new feature, or introduce a new component, please feel free to contract <support@jidesoft.com> so that we can give you the check-in permission to the source code repository. We will code review the contribution and commit them. We will reward frequent contributors with free developer license of JIDE commercial products. 

Features 

UI Components 

 ![](http://www.jidesoft.com/imgs/blt_arrow.gif)<a>JideTabbedPane &#8211; an extended version of JTabbedPane supporting differnt tab shapes, color themes, shrinkable tabs, close button on tab, editable tab etc. </a>   
 ![](http://www.jidesoft.com/imgs/blt_arrow.gif)<a>JideSplitPane &#8211; an extended version of JSplitPane supporting multiple splits (JSplitPane can only have two splits)</a>   
 ![](http://www.jidesoft.com/imgs/blt_arrow.gif)<a>JideButton &#8211; an ideal replacement for a toolbar button</a>   
 ![](http://www.jidesoft.com/imgs/blt_arrow.gif)<a>JideSplitButton &#8211; a composite component which is a combination of a button and a popup menu</a>   
 ![](http://www.jidesoft.com/imgs/blt_arrow.gif)<a>Searchable JList, JTree, JComboBox and JTable &#8211; type in any text to quickly find matching rows, tree nodes, or table cells</a>   
 ![](http://www.jidesoft.com/imgs/blt_arrow.gif)<a>SearchableBar &#8211; as seen in Mozilla Firefox</a>   
 ![](http://www.jidesoft.com/imgs/blt_arrow.gif)<a>ResizablePanel, ResizableWindow and undecorated ResizableDialog</a>   
 ![](http://www.jidesoft.com/imgs/blt_arrow.gif)<a>FolderChooser &#8211; allows you to choose a folder</a>   
 ![](http://www.jidesoft.com/imgs/blt_arrow.gif)<a>RangeSlider &#8211; a slider which allows you to select two values to form a range</a>   
 ![](http://www.jidesoft.com/imgs/blt_arrow.gif)<a>JideScrollPane &#8211; column and row footer support for JScrollPane</a>   
 ![](http://www.jidesoft.com/imgs/blt_arrow.gif)<a>SimpleScrollPane &#8211; a scroll pane having four scroll buttons on the four sides.</a>   
 ![](http://www.jidesoft.com/imgs/blt_arrow.gif)<a>Overlayable &#8211; to put a component on top of another component at a specified location in order to provide a hint about how to use a component, to provide a progress indicator or to provide a status indicator beside a component without affecting the existing layout.</a>   
 ![](http://www.jidesoft.com/imgs/blt_arrow.gif)<a>AutoResizingTextArea &#8211; a text area that can automatically resize its height to fit in the content.</a>   
 ![](http://www.jidesoft.com/imgs/blt_arrow.gif)<a>StyledLabel &#8211; A JLabel that support different fonts, colors, and decorative lines. </a>   
 ![](http://www.jidesoft.com/imgs/blt_arrow.gif)<a>CheckBoxList and CheckBoxTree &#8211; use check boxes inside JLists and JTrees.</a>   
 ![](http://www.jidesoft.com/imgs/blt_arrow.gif)<a>Calculator Component</a>   
 ![](http://www.jidesoft.com/imgs/blt_arrow.gif)<a>DateSpinner and PointSpinner</a>   
 ![](http://www.jidesoft.com/imgs/blt_arrow.gif)<a>Popup &#8211; support any popup window</a>   
 ![](http://www.jidesoft.com/imgs/blt_arrow.gif)<a>AutoCompletion and IntelliHints</a>   
 ![](http://www.jidesoft.com/imgs/blt_arrow.gif)<a>StandardDialog &#8211; built on top of JDialog to support common used dialog standards as well as adding missing standard features of any dialogs. </a>   
 ![](http://www.jidesoft.com/imgs/blt_arrow.gif)<a>ButtonPanel &#8211; arrange buttons in different layouts with different gaps based on OS conventions </a>   
 ![](http://www.jidesoft.com/imgs/blt_arrow.gif)<a>Pre-built panels such as BannerPanel </a>   
 ![](http://www.jidesoft.com/imgs/blt_arrow.gif)<a>AbstractPage &#8211; lazy loading panel with page events (open, closing,<br /> closed, etc.), an ideal panel for building dialogs </a>

Utility Classes 

 ![](http://www.jidesoft.com/imgs/blt_arrow.gif)<a>IconFactory &#8211; simplify and unify the usage of icons across the whole application</a>   
 ![](http://www.jidesoft.com/imgs/blt_arrow.gif)<a>SystemInfo &#8211; a utility class which can be used to retrieve information about the current system, including OS name and version, JDK version requirement, etc.</a>   
 ![](http://www.jidesoft.com/imgs/blt_arrow.gif)<a>A fast gradient paint method in JideSwingUtilities. By leveraging DirectDraw, the fast gradient paint is 2 to 40 times faster than normal GradientPaint.</a> 

Screenshots 

[<img height="135" src="http://www.jidesoft.com/images/jidetabbedpane-s.png" width="111" border="0" />](http://www.jidesoft.com/images/jidetabbedpane.png)   
JideTabbedPane   
[<img height="142" src="http://www.jidesoft.com/images/outlook-tabbed-pane-s.png" width="67" border="0" />](http://www.jidesoft.com/images/outlook-tabbed-pane.png)   
OutlookTabbedPane   
[<img height="135" src="http://www.jidesoft.com/images/jidebutton_s.png" width="70" border="0" />](http://www.jidesoft.com/images/jidebutton.png)   
JideButton with different styles   
[<img height="120" src="http://www.jidesoft.com/images/jidesplitbutton-s.png" width="69" border="0" />](http://www.jidesoft.com/images/jidesplitbutton.png)   
JideSplitButton with different styles 

[<img height="120" src="http://www.jidesoft.com/images/fastgradientpaint_s.png" width="99" border="0" />](http://www.jidesoft.com/images/fastgradientpaint.png)   
Fast GradientPaint   
[<img src="http://www.jidesoft.com/images/searchable-s.png" border="0" />](http://www.jidesoft.com/images/searchable.png)   
Searchable JList, JTree and JTable   
[<img src="http://www.jidesoft.com/images/searchablebar-s.png" border="0" />](http://www.jidesoft.com/images/searchablebar.png)   
Searchable Bar 

[<img height="100" src="http://www.jidesoft.com/images/folderchooser-s.png" width="72" border="0" />](http://www.jidesoft.com/images/folderchooser.png)   
FolderChooser   
[<img height="100" src="http://www.jidesoft.com/images/autocompletion2-s.png" width="89" border="0" />](http://www.jidesoft.com/images/autocompletion2.png)   
AutoCompletion Example 1   
[<img src="http://www.jidesoft.com/images/autocompletion1-s.png" border="0" />](http://www.jidesoft.com/images/autocompletion1.png)   
AutoCompletion   
Example 2   
    <img height="100" src="http://www.jidesoft.com/images/calculator_s.png" width="51" border="0" />  
Calculator 

[<img height="100" src="http://www.jidesoft.com/images/intellihints1-s.png" width="149" border="0" />](http://www.jidesoft.com/images/intellihints1.png)   
IntelliHints   
Example 1   
[<img height="100" src="http://www.jidesoft.com/images/intellihints2-s.png" width="149" border="0" />](http://www.jidesoft.com/images/intellihints2.png)   
IntelliHints   
Example 2   
[<img height="100" src="http://www.jidesoft.com/images/checkboxlist-s.png" width="100" border="0" />](http://www.jidesoft.com/images/checkboxlist.png)   
CheckBoxList   
[<img height="100" src="http://www.jidesoft.com/images/checkboxtree-s.png" width="76" border="0" />](http://www.jidesoft.com/images/checkboxtree.png)   
CheckBoxTree 

[<img height="100" src="http://www.jidesoft.com/images/rangeslider-s.png" width="118" border="0" />](http://www.jidesoft.com/images/rangeslider.png)   
RangeSlider   
[<img height="110" src="http://www.jidesoft.com/images/jidescrollpane_s.png" width="141" border="0" />](http://www.jidesoft.com/images/jidescrollpane.png)   
JideScrollPane and an example   
[<img height="100" src="http://www.jidesoft.com/images/styledlabel-s.png" width="55" border="0" />](http://www.jidesoft.com/images/styledlabel.png)   
StyledLabel   
[<img height="100" src="http://www.jidesoft.com/images/styledlabelbuilder-s.png" width="81" border="0" />](http://www.jidesoft.com/images/styledlabelbuilder.png)   
StyledLabelBuilder 

[<img height="100" src="http://www.jidesoft.com/images/options_icon2_s.png" width="120" border="0" />](http://www.jidesoft.com/images/options_icon2.png)   
MultiplePageDialog ICON_STYLE like Mozilla Firebird   
(icons are not included)   
[<img height="92" src="http://www.jidesoft.com/images/options_icon_s.png" width="130" border="0" />](http://www.jidesoft.com/images/options_icon.png)   
MultiplePageDialog&#160;   
ICON_STYLE like IntelliJ IDEA   
(icons are not included)   
[<img height="92" src="http://www.jidesoft.com/images/options_list_s.png" width="130" border="0" />](http://www.jidesoft.com/images/options_list.png)   
MultiplePageDialog   
LIST_STYLE   
[<img height="87" src="http://www.jidesoft.com/images/options_tree_s.png" width="130" border="0" />](http://www.jidesoft.com/images/options_tree.png)   
MultiplePageDialog   
TREE_STYLE 

[<img height="51" src="http://www.jidesoft.com/images/banner_s.png" width="112" border="0" />](http://www.jidesoft.com/images/banner.png)   
Banners   
[<img height="92" alt="overlayable" src="http://www.jidesoft.com/images/overlayable-s.png" width="148" border="0" />](http://www.jidesoft.com/images/overlayable.png)   
Overlayable 

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [JIDE的开源Swing组件](http://www.beansoft.biz/2008/03/17/jide%e7%9a%84%e5%bc%80%e6%ba%90swing%e7%bb%84%e4%bb%b6/)