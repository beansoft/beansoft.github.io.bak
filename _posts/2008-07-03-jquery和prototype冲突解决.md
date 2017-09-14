---
id: 1846
title: jquery和prototype冲突解决
date: 2008-07-03T19:04:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1846
permalink: '/2008/07/03/jquery%e5%92%8cprototype%e5%86%b2%e7%aa%81%e8%a7%a3%e5%86%b3/'
views:
  - "3728"
original_post_id:
  - "1846"
categories:
  - AJAX/JavaScript
---
问题背景: 想用 jQuery 做 AJAX 处理, 用基于 Prototype 的 EasyValidation 做表单验证, 但是二者不能共存, 因为都用了同一个方法名: $(). 

解决: 

jquery和prototype冲突解决, 网上流传的一篇文章,我这里测试结果是错误的! <http://ajaxbbs.net/blog/post/71/> 

另一种方式是:   
<script type=”text/javascript”>   
&#160;&#160;&#160;&#160;&#160; jQuery.noConflict();   
</script> 

参考: <http://www.d5s.cn/archives/6>, 但我这里测试也有问题! 

本人测试通过的方式: 

1、将jquery.js放到prototype.js前面（这个是必须的!）。   
2、在jquery.js后面将$变量重命名。   
方法如下： 

<script type="text/javascript"&#160; src="jquery.js"></script>   
<script type="text/javascript">   
var jQuery=$;   
</script> 

<script type="text/javascript" type="text/javascript" src="window.js"></script>   
<!&#8211;上面这个window.js调用了jquery框架的方法&#8211;>   
<script type="text/javascript" type="text/javascript" src="prototype.js"></script> 

3、将原来使用的$方法名一律替换为jQuery名，如$("obj")替换为jQuery("obj")。 

例如下面的一段代码, 混合了 jQuery和基于Prototype的 EasyValidation: 

<!&#8211;&#160; jquery, 注意加载顺序 &#8211;>   
<script src="js/jquery-1.2.6.pack.js"></script>   
<script type=”text/javascript”>   
&#160;&#160;&#160;&#160;&#160; var jQuery=$;   
</script> 

<!&#8211; 表单验证 &#8211;>   
<script src="easy_validation/lib/prototype.js" type="text/javascript"></script>   
<script src="easy_validation/lib/effects.js" type="text/javascript"></script>   
<script src="easy\_validation/src/validation\_cn.js" type="text/javascript"></script>   
<link rel="stylesheet" type="text/css" href="easy\_validation/styles/style\_min.css" /> 

&#160;&#160;&#160; <div id="contents"></div>   
&#160; <script>   
&#160; jQuery(document).ready(function(){   
&#160;&#160;&#160; //jQuery("#contents").load("test.jsp");   
&#160;&#160;&#160; jQuery("#contents").load("test.jsp?username=BeanSoft")   
&#160; });   
&#160; </script>   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; <!&#8211; 为form增加required-validate class,标识需要验证form &#8211;>   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; <form id=&#8217;helloworld&#8217; action="#" class=&#8217;required-validate&#8217;>   
<input name="user.name" class="required min-length-6 max-length-20 validate-alphanum" value="beansoft">   
&#160;&#160;&#160;&#160; *密码:   
&#160;&#160;&#160;&#160;&#160; <input name="user.password" type="password" class="required min-length-6 max-length-20" value="123456" > 

&#160;&#160;&#160; *密码(重复):   
&#160;&#160;&#160;&#160;&#160; <input name="password1" type="password" class="required equals-user.password" value="123456" > 

&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; <input type=&#8217;submit&#8217; value=&#8217;Submit&#8217;/>   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; <input type=&#8217;reset&#8217; value=&#8217;Reset&#8217;/>   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; </form> 

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [jquery和prototype冲突解决](http://www.beansoft.biz/2008/07/03/jquery%e5%92%8cprototype%e5%86%b2%e7%aa%81%e8%a7%a3%e5%86%b3/)