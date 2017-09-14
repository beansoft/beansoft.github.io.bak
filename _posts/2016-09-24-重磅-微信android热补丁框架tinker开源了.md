---
id: 3853
title: '重磅: 微信Android热补丁框架Tinker开源了'
date: 2016-09-24T10:09:48+00:00
author: 刘长炯
excerpt: '重磅: 微信Android热补丁框架Tinker开源了'
layout: post
guid: http://www.beansoft.biz/?p=3853
permalink: '/2016/09/24/%e9%87%8d%e7%a3%85-%e5%be%ae%e4%bf%a1android%e7%83%ad%e8%a1%a5%e4%b8%81%e6%a1%86%e6%9e%b6tinker%e5%bc%80%e6%ba%90%e4%ba%86/'
views:
  - "1540"
categories:
  - Android
---
重磅: 微信Android热补丁框架Tinker开源了

https://github.com/Tencent/tinker/wiki

相关文章: 【Dev Club 分享第六期】微信热补丁 Tinker 的实践演进之路 

<http://dev.qq.com/topic/57ad7a70eaed47bb2699e68e></p> 

微信的方案很成熟稳定, 值得在项目中一试!

# Tinker &#8212; 微信Android热补丁方案

[![](http://www.beansoft.biz/wp-content/uploads/2016/09/d4a4821b6b46aacdd126e2b6880827e1.svg+xml)](http://git.code.oa.com/tinker/tinker/blob/master/LICENSE)

## <a name="user-content-tinker是什么" href="https://github.com/Tencent/tinker/wiki#tinker%E6%98%AF%E4%BB%80%E4%B9%88" />Tinker是什么

Tinker是微信官方的Android热补丁解决方案，它支持动态下发代码、So库以及资源，让应用能够在不需要重新安装的情况下实现更新。当然，你也可以使用Tinker来更新你的插件。

它主要包括以下几个部分：

  1. gradle编译插件: `tinker-patch-gradle-plugin`
  2. 核心sdk库: `tinker-android-lib`
  3. 非gradle编译用户的命名行版本: `tinker-patch-cli.jar`

## <a name="user-content-为什么使用tinker" href="https://github.com/Tencent/tinker/wiki#%E4%B8%BA%E4%BB%80%E4%B9%88%E4%BD%BF%E7%94%A8tinker" />为什么使用Tinker

市面的热补丁方案有很多，其中比较出名的有淘宝的Dexposed、支付宝的AndFix以及QZone的超级补丁方案。但它们都存在无法解决的问题，这也是正是我们推出Tinker的原因。

<table>
  <tr>
    <th />
    
    <th>
      Tinker
    </th>
    
    <th>
      QZone
    </th>
    
    <th>
      AndFix
    </th>
    
    <th>
      Dexposed
    </th>
  </tr>
  
  <tr>
    <td>
      类替换
    </td>
    
    <td>
      yes
    </td>
    
    <td>
      yes
    </td>
    
    <td>
      no
    </td>
    
    <td>
      no
    </td>
  </tr>
  
  <tr>
    <td>
      So替换
    </td>
    
    <td>
      yes
    </td>
    
    <td>
      no
    </td>
    
    <td>
      no
    </td>
    
    <td>
      no
    </td>
  </tr>
  
  <tr>
    <td>
      资源替换
    </td>
    
    <td>
      yes
    </td>
    
    <td>
      yes
    </td>
    
    <td>
      no
    </td>
    
    <td>
      no
    </td>
  </tr>
  
  <tr>
    <td>
      全平台支持
    </td>
    
    <td>
      yes
    </td>
    
    <td>
      yes
    </td>
    
    <td>
      yes
    </td>
    
    <td>
      no
    </td>
  </tr>
  
  <tr>
    <td>
      即时生效
    </td>
    
    <td>
      no
    </td>
    
    <td>
      no
    </td>
    
    <td>
      yes
    </td>
    
    <td>
      yes
    </td>
  </tr>
  
  <tr>
    <td>
      性能损耗
    </td>
    
    <td>
      较小
    </td>
    
    <td>
      较大
    </td>
    
    <td>
      较小
    </td>
    
    <td>
      较小
    </td>
  </tr>
  
  <tr>
    <td>
      补丁包大小
    </td>
    
    <td>
      较小
    </td>
    
    <td>
      较大
    </td>
    
    <td>
      一般
    </td>
    
    <td>
      一般
    </td>
  </tr>
  
  <tr>
    <td>
      开发透明
    </td>
    
    <td>
      yes
    </td>
    
    <td>
      yes
    </td>
    
    <td>
      no
    </td>
    
    <td>
      no
    </td>
  </tr>
  
  <tr>
    <td>
      复杂度
    </td>
    
    <td>
      较低
    </td>
    
    <td>
      较低
    </td>
    
    <td>
      复杂
    </td>
    
    <td>
      复杂
    </td>
  </tr>
  
  <tr>
    <td>
      gradle支持
    </td>
    
    <td>
      yes
    </td>
    
    <td>
      no
    </td>
    
    <td>
      no
    </td>
    
    <td>
      no
    </td>
  </tr>
  
  <tr>
    <td>
      接口文档
    </td>
    
    <td>
      丰富
    </td>
    
    <td>
      较少
    </td>
    
    <td>
      一般
    </td>
    
    <td>
      较少
    </td>
  </tr>
  
  <tr>
    <td>
      Rom体积
    </td>
    
    <td>
      Dalvik较大
    </td>
    
    <td>
      较小
    </td>
    
    <td>
      较小
    </td>
    
    <td>
      较小
    </td>
  </tr>
  
  <tr>
    <td>
      成功率
    </td>
    
    <td>
      较高
    </td>
    
    <td>
      最高
    </td>
    
    <td>
      一般
    </td>
    
    <td>
      一般
    </td>
  </tr>
</table>

**总的来说:**

  1. Dexposed无法支持全平台，并不适合应用到商业产品中。
  2. AndFix作为native解决方案，首先面临的是稳定性与兼容性问题，更重要的是它无法实现类替换，它是需要大量额外的开发成本的。
  3. QZone方案主要问题是插桩带来Dalvik的性能问题，以及为了解决Art下内存地址问题而导致补丁包急速增大的。

Tinker热补丁方案不仅支持类、So以及资源的替换，它还是2.X－7.X的全平台支持。它无需插桩，补丁大小也远远小于其他方案。Tinker已运行在微信的数亿Android设备上，那么为什么你不使用Tinker呢？

## <a name="user-content-如何使用tinker" href="https://github.com/Tencent/tinker/wiki#%E5%A6%82%E4%BD%95%E4%BD%BF%E7%94%A8tinker" />如何使用Tinker

  1. 如何快速接入请参考[Tinker 接入指南](https://github.com/Tencent/tinker/wiki/Tinker-%E6%8E%A5%E5%85%A5%E6%8C%87%E5%8D%97)。
  2. 如何自定义类请参考[Tinker 自定义扩展](https://github.com/Tencent/tinker/wiki/Tinker-%E8%87%AA%E5%AE%9A%E4%B9%89%E6%89%A9%E5%B1%95)。
  3. Tinker的API预览请参考[Tinker API预览](https://github.com/Tencent/tinker/wiki/Tinker-API%E6%A6%82%E8%A7%88)。
  4. 还要其他问题，请参考[常见问题](https://github.com/Tencent/tinker/wiki/Tinker-%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98)。

如有其他疑问，欢迎联系我们!

## <a name="user-content-tinker的todo" href="https://github.com/Tencent/tinker/wiki#tinker%E7%9A%84todo" />Tinker的TODO

Tinker经过几次全量上线，也发现了一些热补丁的问题。有以下的一些优化工作尚未完成：

  1. Keep dex apply插件:即保证编译补丁包时使用与基础包一样的分包方案，减少由于dex移动导致的变化；
  2. 资源全量Test，直接使用基础包的resources.arsc生成public.xml，无须applyResourceId；
  3. 假设利用补丁发布功能，即使分平台合成的dex也可能较大，这个时候可以在厂商OTA后增加启动过渡页；

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [重磅: 微信Android热补丁框架Tinker开源了](http://www.beansoft.biz/2016/09/24/%e9%87%8d%e7%a3%85-%e5%be%ae%e4%bf%a1android%e7%83%ad%e8%a1%a5%e4%b8%81%e6%a1%86%e6%9e%b6tinker%e5%bc%80%e6%ba%90%e4%ba%86/)