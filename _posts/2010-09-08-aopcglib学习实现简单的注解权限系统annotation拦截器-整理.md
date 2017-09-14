---
id: 681
title: 'AOP/CGLIB学习:实现简单的注解权限系统(Annotation+拦截器) [整理]'
date: 2010-09-08T22:36:02+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=681
permalink: '/2010/09/08/aopcglib%e5%ad%a6%e4%b9%a0%e5%ae%9e%e7%8e%b0%e7%ae%80%e5%8d%95%e7%9a%84%e6%b3%a8%e8%a7%a3%e6%9d%83%e9%99%90%e7%b3%bb%e7%bb%9fannotation%e6%8b%a6%e6%88%aa%e5%99%a8-%e6%95%b4%e7%90%86/'
views:
  - "4470"
original_post_id:
  - "681"
categories:
  - Spring
---
2008-12-22 作者: 刘长炯(<BeanSoft@126.com>)

注: 本文只是原理性质, 并不实用, 读者可用成熟稳定的开源权限系统如SpringSecurity. 但可参考实现自己的一些小框架. 

Spring 2.5最大的亮点就是基于注解实现配置, 其实这个谈不上什么亮点, EJB3/JPA早就实现了, 而且在原理上也只是利用反射里面的method.getAnnotation(MyAnnotaion.class)即可.   
第二个一直大张旗鼓吹捧的就是AOP, 其实AOP就是个JDK接口方法拦截器/子类增强, 不过Spring加了个配置文件封装, 而且和它的一贯作风一致, 都是集成第三方的框架, 这里基于类增强的是CGLIB.   
CGLIB是什么呢?

