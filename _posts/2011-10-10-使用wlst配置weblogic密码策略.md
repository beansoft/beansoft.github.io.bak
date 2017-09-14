---
id: 2289
title: 使用WLST配置WebLogic密码策略
date: 2011-10-10T22:58:09+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2289
permalink: '/2011/10/10/%e4%bd%bf%e7%94%a8wlst%e9%85%8d%e7%bd%aeweblogic%e5%af%86%e7%a0%81%e7%ad%96%e7%95%a5/'
views:
  - "4987"
original_post_id:
  - "2289"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
<pre>edit()<br />startEdit()</pre>

<a name="wp1215385"></a>

<pre>realm = cmo.getSecurityConfiguration().getDefaultRealm()<br />pwdvalidator = realm.lookupPasswordValidator('systemPasswordValidator')<br /><br />if pwdvalidator:<br />   print 'Password Validator provider is already created'<br /><br />else:<br /># Create SystemPasswordValidator<br /> syspwdValidator = realm.createPasswordValidator('systemPasswordValidator', <br /> 'com.bea.security.providers.authentication.passwordvalidator.SystemPasswordValidator')<br /> print "---  Creation of system Password Validator succeeded!"</pre>

<pre>&nbsp;</pre>

<pre># Configure SystemPasswordValidator<br />try:<br />  pwdvalidator.setMinPasswordLength(8)<br />  pwdvalidator.setMaxPasswordLength(12)<br />  pwdvalidator.setMaxConsecutiveCharacters(3)<br />  pwdvalidator.setMaxInstancesOfAnyCharacter(4)<br />  pwdvalidator.setMinAlphabeticCharacters(1)<br />  pwdvalidator.setMinNumericCharacters(1)<br />  pwdvalidator.setMinLowercaseCharacters(1)<br />  pwdvalidator.setMinUppercaseCharacters(1)<br />  pwdvalidator.setMinNonAlphanumericCharacters(1)<br />  pwdvalidator.setRejectEqualOrContainUsername(true)<br />  pwdvalidator.setRejectEqualOrContainReverseUsername(true)<br />  print " --- Configuration of SystemPasswordValidator complete  ---"<br />except Exception,e:<br />        print e</pre></p> 

<font face="Courier New"></font>

<font face="Courier New"></font>

<font face="Courier New"></font>

<font face="Courier New"></font>

<font face="Courier New"></font>

<font face="Courier New"></font></p> 

<a name="wp1215404"></a>

<pre>save()<br />activate()</pre></p> 

&nbsp;

Ref:

<http://download.oracle.com/docs/cd/E12840_01/wls/docs103/secmanage/atn.html>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [使用WLST配置WebLogic密码策略](http://www.beansoft.biz/2011/10/10/%e4%bd%bf%e7%94%a8wlst%e9%85%8d%e7%bd%aeweblogic%e5%af%86%e7%a0%81%e7%ad%96%e7%95%a5/)