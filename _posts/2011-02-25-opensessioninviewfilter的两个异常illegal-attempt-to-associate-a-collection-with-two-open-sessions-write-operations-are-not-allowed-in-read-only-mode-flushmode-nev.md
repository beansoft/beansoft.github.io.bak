---
id: 1806
title: OpenSessionInViewFilter的两个异常:Illegal attempt to associate a collection with two open sessions; Write operations are not allowed in read-only mode (FlushMode.NEVER/MANUAL)
date: 2011-02-25T19:09:49+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1806
permalink: '/2011/02/25/opensessioninviewfilter%e7%9a%84%e4%b8%a4%e4%b8%aa%e5%bc%82%e5%b8%b8illegal-attempt-to-associate-a-collection-with-two-open-sessions-write-operations-are-not-allowed-in-read-only-mode-flushmode-nev/'
views:
  - "8431"
original_post_id:
  - "1806"
categories:
  - Spring
---
使用 Spring 整合 Hibernate, 在懒加载的情况下, 有时候需要在 JSP/View 层显示数据, 这时候就要用到Spring内置的: OpenSessionInViewFilter, 一般来说配置如下(web.xml):

<div>
  <pre style="font-size:8pt;overflow:visible;width:100%;color:black;line-height:12pt;font-family:consolas, &#039;background-color:#f4f4f4;border-style:none;margin:0;padding:0;">						<span style="color:#0000ff;">&lt;</span>
						<span style="color:#800000;">filter</span>
						<span style="color:#0000ff;">&gt;</span>
						<span style="color:#0000ff;">&lt;</span>
						<span style="color:#800000;">filter-name</span>
						<span style="color:#0000ff;">&gt;</span>hibernateFilter<span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">filter-name</span><span style="color:#0000ff;">&gt;</span><span style="color:#0000ff;">&lt;</span><span style="color:#800000;">filter-class</span><span style="color:#0000ff;">&gt;</span>
        org.springframework.orm.hibernate3.support.OpenSessionInViewFilter
    <span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">filter-class</span><span style="color:#0000ff;">&gt;</span><span style="color:#0000ff;">&lt;</span><span style="color:#800000;">init-param</span><span style="color:#0000ff;">&gt;</span><span style="color:#0000ff;">&lt;</span><span style="color:#800000;">param-name</span><span style="color:#0000ff;">&gt;</span>singleSession<span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">param-name</span><span style="color:#0000ff;">&gt;</span><span style="color:#0000ff;">&lt;</span><span style="color:#800000;">param-value</span><span style="color:#0000ff;">&gt;</span>true<span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">param-value</span><span style="color:#0000ff;">&gt;</span><span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">init-param</span><span style="color:#0000ff;">&gt;</span><span style="color:#008000;">&lt;!-- 和 spring 中的sesssionfactory ID 一致 --&gt;</span><span style="color:#0000ff;">&lt;</span><span style="color:#800000;">init-param</span><span style="color:#0000ff;">&gt;</span><span style="color:#0000ff;">&lt;</span><span style="color:#800000;">param-name</span><span style="color:#0000ff;">&gt;</span>sessionFactoryBeanName<span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">param-name</span><span style="color:#0000ff;">&gt;</span><span style="color:#0000ff;">&lt;</span><span style="color:#800000;">param-value</span><span style="color:#0000ff;">&gt;</span>sessionFactory<span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">param-value</span><span style="color:#0000ff;">&gt;</span><span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">init-param</span><span style="color:#0000ff;">&gt;</span><span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">filter</span><span style="color:#0000ff;">&gt;</span><span style="color:#0000ff;">&lt;</span><span style="color:#800000;">filter-mapping</span><span style="color:#0000ff;">&gt;</span><span style="color:#0000ff;">&lt;</span><span style="color:#800000;">filter-name</span><span style="color:#0000ff;">&gt;</span>hibernateFilter<span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">filter-name</span><span style="color:#0000ff;">&gt;</span><span style="color:#0000ff;">&lt;</span><span style="color:#800000;">url-pattern</span><span style="color:#0000ff;">&gt;</span>*.do<span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">url-pattern</span><span style="color:#0000ff;">&gt;&lt;!</span><span style="color:#800000;">--</span> *.<span style="color:#ff0000;">jsp</span>, *.<span style="color:#ff0000;">do</span><span style="color:#ff0000;">--</span><span style="color:#0000ff;">&gt;</span><span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">filter-mapping</span><span style="color:#0000ff;">&gt;</span></pre>
