---
id: 2788
title: MapEasy 的北京地图 demo(本机运行)
date: 2007-02-06T14:52:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2788
permalink: '/2007/02/06/mapeasy-%e7%9a%84%e5%8c%97%e4%ba%ac%e5%9c%b0%e5%9b%be-demo%e6%9c%ac%e6%9c%ba%e8%bf%90%e8%a1%8c/'
views:
  - "2611"
categories:
  - OpenSource
tags:
  - GIS MapEasy 代码
---
地图版权归 中国地图出版社版权所有.

[mapapi0.4alpha\_beijing\_demo.zip](http://www.blogjava.net/Files/beansoft/mapapi0.4alpha_beijing_demo.zip) 1131KB

在线展示: <http://www.beansoft.biz/doc/mapeasy/demo1_beijing.shtml>

下载后本机运行, 只有一级缩放.

图片切片大小: 500&#215;500 每片

代码:

&nbsp;

<SCRIPT LANGUAGE=&#8221;JavaScript&#8221;>
  
<!&#8211;

/**
  
* 自定义一个地图类型
  
*/
  
function NewMapType() {

MapType.apply(this);

this.getSrc = function(level, row, column) {
  
<span style="color: #0080ff;"><strong>if (row > 6 || column > 9) {<br /> return &#8220;&#8221;<br /> }<br /> return &#8220;./beijing/beijing&#8221; + (row + 1) + &#8220;-&#8221; + (column + 1) + &#8220;.jpg&#8221;;</strong></span>
  
}
  
}

MapModel.mapTypes = new Array(new NewMapType());

MapModel.bound = new Bound(-180e16, 180e16, -90e16, 90e16);
  
/*\* 第一个缩放等级的瓦片数 \*/
  
<span style="color: #0080ff;"><strong>MapModel.firstZoomTileNum = 64;</strong></span>
  
/*\* 每层缩放之间的比例参数 \*/
  
MapModel.scalePara = 1;
  
/*\* 瓦片尺寸 \*/
  
<span style="color: #0080ff;"><strong>MapModel.tileSize = 500;</strong></span>
  
/*\* 最大缩放比例 \*/
  
<span style="color: #0080ff;"><strong>MapModel.maxZoomLevel = 1;</strong></span>

var mapbuilder = new MapBuilder($(&#8220;map&#8221;));
  
mapbuilder.outputMap(new Point(0, 0), 1);
  
// 滑块工具
  
mapbuilder.addTool(MapBuilder.TOOL_SLIDERBAR);
  
// 地图类型工具
  
mapbuilder.addTool(MapBuilder.TOOL_MAPTYPE);
  
// 得到地图对象
  
var map = mapbuilder.getMap();

//&#8211;>
  
</SCRIPT>

&nbsp;

黑体的是我修改的代码, 判断边界, 返回图片地址, 以及定义单个瓦片大小.

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [MapEasy 的北京地图 demo(本机运行)](http://www.beansoft.biz/2007/02/06/mapeasy-%e7%9a%84%e5%8c%97%e4%ba%ac%e5%9c%b0%e5%9b%be-demo%e6%9c%ac%e6%9c%ba%e8%bf%90%e8%a1%8c/)