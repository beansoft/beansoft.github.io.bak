---
id: 1804
title: 使用 HibernateTemplate 实现分页查询
date: 2011-02-25T19:06:27+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1804
permalink: '/2011/02/25/%e4%bd%bf%e7%94%a8-hibernatetemplate-%e5%ae%9e%e7%8e%b0%e5%88%86%e9%a1%b5%e6%9f%a5%e8%af%a2/'
views:
  - "5556"
original_post_id:
  - "1804"
categories:
  - Spring
---
最近有同学做项目的时候发现 Spring 整合 Hibernate 时候用的 HibernateTemplate 不支持分页, 上网搜了搜找到结果并测试成功, 只需要用下面的方法就能分页:

<div>
  <pre style="font-size:8pt;overflow:visible;width:100%;color:black;line-height:12pt;font-family:consolas, &#039;background-color:#f4f4f4;border-style:none;margin:0;padding:0;"><span style="color:#008000;">/**</span>
<span style="color:#008000;">* 使用hql 语句进行操作</span>
<span style="color:#008000;">* @param hql HSQL 查询语句</span>
<span style="color:#008000;">* @param offset 开始取数据的下标</span>
<span style="color:#008000;">* @param length 读取数据记录数</span>
<span style="color:#008000;">* @return List 结果集</span>
<span style="color:#008000;">*/</span>
<span style="color:#0000ff;">public</span> List getListForPage(final String hql, final <span style="color:#0000ff;">int</span> offset,
 final <span style="color:#0000ff;">int</span> length) {

List list = getHibernateTemplate().executeFind(<span style="color:#0000ff;">new</span> HibernateCallback() {
 <span style="color:#0000ff;">public</span> Object doInHibernate(Session session)
 throws HibernateException, SQLException {
 Query query = session.createQuery(hql);
 query.setFirstResult(offset);
 query.setMaxResults(length);
 List list = query.list();
 <span style="color:#0000ff;">return</span> list;
 }
});
<span style="color:#0000ff;">return</span> list;
}</pre>
</div>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [使用 HibernateTemplate 实现分页查询](http://www.beansoft.biz/2011/02/25/%e4%bd%bf%e7%94%a8-hibernatetemplate-%e5%ae%9e%e7%8e%b0%e5%88%86%e9%a1%b5%e6%9f%a5%e8%af%a2/)