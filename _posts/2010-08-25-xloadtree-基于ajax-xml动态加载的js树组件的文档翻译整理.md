---
id: 625
title: 'XLoadTree 基于AJAX + XML动态加载的JS树组件的文档翻译[整理]'
date: 2010-08-25T19:58:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=625
permalink: '/2010/08/25/xloadtree-%e5%9f%ba%e4%ba%8eajax-xml%e5%8a%a8%e6%80%81%e5%8a%a0%e8%bd%bd%e7%9a%84js%e6%a0%91%e7%bb%84%e4%bb%b6%e7%9a%84%e6%96%87%e6%a1%a3%e7%bf%bb%e8%af%91%e6%95%b4%e7%90%86/'
views:
  - "5248"
original_post_id:
  - "625"
image: /wp-content/uploads/2012/09/o_tree1.png
categories:
  - AJAX/JavaScript
---
本文已经翻译完毕, 原始版本可以在这里下载:<http://webfx.eae.net/dhtml/xloadtree/xloadtree.html.> 

全文打包下载:[http://www.blogjava.net/Files/beansoft/xloadtree\_zh\_cn.zip](http://www.blogjava.net/Files/beansoft/xloadtree_zh_cn.zip)&nbsp; 54KB  
. 今天是周末, 小雪. 本翻译属原创作品, 原作品文档和作品规原作者所有. 中文版权所有BeanSoft, 转载请注明作者: BeanSoft(beansoft@126.com), 2006年11月25日.

**** 

**xloadtree.html**:  
(2006-05-28) Changed license to Apache Software License 2.0.  
(2003-05-06) Added target attribute support  
(2002-10-10) Added reload method 

(2006-05-28) 更改许可证为 Apache Software License 2.0.  
(2003-05-06) 添加对 target 属性的支持  
(2002-10-10) 添加 reload 方法 

#### Introduction 介绍</p> 

About a year ago Emil visited me while I was living in USA and he came up with a brilliant idea for a next generation DHTML tree. After some discussions about this it took shape and in the end it turned out to be one of the best DHTML tree scripts I&#8217;ve ever seen. 

大概一年之前我还住在美国的时候 Emil 造访了我, 他带来了一个很炫的关于下一代的 DHTML 树组件的想法. 经过了一番讨论之后, 这个想法成型了, 最后它被证明是一个我所见过的最棒的 DHTML 树组件脚本. 

Since the original <a>xTree</a> script is implemented using Object Oriented JS it is very easy to extend and as soon as it started to take shape we got some wild ideas on how one could extend the tree. One idea that Emil implemented in the original tree was to add support for persistance. Another idea I had some time later was to allow subtrees to be loaded and populated at runtime. For this to work the <a>xTree</a> had to be updated a little to support data model changes at runtime. Emil added support for this after a while and now nothing was in my way to add the dynamic loading support. 

既然原来的 <a>xTree</a> 脚本是做作为面向对象的 JS 实现的, 所以它很容易的进行扩展, 当它刚刚成型的时候, 我们就有一些关于如何扩展它的疯狂的想法.其中的一个想法就是 Emil 对原来的树添加了持久化的实现. 另一个之后不久我提出的想法是允许运行的时候加载和填充子树. 对此 <a>xTree</a> 必须有点小小的更新来支持运行时候的数据模型的改变. 后来 Emil 对此添加了支持, 现在我所做的不过就是添加了动态加载的支持. 

译者注: 其实用的就是现在炒的很热的 AJAX 技术, 通过 XMLHttpRequest 读取内容, 通过 DOM 来解析 XML 内容. 

##### Dynamic loading 动态加载</p> 

The XLoadTree is an extended version of the <a>xTree</a> and it allows you to define a source property for each tree item that points to an xml file that is then loaded, transformed using DOM and inserted using tree item methods. The basic mechanism for this has been working for a long time but since I wanted to cover the <a>xml loading mechanisms</a> before writing this article it is not until now that I can publish this. 

LoadTree 是 <a>xTree</a> 的扩展版本, 它让你可以对每个树的节点定义一个 source 属性, 这个属性指向一个 xml 文件, 然后它可以被载入, 使用 DOM 转换, 插入, 这些都可以用树节点的方法来做. 相关的底层的机制已经使用了很长时间了, 因此我想在 <a>xml 加载机制</a> 中介绍它, 这个文章在我写本文之前都已经发表了. 

##### Known Issues 已知的问题</p> 

The persistance from the original <a>xTree</a> is not sophisticated enough for dynamic loaded trees because the original persistance is dependent on the order of insertion and not the path. I will try to fix this in a later update. 

原来的 <a>xTree</a> 中的持久化机制对动态加载的树来说并不是十分灵活, 因为它依赖于树的插入顺序而不是路径. 我将尝试在后一更新版本中修正这个问题. 

The xml object has some issues when using the file protocol (in IE) so this one only works when located on a web server. I&#8217;ll see what can be done about this. 

使用 file 协议的时候(在 IE中), xml 对象会有一些问题, 所以这个脚本将只能在服务器上加载的时候才能运行. 我将找找看怎么搞定这个问题. 

译者注:就是说在本机执行的时候, 在 Firefox, Opera, Mozilla 浏览器中, 使用 file 协议工作的很好, 但是 IE 浏览器下会弹出一个空的消息框, 无法载入子节点. 

<a>介绍</a>  
<a>使用说明</a>  
<a>API</a>  
<a>实现</a>  
<a>演示</a>  
[下载](http://webfx.eae.net/download/xloadtree111.zip) 

作者: Erik Arvidsson  
中文翻译: [BeanSoft](mailto:beansoft@126.com)  
**usage.html  
** 

#### Usage 用法</p> 

The usage of the XLoadTree is almost identical to the xTree so if you do not remember how that is done take a look at the <a>xTree usage</a>. Anywhere the original xTree accepts a `WebFXTree` you can use a `WebFXLoadTree` and the same applies to `WebFXTreeItem` and`WebFXLoadTreeItem`. 

XLoadTree 的用法几乎和 xTree 相同, 所以您记不得如何做的时候不要忘了看一下 <a>xTree 用法. </a>任何原来的 `WebFXTree` 可以使用 xTree 的地方都可以使用 `WebFXLoadTree`, 这个规则也同样适用于`WebFXTreeItem` 和 `WebFXLoadTreeItem`. 

Taking the first example in the xTree usage and instead of using a `WebFXTreeItem` for the second tree item we use the load counterpart. 

让我们看看第一个 xTree 用法的例子, 注意我们在第二个树节点的地方使用了对应的可载入树节点代替了 `WebFXTreeItem`.

<pre>var tree = new WebFXTree("Root");tree.add(new WebFXTreeItem("Tree Item 1"));<strong>tree.add(new WebFXLoadTreeItem("Tree Item 2", "tree.xml"));</strong>tree.add(new WebFXTreeItem("Tree Item 3"));document.write(tree);</pre></p> 

The code above should result in something looking like this: 

上面的代码将会产生如下结果: 


![](http://www.blogjava.net/images/blogjava_net/beansoft/17589/o_tree1.png) 

When Tree Item 2 is expanded the file <a>tree.xml</a> is loaded and during the load a dummy tree item is inserted to show that the subcontent is loading. This looks something like this: 

当 Tree Item 2 被展开的时候文件 <a>tree.xml</a> 被载入, 在加载的时候插入一个临时的树节点来显示子节点正在被载入中. 看起来就像这样: 

![](http://www.blogjava.net/images/blogjava_net/beansoft/17589/o_tree2.png)

##### The XML format XML 文件格式</p> 

To be able to transform the xml file to an xTree the xml file must be of a certain format. Below is the xml code from the file <a>tree.xml</a>: 

要想从 xml 文件转换成 xTree, xml 文件必须符合一个固定的格式. 下面是文件 <a>tree.xml</a> 中的 xml 代码:

<pre>&lt;tree&gt;&lt;/tree&gt;   &lt;tree action="href://webfx.eae.net" text="Loaded Item 1"&gt;&lt;/tree&gt;   &lt;tree text="Loaded Item 2"&gt;&lt;/tree&gt;      &lt;tree action="javascript:alert(2.1)" text="Loaded Item 2.1"&gt;&lt;/tree&gt;      &lt;tree text="Load &amp;quot;tree1.xml&quot;" src="tree1.xml"&gt;&lt;/tree&gt;      &lt;tree text="Loaded Item 3"&gt;&lt;/tree&gt;</pre></p> 

When this xml file has been loaded and inserted into the tree it looks something like this: 

当这个 xml 文件加载并且插入到树中后它看起来就像这样: 


![](http://www.blogjava.net/images/blogjava_net/beansoft/17589/o_tree3.png) 

Notice how the XML structure can contain nested tree items and tree items that points to other xml files. Notice also the top level tree item that is used to contain all the tree items that are supposed to be inserted into the current `WebFXLoadTreeItem`. 

注意 XML 的结构, 它可以包含嵌套的子节点以及指向其它xml文件的子节点. 也请留意最顶端的树节点被用来包含所有的假定为要插入当前`WebFXLoadTreeItem`的所有子节点. 

To see what xml attributes are supported on the tree items see the <a>api</a> page. 

要了解树节点支持什么样的 xml 属性, 请浏览 <a>api</a> 页. 

<a>介绍</a>  
<a>使用说明</a>  
<a>API</a>  
<a>实现</a>  
<a>演示</a>  
[下载](http://webfx.eae.net/download/xloadtree111.zip) 

作者: Erik Arvidsson  
中文翻译: [BeanSoft](mailto:beansoft@126.com)  
**api.html  
** 

#### WebFXLoadTree</p> 

This object type is used to create the actual tree root and can be used to populate the tree with tree items loaded from an xml file. 

这个对象类型用来创建实际的树的根节点, 并且可以被用来向树添加从一个 xml 文件中定义的树节点. 

The `WebFXLoadTree` extends `WebFXTree` (see the <a>xTree API</a>) so all properties and methods provided by `WebFXTree` are available. 

`WebFXLoadTree` 继承自 `WebFXTree` (请阅读 <a>xTree API</a>) , 因此`WebFXTree`提供的所有的属性和方法都可用.

##### Constructor 构造器

<pre>new WebFXLoadTree(sText, sXmlSrc, sAction, sBehavior, sIcon, sOpenIcon)</pre></p> 

Name  
名称  
Description  
描述 

sText  
The text label for the tree root.  
树的根节点的文本标签. 

sXmlSrc  
The source for the xml file to load when expanded.  
当展开时要加载的xml文件的源路径. 

sAction  
Optional. The action (uri) associated with the tree root.  
可选. 根节点关联的操作(uri地址). 

sBehavior  
Optional. The behavior of the tree. Valid values are `"classic"` and `"explorer"`. When the value is set to `"explorer"` the default icon for an empty item is the same as the folder icon.  
可选. 树的表现方式. 可用的值包括 `"classic"` 和`"explorer". 当值为 "explorer" 时空节点默认的图标和文件夹图标一样.` 

sIcon  
Optional. The icon image to use for this item. In case this item is a folder this will be used when the folder is closed.  
可选. 节点所使用的图标文件. 如果这个节点是个`文件夹`, 这个值将在节点被关闭的时候使用. 

sOpenIcon  
Optional. The icon image to use for this item when it is opened. This is only used for folder items that are opened/expanded.  
可选. 节点打开时使用的图标文件. 这个值仅仅对文件夹节点被打开或者展开的时候有效.

##### Properties 属性</p> 

Name  
名称  
Description  
描述 

All properties from `WebFXTree`.  
`WebFXTree` 的所有属性. 

src  
The source to the xml file that decribes the sub trees. Notice that this is read-only after the xml file has started to load so any changes done to the source are only valid before the loading of the first file.  
描述子树的xml文件的源路径. 注意这个值将在 xml 文件开始载入后变为只读, 所以任何对这个值的修改只在第一个文件载入之前生效. 

loading  
Read only. A boolean flag which is true if the xml file has started loading and not yet finished.  
只读. 布尔变量, xml 文件开始加载但是尚未加载完的时候为 true. 

loaded  
Read only. A boolean flag which is true if the xml file has been loaded.  
只读. 布尔变量, xml 文件加载完成的时候为 true. 

errorText  
Read only String. If the loading for any reason failed the reason can be found in the`errorText` property. If no error occured this is `""` (an empty string).  
只读字符串. 如果加载因为任何原因失败, 这个原因可以在 errorText 属性中找到. 如果没有错误它的值时 &#8220;&#8221;(空字符串).

##### Methods 方法</p> 

Name  
名称  
Description  
描述 

reload()  
Reloads the XML file from the server and recreates the children of this node.  
重新从服务器载入 XML 文件, 并重建这个节点的子节点. 

All methods from `WebFXTree`. 所有继承自 `WebFXTree` 的方法.

#### WebFXLoadTreeItem</p> 

This object type is used to create tree items that can be added to the tree root, or to other tree items to create sub folders in the tree. When an `WebFXLoadTreeItem` is expanded an xml file is loaded that is then used to populate the item with child items. 

这个对象类型用来创建可以加入树根节点的树节点, 或者可以作为子目录添加到别的树节点. 当一个 `WebFXLoadTreeItem` 节点被展开的时候, 将会加载用于填充子节点的 xml 文件. 

The `WebFXLoadTreeItem` extends `WebFXTreeItem` (see the <a>xTree API</a>) so all properties and methods provided by `WebFXTreeItem` are available. 

`WebFXLoadTreeItem` 继承自 `WebFXTreeItem` (请查看 <a>xTree API</a>), 因此`WebFXTreeItem`提供的所有的属性和方法都可用.

##### Constructor 构造器

<pre>new WebFXLoadTreeItem(sText, sXmlSrc, sAction, eParent, sIcon, sOpenIcon)</pre></p> 

Name  
名称  
Description  
描述 

sText  
The text label for the tree item.  
树节点的文本标签. 

sXmlSrc  
The source for the xml file to load when expanded.  
当展开时要加载的xml文件的源路径. 

sAction  
Optional. The action (uri) associated with the tree item.  
可选. 节点关联的操作(uri地址). 

eParent  
Optional. The parent `WebFXTreeItem` or `WebFXTree` that the item should be added to.  
可选. 当前节点要添加进去的父节点, 可以为 `WebFXTreeItem` 或者 `WebFXTree`. 

sIcon  
Optional. The icon image to use for this item. In case this item is a folder this will be used when the folder is closed.  
可选. 节点所使用的图标文件. 如果这个节点是个文件夹, 这个值将在节点被关闭的时候使用. 

sOpenIcon  
Optional. The icon image to use for this item when it is opened. This is only used for folder items that are opened/expanded.  
可选. 节点打开时使用的图标文件. 这个值仅仅对文件夹节点被打开或者展开的时候有效.

##### Properties 属性</p> 

Name  
名称  
Description  
描述 

All properties from `WebFXTreeItem`. 继承自 `WebFXTreeItem` 的所有属性. 

src  
The source to the xml file that decribes the sub trees. Notice that this is read-only after the xml file has started to load so any changes done to the source are only valid before the loading of the first file.  
描述子树的xml文件的源路径. 注意这个值将在 xml 文件开始载入后变为只读, 所以任何对这个值的修改只在第一个文件载入之前生效. 

loading  
Read only. A boolean flag which is true if the xml file has started loading and not yet finished.  
只读. 布尔变量, xml 文件开始加载但是尚未加载完的时候为 true. 

loaded  
Read only. A boolean flag which is true if the xml file has been loaded.  
只读. 布尔变量, xml 文件加载完成的时候为 true. 

errorText  
Read only String. If the loading for any reason failed the reason can be found in the`errorText` property. If no error occured this is `""` (an empty string).  
只读字符串. 如果加载因为任何原因失败, 这个原因可以在 errorText 属性中找到. 如果没有错误它的值时 &#8220;&#8221;(空字符串).

##### Methods 方法</p> 

Name  
Description 

reload()  
Reloads the XML file from the server and recreates the children of this node.  
重新从服务器载入 XML 文件, 并重建这个节点的子节点. 

All methods from `WebFXTree`. 所有继承自 `WebFXTree` 的方法.

#### The xml format xml 格式</p> 

The only valid element in the xml file is the `tree` item. A `tree` item can contain zero, one or more`tree` items. 

xml 文件中唯一有效的元素就是 `tree` 节点. 一个`tree`节点可以包含零个,一个或者更多tree节点.

##### Attributes 属性</p> 

There are five valid attributes that you can provide on a `tree` item. 

您可以为一个 `tree` 节点提供 5 个有效的属性. 

Name  
名称  
Description  
描述 

text  
Required. The text label for the tree item.  
必需. 树节点的文本标签. 

xmlSrc  
Optional. The source for the xml file to load when expanded.  
可选. 当展开时要加载的xml文件的源路径. 

action  
Optional. The action (uri) associated with the tree item.  
可选. 节点关联的操作(uri地址). 

icon  
Optional. The icon image to use for this item. In case this item is a folder this will be used when the folder is closed.  
可选. 节点所使用的图标文件. 如果这个节点是个文件夹, 这个值将在节点被关闭的时候使用. 

openIcon  
Optional. The icon image to use for this item when it is opened. This is only used for folder items that are opened/expanded.  
可选. 节点打开时使用的图标文件. 这个值仅仅对文件夹节点被打开或者展开的时候有效.

##### DTD</p> 

The xml file does not have to be valid to work (only well formed) but if you want to ensure that you didn&#8217;t do anything wrong you can use the <a>following document type definition</a>: 

xml 文件并不必须是有效的格式才能工作(只需要良好的组织起来), 但是如果你想确保你没有写错, 可以使用下面的<a>文档类型定义</a>:

<pre></pre></p> 

To use the dtd in your xml file add a `DOCTYPE` to the head of your xml file. Below is <a>tree.dtd.xml</a>shown. This represents the same xml tree as in <a>tree.xml</a> with a `DOCTYPE` declaration. 

在你的 xml 文件中使用这个 dtd 请在文件的开头包含一个 `DOCTYPE`. 下面显示的是 <a>tree.dtd.xml</a> . 这个表示了和 <a>tree.xml</a> 中相同的 xml 树, 只不过有一个 `DOCTYPE` 声明.

<pre>&lt;tree&gt;&lt;/tree&gt;	&lt;tree action="href://webfx.eae.net" text="Loaded Item 1"&gt;&lt;/tree&gt;	&lt;tree text="Loaded Item 2"&gt;&lt;/tree&gt;		&lt;tree action="javascript:alert(2.1)" text="Loaded Item 2.1"&gt;&lt;/tree&gt;		&lt;tree text="Load &amp;quot;tree1.xml&quot;" src="tree1.xml"&gt;&lt;/tree&gt;</pre></p> 

<a>介绍</a>  
<a>使用说明</a>  
<a>API</a>  
<a>实现</a>  
<a>演示</a>  
[下载](http://webfx.eae.net/download/xloadtree111.zip) 

作者: Erik Arvidsson  
中文翻译: [BeanSoft](mailto:beansoft@126.com)

#### Implementation 实现</p> 

The main idea is to create sub classes to `WebFXTree` and `WebFXTreeItem` and overload the`expand` methods to start the loading of an xml file. Once the loading is done the xml file is tranformed into `WebFXTreeItem`s and `WebFXLoadTreeItem`s and inserted. 

主要的思路就是创建 `WebFXTree` 和 `WebFXTreeItem` 的子类, 并且重载 `expand` 方法来启动加载 xml 文件的过程. 一旦加载结束, xml 文件被转换成 `WebFXTreeItem`s 和`WebFXLoadTreeItem`s, 然后添加到树上. 

译者注: 这里就是面向对象的好处了, 我也用重载或者添加新方法的思路实现了动态添加子节点, 添加失败则回复到原来状态, 成功则加入新的子节点.

#### WebFXLoadTree</p> 

First we create a new constructor and inside this we call the super constructor to make sure that the instance will be correctly initiated. After that we set some property values and finally we check whether the tree is open, if it is we start to load the sub trees. If not, we add a dummy tree item that displays the loading text. 

首先我们创建了一个新的构造器, 在这个方法里面我们首先调用父类的构造器来确保每个实例可以被正确的初始化. 在此之后我们设置一些属性值, 最后我们检查树是否已经被打开, 如果这样的话我们就开始加载树的子节点. 反之, 我们向树节点中添加一个临时的显示正在加载文本的树节点. 

After the constructor is created we set the protype to a new `WebFXTree`.

<pre>function WebFXLoadTree(sText, sXmlSrc, sAction, sBehavior, sIcon, sOpenIcon) {   // call super   this.WebFXTree = WebFXTree;   this.WebFXTree(sText, sAction, sBehavior, sIcon, sOpenIcon);   // setup default property values   this.src = sXmlSrc;   this.loading = false;   this.loaded = false;   this.errorText = "";   // check start state and load if open   if (this.open)      _startLoadXmlTree(this.src, this);   else {      // and create loading item if not      this._loadingItem = new WebFXTreeItem(webFXTreeConfig.loadingText);      this.add(this._loadingItem);   }}WebFXLoadTree.prototype = new WebFXTree;</pre></p> 

The constructor is fairly straight forward and does not do much. Notice however how super is called by binding `WebFXTree` as a method and then calling it. 

这个构造器是相当的直接, 并没有做太多事. 尽管如此请注意我们是如何将父类绑定为了一个方法然后调用它的. 

Next we need to override the `expand` method but since we still need to be able to call the original`expand` method we create a new method called `_webfxtree_expand` that points to the function object used by `WebFXTree` objects. This is the standard way to access super methods but the first few times it might look a bit odd. 

现在我们需要重载 `expand` 方法, 但是我们依然需要调用原来的 `expand` 方法, 因此我们创建了一个新方法`_webfxtree_expand`来指向`WebFXTree`的原来的那个 expand 方法对象. 这是个标准的调用父类的方法, 但是最初的几次看起来似乎是有点多余. 

The logic in the `expand` method is really simple. We just check if we should start loading the xml file and then we expand it using the super expand (`_webfxtree_expand`) method. 

`expand` 方法的逻辑是相当的简单. 我们只是检查是否应该开始载入 xml 文件, 然后使用父类的expand方法(`_webfxtree_expand`)来展开它.

<pre>// override the expand method to load the xml fileWebFXLoadTree.prototype._webfxtree_expand = WebFXTree.prototype.expand;WebFXLoadTree.prototype.expand = function() {   if (!this.loaded && !this.loading) {      // load      _startLoadXmlTree(this.src, this);   }   this._webfxtree_expand();};</pre>

#### WebFXLoadTreeItem</p> 

This class is too similar to `WebFXLoadTree` for me to be entirely comfortable. Since JavaScript does not support multiple inheritance, and I did not want to fake it using expandos, we just have to repeat the code. For everyone that are interested, the code for this can be found in <a>xloadtree.js</a>. 

这个类和`WebFXLoadTree`太相似了, 对我来说是完全的相同. 因为 JavaScript 不提供多重继承, 我也不想使用 expandos 来欺骗它, 我们只是不得不重复代码. 如果您对此感兴趣, 这些代码可以在<a>xloadtree.js</a> 中找到.

#### Loading the Tree 载入树</p> 

As you can see in the code above there is a function called `_startLoadXmlTree` that is called to load the actual xml file. This function uses an `XmlHttp` object to do the actual loading. The loading of the xml file is done asynchronously to prevent the UI to lock up while the file is being loaded and therefore we wait for the `onreadystatechange` event to fire before we continue. See the <a>Xml Extras article</a> for a more detailed description about the `XmlHttp` object. 

你可以看到上面已经有了个方法叫 `_startLoadXmlTree`, 它将被用来加载实际的 xml 文件. 这个方法使用了严格 `XmlHttp` 对象来执行真正的加载. 对 xml 文件的载入使用了异步方式来防止文件正在读取的时候 UI 被锁定, 因此我们等待 `onreadystatechange`事件被触发之后才继续进行. 请阅读 <a>Xml 增强文章 </a>来了解关于 `XmlHttp` 对象的更多信息.

<pre>// creates the xmlhttp object and starts the load of the xml documentfunction _startLoadXmlTree(sSrc, jsNode) {   jsNode.loading = true;   var xmlHttp = XmlHttp.create();   xmlHttp.open("GET", sSrc, true);	// async   xmlHttp.onreadystatechange = function () {      if (xmlHttp.readyState == 4)         _xmlFileLoaded(xmlHttp.responseXML, jsNode);   };   // call in new thread to allow ui to update   window.setTimeout(function () {      xmlHttp.send(null);   }, 10);}</pre></p> 

Once the xml file has finished loading we call the function `_xmlFileLoaded`. This function checks that we got an xml document back and if we did it goes through the document and recursively converts the xml elements to js `WebFXTreeItem` and inserts them. Once the xml elements have been converted and inserted we remove the dummy tree item that was only used to show that we were loading the contents. 

一旦 xml 文件加载完毕, 我们调用方法 `_xmlFileLoaded`. 这个方法检查我们得到的 xml 文件, 如果得到了文件内容我们将递归转换 xml 元素到 js 的 `WebFXTreeItem` 对象, 然后添加他们. 一旦 xml 元素转换并添加完毕, 我们将删除那个临时的只不过是用来显示正在加载内容的树节点.

<pre>// Inserts an xml document as a subtree to the provided nodefunction _xmlFileLoaded(oXmlDoc, jsParentNode) {   var bIndent = false;   var bAnyChildren = false;   jsParentNode.loaded = true;   jsParentNode.loading = false;   // check that the load of the xml file went well   if( oXmlDoc == null || oXmlDoc.documentElement == null) {      jsParentNode.errorText = parseTemplateString(webFXTreeConfig.loadErrorTextTemplate,                                                   jsParentNode.src);   }   else {      // there is one extra level of tree elements      var root = oXmlDoc.documentElement;      // loop through all tree children      var cs = root.childNodes;      var l = cs.length;      for (var i = 0; i &lt; l; i++) {         if (cs[i].tagName == "tree") {            bAnyChildren = true;            bIndent = true;            jsParentNode.add( _xmlTreeToJsTree(cs[i]), true);         }      }      // if no children we got an error      if (!bAnyChildren)         jsParentNode.errorText = parseTemplateString(webFXTreeConfig.emptyErrorTextTemplate,                                                      jsParentNode.src);   }   // remove dummy   if (jsParentNode._loadingItem != null) {      jsParentNode._loadingItem.remove();      bIndent = true;   }   if (bIndent) {      // indent now that all items are added      jsParentNode.indent();   }   // show error in status bar   if (jsParentNode.errorText != "")      window.status = jsParentNode.errorText;}</pre></p> 

A few more things happen in this function but nothing really important. There is some code that checks the errors and a few properties are set to reflect the state of the `WebFXLoadTree` or`WebFXLoadTreeItem` object. 

其它一些这个方法中发生更多的事情并不是很重要. 有一些代码来检查错误, 一些属性被设置, 来显示 `WebFXLoadTree` 和 `WebFXLoadTreeItem` 的状态.

#### Converting the Xml 转换 Xml</p> 

The only important thing left to do is to convert the xml tree item to a js `WebFXTreeItem`. This is done in the function `_xmlTreeToJsTree`. Here we retreive the xml attributes and if there was a`src` attribute defined we create a new `WebFXLoadTreeItem` and otherwise a`WebFXTreeItem`. Once that is created we go through all the `childNodes` of the xml node and convert and add those as well. 

剩下的唯一要做的重要的事情就是转换 xml 树节点为 js `WebFXTreeItem` 对象. 这在方法`_xmlTreeToJsTree` 中完成. 在这里读取 xml 属性值, 如果有 `src` 属性我们就创建一个`WebFXLoadTreeItem` 对象, 否则就创建 `WebFXTreeItem`. 一旦创建完成, 我们就遍历所有 xml 节点的 `childNodes`, 转换并添加他们.

<pre>// Converts an xml tree to a js tree. See article about xml tree formatfunction _xmlTreeToJsTree(oNode) {	// retreive attributes   var text = oNode.getAttribute("text");   var action = oNode.getAttribute("action");   var parent = null;   var icon = oNode.getAttribute("icon");   var openIcon = oNode.getAttribute("openIcon");   var src = oNode.getAttribute("src");   // create jsNode   var jsNode;   if (src != null && src != "")      jsNode = new WebFXLoadTreeItem(text, src, action, parent, icon, openIcon);   else      jsNode = new WebFXTreeItem(text, action, parent, icon, openIcon);   // go through childNOdes   var cs = oNode.childNodes;   var l = cs.length;   for (var i = 0; i &lt; l; i++) {      if (cs[i].tagName == "tree")         jsNode.add( _xmlTreeToJsTree(cs[i]), true );   }   return jsNode;}

<p>
  <a>介绍</a><br /><a>使用说明</a><br /><a>API</a><br /><a>实现</a><br /><a>演示</a><br /><a href="http://webfx.eae.net/download/xloadtree111.zip">下载</a>
</p>

<p>
  作者: Erik Arvidsson<br />中文翻译: <a href="mailto:beansoft@126.com">BeanSoft</a>
</p></pre></p> 

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [XLoadTree 基于AJAX + XML动态加载的JS树组件的文档翻译[整理]](http://www.beansoft.biz/2010/08/25/xloadtree-%e5%9f%ba%e4%ba%8eajax-xml%e5%8a%a8%e6%80%81%e5%8a%a0%e8%bd%bd%e7%9a%84js%e6%a0%91%e7%bb%84%e4%bb%b6%e7%9a%84%e6%96%87%e6%a1%a3%e7%bf%bb%e8%af%91%e6%95%b4%e7%90%86/)