cglib is a powerful, high performance and quality Code Generation Library, It is used to extend JAVA classes and implements interfaces at runtime. See [samples](http://cglib.sourceforge.net/xref/samples/index.html) and [API documentation](http://cglib.sourceforge.net/apidocs/index.html) to learn more about features. 

This library is [free software,](http://www.apache.org/foundation/licence-FAQ.html) freely reusable for personal or commercial purposes. 

cglib是一个强大的,高性能,高质量的Code生成类库。它可以在运行期扩展Java类与实现Java 接口. 而CGLIB本身又用了ASM框架, 来避免直接解析字节码.   
OK, 废话少说, 我们来通过一个例子看看基于注解和AOP的权限系统(本代码只需要CGLIB及其依赖类库ASM, 或者直接下载cglib-nodep-2.2.jar [http://sourceforge.net/project/showfiles.php?group\_id=56933&package\_id=98218&release_id=601998](http://sourceforge.net/project/showfiles.php?group_id=56933&package_id=98218&release_id=601998)).   
先看业务层:

public class MyClass {   
private String role;// 运行时角色   
public String getRole() {   
return role;   
&#160;&#160;&#160; }   
public void setRole(String role) {   
this.role = role;   
&#160;&#160;&#160; }   
&#160;&#160;&#160; @Role(name="admin")   
public String adminMethod(String name) {   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; System.out.println("MyClass.adminMethod()" + name);   
return "adminMethod 结果";   
&#160;&#160;&#160; }   
&#160;&#160;&#160; @Role(name="guest")   
public String guestMethod(String name) {   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; System.out.println("MyClass.guestMethod()" + name);   
return "guestMethod 结果";   
&#160;&#160;&#160; }   
}

基本上就是普通的方法加上了角色注解, 当然注解类也是我们自己写的:

import java.lang.annotation.*;   
@Documented   
@Target({ElementType.CONSTRUCTOR, ElementType.METHOD, ElementType.FIELD})//指定目标, 必须包含方法   
@Retention(RetentionPolicy.RUNTIME)//设置保持性   
@Inherited   
public @interface Role {   
&#160;&#160;&#160; String name();   
}

所有的Magic都在后台通过反射和CGLIB的方法拦截器来实现, 先通过JDK本身的反射来检查注解, 然后读取注解的值, 随后进行判断并决定是否执行此方法, 如果中间加上Spring容器, 那就是实现了所谓的专门的权限控制Bean了. 代码:

import java.lang.reflect.Method;   
import net.sf.cglib.proxy.Enhancer;   
import net.sf.cglib.proxy.MethodProxy;   
import net.sf.cglib.proxy.MethodInterceptor;   
public class Main {   
public static void main(String[] args) {   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; Enhancer enhancer = new Enhancer();   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; enhancer.setSuperclass(MyClass.class);   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; enhancer.setCallback( new MethodInterceptorImpl() );   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; MyClass my = (MyClass)enhancer.create();   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; my.setRole("admin");   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; System.out.println(my.adminMethod("名字"));// 这一行将会执行通过   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; System.out.println(my.guestMethod("名字"));// 这一行将会执行失败   
/* &#8211;> new 父类 &#8211;> obj &#8211;>   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; * MyClass_proxy   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; * MyClass obj = new MyClass();// 本来父类   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; * MethodInterceptor interceptor;   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; public String method(String name) {   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; Object value = interceptor.intercept(obj, ojb.getClass().getMethod("method"), new Object[] {name},   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; proxy);   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; if(value != null) {   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; return value;   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; }   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; return obj.method(name);   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; }   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; */   
&#160;&#160;&#160; }   
private static class MethodInterceptorImpl implements MethodInterceptor {   
// obj => 父类的实例, method是被调用的方法, args = {String name}, proxy 专门执行方法的工具类   
public Object intercept(Object obj,   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; Method method,   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; Object[] args,   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; MethodProxy proxy) throws Throwable {   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; System.out.println("即将调用方法" + method);   
// 检查是否有Role注解 @Role(name="角色名")   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; Role role = method.getAnnotation(Role.class);   
if(role != null) {   
// 有注解   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; System.out.println("发现方法上" +method.getName() + " 有一个注解 Role, 它的值是" + role.name());   
// 把被调用对象类型还原   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; MyClass my = (MyClass)obj;   
if(!**role.name()**.equals(my.getRole())) {   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; System.err.println("对不起, 您的权限不足, 不能调用此方法!");   
throw new Exception("对不起, 您的权限不足, 不能调用此方法!");   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; } else {   
// ojb ==> MyClass my   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; // Before   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#1
  
60;&#160; Object value = proxy.invokeSuper(obj, args);// 正在调用方法   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; // invoke 等价于 String return = obj.method(args);   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; System.out.println("已经调用了方法, 原本应该返回的值:" + value);   
// After   
return value;   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; }   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; } else {   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; System.out.println("发现方法" +method.getName() + " 没有角色限制");   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; Object value = proxy.invokeSuper(obj, args);   
return value;   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; }   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; }   
&#160;&#160;&#160; }   
class A {   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; String a() {   
return "";   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; }   
&#160;&#160;&#160; }   
class A_proxy extends A {   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; A a = new A();   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; String a() {   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; String oldValue = a.a();   
return oldValue;   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; }   
&#160;&#160;&#160; }   
}

代码末尾的类A和A_proxy试图说明代理这种模式的实现方式. OK, 运行代码, 应该可以得到我们期望的结果了. admin方法执行成功, 而另一个则失败了.   
运行输出:   
即将调用方法public void MyClass.setRole(java.lang.String)   
发现方法setRole 没有角色限制   
即将调用方法public java.lang.String MyClass.adminMethod(java.lang.String)   
发现方法上adminMethod 有一个注解 Role, 它的值是admin   
即将调用方法public java.lang.String MyClass.getRole()   
发现方法getRole 没有角色限制   
MyClass.adminMethod()名字   
已经调用了方法, 原本应该返回的值:adminMethod 结果   
adminMethod 结果   
即将调用方法public java.lang.String MyClass.guestMethod(java.lang.String)   
发现方法上guestMethod 有一个注解 Role, 它的值是guest   
即将调用方法public java.lang.String MyClass.getRole()   
发现方法getRole 没有角色限制   
对不起, 您的权限不足, 不能调用此方法!   
Exception in thread "main" java.lang.Exception: 对不起, 您的权限不足, 不能调用此方法!    
at Main$MethodInterceptorImpl.intercept(Main.java:60)    
at MyClass$$EnhancerByCGLIB$$e6aea994.guestMethod(<generated>)    
at Main.main(Main.java:20)   
小结: 基于类的权限系统可通过CGLIB/AOP实现; 基于URL的权限系统可通过过滤器实现. 其实, Servlet的Filter也是AOP的一种基于Web的实现.   
后记: 最近网上有一种很普遍的论调, 当大家说XX不好的时候, 有人说XX不行, 有本事你也去跑啊, 去导啊, 不行你就闭嘴. 我想这是一种转移话题的谬论, 举个例子: 如果病人被庸医给看死了, 他的家人是不是还不能说这医生治的不好, 不应该追究责任, 因为他们不会看病啊? 吃菜的不需要会做菜, 但是吃菜的有权利评价菜是否好吃, 所以真正应该闭嘴的是说这种话的人. 所以我们评论框架好坏的时候, 有人就说了: 你说XXX框架不好, 那你有本事也自己去做一个啊; 这是相当荒谬的跑题的论调.   
参考资料: http://cglib.sourceforge.net/ [CGLib 学习](http://www.blogjava.net/Good-Game/archive/2007/11/05/158192.html) [Java下的框架编程(5)&#8211;cglib的应用](http://www.blogjava.net/calvin/archive/2005/11/28/21741.html) 

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [AOP/CGLIB学习:实现简单的注解权限系统(Annotation+拦截器) [整理]](http://www.beansoft.biz/2010/09/08/aopcglib%e5%ad%a6%e4%b9%a0%e5%ae%9e%e7%8e%b0%e7%ae%80%e5%8d%95%e7%9a%84%e6%b3%a8%e8%a7%a3%e6%9d%83%e9%99%90%e7%b3%bb%e7%bb%9fannotation%e6%8b%a6%e6%88%aa%e5%99%a8-%e6%95%b4%e7%90%86/)