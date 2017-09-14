---
id: 1359
title: 'Memory Limits for Windows Releases[FW]'
date: 2010-10-31T08:33:33+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1359
permalink: /2010/10/31/memory-limits-for-windows-releasesfw/
views:
  - "3737"
original_post_id:
  - "1359"
categories:
  - Windows
---
各Windows发行版的内存限制

From: <http://msdn.microsoft.com/en-us/library/aa366778(VS.85).aspx>

<span class="Apple-style-span" style="word-spacing:0;font:medium simsun;text-transform:none;color:rgb(0,0,0);text-indent:0;white-space:normal;letter-spacing:normal;border-collapse:separate;orphans:2;widows:2;"><span class="Apple-style-span" style="font-size:13px;font-family:&#039;text-align:left;"> </p> 

<h1 class="title" style="font:bold 1.76em &#039;color:rgb(63,82,156);margin:0 0 10px;">
  Memory Limits for Windows Releases
</h1>

<div id="mainSection" style="padding-top:5px;">
  <div class="clsServerSDKContent">
  </div>
  
  <p>
    This topic describes memory limits for supported Windows releases:
  </p></p> 
  
  <ul>
    <li>
      <a style="color:rgb(19,100,196);text-decoration:none;" href="http://msdn.microsoft.com/en-us/library/aa366778(VS.85).aspx#memory_limits">Memory and Address Space Limits</a>
    </li>
    <li>
      <a style="color:rgb(19,100,196);text-decoration:none;" href="http://msdn.microsoft.com/en-us/library/aa366778(VS.85).aspx#physical_memory_limits_windows_7">Physical Memory Limits: Windows 7</a>
    </li>
    <li>
      <a style="color:rgb(19,100,196);text-decoration:none;" href="http://msdn.microsoft.com/en-us/library/aa366778(VS.85).aspx#physical_memory_limits_windows_server_2008_r2">Physical Memory Limits: Windows Server 2008 R2</a>
    </li>
    <li>
      <a style="color:rgb(19,100,196);text-decoration:none;" href="http://msdn.microsoft.com/en-us/library/aa366778(VS.85).aspx#physical_memory_limits_windows_server_2008">Physical Memory Limits: Windows Server 2008</a>
    </li>
    <li>
      <a style="color:rgb(19,100,196);text-decoration:none;" href="http://msdn.microsoft.com/en-us/library/aa366778(VS.85).aspx#physical_memory_limits_windows_vista">Physical Memory Limits: Windows Vista</a>
    </li>
    <li>
      <a style="color:rgb(19,100,196);text-decoration:none;" href="http://msdn.microsoft.com/en-us/library/aa366778(VS.85).aspx#physical_memory_limits_windows_home_server">Physical Memory Limits: Windows Home Server</a>
    </li>
    <li>
      <a style="color:rgb(19,100,196);text-decoration:none;" href="http://msdn.microsoft.com/en-us/library/aa366778(VS.85).aspx#physical_memory_limits_windows_server_2003">Physical Memory Limits: Windows Server 2003</a>
    </li>
    <li>
      <a style="color:rgb(19,100,196);text-decoration:none;" href="http://msdn.microsoft.com/en-us/library/aa366778(VS.85).aspx#physical_memory_limits_windows_xp">Physical Memory Limits: Windows XP</a>
    </li>
    <li>
      <a style="color:rgb(19,100,196);text-decoration:none;" href="http://msdn.microsoft.com/en-us/library/aa366778(VS.85).aspx#physical_memory_limits_win2k">Physical Memory Limits: Windows 2000</a>
    </li>
    <li>
      <a style="color:rgb(19,100,196);text-decoration:none;" href="http://msdn.microsoft.com/en-us/library/aa366778(VS.85).aspx#related_topics">Related Topics</a>
    </li>
  </ul>
  
  <p>
    Limits on memory and address space vary by platform, operating system, and by whether the IMAGE_FILE_LARGE_ADDRESS_AWARE value of the<span class="Apple-converted-space">&#160;</span><a style="color:rgb(19,100,196);text-decoration:none;" href="http://msdn.microsoft.com/en-us/library/ms680349(v=VS.85).aspx"><strong>LOADED_IMAGE</strong></a><span class="Apple-converted-space">&#160;</span>structure and<span class="Apple-converted-space">&#160;</span><a style="color:rgb(19,100,196);text-decoration:none;" href="http://msdn.microsoft.com/en-us/library/bb613473(v=VS.85).aspx">4-gigabyte tuning</a><span class="Apple-converted-space">&#160;</span>(4GT) are in use. IMAGE_FILE_LARGE_ADDRESS_AWARE is set or cleared by using the<span class="Apple-converted-space">&#160;</span><a style="color:rgb(19,100,196);text-decoration:none;" href="http://go.microsoft.com/fwlink/?LinkId=132948" target="_blank"><strong>/LARGEADDRESSAWARE</strong></a><span class="Apple-converted-space">&#160;</span>linker option.
  </p>
  
  <p>
    Limits on physical memory for 32-bit platforms also depend on the<span class="Apple-converted-space">&#160;</span><a style="color:rgb(19,100,196);text-decoration:none;" href="http://msdn.microsoft.com/en-us/library/aa366796(v=VS.85).aspx">Physical Address Extension</a><span class="Apple-converted-space">&#160;</span>(PAE), which allows 32-bit Windows systems to use more than 4 GB of physical memory.
  </p>
  
  <h3 style="font-weight:bold;font-size:1.07em;color:rgb(63,82,156);font-family:&#039;">
    <a id="memory_limits"></a>Memory and Address Space Limits
  </h3>
  
  <p>
    The following table specifies the limits on memory and address space for supported releases of Windows. Unless otherwise noted, the limits in this table apply to all supported releases.
  </p>
  
  <table style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;width:1395px;border-bottom:rgb(187,187,187) 1px solid;border-collapse:collapse;">
    <tr style="vertical-align:top;">
      <th>
        Memory type
      </th>
      
      <th>
        Limit in 32-bit Windows
      </th>
      
      <th>
        Limit in 64-bit Windows
      </th>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          User-mode virtual address space for each 32-bit process
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          2 GB
        </p>
        
        <p>
          Up to 3 GB with IMAGE_FILE_LARGE_ADDRESS_AWARE and 4GT
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          2 GB with IMAGE_FILE_LARGE_ADDRESS_AWARE cleared (default)
        </p>
        
        <p>
          4 GB with IMAGE_FILE_LARGE_ADDRESS_AWARE set
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          User-mode virtual address space for each 64-bit process
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Not applicable
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          With IMAGE_FILE_LARGE_ADDRESS_AWARE set (default):
        </p></p> 
        
        <blockquote>
          <div>
            <strong>x64:&#160; </strong>8 TB
          </div>
        </blockquote>
        
        <blockquote>
          <div>
            <strong>Intel IPF:&#160; </strong>7 TB
          </div>
        </blockquote>
        
        <p>
          2 GB with IMAGE_FILE_LARGE_ADDRESS_AWARE cleared
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Kernel-mode virtual address space
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          2 GB
        </p>
        
        <p>
          From 1 GB to a maximum of 2 GB with 4GT
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          8 TB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Paged pool
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Limited by available kernel-mode virtual address space or the<span class="Apple-converted-space">&#160;</span><a style="color:rgb(19,100,196);text-decoration:none;" href="http://msdn.microsoft.com/en-us/library/bb870880(v=VS.85).aspx">PagedPoolLimit</a><span class="Apple-converted-space">&#160;</span>registry key value.
        </p>
        
        <blockquote>
          <div>
            <strong>Windows Vista:&#160; </strong>Limited only by kernel mode virtual address space. Starting with Windows Vista with Service Pack 1 (SP1), the paged pool can also be limited by the<span class="Apple-converted-space">&#160;</span><a style="color:rgb(19,100,196);text-decoration:none;" href="http://msdn.microsoft.com/en-us/library/bb870880(v=VS.85).aspx">PagedPoolLimit</a><span class="Apple-converted-space">&#160;</span>registry key value.
          </div>
        </blockquote>
        
        <blockquote>
          <div>
            <strong>Windows Home Server and Windows Server 2003:&#160; </strong>530 MB
          </div>
        </blockquote>
        
        <blockquote>
          <div>
            <strong>Windows XP:&#160; </strong>490 MB
          </div>
        </blockquote>
        
        <blockquote>
          <div>
            <strong>Windows 2000:&#160; </strong>350 MB
          </div>
        </blockquote>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          128 GB
        </p>
        
        <blockquote>
          <div>
            <strong>Windows Server 2003 and Windows XP:&#160; </strong>Up to 128 GB depending on configuration and RAM.
          </div>
        </blockquote>
        
        <blockquote>
          <div>
            <strong>Windows 2000:&#160; </strong>Not applicable
          </div>
        </blockquote>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Nonpaged pool
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Limited by available kernel-mode virtual address space, the<span class="Apple-converted-space">&#160;</span><a style="color:rgb(19,100,196);text-decoration:none;" href="http://msdn.microsoft.com/en-us/library/bb870880(v=VS.85).aspx">NonPagedPoolLimit</a><span class="Apple-converted-space">&#160;</span>registry key value, or physical memory.
        </p>
        
        <blockquote>
          <div>
            <strong>Windows Vista:&#160; </strong>Limited only by kernel mode virtual address space and physical memory. Starting with Windows Vista with SP1, the nonpaged pool can also be limited by the<span class="Apple-converted-space">&#160;</span><a style="color:rgb(19,100,196);text-decoration:none;" href="http://msdn.microsoft.com/en-us/library/bb870880(v=VS.85).aspx">NonPagedPoolLimit</a><span class="Apple-converted-space">&#160;</span>registry key value.
          </div>
        </blockquote>
        
        <blockquote>
          <div>
            <strong>Windows Home Server, Windows Server 2003, and Windows XP/2000:&#160; </strong>256 MB, or 128 MB with 4GT.
          </div>
        </blockquote>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          75% of RAM up to a maximum of 128 GB
        </p>
        
        <blockquote>
          <div>
            <strong>Windows Vista:&#160; </strong>40% of RAM up to a maximum of 128 GB.
          </div>
        </blockquote>
        
        <blockquote>
          <div>
            <strong>Windows Server 2003 and Windows XP:&#160; </strong>Up to 128 GB depending on configuration and RAM.
          </div>
        </blockquote>
        
        <blockquote>
          <div>
            <strong>Windows 2000:&#160; </strong>Not applicable
          </div>
        </blockquote>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          System cache virtual address space (physical size limited only by physical memory)
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Limited by available kernel-mode virtual address space or the<span class="Apple-converted-space">&#160;</span><a style="color:rgb(19,100,196);text-decoration:none;" href="http://msdn.microsoft.com/en-us/library/bb870880(v=VS.85).aspx">SystemCacheLimit</a><span class="Apple-converted-space">&#160;</span>registry key value.
        </p></p> 
        
        <blockquote>
          <div>
            <strong>Windows Vista:&#160; </strong>Limited only by kernel mode virtual address space. Starting with Windows Vista with SP1, system cache virtual address space can also be limited by the<span class="Apple-converted-space">&#160;</span><a style="color:rgb(19,100,196);text-decoration:none;" href="http://msdn.microsoft.com/en-us/library/bb870880(v=VS.85).aspx">SystemCacheLimit</a><span class="Apple-converted-space">&#160;</span>registry key value.
          </div>
        </blockquote>
        
        <blockquote>
          <div>
            <strong>Windows Home Server, Windows Server 2003, and Windows XP/2000:&#160; </strong>860 MB with<span class="Apple-converted-space">&#160;</span><a style="color:rgb(19,100,196);text-decoration:none;" href="http://go.microsoft.com/fwlink/?LinkId=97918" target="_blank">LargeSystemCache</a>registry key set and without 4GT; up to 448 MB with 4GT.
          </div>
        </blockquote>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Always 1 TB regardless of physical RAM
        </p>
        
        <blockquote>
          <div>
            <strong>Windows Server 2003 and Windows XP:&#160; </strong>Up to 1 TB depending on configuration and RAM.
          </div>
        </blockquote>
        
        <blockquote>
          <div>
            <strong>Windows 2000:&#160; </strong>Not applicable
          </div>
        </blockquote>
      </td>
    </tr>
  </table>
  
  <p>
    &#160;
  </p>
  
  <h3 style="font-weight:bold;font-size:1.07em;color:rgb(63,82,156);font-family:&#039;">
    <a id="physical_memory_limits_windows_7"></a>Physical Memory Limits: Windows 7
  </h3>
  
  <p>
    The following table specifies the limits on physical memory for Windows 7.
  </p>
  
  <table style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;width:1395px;border-bottom:rgb(187,187,187) 1px solid;border-collapse:collapse;">
    <tr style="vertical-align:top;">
      <th>
        Version
      </th>
      
      <th>
        Limit in 32-bit Windows
      </th>
      
      <th>
        Limit in 64-bit Windows
      </th>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows 7 Ultimate
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          4 GB
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          192 GB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows 7 Enterprise
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          4 GB
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          192 GB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows 7 Professional
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          4 GB
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          192 GB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows 7 Home Premium
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          4 GB
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          16 GB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows 7 Home Basic
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          4 GB
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          8 GB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows 7 Starter
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          2 GB
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          2 GB
        </p>
      </td>
    </tr>
  </table>
  
  <p>
    &#160;
  </p>
  
  <h3 style="font-weight:bold;font-size:1.07em;color:rgb(63,82,156);font-family:&#039;">
    <a id="physical_memory_limits_windows_server_2008_r2"></a>Physical Memory Limits: Windows Server 2008 R2
  </h3>
  
  <p>
    The following table specifies the limits on physical memory for Windows Server 2008 R2. Windows Server 2008 R2 is available only in 64-bit editions.
  </p>
  
  <table style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;width:1395px;border-bottom:rgb(187,187,187) 1px solid;border-collapse:collapse;">
    <tr style="vertical-align:top;">
      <th>
        Version
      </th>
      
      <th>
        Limit in 64-bit Windows
      </th>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows Server 2008 R2 Datacenter
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          2 TB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows Server 2008 R2 Enterprise
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          2 TB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows Server 2008 R2 for Itanium-Based Systems
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          2 TB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows Server 2008 R2 Foundation
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          8 GB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows Server 2008 R2 Standard
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          32 GB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows HPC Server 2008 R2
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          128 GB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows Web Server 2008 R2
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          32 GB
        </p>
      </td>
    </tr>
  </table>
  
  <p>
    &#160;
  </p>
  
  <h3 style="font-weight:bold;font-size:1.07em;color:rgb(63,82,156);font-family:&#039;">
    <a id="physical_memory_limits_windows_server_2008"></a>Physical Memory Limits: Windows Server 2008
  </h3>
  
  <p>
    The following table specifies the limits on physical memory for Windows Server 2008. Limits greater than 4 GB for 32-bit Windows assume that<span class="Apple-converted-space">&#160;</span><a style="color:rgb(19,100,196);text-decoration:none;" href="http://msdn.microsoft.com/en-us/library/aa366796(v=VS.85).aspx">PAE</a><span class="Apple-converted-space">&#160;</span>is enabled.
  </p>
  
  <table style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;width:1395px;border-bottom:rgb(187,187,187) 1px solid;border-collapse:collapse;">
    <tr style="vertical-align:top;">
      <th>
        Version
      </th>
      
      <th>
        Limit in 32-bit Windows
      </th>
      
      <th>
        Limit in 64-bit Windows
      </th>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows Server 2008 Datacenter
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          64 GB
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          1 TB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows Server 2008 Enterprise
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          64 GB
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          1 TB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows Server 2008 HPC Edition
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Not applicable
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          128 GB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows Server 2008 Standard
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          4 GB
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          32 GB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows Server 2008 for Itanium-Based Systems
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Not applicable
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          2 TB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows Small Business Server 2008
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          4 GB
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          32 GB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows Web Server 2008
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          4 GB
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          32 GB
        </p>
      </td>
    </tr>
  </table>
  
  <p>
    &#160;
  </p>
  
  <h3 style="font-weight:bold;font-size:1.07em;color:rgb(63,82,156);font-family:&#039;">
    <a id="physical_memory_limits_windows_vista"></a>Physical Memory Limits: Windows Vista
  </h3>
  
  <p>
    The following table specifies the limits on physical memory for Windows Vista.
  </p>
  
  <table style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;width:1395px;border-bottom:rgb(187,187,187) 1px solid;border-collapse:collapse;">
    <tr style="vertical-align:top;">
      <th>
        Version
      </th>
      
      <th>
        Limit in 32-bit Windows
      </th>
      
      <th>
        Limit in 64-bit Windows
      </th>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows Vista Ultimate
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          4 GB
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          128 GB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows Vista Enterprise
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          4 GB
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          128 GB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows Vista Business
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          4 GB
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          128 GB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows Vista Home Premium
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          4 GB
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          16 GB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows Vista Home Basic
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          4 GB
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          8 GB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows Vista Starter
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          1 GB
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Not applicable
        </p>
      </td>
    </tr>
  </table>
  
  <p>
    &#160;
  </p>
  
  <h3 style="font-weight:bold;font-size:1.07em;color:rgb(63,82,156);font-family:&#039;">
    <a id="physical_memory_limits_windows_home_server"></a>Physical Memory Limits: Windows Home Server
  </h3>
  
  <p>
    Windows Home Server is available only in a 32-bit edition. The physical memory limit is 4 GB.
  </p>
  
  <h3 style="font-weight:bold;font-size:1.07em;color:rgb(63,82,156);font-family:&#039;">
    <a id="physical_memory_limits_windows_server_2003"></a>Physical Memory Limits: Windows Server 2003
  </h3>
  
  <p>
    The following table specifies the limits on physical memory for Windows Server 2003.<br /> Limits over 4 GB for 32-bit Windows assume that<span class="Apple-converted-space">&#160;</span><a style="color:rgb(19,100,196);text-decoration:none;" href="http://msdn.microsoft.com/en-us/library/aa366796(v=VS.85).aspx">PAE</a><span class="Apple-converted-space">&#160;</span>is enabled.
  </p>
  
  <table style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;width:1395px;border-bottom:rgb(187,187,187) 1px solid;border-collapse:collapse;">
    <tr style="vertical-align:top;">
      <th>
        Version
      </th>
      
      <th>
        Limit in 32-bit Windows
      </th>
      
      <th>
        Limit in 64-bit Windows
      </th>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Windows Server 2003 with Service Pack 2 (SP2), Datacenter Edition
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          128 GB
        </p>
        
        <p>
          64 GB with 4GT
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          IA64 2 TB
        </p>
        
        <p>
          X64 1 TB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Windows Server 2003 with Service Pack 2 (SP2), Enterprise Edition
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          64 GB
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          IA64 2 TB
        </p>
        
        <p>
          X64 1 TB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Windows Storage Server 2003, Enterprise Edition
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          8 GB
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Not applicable
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Windows Storage Server 2003
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          4 GB
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Not applicable
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Windows Server 2003 R2 Datacenter Edition
        </p>
        
        <p>
          Windows Server 2003 with Service Pack 1 (SP1), Datacenter Edition
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          128 GB
        </p>
        
        <p>
          16 GB with 4GT
        </p>
      </td>
      
      <td style="border-right:rg b(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          1 TB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Windows Server 2003 R2 Enterprise Edition
        </p>
        
        <p>
          Windows Server 2003 with Service Pack 1 (SP1), Enterprise Edition
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          64 GB
        </p>
        
        <p>
          16 GB with 4GT
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          1 TB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Windows Server 2003 R2 Standard Edition
        </p>
        
        <p>
          Windows Server 2003, Standard Edition SP1
        </p>
        
        <p>
          Windows Server 2003, Standard Edition SP2
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          4 GB
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          32 GB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Windows Server 2003, Datacenter Edition
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          128 GB
        </p>
        
        <p>
          16 GB with 4GT
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          512 GB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Windows Server 2003, Enterprise Edition
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          32 GB
        </p>
        
        <p>
          16 GB with 4GT
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          64 GB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Windows Server 2003, Standard Edition
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          4 GB
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          16 GB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Windows Server 2003, Web Edition
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          2 GB
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Not applicable
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Windows Small Business Server 2003
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          4 GB
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Not applicable
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Windows Compute Cluster Server 2003
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Not applicable
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          32 GB
        </p>
      </td>
    </tr>
  </table>
  
  <p>
    &#160;
  </p>
  
  <h3 style="font-weight:bold;font-size:1.07em;color:rgb(63,82,156);font-family:&#039;">
    <a id="physical_memory_limits_windows_xp"></a>Physical Memory Limits: Windows XP
  </h3>
  
  <p>
    The following table specifies the limits on physical memory for Windows XP.
  </p>
  
  <table style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;width:1395px;border-bottom:rgb(187,187,187) 1px solid;border-collapse:collapse;">
    <tr style="vertical-align:top;">
      <th>
        Version
      </th>
      
      <th>
        Limit in 32-bit Windows
      </th>
      
      <th>
        Limit in 64-bit Windows
      </th>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows XP
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          4 GB
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          128 GB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows XP Starter Edition
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          512 MB
        </p>
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          Not applicable
        </p>
      </td>
    </tr>
  </table>
  
  <p>
    &#160;
  </p>
  
  <h3 style="font-weight:bold;font-size:1.07em;color:rgb(63,82,156);font-family:&#039;">
    <a id="physical_memory_limits_win2k"></a>Physical Memory Limits: Windows 2000
  </h3>
  
  <p>
    The following table specifies the limits on physical memory for Windows 2000.
  </p>
  
  <table style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;width:1395px;border-bottom:rgb(187,187,187) 1px solid;border-collapse:collapse;">
    <tr style="vertical-align:top;">
      <th>
        Version
      </th>
      
      <th>
        Limit in 32-bit Windows
      </th>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows 2000 Professional
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          4 GB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows 2000 Server
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          4 GB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows 2000 Advanced Server
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          8 GB
        </p>
      </td>
    </tr>
    
    <tr style="vertical-align:top;">
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        Windows 2000 Datacenter Server
      </td>
      
      <td style="border-right:rgb(187,187,187) 1px solid;border-top:rgb(187,187,187) 1px solid;border-left:rgb(187,187,187) 1px solid;line-height:18px;border-bottom:rgb(187,187,187) 1px solid;background-color:rgb(255,255,255);margin:1px;padding:4px;">
        <p>
          32 GB
        </p>
      </td>
    </tr>
  </table>
  
  <p>
    &#160;
  </p>
  
  <h3 style="font-weight:bold;font-size:1.07em;color:rgb(63,82,156);font-family:&#039;">
    <a id="related_topics"></a>Related Topics
  </h3>
  
  <dl>
    <dt>
      <a style="color:rgb(19,100,196);text-decoration:none;" href="http://msdn.microsoft.com/en-us/library/bb613473(v=VS.85).aspx">4-Gigabyte Tuning</a>
    </dt>
    
    <dt>
      <a style="color:rgb(19,100,196);text-decoration:none;" href="http://msdn.microsoft.com/en-us/library/ms680349(v=VS.85).aspx">IMAGE_FILE_LARGE_ADDRESS_AWARE</a>
    </dt>
    
    <dt>
      <a style="color:rgb(19,100,196);text-decoration:none;" href="http://msdn.microsoft.com/en-us/library/aa366796(v=VS.85).aspx">Physical Address Extension</a>
    </dt>
  </dl>
  
  <p>
    &#160;
  </p>
  
  <p>
    &#160;
  </p>
  
  <p>
    <a title="Send comments about this topic to Microsoft" style="color:rgb(19,100,196);text-decoration:none;" href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20[memorybase]:%20Memory%20Limits%20for%20Windows%20Releases%20%20RELEASE:%20(10/14/2010)&body=%0A%0APRIVACY%20STATEMENT%0A%0AThe%20SDK%20team%20uses%20the%20feedback%20submitted%20to%20improve%20the%20SDK%20documentation.%20We%20do%20not%20use%20your%20email%20address%20for%20any%20other%20purpose.%20We%20will%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20you%20are%20reporting%20has%20been%20resolved.%20While%20we%20are%20working%20to%20resolve%20this%20issue,%20we%20may%20send%20you%20an%20email%20message%20to%20request%20more%20information%20about%20your%20feedback.%20After%20the%20issues%20have%20been%20addressed,%20we%20may%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20your%20feedback%20has%20been%20addressed.%0A%0AFor%20more%20information%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/en-us/default.aspx.">Send comments about this topic to Microsoft</a>
  </p>
  
  <p>
    Build date: 10/14/2010
  </p></p>
</div>

<p>
  </span></span>
</p>

<p>
  转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2010/10/31/memory-limits-for-windows-releasesfw/">Memory Limits for Windows Releases[FW]</a>
</p>