---
id: 2945
title: Jersey get all form parameters
date: 2012-05-26T22:12:13+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2945
permalink: /2012/05/26/jersey-get-all-form-parameters/
views:
  - "4867"
categories:
  - Java EE
tags:
  - Jersey
  - REST
---
Ref:

<http://docs.oracle.com/cd/E19776-01/820-4867/ghrst/index.html>

<http://markmail.org/message/j6mcijemvaeya3ud>

<http://codahale.com/what-makes-jersey-interesting-parameter-classes/>

**Best solution:**

@POST   
@Produces(&#8220;text/plain;charset=UTF-8&#8221;)   
@Consumes(MediaType.APPLICATION\_FORM\_URLENCODED)   
public String form(MultivaluedMap<String, String> formParams) {   
System.out.println(&#8220;form=&#8221; + formParams);   
return &#8220;&#8221;;   
}

And below solution is not suggested but can also work:

@POST   
@Produces(&#8220;text/plain;charset=UTF-8&#8221;)   
@Consumes(MediaType.APPLICATION\_FORM\_URLENCODED)   
public String form( Form form) {   
System.out.println(&#8220;form=&#8221; + form);   
return &#8220;&#8221;;   
}

**And below is only working with GET:**

@GET   
public String get(@Context   
HttpServletRequest request, @Context HttpServletResponse resp, @Context UriInfo ui   
) {   
System.out.println(ui.getQueryParameters());   
return &#8220;success&#8221;;   
}

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Jersey get all form parameters](http://www.beansoft.biz/2012/05/26/jersey-get-all-form-parameters/)