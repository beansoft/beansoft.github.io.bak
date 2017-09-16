---
id: 3941
title: wordpress搬家到github Jekyll
date: 2017-09-16T22:08:38+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3941
permalink: '/2017/09/15/wordpress-github-Jekyll/'
views:
  - "106"
categories:
  - Jekyll
  
---

由于我的Wordpress事实上已经处于只读状态, 很久也没发表新文章了. 一个原因是Mac上没有太好的媲美Windows Live Writer的软件, 另一个原因是工作有点忙, 第三个原因是现在几乎都是用Markdown写文档, 而一年托管的bluehost费用也够吃几顿午餐了, 所以就考虑搬家到了github. 用 Jekyll 是因为github pages默认支持自动生成站点, 比较方便, 这个比hexo好太多.

我的电脑是Mac, Windows类似.

推荐Markdown编辑软件: Typora (Win/Mac都有)

先安装ruby:

brew install ruby

然后参考 <http://jekyllcn.com/docs/installation/> 安装 Jekyll.

gem install jekyll bundler

bundle install

bundle exec jekyll serve

bundle exec jekyll serve —incremental

<http://127.0.0.1:4000/>

Wordpress一定要把Wordpress的自定义路径修改为: 年/月/日/标题/ 模式.

Wordpress 转 Jekyll 需要在原来的网站上安装插件: <https://wordpress.org/plugins/jekyll-exporter/>

然后导出的文件解压缩后, 中文路径都是转码过的, 不好阅读, 可以用下面的Java程序重新命名一次:

```java
import java.io.File;
import java.io.UnsupportedEncodingException;
public class WordpressFileRenamer {

    public static void main(String[] args) throws Exception {
        String inputDir = "/Users/beansoft/jekyll_export/_posts";
        File rootDir = new File(inputDir);
        String[] posts = rootDir.list();
        if(posts != null) {
            for(String postName : posts) {
                String chnName = decode(postName);
                System.out.println(chnName);
                if(chnName != null && !chnName.equals(postName)) {
                    new File(inputDir, postName).renameTo(new File(inputDir, chnName));
                }
            }
        }
    }

    static String decode(String input) {
        try {
            String out = java.net.URLDecoder.decode(
                    input, "UTF-8");
            return out;
        } catch (UnsupportedEncodingException e) {
            e.printStackTrace();
        }
        return input;
    }
}
```

从备份里 wp-content 目录到Jekyll根目录下, _posts中的内容也要复制过来, 选择合适的主题, 最后映射下域名, 就完工了.