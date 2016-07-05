---
title: "使用基于 Web 的 Windows PowerShell 控制台"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 02964dd763ccccbf27a963c0f8eef20aa23cc117

---

#  使用基于 Web 的 Windows PowerShell 控制台

更新时间：2013年 6 月 24日

适用于：Windows Server 2012 R2、Windows Server 2012

Windows PowerShell® Web 访问让 Windows PowerShell® 用户登录到由安全套接字层 (SSL) 确保安全的网站，以使用 Windows PowerShell 会话、cmdlet 和脚本管理远程计算机。 由于 Windows PowerShell 控制台在 Web 浏览器中运行，因此，它可从各种客户端设备中打开，包括手机、平板电脑、公用计算机展台、便携式计算机或共享或借来的计算机。 基于 Web 的 Windows PowerShell 控制台以用户在登录过程中指定的远程计算机为目标。 本主题描述如何登录以及开始使用 Windows PowerShell Web 访问基于 Web 的控制台。

本主题不描述如何使用 Windows PowerShell 或运行 cmdlet 或脚本。 有关如何使用 Windows PowerShell 和脚本资源的信息，请参阅本主题结尾的“另请参阅”部分。

本主题内容：

-   [受支持的浏览器和客户端设备](#BKMK_browser)

-   [登录到 Windows PowerShell Web Access](#BKMK_sign)

-   [注销和超时](#BKMK_timeout)

-   [基于 Web 的 Windows PowerShell 控制台的独特之处](#BKMK_web)

<a href="" id="BKMK_browser"></a>
------------------------------------------------------------------------

Windows PowerShell Web 访问支持以下 Internet 浏览器。 虽然移动浏览器未正式受到支持，但许多此类浏览器均可运行基于 Web 的 Windows PowerShell 控制台。 其他接受 Cookies、运行 JavaScript 和 HTTPS 网站的浏览器有望投入使用，但尚未接受正式测试。

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">受支持的台式计算机浏览器</span></a>

------------------------------------------------------------------------

-   Microsoft Windows® 8.0、9.0、10.0 和 11.0 的 Windows® Internet Explorer®

-   Mozilla Firefox(R) 10.0.2

-   Windows 的 Google Chrome(TM) 17.0.963.56m

-   用于 Windows 的 Apple Safari® 5.1.2

-   用于 Mac OS® 的 Apple Safari 5.1.2

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">经过最小限度测试的移动设备或浏览器</span></a>

------------------------------------------------------------------------

-   Windows Phone 7 和 7.5

-   Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)

-   iPhone 操作系统 5.0.1 的 Apple Safari

-   iPad 2 操作系统 5.0.1 的 Apple Safari

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">浏览器要求</span></a>

------------------------------------------------------------------------

若要使用 Windows PowerShell Web 访问基于 Web 的控制台，浏览器必须执行以下操作。

-   允许 Windows PowerShell Web 访问网关网站中的 Cookie。

-   可打开和访问 HTTPS 页面。

-   打开和运行使用 JavaScript 的网站。

<a href="" id="BKMK_sign"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">登录到 Windows PowerShell Web Access</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

Windows PowerShell Web 访问管理员应为你提供一个 URL，该 URL 是贵组织 Windows PowerShell Web 访问网关网站的地址。 默认情况下，此网址的地址为 https://&lt;server\_name&gt;/pswa。 在登录到 Windows PowerShell Web 访问之前，确保拥有想要管理的远程计算机的名称或 IP 地址。 你必须是远程计算机上的授权用户，并且必须将远程计算机配置为可远程管理。 有关将计算机配置为可远程管理的详细信息，请参阅[在 Windows PowerShell 中启用和使用远程命令](https://technet.microsoft.com/magazine/ff700227.aspx)。 将计算机配置为可远程管理的最简单方法是：在使用提升的用户权限打开的 Windows PowerShell 会话中（**以管理员身份运行**），在计算机上运行**Enable-PSRemoting -force** cmdlet。

### 登录到 Windows PowerShell Web Access

1.  在 Internet 浏览器窗口或选项卡中打开 Windows PowerShell Web 访问网站。

2.  在 Windows PowerShell Web 访问登录页面中，提供你的网络用户名、密码以及你想管理（以及你是其授权用户）的计算机的名称。 如果 Windows PowerShell Web 访问管理员指示你将 URI（而非计算机名称）用于自定义网站或代理服务器，请在“连接类型”字段中选择“连接 URI”，然后提供 URI。

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
    <td><ul>
    <li><p>如果目标计算机在工作组中，则使用以下语法提供你的用户名并登录到计算机：&lt;<em>workgroup_name</em>&gt;\&lt;<em>user_name</em>&gt;。</p></li>
    <li><p>如果目标计算机是网关服务器，则可在“计算机名”<strong></strong>字段中指定“localhost”<strong></strong>。</p></li>
    <li><p>如果目标计算机是网关服务器，并且该网关服务器在工作组中，则可在“<strong>计算机名</strong>”字段中使用“<strong>localhost</strong>”，但不可在“<strong>用户名</strong>”字段中使用 localhost\&lt;<em>user_name</em>&gt;。 必须使用 &lt;<em>workgroup name</em>&gt;\&lt;<em>user_name</em>&gt;。</p></li>
    </ul></td>
    </tr>
    </tbody>
    </table>

3.  “可选的连接设置”部分涉及你想要管理的远程计算机的授权要求。 有关与可选的连接设置等效的参数的详细信息，请参阅 [Enter-PSSession cmdlet 帮助](https://technet.microsoft.com/library/dd315384.aspx)。

    一般情况下，你用于通过 Windows PowerShell Web 访问网关的凭据与你想要管理的远程计算机所识别的凭据是一样的。 但是，如果你想要使用不同的凭据管理你在步骤 2 中指定的远程计算机，请展开“可选的连接设置”部分，并提供备用凭据。 否则，请跳到步骤 6。

4.  如果 Windows PowerShell Web 访问管理员已经为 Windows PowerShell Web 访问用户创建了自定义会话配置，则在“配置名称”字段中键入会话配置名称。 有关会话配置的详细信息，请参阅 Microsoft 网站上的 [about\_Session\_Configurations](https://technet.microsoft.com/library/dd819508.aspx)。

5.  除非 Windows PowerShell Web 访问管理员指示你以其他方式处理，否则将“身份验证类型”设置保持为“默认”。

6.  单击**登录**。

<a href="" id="BKMK_timeout"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">注销和超时</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

执行以下任一操作，均可注销基于 Web 的 Windows PowerShell 会话。

-   在控制台的右下角单击“注销”。 （仅限 Windows Server 2012）

-   在控制台的右下角单击“保存”或“退出”（仅适用于 Windows Server 2012 R2）。 单击“保存”将保存并关闭你的 Windows PowerShell Web 访问会话；稍后可以重新连接到该会话。 再次登录到 Windows PowerShell Web 访问时，Windows PowerShell Web 访问将显示已保存会话的列表；你可以选择并重新连接到某个已保存的会话，也可以启动新的会话。 允许用户打开的最大会话数（包括已保存的会话和活动会话）由网关管理员配置。

    单击“退出”将直接注销 Windows PowerShell Web 访问会话，而不保存该会话。

-   尝试登录，以便在相同的浏览器会话中或在相同浏览器会话的新选项卡中，管理不同的远程计算机。 （这种情况不适用于运行 Windows Server 2012 R2 的网关服务器；Windows Server 2012 R2 上运行的 Windows PowerShell Web 访问允许在相同浏览器会话的新选项卡中打开多个用户会话。）有关如何在相同计算机上使用多个活动会话的详细信息，请参阅本主题[基于 Web 的控制台的限制](#BKMK_limits)部分中的“同时连接到多台目标计算机”。

-   会话停止活动 20 分钟。 网关管理员可以自定义停止活动超时时间；有关详细信息，请参阅[会话管理](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx#BKMK_sesmgmt)。

    -   如果你从基于 Web 的控制台中的会话断开连接是由于网络错误或其他计划外关机或故障，而不是因为自己关闭了会话，Windows PowerShell Web 访问会话将继续运行并连接到目标计算机，直到客户端的超时期结束。 默认情况下，此超时期为 20 分钟，并由网关管理员配置。 会话在默认的 20 分钟或网关管理员指定的超时期（以时间较短者为准）后断开连接。

        如果网关服务器正在运行 Windows Server 2012 R2，Windows PowerShell Web 访问将允许用户稍后重新连接到已保存的会话，但是，需在网关管理员指定的超时期过后，才能查看或重新连接到已保存的会话。

-   关闭浏览器窗口或选项卡。

-   关闭正在运行浏览器的客户端设备，或将它从网络中断开。

-   在 Web 控制台中运行“退出”命令。 如果已连接的会话配置为支持 [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) 模式，或处于受限的运行空间中，则此命令不可用。

如果你想再次登录，则再次打开 Windows PowerShell Web 访问网页，然后执行本主题中[登录到 Windows PowerShell Web 访问](#BKMK_signin)部分的以下步骤，即可登录。

<a href="" id="BKMK_web"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">基于 Web 的 Windows PowerShell 控制台的独特之处</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

在登录到 Windows PowerShell Web 访问之后, 在浏览器窗口或选项卡中将打开一个基于 Web 的 Windows PowerShell 控制台。 因为控制台连接到你在登录过程中指定的远程计算机，所以在控制台中仅可使用那些在远程计算机上可用的 Windows PowerShell cmdlet 或脚本。 本部分介绍 Windows PowerShell Web 访问控制台存在的限制，以及 Windows PowerShell Web 访问控制台和已安装的 **PowerShell.exe** 控制台之间的差异。

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">PowerShell.exe 的功能差异</span></a>

------------------------------------------------------------------------

大多数 Windows PowerShell 主机功能都可在 Windows PowerShell Web 访问基于 Web 的控制台中使用，但有些功能则不可用。

-   <span class="label">将会显示嵌套的进度。</span>  Windows PowerShell Web 访问显示 cmdlet 的进度 GUI（报告进度），但仅显示最高层的进度信息。

-   <span class="label">输入颜色修改。</span>  无法更改输入颜色（前景和背景）。 输出风格、警告、详细和错误信息均可通过运行脚本进行更改。

-   <span class="label">PSHostRawUserInterface。</span>  Windows PowerShell Web 访问通过 Windows PowerShell 远程管理实施，并且使用远程运行空间。 Windows PowerShell Web 访问在此界面不执行一些方法；例如，任何写入 Windows 控制台的命令。 **PowerTab** 等命令在 Windows PowerShell Web 访问中不起作用。

-   <span class="label">功能键。</span>  在许多种情况下，Windows PowerShell Web 访问并不支持一些功能键，因为浏览器保留了此类命令。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>不受支持的功能键</p></th>
<th><p>操作</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Ctrl+C</p></td>
<td><p>在 Windows PowerShell Web 访问中，浏览器使用 <strong>Ctrl + C</strong> 复制内容。 控制台提供“取消”<strong></strong>按钮，用户还可使用 <strong>Ctrl+Q</strong> 来取消命令。</p></td>
</tr>
<tr class="even">
<td><p>Alt-space、e、l</p></td>
<td><p>滚动屏幕缓冲区</p></td>
</tr>
<tr class="odd">
<td><p>Alt+Space、e、f</p></td>
<td><p>搜索屏幕缓冲区中的文本</p></td>
</tr>
<tr class="even">
<td><p>Alt+Space、e、k</p></td>
<td><p>选择从屏幕缓冲区中复制而来的文本</p></td>
</tr>
<tr class="odd">
<td><p>Alt+Space、e、p</p></td>
<td><p>将剪贴板内容粘贴到 Windows PowerShell 控制台</p></td>
</tr>
<tr class="even">
<td><p>Alt+Space、c</p></td>
<td><p>关闭 Windows PowerShell 控制台</p></td>
</tr>
<tr class="odd">
<td><p>Ctrl+Break</p></td>
<td><p>强制关闭 Windows PowerShell 窗口</p></td>
</tr>
<tr class="even">
<td><p>Ctrl+Home</p></td>
<td><p>从当前命令行的开始部分删除</p></td>
</tr>
<tr class="odd">
<td><p>Ctrl+End</p></td>
<td><p>在命令行的末尾结束删除</p></td>
</tr>
<tr class="even">
<td><p>F1</p></td>
<td><p>将光标向命令行的右侧移动一个字符</p></td>
</tr>
<tr class="odd">
<td><p>F2</p></td>
<td><p>通过将最后一个命令复制到你键入的字符，创建新的命令</p></td>
</tr>
<tr class="even">
<td><p>F3</p></td>
<td><p>用最后一个命令行中的内容完成命令行</p></td>
</tr>
<tr class="odd">
<td><p>F4</p></td>
<td><p>从光标位置删除字符</p></td>
</tr>
<tr class="even">
<td><p>F5</p></td>
<td><p>向后扫描你的命令历史记录。 若要访问 Windows PowerShell Web 访问的命令历史记录中的命令，请在基于 Web 的控制台中单击“历史记录”<strong></strong>滚动按钮。</p></td>
</tr>
<tr class="odd">
<td><p>F7</p></td>
<td><p>从命令历史记录中交互选择一个命令</p></td>
</tr>
<tr class="even">
<td><p>F8</p></td>
<td><p>扫描与当前文本匹配的历史记录显示命令</p></td>
</tr>
<tr class="odd">
<td><p>F9</p></td>
<td><p>运行历史记录中特定编号的命令</p></td>
</tr>
<tr class="even">
<td><p>Page Up</p></td>
<td><p>运行历史记录中的第一个命令</p></td>
</tr>
<tr class="odd">
<td><p>Page Down</p></td>
<td><p>运行历史记录中的最后一个命令</p></td>
</tr>
<tr class="even">
<td><p>Alt+F7</p></td>
<td><p>清空命令历史记录列表</p></td>
</tr>
</tbody>
</table>

<a href="" id="BKMK_limits"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">基于 Web 的控制台的限制</span></a>

------------------------------------------------------------------------

-   <span class="label">双跃点。</span>   如果尝试通过使用 Windows PowerShell Web 访问来创建或运行新的会话，你会遇到双跃点（或从第一个连接到第二台计算机之间的连接）限制。 Windows PowerShell Web 访问使用远程运行空间，目前，**PowerShell.exe** 不支持建立从远程运行空间到第二台计算机的远程连接。 例如，如果你尝试使用 **Enter-PSSession** cmdlet 从现有的连接连接到第二台远程计算机，你会遇到各种错误，例如“无法获得网络资源”。

    若要避免双跃点错误，你的管理员应在你组织的网络环境中配置 CredSSP 身份验证。 有关如何配置 CredSSP 身份验证的详细信息，请参阅 Microsoft 网站上的[适用于第二跃点远程处理的 CredSSP](http://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx)。 当你想要管理第二台远程计算机时，你还可提供显式凭据；隐式凭据不可能接受第二跃点。

-   Windows PowerShell Web 访问使用远程 Windows PowerShell 会话并具有与它相同的限制。 直接调用 Windows 控制台 API 的命令（例如基于控制台的编辑器或基于文本的菜单程序）不可用，因为此类命令不可读取或写入标准的输入、输出和错误管道。 因此，启用可执行文件（如 **notepad.exe**）或显示 GUI（如 <span class="code">OpenGridView</span> 或 <span class="code">ogv</span>）的命令不可用。 此操作将影响你的体验；你会觉得好像 Windows PowerShell Web 访问并不响应你的命令。

-   Tab 自动补全不适用于带有受限运行空间的会话配置或在 **NoLanguage** 模式下的会话配置。 虽然管理员可以配置会话以支持选项卡完成，但出于安全考虑，建议不要这样做，因为此操作会向未授权用户披露以下信息。

    -   内部文件系统路径

    -   内部计算机上的共享文件夹

    -   运行空间中的变量

    -   已加载的类型或 .NET Framework 名称空间

    -   环境变量

-   登录到 **NoLanguage** 会话配置或 Windows PowerShell Web 访问的受限运行空间的用户不能运行“退出”命令以结束会话。 若要注销，用户应在控制台页面上单击“注销”。

-   <span class="label">同时连接到多台目标计算机。</span>   如果网关服务器正在运行 Windows Server 2012，Windows PowerShell Web 访问仅允许每个浏览器会话连接一台远程计算机；它不允许用户只登录一次，即使用独立的浏览器选项卡连接到多台远程计算机。 当你打开新的选项卡或浏览器窗口时，Windows PowerShell Web 访问将提示你断开当前的会话，并启动新的会话，以使你可以连接到新的（或相同的）远程计算机。 但是，如果不同的远程计算机需要两个或更多独立会话，Internet Explorer 中的某一功能可让你创建新的会话。 若要在 Internet Explorer 中启动新的浏览器会话，请按下 **ALT**，打开“文件”菜单，然后选择“新建会话”。 随后在新的会话中打开 Windows PowerShell Web 访问网站，登录即可访问其他远程计算机。

    当 Windows PowerShell Web 访问网关在 Windows Server 2012 R2 上运行时，用户可以在不同的浏览器选项卡中打开与远程计算机之间的多个连接。 如果想要使用基于 Web 的 Windows PowerShel 控制台打开与远程计算机之间的多个连接，请咨询 Windows PowerShell Web 访问网关管理员，了解网关服务器是否支持此功能。

-   <span class="label">持续的 Windows PowerShell 会话（重新连接）。</span>   Windows PowerShell Web 访问网关超时后，网关和目标计算机之间的远程连接将关闭。 这会阻止当前正在运行的任何 cmdlet 或脚本。 当你执行长时间运行的任务时，建议使用 **-Job** 基础结构，这样就可以启动作业，断开计算机的连接，稍后重新连接，让作业持续进行。 使用 **-Job** cmdlet 的另一个好处是可以使用 Windows PowerShell Web 访问启动它们，注销并通过运行 Windows PowerShell Web 访问或另一台主机（如 Windows PowerShell® 集成脚本环境 (ISE)）来重新连接它们。

-   <span class="label">调整控制台大小。</span>   可通过以下三种方式调整 **PowerShell.exe** 控制台窗口大小。

    -   拖动并使用鼠标调整控制台窗口大小

    -   使用控制台属性的 GUI，更改高度和宽度属性

    -   使用 cmdlet，更改控制台窗口的高度和宽度

        可按以下方式使用 cmdlet 来配置 Windows PowerShell Web 访问控制台窗口。 在下例中，用户将 Windows PowerShell Web 访问控制台的宽度更改为**20**。

        [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_778d5e55-9195-4bd7-b313-d1fbca7876e4'); "Copy to clipboard.")

            $newSize = $Host.UI.RawUI.WindowSize
            $newSize.Width = $newSize.Width - 20

            $oldSize = $Host.UI.RawUI.WindowSize

            $Host.UI.RawUI.WindowSize = $newSize

        你可以使用类似的方式更改控制台的高度。

        如要获取自定义控制台视图的其他示例，请参阅 [Windows PowerShell 团队博客](http://blogs.msdn.com/b/powershell/)。

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">另请参阅</span></a>
<a href="/en-us/library/hh831417(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

[Windows PowerShell Cmdlet 参考](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
[ Microsoft TechNet 上的 Windows PowerShell](https://technet.microsoft.com/library/bb978526.aspx)
[TechNet 脚本中心存储库](http://gallery.technet.microsoft.com/scriptcenter)
[脚本中心 - 嗨，脚本专家！](https://technet.microsoft.com/scriptcenter)
[Windows PowerShell 团队博客](http://blogs.msdn.com/b/powershell/)

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


