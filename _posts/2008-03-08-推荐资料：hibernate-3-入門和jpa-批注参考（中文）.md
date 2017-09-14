---
id: 253
title: 推荐资料：Hibernate 3 入門和JPA 批注参考（中文）
date: 2008-03-08T20:40:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=253
permalink: '/2008/03/08/%e6%8e%a8%e8%8d%90%e8%b5%84%e6%96%99%ef%bc%9ahibernate-3-%e5%85%a5%e9%96%80%e5%92%8cjpa-%e6%89%b9%e6%b3%a8%e5%8f%82%e8%80%83%ef%bc%88%e4%b8%ad%e6%96%87%ef%bc%89/'
views:
  - "4153"
original_post_id:
  - "253"
image: /wp-content/uploads/2012/09/linkext7.gif
categories:
  - Java EE
tags:
  - Hibernate JPA 批注
---
### Hibernate 3 入門和[JPA 批注参考（中文）](http://www.oracle.com/technology/global/cn/products/ias/toplink/jpa/resources/toplink-jpa-annotations.html)

**Hibernate 3 入門**

台湾 [良葛格](http://www.javaworld.com.tw/confluence/display/~caterpillar)&#160; ，比较详细，按照开发步骤讲解的Hibernate学习资料，个人觉得比那本中文版的Hibernate参考手册要有可操作性的多。地址：<http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3077>

内容一览：

Hibernate 是「物件/關係對應」（Object/Relational Mapping）的解決方案，簡寫為ORM，簡單的說就是將 Java 中的物件與物件關係，映射至關聯式資料庫中的表格與表格之間的關係， Hibernate 提供了這個過程中自動對應轉換的方案。 

2001年未 Hibernate 第一個版本發表，2003年6月8日 Hibernate 2 發表，並於年未獲得 Jolt 2004 大獎，後被 JBOSS 收納而成為其子項目之一，2005年3月 Hibernate 3 正式發表，當中有了一些重大的改變，這份文件將以之前 Hibernate 2 時撰寫的 [文件<sup><img height="7" alt="" src="http://www.javaworld.com.tw/confluence/images/icons/linkext7.gif" width="7" align="absMiddle" border="0" /></sup>](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=833) 為基礎，針對 Hibernate 3作重新整理的動作，所使用的版本為Hibernate 3.0。 

**<ins>基礎入門</ins>**   
從一個最基本的物件關係映射自動化程式，瞭解 Hibernate 組成的基本元素，並進一步瞭解 Hibernate 的基礎語義、配置等概念。 

  * O/R 映射入門   
    第一個 Hibernate 程式很簡單，將一個物件映射至一個資料表。 
      * [配置 Hibernate](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3084)
      * [第一個 Hibernate](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3090)
      * [第二個 Hibernate](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3094)

  * 基本配置   
    瞭解一下配置文件、映射文件中各種元素的意義，在進入物件關係映射的學習之前，這是必備的基本功夫。 
      * [配置文件](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3112)
      * [資料庫連結](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3114)
      * [簡介快取（Session Level）](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3115)
      * [簡介事務管理（基於 JDBC ）](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3116)
      * [映射文件](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3117)

  * 基本 API   
    瞭解一下 Hibernate 常使用的幾個類別之基本使用方式。 
      * [Session](http://www.javaworld.com.tw/confluence/display/opensrc/Session)
      * [Session 管理](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3120)
      * [Criteria 基本查詢](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3128)
      * [Criteria 進階查詢](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3129)
      * [DetchedCriteria](http://www.javaworld.com.tw/confluence/display/opensrc/DetchedCriteria)
      * [Query](http://www.javaworld.com.tw/confluence/display/opensrc/Query)

  * HQL（Hibernate Query Language）   
    這是 Hibernate 官方所推薦的查詢語言，接近 SQL 的語法，並提供更多的特性與封裝。 
      * [基本查詢](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3133)
      * [where、group by、order by 子句](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3134)
      * [更新、刪除](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3135)

  * SQL 支援   
    Hibernate 提供了對 SQL 的支援，並可以自行定義持久化方式。 
      * [建立 SQL 查詢](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3136)
      * [自定義 insert、update、delete](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3137)

  * 映射基礎議題   
    一邊是物件，一邊是資料表格，兩者在映射時有一些過渡的基礎議題必須瞭解。 
      * [實體物件生命週期](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3138)
      * [資料識別（Data Identity）](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3140)

**<ins>物件關聯映射（Object/Relational Mapping, ORM）</ins>**   
學習 Hibernate，大部份的時間都在瞭解如何實現映射，而從中您也可以瞭解到不少關聯式資料庫的表格設計方式。 

  * 實體映射   
    來看看一些進階的實體映射議題。 
      * [複合主鍵（一）](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3142)
      * [複合主鍵（二）](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3145)
      * [Blob、Clob](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3146)
      * [Component](http://www.javaworld.com.tw/confluence/display/opensrc/Component)
      * [動態模型（Dynamic Model）](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3150)

  * 繼承映射   
    在物件導向設計中，繼承關係是很常見的，但繼承與關聯式資料庫有著先天上的差異，繼承關係至表格的設計上有三種方式。 
      * [繼承 &#8211; Table per concrete class](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3152)
      * [繼承 &#8211; Table per class hierarchy](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3154)
      * [繼承 &#8211; Table per subclass](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3159)

  * 容器映射   
    容器常用來儲存物件，這邊來瞭解一下如何將容器的關係映射至表格。 
      * [Set](http://www.javaworld.com.tw/confluence/display/opensrc/Set)
      * [List](http://www.javaworld.com.tw/confluence/display/opensrc/List)
      * [Map](http://www.javaworld.com.tw/confluence/display/opensrc/Map)
      * [Bag](http://www.javaworld.com.tw/confluence/display/opensrc/Bag)
      * [內含 Component 的容器](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3178)
      * [容器的排序](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3180)
      * [容器的延遲初始（Lazy Initialization）](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3181)

  * 關係映射   
    來看看實體與實體之間的多對一、一對多、一對一、多對多如何與Java物件之間進行映射。 
      * [多對一](http://www.javaworld.
com.tw/confluence/pages/viewpage.action?pageId=3187)
      * [cascade 的意義](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3283)
      * [一對多](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3346)
      * [雙向關聯（inverse 的意義）](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3479)
      * [一對一（唯一外鍵關聯）](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3481)
      * [一對一（主鍵關聯）](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3524)
      * [多對多](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3526)

**<ins>進階特性</ins>**   
有關於Hibernate的快取、事務等進階特性的探討。 

  * 快取   
    二級快取可以跨越 Session 生命週期，Hibernate 透過第三方來實現二級快取，這邊也來看看 Query 的快取。 
      * [二級快取（Second-level）](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3576)
      * [Query 快取](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3606)
      * [Query.list、iterator](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3607)

  * Locking   
    Hibernate 透過兩種 Locking 機制來保證資料在操作過程中不會被干擾。 
      * [悲觀鎖定（Pessimistic Locking）](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3608)
      * [樂觀鎖定（Optimistic Locking）](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3609)

  * Validatable、Lifecycle、Interceptor   
    分別透過這三個介面，來進行資料驗證、於 CRUD（Create Retrieve Update Delete）作對應動作、欄截動作。 
      * [Lifecycle 介面、Validatable 介面](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3610)
      * [Interceptor 介面](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3611)

**<ins>工具</ins>**   
透過一些工具來自動生成映射文件或資料庫表格。 

  * [從映射文件生成資料表](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3612)
  * [從資料表生成映射文件](http://www.javaworld.com.tw/confluence/pages/viewpage.action?pageId=3613)

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [推荐资料：Hibernate 3 入門和JPA 批注参考（中文）](http://www.beansoft.biz/2008/03/08/%e6%8e%a8%e8%8d%90%e8%b5%84%e6%96%99%ef%bc%9ahibernate-3-%e5%85%a5%e9%96%80%e5%92%8cjpa-%e6%89%b9%e6%b3%a8%e5%8f%82%e8%80%83%ef%bc%88%e4%b8%ad%e6%96%87%ef%bc%89/)