</div>

<div>
  不过, 这时候又会导致更新数据时抛出如下异常:
</div>

> <div>
>   Write operations are not allowed in read-only mode (FlushMode.NEVER/MANUAL): Turn your Session into FlushMode.COMMIT/AUTO or remove &#8216;readOnly&#8217; marker from transaction definition.
> </div>

这时候再去网上找解决方案, 会有人说: 把参数 singleSession改为false, 就行了. 不过, 改完后, 估计不久就会遇到另一个郁闷的异常:

> org.hibernate.HibernateException: Illegal attempt to associate a collection with two open sessions

这下完了, 两个方案都不行, 到底怎么办? 还好, 在[http://xuliangyong.javaeye.com/blog/144818](http://xuliangyong.javaeye.com/blog/144818 "http://xuliangyong.javaeye.com/blog/144818")的主页上, 给了一个方案, 就是改写 OpenSessionInViewFilter 的代码, 非常感谢, 下面给出的就是最终方案: 

web.xml 

<span style="color:#0000ff;"><</span> <span style="color:#800000;">filter-name</span> <span style="color:#0000ff;">></span>hibernateFilter<span style="color:#0000ff;"></</span><span style="color:#800000;">filter-name</span><span style="color:#0000ff;">></span>

<span style="color:#0000ff;"><</span> <span style="color:#800000;">filter-class</span> <span style="color:#0000ff;">></span> org.springframework.orm.hibernate3.support.OurOpenSessionInViewFilter <span style="color:#0000ff;"></</span><span style="color:#800000;">filter-class</span><span style="color:#0000ff;">></span>

OurOpenSessionInViewFilter.java 代码: 

<div>
  <pre style="font-size:8pt;overflow:visible;width:100%;color:black;line-height:12pt;font-family:consolas, &#039;background-color:#f4f4f4;border-style:none;margin:0;padding:0;">package org.springframework.orm.hibernate3.support;

import org.hibernate.*;

<span style="color:#008000;">/**</span><span style="color:#008000;"> * 单session模式下, 默认会发生无法提交的错误:</span><span style="color:#008000;"> * Write operations are not allowed in read-only mode (FlushMode.NEVER/MANUAL): Turn your Session into FlushMode.COMMIT/AUTO or remove 'readOnly' marker from transaction definition.</span><span style="color:#008000;"> * 需要设置FlushMode并刷新session.</span><span style="color:#008000;"> * 参考: http://xuliangyong.javaeye.com/blog/144818</span><span style="color:#008000;"> * @author 刘长炯</span><span style="color:#008000;"> */</span><span style="color:#0000ff;">public</span><span style="color:#0000ff;">class</span> OurOpenSessionInViewFilter extends OpenSessionInViewFilter {

    <span style="color:#0000ff;">public</span> OurOpenSessionInViewFilter() {
        super.setFlushMode(FlushMode.AUTO);
    }

    <span style="color:#0000ff;">protected</span><span style="color:#0000ff;">void</span> closeSession(Session session, SessionFactory sessionFactory) {
        session.flush();

        <span style="color:#0000ff;">try</span> {
            session.getTransaction().commit();
        } <span style="color:#0000ff;">catch</span> (HibernateException e) {
            <span style="color:#008000;">// TODO Auto-generated catch block</span><span style="color:#008000;">//e.printStackTrace();</span>
        }

        super.closeSession(session, sessionFactory);
    }
}</pre>
</div>

如果各位有更好的解决方案, 欢迎讨论哦!!!

题外话:

感觉 Spring + Hibernate 的健壮性还是不够啊! 容易抛异常, 这是事实, 也许这是开源软件的通病吧.

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [OpenSessionInViewFilter的两个异常:Illegal attempt to associate a collection with two open sessions; Write operations are not allowed in read-only mode (FlushMode.NEVER/MANUAL)](http://www.beansoft.biz/2011/02/25/opensessioninviewfilter%e7%9a%84%e4%b8%a4%e4%b8%aa%e5%bc%82%e5%b8%b8illegal-attempt-to-associate-a-collection-with-two-open-sessions-write-operations-are-not-allowed-in-read-only-mode-flushmode-nev/)