---
id: 1423
title: JSP 生成随机验证码图片(Code Share)
date: 2010-11-25T17:11:44+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1423
permalink: '/2010/11/25/jsp-%e7%94%9f%e6%88%90%e9%9a%8f%e6%9c%ba%e9%aa%8c%e8%af%81%e7%a0%81%e5%9b%be%e7%89%87code-share/'
views:
  - "5442"
original_post_id:
  - "1423"
image: /wp-content/uploads/2012/09/image_thumb32.png
categories:
  - JSP
---
[<img style="border-bottom:0;border-left:0;display:inline;border-top:0;border-right:0;" title="image" border="0" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2010/11/image_thumb3.png" width="477" height="37" />](http://www.beansoft.biz/wp-content/uploads/2010/11/image3.png) 

&#160;

**regcode.jsp**

> <font face="Consolas"><%@ page language="java" contentType="image/png" <br />&#160;&#160;&#160; import="java.util.*,java.awt.*,java.awt.image.*" pageEncoding="GBK"%> <br /><%!Color getRandColor(int fc, int bc) {//给定范围获得随机颜色 <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160; Random random = new Random(); <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160; if (fc > 255) <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; fc = 255; <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160; if (bc > 255) <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; bc = 255; <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160; int r = fc + random.nextInt(bc &#8211; fc); <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160; int g = fc + random.nextInt(bc &#8211; fc); <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160; int b = fc + random.nextInt(bc &#8211; fc); <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160; return new Color(r, g, b); <br />&#160;&#160;&#160; }%> </font>
> 
> <font face="Consolas"><% <br />//将过期日期设置为一个过去时间 </font>
> 
> <font face="Consolas">response.setHeader("Expires", "Sat, 6 May 1995 12:00:00 GMT"); </font>
> 
> <font face="Consolas">// 设置 HTTP/1.1 no-cache 头 <br />response.setHeader("Cache-Control", "no-store,no-cache,must-revalidate"); </font>
> 
> <font face="Consolas">// 设置 IE 扩展 HTTP/1.1 no-cache headers， 用户自己添加 <br />response.addHeader("Cache-Control", "post-check=0, pre-check=0"); </font>
> 
> <font face="Consolas">// 设置标准 HTTP/1.0 no-cache header. <br />response.setHeader("Pragma", "no-cache"); </font>
> 
> <font face="Consolas">&#160;&#160;&#160; out.clear();&#160;&#160;&#160; <br />&#160;&#160;&#160; //response.reset();// 清空以前缓冲区 <br />&#160;&#160;&#160; //生成随机类 <br />&#160;&#160;&#160; Random random = new Random(); <br />&#160;&#160;&#160; BufferedImage img = new BufferedImage(60, 20, <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; BufferedImage.TYPE_INT_RGB);// 创建彩色缓冲图, 宽 60, 高 20 </font>
> 
> <font face="Consolas">&#160;&#160;&#160; Graphics g = img.getGraphics();// 画笔对象 </font>
> 
> <font face="Consolas">&#160;&#160;&#160; // 填充白色的背景 <br />&#160;&#160;&#160; g.setColor(Color.white); <br />&#160;&#160;&#160; g.fillRect(0, 0, 100, 20); </font>
> 
> <font face="Consolas">&#160;&#160;&#160; //随机产生155条干扰线，使图象中的认证码不易被其它程序探测到 <br />&#160;&#160;&#160; g.setColor(getRandColor(160, 200)); <br />&#160;&#160;&#160; for (int i = 0; i < 155; i++) { <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160; int x = random.nextInt(100); <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160; int y = random.nextInt(20); <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160; int xl = random.nextInt(12); <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160; int yl = random.nextInt(12); <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160; g.drawLine(x, y, x + xl, y + yl); <br />&#160;&#160;&#160; } </font>
> 
> <font face="Consolas">&#160;&#160;&#160; // 绘制蓝色文字 <br />&#160;&#160;&#160; g.setColor(Color.blue); </font>
> 
> <font face="Consolas">&#160;&#160;&#160; // 生成 4 位随机数字验证码并存入session, 然后输出到图片中 <br />&#160;&#160;&#160; String code = ""; <br />&#160;&#160;&#160; for(int i = 0; i < 4; i++) { <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160; Random rand = new Random(); <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160; // code += rand.nextInt(10) + ""; // 随机数字 <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160; code += (char) ( rand.nextInt(26) + &#8216;A&#8217;) ; // 随机字母 <br />&#160;&#160;&#160; } </font>
> 
> <font face="Consolas">&#160;&#160;&#160; session.setAttribute("regcode", code);// 存放值名字为 regcode </font>
> 
> <font face="Consolas">&#160;&#160;&#160; //设定字体 <br />&#160;&#160;&#160; g.setFont(new Font("Times New Roman", Font.PLAIN, 20)); </font>
> 
> <font face="Consolas">&#160;&#160;&#160; g.drawString(code, 2, 16); </font>
> 
> <font face="Consolas">&#160;&#160;&#160; g.dispose();// 关闭对象, 释放内存, 刷新到图形对象 </font>
> 
> <font face="Consolas">&#160;&#160;&#160; out.clearBuffer();// 清空缓冲区 <br />&#160;&#160;&#160; javax.imageio.ImageIO.write(img, "png", response.getOutputStream());// 把内存的图片编码到输出流, 参数依次为: 图片对象, 格式(png,jpg), 输出流 <br />&#160;&#160;&#160; out.flush(); // 输出全部内容, 防止 Tomcat 后台报 Socket 错误, IE 6 下会出现问题 <br />&#160;&#160;&#160; //out.close();// 关闭, 防止后台无法写入数据 <br />%></font>

对应的表单:

**form.jsp**

> <font face="Consolas"><%@ page pageEncoding="GBK" contentType="text/html; charset=GBK" %> </font>
> 
> <font face="Consolas"><script> </font>
> 
> <font face="Consolas">function loadNewCode() { <br />&#160;&#160;&#160; document.getElementById(&#8216;regcodeImg&#8217;).src = &#8216;regcode.jsp?d=&#8217; + new Date(); <br />} </font>
> 
> <font face="Consolas"></script> <br /><body onload="loadNewCode()"> </font>
> 
> <font face="Consolas"><form method=post action="form_action.jsp"> <br /><input name="keycode" > <img id="regcodeImg" src="regcode.jsp?d=<%=System.currentTimeMillis() %>"> <a href="javascript:void(0);" <br />onclick="loadNewCode(); return false;" <br />>看不清楚?换一张</a> </font>
> 
> <font face="Consolas"><input type=submit > <br /></form> </font>
> 
> <font face="Consolas"></body></font>

后台处理示例代码:

**form_action.jsp**

> <font face="Consolas"><%@ page pageEncoding="GBK" %> </font>
> 
> <font face="Consolas">您输入的验证码是: <br /><%=request.getParameter("keycode")%> </font>
> 
> <font face="Consolas"><% <br />String codeSession =&#160; (String)session.getAttribute("regcode"); </font>
> 
> <font face="Consolas">session.removeAttribute("regcode"); // 清空验证码, 防止重复提交 </font>
> 
> <font face="Consolas">if(codeSession != null && codeSession.equals(request.getParameter("keycode") ) ) { <br />&#160;&#160;&#160; out.println("正确"); <br />} else { <br />&#160;&#160;&#160; out.println("错误"); <br />} <br />%></font>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [JSP 生成随机验证码图片(Code Share)](http://www.beansoft.biz/2010/11/25/jsp-%e7%94%9f%e6%88%90%e9%9a%8f%e6%9c%ba%e9%aa%8c%e8%af%81%e7%a0%81%e5%9b%be%e7%89%87code-share/)