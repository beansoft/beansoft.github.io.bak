---
id: 1249
title: IE下用JavaScript动态生成excel
date: 2009-09-24T09:47:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1249
permalink: '/2009/09/24/ie%e4%b8%8b%e7%94%a8javascript%e5%8a%a8%e6%80%81%e7%94%9f%e6%88%90excel/'
views:
  - "3677"
original_post_id:
  - "1249"
image: /wp-content/uploads/2012/09/ie_thumb.png
categories:
  - AJAX/JavaScript
---
2009-04-29

<script>

// 这个代码可以大大减少IE下的当前页面的Excel导出工作量   
// 如果不能正确执行, 请把当前站点加入可信站点并调低安全级 参考图片: IE添加可信站点.png   
// 导出为Excel, 参数为 HTML 或者 表格代码, 如: "AtB", xxx.innerHTML   
function printToExcel(html) {   
&#160; try{   
&#160;&#160;&#160; var ExApp = new ActiveXObject("Excel.Application")   
&#160;&#160;&#160; var ExWBk = ExApp.workbooks.add()   
&#160;&#160;&#160; var ExWSh = ExWBk.worksheets(1)   
&#160;&#160;&#160; ExApp.DisplayAlerts = false   
&#160;&#160;&#160; ExApp.visible = true   
&#160; }catch(e){   
&#160;&#160;&#160; alert("您所设定的安全级别太高，或者您的电脑没有安装Microsoft Excel软件！")   
&#160;&#160;&#160; return false   
&#160; }   
&#160; window.clipboardData.setData("Text", html);&#160;   
&#160; ExWBk.worksheets(1).Paste;   
&#160; ExWBk.worksheets(1).Columns.AutoFit;   
&#160; ExWBk.worksheets(1).Rows.AutoFit;   
}   
&#160;&#160; // 将 HTML 表格导出为 Excel   
&#160; function&#160;&#160; exportToExcel(table)&#160;&#160;&#160;   
&#160; {   
&#160;&#160;&#160;&#160;&#160; if(confirm("确认要导出吗?")){   
&#160;&#160;&#160;&#160;&#160; //&#160;&#160; Start&#160;&#160; Excel&#160;&#160; and&#160;&#160; get&#160;&#160; Application&#160;&#160; object.&#160;   
&#160;&#160;&#160;&#160;&#160; var&#160;&#160; oXL&#160;&#160; =&#160;&#160; new&#160;&#160; ActiveXObject("Excel.Application");&#160;&#160;&#160;   
&#160;&#160;&#160;&#160;&#160; //&#160;&#160; Get&#160;&#160; a&#160;&#160; new&#160;&#160; workbook.&#160;   
&#160;&#160;&#160;&#160;&#160; var&#160;&#160; oWB&#160;&#160; =&#160;&#160; oXL.Workbooks.Add();&#160;   
&#160;&#160;&#160;&#160;&#160; var&#160;&#160; oSheet&#160;&#160; =&#160;&#160; oWB.ActiveSheet;   
&#160;&#160;&#160;&#160;&#160; var&#160;&#160; hang&#160;&#160; =&#160;&#160; table.rows.length;&#160;&#160;&#160;&#160;   
&#160;&#160;&#160;&#160;&#160; var&#160;&#160; lie&#160;&#160; =&#160;&#160; table.rows(0).cells.length;&#160;&#160;&#160;&#160;&#160;&#160;   
&#160;&#160;&#160;&#160;&#160; //&#160;&#160; Add&#160;&#160; table&#160;&#160; headers&#160;&#160; going&#160;&#160; cell&#160;&#160; by&#160;&#160; cell.&#160;   
&#160;&#160;&#160;&#160;&#160; for&#160;&#160; (i=0;i<hang;i++)&#160;   
&#160;&#160;&#160;&#160;&#160; {&#160;   
&#160;&#160;&#160;&#160;&#160; for&#160;&#160; (j=0;j<lie;j++)&#160;   
&#160;&#160;&#160;&#160;&#160; {&#160;   
&#160;&#160;&#160;&#160;&#160; oSheet.Cells(i+1,j+1).Value&#160;&#160; =&#160;&#160; table.rows(i).cells(j).innerText;&#160;   
&#160;&#160;&#160;&#160;&#160; }&#160;&#160;&#160;&#160;   
&#160;&#160;&#160;&#160;&#160; }&#160;   
&#160;&#160;&#160;&#160;&#160; oXL.Visible&#160;&#160; =&#160;&#160; true;&#160;   
&#160;&#160;&#160;&#160;&#160; oXL.UserControl&#160;&#160; =&#160;&#160; true;&#160;&#160;&#160;&#160;&#160;&#160;   
&#160;&#160;&#160;&#160;&#160; }   
&#160; }   
//printToExcel("AtB");   
</script>   
<!&#8211; 以下为数据区 &#8211;>   
<div id="dataArea">   
<font color=red>2009年猪流感统计表</font>   
&#160;&#160;&#160; <table border="1"&#160; cellpadding="0" style="border-collapse: collapse; " bordercolor="#000000">   
<tbody><tr>   
<td>&nbsp;<b>编号</b></td>   
<td>&nbsp;<b>用户名</b></td></tr>   
<tr>   
<td>&nbsp;1</td>   
<td>&nbsp;金正日</td></tr>   
<tr>   
<td>&nbsp;2</td>   
<td>&nbsp;萨达姆</td></tr>   
</tbody> 

</table> 

</div>   
<script>   
if(confirm("是否导出表格数据为 Excel?")) {   
&#160;&#160;&#160; printToExcel(dataArea.innerHTML);   
}   
</script> 

&#160; 

[<img title="IE添加可信站点" style="display:inline;border-width:0;" height="477" alt="IE添加可信站点" src="http://www.beansoft.biz/wp-content/uploads/2010/09/ie_thumb.png" width="807" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/09/ie.png)

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [IE下用JavaScript动态生成excel](http://www.beansoft.biz/2009/09/24/ie%e4%b8%8b%e7%94%a8javascript%e5%8a%a8%e6%80%81%e7%94%9f%e6%88%90excel/)