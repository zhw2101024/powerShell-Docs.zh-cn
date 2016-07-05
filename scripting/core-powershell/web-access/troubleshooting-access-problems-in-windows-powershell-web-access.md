---
title: "Windows PowerShell Web 访问中的访问问题疑难解答"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 6366ec9c49f721b758b6a520f68cf2b3c5ee0caf

---

#  Windows PowerShell Web 访问中的访问问题疑难解答

更新时间： 2013年 6 月 24日

适用于：Windows Server 2012 R2、Windows Server 2012

<a href="" id="BKMK_trouble"></a>

------------------------------------------------------------------------

下表识别了一些用户使用 Windows PowerShell Web 访问尝试连接到远程计算机时可能遇到的常见问题，其中包括解决这些问题的建议。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>问题</p></th>
<th><p>可能原因和解决方案</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>登录失败</p></td>
<td><p>失败可能是由于下列某个原因所至：</p>
<ul>
<li><p>允许用户访问计算机的授权规则或远程计算机上的特定会话配置并不存在。 Windows PowerShell Web 访问安全是严谨的；必须使用授权规则明确赋予用户访问远程计算机的权限。 有关创建授权规则的详细信息，请参阅本指南中的 <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Windows PowerShell Web 访问的授权规则和安全功能</a>。</p></li>
<li><p>用户未获得访问目标计算机的权限。 这是由访问控制列表 (ACL) 来确定的。 有关详细信息，请参阅<a href="https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx">使用基于 Web 的 Windows PowerShell 控制台</a>中的“登录到 Windows PowerShell Web 访问”或 <a href="https://msdn.microsoft.com/library/windows/desktop/ee706585.aspx">Windows PowerShell Team Blog</a>（Windows PowerShell 团队博客）。</p>
<ul>
<li><p>可能无法在目标计算机上启用 Windows PowerShell 远程管理。 验证它是否已在用户尝试连接的计算机上启用。 有关详细信息，请参阅 Windows PowerShell 相关帮助主题中 <a href="https://technet.microsoft.com/library/dd315349.aspx">about_Remote_Requirements</a> 的“如何为进行远程处理而配置计算机”。</p></li>
</ul></li>
</ul></td>
</tr>
<tr class="even">
<td><p>当用户尝试在 Internet Explorer 窗口中登录到 Windows PowerShell Web 访问时，会向他们显示“内部服务器错误”<strong></strong>页面或 Internet Explorer 停止响应。 此问题特定于 Internet Explorer。</p></td>
<td><p>对于已使用包含中文字符的域名登录的用户或网关服务器名称中包含一个或多个中文字符时会出现此问题。 若要解决此问题，用户应<a href="http://ie.microsoft.com/testdrive/info/downloads/Default.html">安装并运行 Internet Explorer 10</a>，然后执行以下步骤。</p>
<ol>
<li><p>将 Internet Explorer“文档模式”<strong></strong>设置更改为“IE10 标准”<strong></strong>。</p>
<ol>
<li><p>按 <strong>F12</strong> 可打开“开发人员工具”控制台。</p></li>
<li><p>在 Internet Explorer 10 中，单击“浏览器模式”<strong></strong>，然后选择“Internet Explorer 10”<strong></strong>。</p></li>
<li><p>单击“文档模式”<strong></strong>，然后单击“IE10 标准”<strong></strong>。</p></li>
<li><p>再次按 <strong>F12</strong> 可关闭“开发人员工具”控制台。</p></li>
</ol></li>
<li><p>禁用自动代理配置。</p>
<ol>
<li><p>在 Internet Explorer 10 中，单击“工具”<strong></strong>，然后单击“Internet 选项”<strong></strong>。</p></li>
<li><p>在“Internet 选项”<strong></strong>对话框中的“连接”<strong></strong>选项卡上，单击“LAN 设置”<strong></strong>。</p></li>
<li><p>清除“自动检测设置”<strong></strong>复选框。 单击“确定”<strong></strong>，然后再次单击“确定”<strong></strong>可关闭“Internet 选项”<strong></strong>对话框。</p></li>
</ol></li>
</ol></td>
</tr>
<tr class="odd">
<td><p>无法连接到远程工作组计算机</p></td>
<td><p>如果目标计算机在工作组中，则使用以下语法，提供你的用户名，并且登录到计算机：&lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;</p></td>
</tr>
<tr class="even">
<td><p>找不到 Web 服务器 (IIS) 管理工具，即使已安装了角色</p></td>
<td><p>如果你通过使用 <span class="code">Install-WindowsFeature</span> cmdlet 安装了 Windows PowerShell Web 访问，则不会安装管理工具，除非将 <span class="code">IncludeManagementTools</span> 参数添加到该 cmdlet。 例如，参阅<a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">安装和使用 Windows PowerShell Web 访问</a>中的“使用 Windows PowerShell cmdlet 安装 Windows PowerShell Web 访问”。 你可选择在以网关服务器为目标的“添加角色和功能向导”会话中的工具，添加 IIS 管理器控制台及其他你需要的 IIS 管理工具。 “添加角色和功能向导”可从服务器管理器中打开。</p></td>
</tr>
<tr class="odd">
<td><p>无法访问 Windows PowerShell Web 访问网站</p></td>
<td><p>如果已在 Internet Explorer 中启用了增强的安全配置 (IE ESC)，你可以将 Windows PowerShell Web 访问网站添加到受信任的站点列表，或禁用 IE ESC。 你可以在服务器管理器中的“本地服务器”<strong></strong>页面上的“属性”<strong></strong>磁贴中禁用 IE ESC。</p></td>
</tr>
<tr class="even">
<td><p>尝试当网关服务器为目标计算机且又位于工作组中时连接，会显示以下错误消息：“出现授权失败。”<strong> 请验证你是否被授权连接到目标计算机。</strong></p></td>
<td><p>当网关服务器也是目标服务器且位于工作组中时，指定下表所示的用户名、计算机名称以及用户组名。 不要使用点 (.) 自行表示计算机名称。</p>
<div>
<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th><p>方案</p></th>
<th><p>UserName 参数</p></th>
<th><p>UserGroup 参数</p></th>
<th><p>ComputerName 参数</p></th>
<th><p>ComputerGroup 参数</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>网关服务器位于域中</p></td>
<td><p><em>Server_name</em>\<em>user_name</em>、Localhost\<em>user_name</em> 或 .\<em>user_name</em></p></td>
<td><p><em>Server_name</em>\<em>user_group</em>、Localhost\<em>user_group</em> 或 .\<em>user_group</em></p></td>
<td><p>网关服务器的完全限定名称或 Localhost</p></td>
<td><p><em>Server_name</em>\<em>computer_group</em>、Localhost\<em>computer_group</em> 或 .\<em>computer_group</em></p></td>
</tr>
<tr class="even">
<td><p>网关服务器位于工作组中</p></td>
<td><p><em>Server_name</em>\<em>user_name</em>、Localhost\<em>user_name</em> 或 .\<em>user_name</em></p></td>
<td><p><em>Server_name</em>\<em>user_group</em>、Localhost\<em>user_group</em> 或 .\<em>user_group</em></p></td>
<td><p>服务器名称</p></td>
<td><p><em>Server_name</em>\<em>computer_group</em>、Localhost\<em>computer_group</em> 或 .\<em>computer_group</em></p></td>
</tr>
</tbody>
</table>
</div>
<p>以目标计算机身份登录到网关服务器，方法是使用以下格式之一的凭据。</p>
<ul>
<li><p><em>Server_name</em>\<em>user_name</em></p></li>
<li><p>Localhost\<em>user_name</em></p></li>
<li><p>.\<em>user_name</em></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>在授权规则中显示安全标识符 (SID) 而不是语法 <em>user_name</em>/<em>computer_name</em> </p></td>
<td><p>规则不再有效或 Active Directory 域服务查询失败。 如果网关服务器曾一时位于工作组中，但后来加入域中，则这种情形下通常授权规则无效。</p></td>
</tr>
<tr class="even">
<td><p>无法登录到已在授权规则中指定为带有域的 IPv6 地址的目标计算机。</p></td>
<td><p>授权规则不支持域名形式的 IPv6 地址。 若要使用 IPv6 地址指定目标计算机，请在授权规则中使用原始 IPv6 地址（包含冒号）。 支持域和数值（带有冒号）IPv6 地址作为 Windows PowerShell Web 访问登录页面而非授权规则中的目标计算机名称。 有关 IPv6 地址的详细信息，请参阅 <a href="https://technet.microsoft.com/library/cc781672.aspx">How IPv6 Works</a>（IPv6 的工作原理）。</p></td>
</tr>
</tbody>
</table>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">另请参阅</span></a>
<a href="/en-us/library/dn282395(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

