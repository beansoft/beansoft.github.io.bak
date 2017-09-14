---
id: 1805
title: Apache BeanUtils 妙用
date: 2011-02-25T19:08:13+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1805
permalink: '/2011/02/25/apache-beanutils-%e5%a6%99%e7%94%a8/'
views:
  - "4060"
original_post_id:
  - "1805"
categories:
  - Apache开源产品
---
1) 从 FormBean 复制值到 JavaBean 或者互相复制.   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; TdepartmentForm deptForm = (TdepartmentForm) form;   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; Tdepartment tdepartment = new Tdepartment();   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; BeanUtils.copyProperties(tdepartment, deptForm);   
2) 复制实体(实体一般是动态的代理类)为 ValueObject 防止原始实体的值被更新掉   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; Tproviderbill billVO = new Tproviderbill();   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; BeanUtils.copyProperties(billVO, dao.getBill(1));// 复制属性, 防止原实体被修改   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; if(billVO.xxx == xxx) {   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; billVO.setName(“aaaa”);   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; }   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; // 保存查询结果   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; request.setAttribute("bill", billVO); 

不过, 又有人指出 CGLIB 复制 Bean 速度更快, 效率更高(目前尚未做相关测试)! 

static BeanCopier copy = BeanCopier.create(Bean.class, Bean2.class, false); 

void beanCopies(Object source , Object target)｛   
&#160;&#160;&#160; copy.copy(source, target, null);   
}

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Apache BeanUtils 妙用](http://www.beansoft.biz/2011/02/25/apache-beanutils-%e5%a6%99%e7%94%a8/)