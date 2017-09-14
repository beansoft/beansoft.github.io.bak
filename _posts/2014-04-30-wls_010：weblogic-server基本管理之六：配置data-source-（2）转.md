---
id: 3647
title: 'WLS_010：WebLogic Server基本管理之六：配置Data Source （2）[转]'
date: 2014-04-30T18:08:23+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3647
permalink: '/2014/04/30/wls_010%ef%bc%9aweblogic-server%e5%9f%ba%e6%9c%ac%e7%ae%a1%e7%90%86%e4%b9%8b%e5%85%ad%ef%bc%9a%e9%85%8d%e7%bd%aedata-source-%ef%bc%882%ef%bc%89%e8%bd%ac/'
views:
  - "3214"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
来源: [http://maping930883.blogspot.jp/2009/03/wls010weblogic-serverdata-source-2.html](http://maping930883.blogspot.jp/2009/03/wls010weblogic-serverdata-source-2.html "http://maping930883.blogspot.jp/2009/03/wls010weblogic-serverdata-source-2.html")

在上一个Data Source配置中，我们使用的是pointbase数据库，在本文中，我们将使用Oracle数据库。   
运行环境：WebLogic Server 10.3.5 + Oracle Database 10g Express Edition 10.2.0.1。   
[<img border="0" alt="" src="http://4.bp.blogspot.com/-Lc_A5m-S_sI/Tt1y3MvUQ5I/AAAAAAAACRI/jdP9PQYOfDM/s400/1.GIF" />](http://4.bp.blogspot.com/-Lc_A5m-S_sI/Tt1y3MvUQ5I/AAAAAAAACRI/jdP9PQYOfDM/s1600/1.GIF)   
**1. 创建数据库Schema：PBPUBLIC**   
以system用户作为SYSDBA登录：sqlplus system/welcome1@XE as SYSDBA   
然后执行如下脚本：   
REM =======================================================   
REM Login as SYSTEM or SYSDBA user and run this script   
REM =======================================================   
DROP USER PBPUBLIC CASCADE;   
CREATE USER PBPUBLIC IDENTIFIED BY PBPUBLIC;   
ALTER USER PBPUBLIC DEFAULT TABLESPACE users   
QUOTA UNLIMITED ON users;   
ALTER USER PBPUBLIC TEMPORARY TABLESPACE temp;   
GRANT create session   
, create table   
, create procedure   
, create sequence   
, create trigger   
, create view   
, create synonym   
, alter session   
TO PBPUBLIC;   
CONNECT PBPUBLIC/PBPUBLIC   
CREATE TABLE EMPLOYEE   
(   
ID INT ,   
NAME CHARACTER (100) ,   
TITLE CHARACTER (100) ,   
SALARY CHARACTER (50) ,   
BONUS_STRUCTURE CHARACTER (50) ,   
TIME_OFF INT ,   
SICK_TIME INT ,   
HEALTH_PLAN CHARACTER (100) ,   
VISION_PLAN CHARACTER (100) ,   
DENTAL_PLAN CHARACTER (100) ,   
PLAN INT ,   
SAVINGS INT   
);   
CREATE TABLE WLS\_CATALOG\_ITEMS   
(   
SKU CHARACTER (50) ,   
NAME CHARACTER (100) ,   
DESCRIPTION CHARACTER (100) ,   
PRICE DOUBLE PRECISION ,   
INV_AMOUNT INT ,   
CATEGORY CHARACTER (100)   
);   
CREATE TABLE WLS\_CLIENT\_INFO   
(   
CLIENT_ID CHARACTER (100) ,   
NAME CHARACTER (100) ,   
EMAIL CHARACTER (100)   
);   
INSERT INTO EMPLOYEE VALUES(1,&#8217;Chris Montgomery&#8217;,&#8217;Manager&#8217;,&#8217;70,000&#8242;,&#8217;25% Quarterly&#8217;,15,5,&#8217;Blue Cross and Blue Shield&#8217;,&#8217;Aetna Vision&#8217;,&#8217;Delta Dental&#8217;,25000,12000);   
INSERT INTO EMPLOYEE VALUES(2,&#8217;Doris Sylvester&#8217;,&#8217;Programmer&#8217;,&#8217;55,000&#8242;,&#8217;15% Quarterly&#8217;,10,5,&#8217;Blue Cross and Blue Shield&#8217;,&#8217;Aetna Vision&#8217;,&#8217;Aetna Dental&#8217;,22000,16000);   
INSERT INTO EMPLOYEE VALUES(3,&#8217;George Garcia&#8217;,&#8217;Senior Programmer&#8217;,&#8217;62,000&#8242;,&#8217;20% Quarterly&#8217;,10,5,&#8217;Mathew Thornton Health Plan&#8217;,&#8217;Aetna Vision&#8217;,&#8217;Delta Dental&#8217;,18000,9600);   
INSERT INTO EMPLOYEE VALUES(4,&#8217;Jeff Hodgkins&#8217;,&#8217;Manager&#8217;,&#8217;75,000&#8242;,&#8217;25% Quarterly&#8217;,15,5,&#8217;Blue Cross and Blue Shield&#8217;,&#8217;Aetna Vision&#8217;,&#8217;Aetna Dental&#8217;,15000,22000);   
INSERT INTO EMPLOYEE VALUES(5,&#8217;Jennifer Ackerman&#8217;,&#8217;Manager&#8217;,&#8217;75,000&#8242;,&#8217;25% Quarterly&#8217;,15,5,&#8217;Mathew Thornton Health Plan&#8217;,&#8217;Aetna Vision&#8217;,&#8217;Aetna Dental&#8217;,18000,23000);   
INSERT INTO EMPLOYEE VALUES(6,&#8217;Jill Champagne&#8217;,&#8217;Senior Programmer&#8217;,&#8217;60,000&#8242;,&#8217;20% Quarterly&#8217;,10,5,&#8217;Mathew Thornton Health Plan&#8217;,&#8217;Aetna Vision&#8217;,&#8217;Delta Dental&#8217;,12000,16000);   
INSERT INTO EMPLOYEE VALUES(7,&#8217;Katherine Frederick&#8217;,&#8217;Manager&#8217;,&#8217;70,000&#8242;,&#8217;25% Quarterly&#8217;,15,5,&#8217;Mathew Thornton Health Plan&#8217;,&#8217;Aetna Vision&#8217;,&#8217;Aetna Dental&#8217;,25000,6000);   
INSERT INTO EMPLOYEE VALUES(8,&#8217;Michael Fuller&#8217;,&#8217;Programmer&#8217;,&#8217;50,000&#8242;,&#8217;15% Quarterly&#8217;,10,5,&#8217;Blue Cross and Blue Shield&#8217;,&#8217;Aetna Vision&#8217;,&#8217;Delta Dental&#8217;,13500,9500);   
INSERT INTO EMPLOYEE VALUES(9,&#8217;Ryan Lewis&#8217;,&#8217;Programmer&#8217;,&#8217;52,000&#8242;,&#8217;15% Quarterly&#8217;,10,5,&#8217;Blue Cross and Blue Shield&#8217;,&#8217;Aetna Vision&#8217;,&#8217;Delta Dental&#8217;,16000,7600);   
INSERT INTO EMPLOYEE VALUES(10,&#8217;Thomas Bernard&#8217;,&#8217;Manager&#8217;,&#8217;65,000&#8242;,&#8217;25% Quarterly&#8217;,15,5,&#8217;Mathew Thornton Health Plan&#8217;,&#8217;Aetna Vision&#8217;,&#8217;Delta Dental&#8217;,28520,1480);   
INSERT INTO WLS\_CATALOG\_ITEMS VALUES(&#8216;101&#8242;,&#8217;baseball cap&#8217;,&#8217;black baseball cap with company logo&#8217;,19.99,44,&#8217;Clothing&#8217;);   
INSERT INTO WLS\_CATALOG\_ITEMS VALUES(&#8216;102&#8242;,&#8217;polo shirt&#8217;,&#8217;white polo shirt with company logo&#8217;,29.99,77,&#8217;Clothing&#8217;);   
INSERT INTO WLS\_CATALOG\_ITEMS VALUES(&#8216;103&#8242;,&#8217;pens&#8217;,&#8217;a box of pens that have the company logo&#8217;,5.99,100,&#8217;Office Supplies&#8217;);   
INSERT INTO WLS\_CATALOG\_ITEMS VALUES(&#8216;104&#8242;,&#8217;paper&#8217;,&#8217;pads of legal paper with the company logo&#8217;,9.99,120,&#8217;Office Supplies&#8217;);   
INSERT INTO WLS\_CATALOG\_ITEMS VALUES(&#8216;105&#8242;,&#8217;beach towel&#8217;,&#8217;an oversized beach towel with the company logo&#8217;,14.99,88,&#8217;Misc&#8217;);   
INSERT INTO WLS\_CATALOG\_ITEMS VALUES(&#8216;106&#8242;,&#8217;sweatshirt&#8217;,&#8217;grey sweatshirt with the company logo&#8217;,39.99,7,&#8217;Clothing&#8217;);   
INSERT INTO WLS\_CLIENT\_INFO VALUES(&#8216;id2&#8242;,&#8217;Homer Simpson&#8217;,&#8217;homer.simpson@springfield.com&#8217;);   
INSERT INTO WLS\_CLIENT\_INFO VALUES(&#8216;id3&#8242;,&#8217;Elmer Fudd&#8217;,&#8217;elmer.fudd@warnerbrothers.com&#8217;);   
INSERT INTO WLS\_CLIENT\_INFO VALUES(&#8216;id4&#8242;,&#8217;Your Name&#8217;,&#8217;Your Email&#8217;);   
exit;   
**2. 配置Data Source：dizzyworldDS**   
Data Source的JNDI名称与上一个实验一样，这样正是使用Data Source的好处：   
只要Data Source的JNDI名称不变，可以切换使用其它的数据库，而代码不用做任何改变。   
    ![](http://1.bp.blogspot.com/-PR553iKhbdk/Tt16-dEED-I/AAAAAAAACRg/sd_j_jYBj38/s1600/2.GIF)  
为了简单起见，这里没有选用支持XA的Driver：   
[<img border="0" alt="" src="http://2.bp.blogspot.com/-14leitenSrk/Tt18NVi5nGI/AAAAAAAACRs/NtxZrNWxPEY/s400/3.GIF" />](http://2.bp.blogspot.com/-14leitenSrk/Tt18NVi5nGI/AAAAAAAACRs/NtxZrNWxPEY/s1600/3.GIF)   
因此，只能支持One-phase commit：   
[<img border="0" alt="" src="http://1.bp.blogspot.com/-eIVqgbt5rEQ/Tt19fIQVu3I/AAAAAAAACR4/UgDhBjHmXc8/s400/4.GIF" />](http://1.bp.blogspot.com/-eIVqgbt5rEQ/Tt19fIQVu3I/AAAAAAAACR4/UgDhBjHmXc8/s1600/4.GIF)   
**3. 在testdatasource.jsp中访问DataSource，获取数据库连接**   
testdatasource.jsp代码与上一篇文章完全相同。   
**4. 配置XA Data Source：dizzyworldXADS**   
配置支持XA的Driver：   
[<img border="0" alt="" src="http://2.bp.blogspot.com/-kwJd9rM84V4/Tt2HE6grjZI/AAAAAAAACSE/kRkjic8pAyA/s400/5.GIF" />](http://2.bp.blogspot.com/-kwJd9rM84V4/Tt2HE6grjZI/AAAAAAAACSE/kRkjic8pAyA/s1600/5.GIF)   
可以看出使用的Driver Class支持XA：   
[<img border="0" alt="" src="http://3.bp.blogspot.com/-l91Zt7UfFks/Tt2HFNa_tnI/AAAAAAAACSU/azXt7yIy5Qk/s400/6.GIF" />](http://3.bp.blogspot.com/-l91Zt7UfFks/Tt2HFNa_tnI/AAAAAAAACSU/azXt7yIy5Qk/s1600/6.GIF)   
运行同样的testdatasource.jsp，使用dizzyworldXADS作为JNDI名称。   
[<img border="0" alt="" src="http://2.bp.blogspot.com/-bYfP1EtXQpk/Tt2HFVdRmpI/AAAAAAAACSc/g880fwplloQ/s400/7.GIF" />](http://2.bp.blogspot.com/-bYfP1EtXQpk/Tt2HFVdRmpI/AAAAAAAACSc/g880fwplloQ/s1600/7.GIF)   
Project下载：[conf\_jdbc\_obe.zip](http://java-never-die.googlecode.com/files/conf_jdbc_obe.zip)

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [WLS_010：WebLogic Server基本管理之六：配置Data Source （2）[转]](http://www.beansoft.biz/2014/04/30/wls_010%ef%bc%9aweblogic-server%e5%9f%ba%e6%9c%ac%e7%ae%a1%e7%90%86%e4%b9%8b%e5%85%ad%ef%bc%9a%e9%85%8d%e7%bd%aedata-source-%ef%bc%882%ef%bc%89%e8%bd%ac/)