[Windows PowerShell Web 访问的授权规则和安全功能](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
[使用基于 Web 的 Windows PowerShell 控制台](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
[about\_Remote\_Requirements](https://technet.microsoft.com/library/dd315349.aspx)

<span>显示：</span>继承内容受保护

<span class="stdr-votetitle">此页面是否有所帮助？</span>
是 否

更多反馈？

<span class="stdr-count"><span class="stdr-charcnt">剩余 1500</span> 个字符</span> 提交 跳过此部分

<span class="stdr-thankyou">谢谢！</span> <span class="stdr-appreciate">我们非常感谢你的反馈意见。</span>

[管理你的个人资料](https://social.technet.microsoft.com/profile)

|

<a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> 站点反馈</a>站点反馈

<a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a>

告诉我们你的体验...

页面加载速度快吗？

<span> 是<span> </span></span> <span> 否<span> </span></span>

你喜欢页面设计吗？

<span> 是<span> </span></span> <span> 否<span> </span></span>

告诉我们更多内容

-   [快讯](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [联系我们](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [隐私声明](https://privacy.microsoft.com/privacystatement)
-   |
-   [使用条款](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [商标](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

© 2016 Microsoft

© 2016 Microsoft

链接到此站点或从中引用的第三方脚本或代码由拥有此类代码的第三方（而非 Microsoft）授权给你。 请参阅 ASP.NET Ajax CDN 使用条款 – http://www.asp.net/ajaxlibrary/CDN.ashx。
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />




<!--HONumber=Jun16_HO4-->


