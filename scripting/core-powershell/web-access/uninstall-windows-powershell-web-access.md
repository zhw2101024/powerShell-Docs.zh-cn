---
title: "卸载 Windows PowerShell Web 访问"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: ee5e88ece27add955fcef3a9df0a441a08251e77

---

#  卸载 Windows PowerShell Web 访问

更新时间：2013年 6 月 24日

适用于：Windows Server 2012 R2、Windows Server 2012

按照本主题中的步骤从运行 Windows Server 2012 R2 或 Windows Server 2012 的网关服务器删除 Windows PowerShell Web 访问网站和应用程序。 开始前，先通知基于 Web 控制台的用户，你准备删除网站。

<a href="" id="BKMK_uninstall"></a>

------------------------------------------------------------------------

从网关服务器中卸载 Windows PowerShell Web 访问之前，运行 <span class="code">Uninstall-PswaWebApplication</span> cmdlet 删除网站和 Windows PowerShell Web 访问 Web 应用程序，或使用 IIS Manager 程序，即[通过使用 IIS Manager 删除 Windows PowerShell Web 访问网站和 Web 应用程序](#BKMK_delsite)。

卸载 Windows PowerShell Web 访问并不卸载 IIS 或任何其他自动安装的功能，因为 Windows PowerShell Web 访问需要它们处于运行状态。 卸载过程保留了依赖 Windows PowerShell Web 访问的功能；必要时你可以单独卸载那些功能。

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">建议（快速）卸载</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

本部分中的过程帮助你通过使用 Windows PowerShell cmdlet 卸载 Windows PowerShell Web 访问 Web 应用程序和 Windows PowerShell Web 访问功能。

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步骤 1：删除 Web 应用程序</span></a>

------------------------------------------------------------------------

如果指定了自己的自定义网站名称，请将 <span class="code">WebsiteName</span> 参数添加到命令中，并指定网站名称。 如果使用了自定义 Web 应用程序（不是默认应用程序 **pswa**)，请将 <span class="code">WebApplicationName</span> 参数添加到命令中，并指定 Web 应用程序的名称。

#### 使用 Uninstall-PswaWebApplication cmdlet 删除网站和 Web 应用程序

1.  执行以下操作之一，打开 Windows PowerShell 会话。

    -   在 Windows 桌面上，右键单击任务栏上的 Windows PowerShell。

    -   在 Windows **开始**屏幕上，单击**Windows PowerShell**。

2.  键入**Uninstall-PswaWebApplication**，然后按**Enter**。

3.  如果你使用的是测试证书，则将 <span class="code">DeleteTestCertificate</span> 参数添加到 cmdlet（如以下示例所述）。

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_28147344-ab2f-49e7-b1c2-6dbe649d4366'); "Copy to clipboard.")

        Uninstall-PswaWebApplication -DeleteTestCertificate

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步骤 2：卸载 Windows PowerShell Web 访问</span></a>

------------------------------------------------------------------------

#### 使用 Windows PowerShell cmdlet 卸载 Windows PowerShell Web 访问

1.  使用提升的用户权限执行以下操作之一打开 Windows PowerShell 会话。 如果会话已经打开，则继续执行下一步。

    -   在 Windows 桌面上，右键单击任务栏上的**Windows PowerShell**，然后单击**以管理员身份运行**。

    -   在 Windows **开始**屏幕上，右键单击**Windows PowerShell**，然后单击**以管理员身份运行**。

2.  键入以下内容，然后按 **Enter**，其中的 *computer\_name* 代表要从中删除 Windows PowerShell Web 访问的远程服务器。 如果在删除过程中有必要，<span class="code">–Restart</span> 参数将自动重新启动目标服务器。

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_7b534520-f292-471f-89e3-a1079c03e369'); "Copy to clipboard.")

        Uninstall-WindowsFeature –Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    若要在离线的 VHD 上删除角色和功能，你必须添加 <span class="code">-ComputerName</span> 参数和 <span class="code">-VHD</span> 参数。 <span class="code">-ComputerName</span> 参数含有安装 VHD 的服务器的名称，<span class="code">-VHD</span> 参数含有 VHD 文件在指定服务器上的路径。

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_5d8f91ee-b91a-4653-b7df-e745187fd72d'); "Copy to clipboard.")

        Uninstall-WindowsFeature –Name WindowsPowerShellWebAccess –VHD <path> -ComputerName <computer_name> -Restart

