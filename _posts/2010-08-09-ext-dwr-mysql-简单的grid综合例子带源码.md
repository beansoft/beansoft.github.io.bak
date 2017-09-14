---
id: 536
title: Ext + DWR + Mysql 简单的Grid综合例子(带源码)
date: 2010-08-09T21:27:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=536
permalink: '/2010/08/09/ext-dwr-mysql-%e7%ae%80%e5%8d%95%e7%9a%84grid%e7%bb%bc%e5%90%88%e4%be%8b%e5%ad%90%e5%b8%a6%e6%ba%90%e7%a0%81/'
views:
  - "4061"
original_post_id:
  - "536"
image: /wp-content/uploads/2012/09/image_thumb81.png
categories:
  - AJAX/JavaScript
---
**<font color="#800080">[整理文章] 注: 本人目前不从事Web相关研究, 本文仅为提供信息参考之目的, 如有疑问请自行Google.</font>**

**<font color="#ff0000"></font>**

<font color="#ff0000"><strong>友情提示</strong><strong>: </strong><strong>下载微软网盘文件时关闭下载工具</strong><strong>,&#160; </strong><strong>否则你将得到错误的文件</strong><strong>, </strong><strong>双击</strong><strong> EXE </strong><strong>会出来</strong><strong> DOS </strong><strong>窗口</strong><strong>. </strong><strong>正确操作是点击文件名后能看到显示下载链接和文件大小等信息</strong><strong>.</strong></font> 

微软的网盘终于又能用了,5G空间呢,微软就是有钱啊. 

