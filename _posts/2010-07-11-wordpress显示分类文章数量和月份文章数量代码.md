---
id: 188
title: wordpress显示分类文章数量和月份文章数量代码
date: 2010-07-11T12:02:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=188
permalink: '/2010/07/11/wordpress%e6%98%be%e7%a4%ba%e5%88%86%e7%b1%bb%e6%96%87%e7%ab%a0%e6%95%b0%e9%87%8f%e5%92%8c%e6%9c%88%e4%bb%bd%e6%96%87%e7%ab%a0%e6%95%b0%e9%87%8f%e4%bb%a3%e7%a0%81/'
views:
  - "6331"
original_post_id:
  - "188"
categories:
  - OpenSource
---
<p style="MARGIN: 0cm 0cm 0pt">
  <strong>2012-4-12</strong> <strong>刘长炯更新备注：</strong><strong>3.3.1</strong> <strong>版本</strong>已经内置了设置选项，不需要改任何代码。进入后台管理，选外观<strong>à</strong><strong>小工具即可设置。</strong>
</p>

<img src="http://www.beansoft.biz/wp-content/uploads/2012/04/zrclip_001p687cbbff.png" height="382" width="823" />

<p style="MARGIN: 0cm 0cm 0pt">
  以下原文内容适用于Wordpress 2.x 版本。
</p>

&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;

原文为: [http://www.54tomgo.com/archives/295.html](http://www.54tomgo.com/archives/295.html "http://www.54tomgo.com/archives/295.html") 略有改动

[<img src="http://www.beansoft.biz/wp-content/uploads/2010/07/image_thumb2.png" style="BORDER-RIGHT-WIDTH: 0px; DISPLAY: inline; BORDER-TOP-WIDTH: 0px; BORDER-BOTTOM-WIDTH: 0px; BORDER-LEFT-WIDTH: 0px" title="image" height="436" width="166" alt="image" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/07/image3.png)

显示分类文章数量和月份文章数量代码

wordpress的代码很多，不知道为什么wordpress不把大家常用的，直接显示在页面上。可能是要锻炼大家的DIY精神？   
这个是显示首页的分类的文章数量的代码，打开sidebar.php，查找

  1. <?php wp\_list\_categories(&#8216;orderby=name&title_li=&#8217;); ?>

替换为：

  1. <?php wp\_list\_categories(&#8216;show\_count=1&orderby=name&title\_li=&#8217;); ?

这个是显示首页的月份分类的文章数量的代码，还是查找sidebar.php文件里面的，

  1. <?php wp\_get\_archives(&#8216;type=monthly&limit=12&#8217;); ?>

一样是添加

  1. show\_post\_count=1&

替换为：

  1. <?php wp\_get\_archives(&#8216;show\_post\_count=1&type=monthly&limit=12&#8217;); ?>

FTP上传后，OK~~

附一份完整的 sidebar.php的源代码(仅供参考):

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;
          div id="sidebar"
          &gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;
          ul
          &gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;"></pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;?php <a style="COLOR: #0000ff" href="http://www.php.net/if">if</a> ( !<a style="COLOR: #ffa500" href="http://www.php.net/function_exists">function_exists</a>('dynamic_sidebar')
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">|| !dynamic_sidebar() ) : ?&gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;"></pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;!-- Author information is disabled per default. Uncomment and fill in your details if you want to use it.

</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;li&gt;&lt;h2&gt;&lt;?php _e('Author') ?&gt;&lt;/h2&gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;p&gt;A little something about you, the author. Nothing lengthy, just an overview.&lt;/p&gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;/li&gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">--&gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;"></pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;?php wp_list_pages('title_li=&lt;h2&gt;'.__('Pages').'&lt;/h2&gt;' ); ?&gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;"></pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;
          li
          &gt;
          &lt;
          h2
          &gt;
          &lt;?php _e('Categories') ?&gt;
          &lt;/
          h2
          &gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;
          ul
          &gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;?php wp_list_categories('show_count=1&orderby=name&title_li='); ?&gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;/
          ul
          &gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;/
          li
          &gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;"></pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;
          li
          &gt;
          &lt;
          h2
          &gt;
          &lt;?php _e('Archives') ?&gt;
          &lt;/
          h2
          &gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;
          ul
          &gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;?php wp_get_archives('show_post_count=1&type=monthly'); ?&gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;/
          ul
          &gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;/
          li
          &gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;"></pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;?php /* If this is the frontpage */ <a style="COLOR: #0000ff" href="http://www.php.net/if">if</a> ( is_home() || is_page() ) { ?&gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;?php get_links_list(); ?&gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;"></pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;
          li
          &gt;
          &lt;
          h2
          &gt;
          &lt;?php _e('Meta') ?&gt;
          &lt;/
          h2
          &gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;
          ul
          &gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;?php wp_register(); ?&gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;
          li
          &gt;
          &lt;?php wp_loginout(); ?&gt;
          &lt;/
          li
          &gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;"><br />                &lt;
          li
          &gt;
          &lt;
          a href="http://validator.w3.org/check/referer" title="&lt;?php _e('This page validates as XHTML 1.0 Transitional') ?&gt;"
          &gt;Valid<br /> &lt;
          abbr title="eXtensible HyperText Markup Language"
          &gt;XHTML&lt;/
          abbr
          &gt;
          &lt;/
          a
          &gt;
          &lt;/
          li
          &gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;
          li
          &gt;
          &lt;
          a href="http://gmpg.org/xfn/"
          &gt;
          &lt;
          abbr title="&lt;?php _e('XHTML Friends Network') ?&gt;"
          &gt;XFN&lt;/
          abbr
          &gt;
          &lt;/
          a
          &gt;
          &lt;/
          li
          &gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;
          li
          &gt;
          &lt;
          a href="http://wordpress.org/" title="&lt;?php _e('Powered by WordPress, state-of-the-art semantic personal publishing platform.')?&gt; "
          &gt;WordPress&lt;/
          a
          &gt;
          &lt;/
          li
          &gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;?php wp_meta(); ?&gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;/
          ul
          &gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;/
          li
          &gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;?php } ?&gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;"></pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;?php <a style="COLOR: #0000ff" href="http://www.php.net/endif">endif</a>; ?&gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;/
          ul
          &gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;">&lt;/
          div
          &gt;
</pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;"></pre>

<pre style="BACKGROUND-COLOR: #ffffff; WIDTH: 100%; FONT-FAMILY: consolas,'font-size:10px;margin:0;"></pre>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [wordpress显示分类文章数量和月份文章数量代码](http://www.beansoft.biz/2010/07/11/wordpress%e6%98%be%e7%a4%ba%e5%88%86%e7%b1%bb%e6%96%87%e7%ab%a0%e6%95%b0%e9%87%8f%e5%92%8c%e6%9c%88%e4%bb%bd%e6%96%87%e7%ab%a0%e6%95%b0%e9%87%8f%e4%bb%a3%e7%a0%81/)