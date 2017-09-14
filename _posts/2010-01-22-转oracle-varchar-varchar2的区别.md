---
id: 43
title: 转:Oracle varchar, varchar2的区别
date: 2010-01-22T00:29:00+00:00
author: 刘长炯
layout: post
guid: http://www.blogjava.net/beansoft/archive/2010/01/22/310453.html
permalink: '/2010/01/22/%e8%bd%acoracle-varchar-varchar2%e7%9a%84%e5%8c%ba%e5%88%ab/'
views:
  - "3170"
original_post_id:
  - "43"
categories:
  - Oracle
---
[http://blog.csdn.net/sunny110/archive/2006/05/10/721766.aspx](http://blog.csdn.net/sunny110/archive/2006/05/10/721766.aspx "http://blog.csdn.net/sunny110/archive/2006/05/10/721766.aspx")

varchar       存放固定长度的字符数据，最长2000个字符。

varchar2    存放可变长字符数据，最大长度为4000字符。，最大長度為4000字符。

varchar     是标准sql提供的数据类型。

varchar2  是oracle提供的独特的数据类型。

oracle保证在任何版本中该数据类型向上和向下兼容，但不保证varchar。

总之，如果想新版本的数据库兼容就不要用varchar,如果想和其他数据库兼容就不要用varchar2。

[char、varchar和varchar2的区别(转)](http://www.cnblogs.com/boulder19830907/archive/2007/11/09/954104.html)

#### 区别：
  
1．CHAR的长度是固定的，而VARCHAR2的长度是可以变化的， 比如，存储字符串“abc&#8221;，对于CHAR (20)，表示你存储的字符将占20个字节(包括17个空字符)，而同样的VARCHAR2 (20)则只占用3个字节的长度，20只是最大值，当你存储的字符小于20时，按实际长度存储。
  
2．CHAR的效率比VARCHAR2的效率稍高。
  
3．目前VARCHAR是VARCHAR2的同义词。工业标准的VARCHAR类型可以存储空字符串，但是oracle不这样做，尽管它保留以后这样做的权利。Oracle自己开发了一个数据类型VARCHAR2，这个类型不是一个标准的VARCHAR，它将在数据库中varchar列可以存储空字符串的特性改为存储NULL值。如果你想有向后兼容的能力，Oracle建议使用VARCHAR2而不是VARCHAR。
  
何时该用CHAR，何时该用varchar2？
  
CHAR与VARCHAR2是一对矛盾的统一体，两者是互补的关系.
  
VARCHAR2比CHAR节省空间，在效率上比CHAR会稍微差一些，即要想获得效率，就必须牺牲一定的空间，这也就是我们在数据库设计上常说的‘以空间换效率’。
  
VARCHAR2虽然比CHAR节省空间，但是如果一个VARCHAR2列经常被修改，而且每次被修改的数据的长度不同，这会引起‘行迁移’(Row Migration)现象，而这造成多余的I/O，是数据库设计和调整中要尽力避免的，在这种情况下用CHAR代替VARCHAR2会更好一些。

char中还会自动补齐空格，因为你insert到一个char字段自动补充了空格的,但是select 后空格没有删除

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [转:Oracle varchar, varchar2的区别](http://www.beansoft.biz/2010/01/22/%e8%bd%acoracle-varchar-varchar2%e7%9a%84%e5%8c%ba%e5%88%ab/)