[http://cid-519b3f7aa2172030.skydrive.live.com/self.aspx/Public/AJAX/extdwrgrid.zip](http://cid-519b3f7aa2172030.skydrive.live.com/self.aspx/Public/AJAX/extdwrgrid.zip "http://cid-519b3f7aa2172030.skydrive.live.com/self.aspx/Public/AJAX/extdwrgrid.zip") 1.13 MB 导入MyEclipse即可,也可用其它开发工具. 

运行截图: 

[<img height="187" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2010/08/image_thumb8.png" width="434" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/08/image8.png) 

[<img height="172" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2010/08/image_thumb9.png" width="552" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/08/image9.png) 

这次是真的了, 和数据库同步操作,不过,有安全性问题,建议加密码,一共有20个字段.后台数据库: 

[<img height="96" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2010/08/image_thumb10.png" width="640" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/08/image10.png) 

导出为Excel:

<table style="width:1134pt;border-collapse:collapse;" cellspacing="0" cellpadding="0" width="1512" border="0">
  <col style="width:54pt;" span="span" width="72" /> <tr style="height:14.25pt;">
    <td style="width:324pt;height:14.25pt;" width="432" colspan="6" height="19">
      Netbeans 6 团队在线通讯录 版本 2008-6-6 15:02:08
    </td>
    
    <td style="width:54pt;" width="72">
    </td>
    
    <td style="width:54pt;" width="72">
    </td>
    
    <td style="width:54pt;" width="72">
    </td>
    
    <td style="width:54pt;" width="72">
    </td>
    
    <td style="width:54pt;" width="72">
    </td>
    
    <td style="width:54pt;" width="72">
    </td>
    
    <td style="width:54pt;" width="72">
    </td>
    
    <td style="width:54pt;" width="72">
    </td>
    
    <td style="width:54pt;" width="72">
    </td>
    
    <td style="width:54pt;" width="72">
    </td>
    
    <td style="width:54pt;" width="72">
    </td>
    
    <td style="width:54pt;" width="72">
    </td>
    
    <td style="width:54pt;" width="72">
    </td>
    
    <td style="width:54pt;" width="72">
    </td>
    
    <td style="width:54pt;" width="72">
    </td>
  </tr>
  
  <tr style="height:28.5pt;">
    <td class="xl24" style="width:54pt;height:28.5pt;" width="72" height="38">
      序号
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      姓名
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      英文名
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      性别
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      QQ
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      QQ昵称
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      手机
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      宅电
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      Email
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      MSN
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      MSN昵称
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      生日
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      通信地址
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      邮编
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      籍贯地址
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      籍贯邮编
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      紧急联系方式
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      职业
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      最近状态
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      备注
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      最后更新
    </td>
  </tr>
  
  <tr style="height:42.75pt;">
    <td class="xl24" style="width:54pt;height:42.75pt;" align="right" width="72" height="57">
      1
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      刘长炯
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      BeanSoft
    </td>
    
    <td class="xl24" style="width:54pt;" align="center" width="72">
      TRUE
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      BeanSoft
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      beansoft@126.com
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      beansoft@gmail.com
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      beansoftstudio@msn.com
    </td>
    
    <td class="xl25" style="width:54pt;" align="right" width="72">
      1980-1-5
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      北京市
    </td>
    
    <td class="xl24" style="width:54pt;" align="right" width="72">
      100088
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      河南南阳
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
    </td>
    
    <td class="xl24" style="width:54pt;" align="right" width="72">
      999
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      培训
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      编写Netbeans 6 安装
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      Netbeans开放文档团队
    </td>
    
    <td class="xl25" style="width:54pt;" align="right" width="72">
      2008-6-6
    </td>
  </tr>
  
  <tr style="height:28.5pt;">
    <td class="xl24" style="width:54pt;height:28.5pt;" align="right" width="72" height="38">
      2
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      我很忙
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
      没事不要打扰！
    </td>
    
    <td class="xl24" style="width:54pt;" align="center" width="72">
      TRUE
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
    </td>
    
    <td class="xl24" style="width:54pt;" width="72">
    </td>
    
    <td class="xl25" style="width:54pt;" align="right" width="72">
      2008-6-6
    </td>
  </tr>
</table>

&#160; 

[<img height="209" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2010/08/image_thumb11.png" width="562" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/08/image11.png) 

&#160; 

### **Ext + DWR + Mys
  
ql 简单例子** 

包括5个例子:   
EXT 2 和 DWR 1 表格编辑控件示例(无数据库版本)   
EXT 2 表格编辑控件示例(静态页面，Java和DWR无关版本)   
Netbeans 6 开放文档团队在线通讯录(Ext + DWR + MySQL)   
DWR 检查注册用户名是否存在   
模拟DWR 引擎通过反射调用类中方法并获取返回值 

要运行此例子,请先   
1. 运行 table.sql 在 Mysql 中建表;   
2. 修改 src/dao/UserManagerNB.java 的   
&#160;&#160;&#160; public static Connection getConnection() 方法, 来连接到   
&#160;&#160;&#160; 正确的数据库地址.   
3. 发布项目并键入地址 <http://localhost:8080/extdwrgrid/> 访问;   
4. 要修改例子, 注意绝大多数页面都是 UTF-8 编码的, 例如 .js 文件. 

附件:   
DWR通过AJAX后台POST调用参数,然后使用反射技术调用类的方法并获得结果. 

后台发送的AJAX请求:   
POST dwr/exec/JUserManager.checkUserExits.dwr HTTP/1.1   
Accept: \*/\*   
Accept-Language: zh-cn   
Referer: [http://192.168.1.200:8000/ajaxreview/ajax\_reg\_dwr.html](http://192.168.1.200:8000/ajaxreview/ajax_reg_dwr.html)   
Content-Type: text/plain   
Accept-Encoding: gzip, deflate   
User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)   
Host: 192.168.1.200:8000   
Content-Length: 146   
Connection: Keep-Alive   
Cache-Control: no-cache   
Cookie: JSESSIONID=F0D84EF983957A66162555D3AB966A29 

callCount=1   
c0-scriptName=JUserManager // 类   
c0-methodName=checkUserExits// 方法名   
c0-id=358_1212542593797   
c0-param0=string:%E6%B8%A9%E5%AE%B6%E5%AE%9D // 编码过的参数值   
xml=true 

后台返回的值:   
头部   
HTTP/1.1 200 OK   
Server: Apache-Coyote/1.1   
Content-Type: text/plain;charset=ISO-8859-1   
Transfer-Encoding: chunked   
Date: Wed, 04 Jun 2008 01:23:14 GMT 

正文(responseText)是方法的执行结果   
var s0="u5BF9u4E0Du8D77, u6B64u7528u6237u540Du4E0Du5141u8BB8u6CE8u518C";   
DWREngine.\_handleResponse(&#8216;358\_1212542593797&#8217;, s0); 

BeanSoft@126.com (刘长炯)   
<http://beansoft.biz/>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Ext + DWR + Mysql 简单的Grid综合例子(带源码)](http://www.beansoft.biz/2010/08/09/ext-dwr-mysql-%e7%ae%80%e5%8d%95%e7%9a%84grid%e7%bb%bc%e5%90%88%e4%be%8b%e5%ad%90%e5%b8%a6%e6%ba%90%e7%a0%81/)