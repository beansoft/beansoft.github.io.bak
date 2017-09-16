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