3.  删除完成后，验证你已删除 Windows PowerShell Web 访问，方法是打开服务管理器中的“所有服务器”页面，选择要删除其功能的服务器，然后在选定服务器的页面上查看“角色和功能”磁贴。 你也可以将选定的服务器作为目标运行 <span class="code">Get-WindowsFeature</span> cmdlet (Get-WindowsFeature -ComputerName &lt;*computer\_name*&gt;)，以查看该服务器上安装的角色和功能的列表。

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">自定义卸载</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

本部分中的过程帮助你通过使用服务管理器中的“删除角色和功能向导”和 IIS 管理器卸载 Windows PowerShell Web 访问 Web 应用程序和 Windows PowerShell Web 访问功能。

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步骤 1：删除 Web 应用程序</span></a>

------------------------------------------------------------------------

#### 使用 IIS 管理器删除 Windows PowerShell Web 访问网站和 Web 应用程序

1.  通过执行以下操作之一，打开 IIS 管理器控制台。 如果该控制台已经打开，则继续执行下一步。

    -   在 Windows 桌面上，启动服务器管理器，方法是单击 Windows 任务栏中的“服务器管理器”。 在“服务器管理器”的**工具**菜单中，单击**Internet Information Services (IIS) Manager**。

    -   在 Windows“开始”屏幕上，键入“Internet 信息服务 (IIS) 管理器”名称的任何部分。 当快捷方式在“应用程序”结果中显示时，单击它。

2.  在 IIS 管理器树窗格中，选择运行 Windows PowerShell Web 访问 Web 应用程序的网站。

3.  在**操作**窗格中，在**管理网站**下，单击**停止**。

4.  在树窗格中，右键单击运行 Windows PowerShell Web 访问 Web 应用程序的网站中的 Web 应用程序，然后单击**删除**。

5.  在树窗格中，选择“应用程序池”，并选择 Windows PowerShell Web 访问应用程序池文件夹，单击“操作”窗格中的“停止”，然后单击内容窗格中的“删除”。

6.  关闭 IIS 管理器。

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">注意 </span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>在卸载过程中未删除证书。 如果你创建了自签名的证书或使用测试证书，现想将它删除，则可在 IIS 管理器中删除该证书。</p></td>
    </tr>
    </tbody>
    </table>

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步骤 2：卸载 Windows PowerShell Web 访问</span></a>

------------------------------------------------------------------------

#### 使用“删除角色和功能向导”卸载 Windows PowerShell Web 访问

1.  如果服务管理器已经打开，则继续执行下一步。 如果服务器管理器尚未打开，请执行以下任一操作打开它。

    -   在 Windows 桌面上，启动服务器管理器，方法是单击 Windows 任务栏中的“服务器管理器”。

    -   在 Windows **开始**屏幕上，单击**服务器管理器**。

2.  在**管理**菜单上，单击**删除角色和功能**。

3.  在“选择目标服务器”页面上，选择你想删除其功能的服务器或离线 VHD。 若要选择离线的 VHD，请选择安装 VHD 的服务器，然后选择 VHD 文件。 选择目标服务器后，单击**下一步**。

4.  再次单击“下一步”，跳到“删除功能”页面。

5.  清除**Windows PowerShell Web 访问**复选框，然后单击**下一步**。

6.  在**确认删除选择**页面上，单击**删除**。

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">另请参阅</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

[安装和使用 Windows PowerShell Web 访问](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[IIS Manager 7.0 帮助](https://technet.microsoft.com/library/cc732664.aspx)

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


