#  安装和使用 Windows PowerShell Web 访问

更新时间：2013 年 11 月 5 日

适用于：Windows Server 2012 R2、Windows Server 2012

Windows PowerShell® Web 访问在 Windows Server® 2012 中首次引入，充当 Windows PowerShell 网关，提供以远程计算机为目标的基于 Web 的 Windows PowerShell 控制台。 它可让 IT 专业人士在 Web 浏览器中运行来自 Windows PowerShell 控制台的 Windows PowerShell 命令和脚本，无需在客户端设备上安装 Windows PowerShell、远程管理软件或浏览器插件。 运行基于 web 的 Windows PowerShell 控制台只需要正确配置的 Windows PowerShell Web 访问网关以及支持 JavaScript® 和接受 Cookie 的客户端设备浏览器。

客户端设备的示例包括便携式计算机、非工作的个人计算机、借来的计算机、平板计算机、Web 展台、不运行基于 Windows 的操作系统的计算机和手机浏览器。 IT 专业人士可在远程基于 Windows 的服务器上执行重要的管理任务，这些服务器所属的设备配有 Web 浏览器，并可访问 Internet 连接。

成功安装和配置网关后，用户可通过使用 Web 浏览器访问 Windows PowerShell 控制台。 当用户打开安全的 Windows PowerShell Web 访问网站时，他们可在成功通过身份验证后运行基于 Web 的 Windows PowerShell 控制台。

Windows PowerShell Web 访问安装和配置过程包含三个步骤：

1.  安装 Windows PowerShell Web 访问

2.  配置网关

3.  配置允许用户访问基于 Web 的 Windows PowerShell 控制台的授权规则

安装和配置 Windows PowerShell Web Access 前，我们建议你阅读该完整指南，其中包括有关如何安装、保护和卸载 Windows PowerShell Web 访问的说明。 [使用基于 Web 的 Windows PowerShell 控制台](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)主题介绍了用户如何登录基于 Web 的控制台，并涵盖基于 Web 的 Windows PowerShell 控制台与 **powershell.exe** 控制台之间的限制和差异。 基于 Web 的控制台的最终用户应阅读[使用基于 Web 的 Windows PowerShell 控制台](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)部分，但无需阅读本指南的其余部分。

本主题并不提供详尽的 Web Server (IIS) 操作指导；仅描述了配置 Windows PowerShell Web Access 网关所必需的步骤。 有关配置和保护 IIS 中的网站安全的详细信息，请参阅“另请参阅”部分中的 IIS 文档资源。

下图显示 Windows PowerShell Web 访问的工作原理。

<span><img src="https://i-technet.sec.s-msft.com/dynimg/IC564303.jpeg" title="Windows PowerShell Web Access diagram" alt="Windows PowerShell Web Access diagram" id="ee15fa8f-ce13-49e5-933d-514f6d60a2b1" /></span>

本主题内容：

-   [运行 Windows PowerShell Web 访问的要求](#BKMK_reqs)

-   [浏览器和客户端设备支持](#BKMK_browser)

-   [建议（快速）部署](#BKMK_recm)

-   [自定义部署](#BKMK_custom)

-   [配置正版证书](#BKMK_configcert)

<a href="" id="BKMK_reqs"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">运行 Windows PowerShell Web 访问的要求</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_0" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

Windows PowerShell Web 访问需要 Web 服务器 (IIS)、.NET Framework 4.5 和 Windows PowerShell 3.0 或 Windows PowerShell 4.0 在你想运行网关的服务器上运行。 通过使用服务器管理器中的“添加角色和功能向导”或适用于服务器管理器的 Windows PowerShell 部署 cmdlet，你可以在运行 Windows Server 2012 R2 或 Windows Server 2012 的服务器上安装 Windows PowerShell Web 访问。 当你使用服务器管理器或其部署 cmdlet 安装 Windows PowerShell Web 访问时，所需的角色和功能将在安装过程中自动添加。

Windows PowerShell Web 访问可让远程用户使用 Web 浏览器中的 Windows PowerShell 访问你组织中的计算机。 虽然 Windows PowerShell Web 访问是便利和功能强大的管理工具，但基于 Web 的访问存在安全风险，应尽可能安全地配置。 我们建议配置 Windows PowerShell Web 访问网关的管理员使用可用的安全层，它们分别是包括在 Windows PowerShell Web 访问内的基于 cmdlet 的授权规则以及在 Web 服务器 (IIS) 中和第三方应用程序中可用的安全层。 本文档包括仅建议在测试环境中使用的不安全示例以及建议在安全部署过程中使用的示例。

<a href="" id="BKMK_browser"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">浏览器和客户端设备支持</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

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

<a href="" id="BKMK_recm"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">建议（快速）部署</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

通过使用 Windows PowerShell cmdlet 或从服务器管理器中打开的“添加角色和功能向导”，你可以在运行 Windows Server 2012 R2 或 Windows Server 2012 的服务器上安装 Windows PowerShell Web 访问网关。 对于快速安装和配置，使用 Windows PowerShell cmdlet，如本部分中所述。

-   [步骤 1：安装 Windows PowerShell Web 访问](#BKMK_step1)

-   [步骤 2：配置网关](#BKMK_step2)

-   [步骤 3：配置受限的授权规则](#BKMK_step3)

<a href="" id="BKMK_step1"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步骤 1：安装 Windows PowerShell Web 访问</span></a>

------------------------------------------------------------------------

#### 使用 Windows PowerShell cmdlet 安装 Windows PowerShell Web 访问

1.  使用提升的用户权限执行以下操作之一以打开 Windows PowerShell 会话。

    -   在 Windows 桌面上，右键单击任务栏上的 Windows PowerShell，然后单击“以管理员身份运行”.

    -   在 Windows“开始”屏幕上，右键单击“Windows PowerShell”，然后单击“以管理员身份运行”.

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
    <td><p>在 Windows PowerShell 3.0 和 4.0 中，在运行作为模块一部分的 cmdlet 之前，无需将 Server Manager cmdlet 模块导入到 Windows PowerShell 会话。 在你首次运行 cmdlet（模块的一部分）时，模块被自动导入。 此外，Windows PowerShell cmdlet 不区分大小写。</p></td>
    </tr>
    </tbody>
    </table>

2.  键入以下内容，然后按 **Enter**，其中 *computer_name* 代表要安装 Windows PowerShell Web 访问的远程计算机（如果适用）。 必要时，<span class="code">Restart</span> 参数会自动重新启动目标服务器。

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_374a9c21-4f6e-471e-b957-bb190a594533'); "Copy to clipboard.")

        Install-WindowsFeature –Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart

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
    <td><p>使用 Windows PowerShell cmdlet 安装 Windows PowerShell Web 访问在默认情况下不会添加 Web 服务器 (IIS) 管理工具。 如果你想在相同的服务器上安装管理工具并用作 Windows PowerShell Web 访问网关，请将 <span class="code">IncludeManagementTools</span> 参数添加到安装命令（如本步骤所述）。 如果你通过远程计算机管理 Windows PowerShell Web 访问网站，请安装 IIS 管理器管理单元，方法是在你想通过其管理网关的计算机上安装<a href="http://go.microsoft.com/fwlink/?LinkID=304145">适用于 Windows 8.1 的远程服务器管理工具</a>或<a href="http://go.microsoft.com/fwlink/p/?LinkID=238560">适用于 Windows 8 的远程服务器管理工具</a>。</p></td>
    </tr>
    </tbody>
    </table>

    若要在离线的 VHD 上安装角色和功能，你必须添加 <span class="code">ComputerName</span> 参数和 <span class="code">VHD</span> 参数。 <span class="code">ComputerName</span> 参数含有安装 VHD 的服务器的名称，<span class="code">VHD</span> 参数含有 VHD 在指定服务器上的路径。

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_d841d509-347e-49d0-bf54-8d1f306bece6'); "Copy to clipboard.")

        Install-WindowsFeature –Name WindowsPowerShellWebAccess –VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart

3.  安装完成后，验证 Windows PowerShell Web 访问是否已安装在目标服务器上，方法是在使用提升的用户权限打开的 Windows PowerShell 控制台中，在目标服务器上运行 **Get-WindowsFeature**。 你还可以验证 Windows PowerShell Web 访问是否已安装在 Server Manager 控制台中，方法是在“所有服务器”页面上选择目标服务器，然后查看所选服务器的“角色和功能”磁贴。 你还可以查看 Windows PowerShell Web 访问的自述文件。

4.  安装 Windows PowerShell Web 访问后，系统将提示你查看自述文件，该文件包含网关的基本且必需的设置说明。 有关这些设置说明，还可以参阅以下部分：[步骤 2：配置网关](#BKMK_step2)。 自述文件的路径是 <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.

<a href="" id="BKMK_step2"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步骤 2：配置网关</span></a>

------------------------------------------------------------------------

使用 **Install-PswaWebApplication** cmdlet 可快速配置 Windows PowerShell Web 访问。 虽然你可将 <span class="code">UseTestCertificate</span> 参数添加到 <span class="code">Install-PswaWebApplication</span> cmdlet，以出于测试目的而安装自签名的 SSL 证书，但这种做法是不安全的；对安全的生产环境而言，应始终使用证书颁发机构 (CA) 签名的有效 SSL 证书。 管理员可通过 IIS 管理器控制台，使用自行选择的已签名证书代替测试证书。

你可完成 Windows PowerShell Web 访问 Web 应用程序配置，方法是运行 <span class="code">Install-PswaWebApplication</span> cmdlet，或在 IIS 管理器中执行基于 GUI 的配置步骤。 默认情况下，cmdlet 在**默认网站**容器中安装 Web 应用程序、**pswa**（及其应用程序池 **pswa_pool**），如 IIS 管理器所示；必要时，你可指示 cmdlet 更改 Web 应用程序的默认网站容器。 IIS 管理器提供可供 Web 应用程序使用的配置选项，例如更改端口号或安全套接字层 (SSL) 证书。

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> 安全说明 </span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>我们强烈推荐管理员配置网关，以使用 CA 已签名的有效证书。</p></td>
</tr>
</tbody>
</table>

-   [使用 Install-PswaWebApplication，配置带有测试证书的 Windows PowerShell Web 访问网关。](#BKMK_testcert)

-   [使用 Install-PswaWebApplication 和 IIS 管理器，配置带有正版证书的 Windows PowerShell Web 访问网关](#BKMK_gencert)

#### 使用 Install-PswaWebApplication，配置带有测试证书的 Windows PowerShell Web 访问网关。

1.  执行以下操作之一，打开 Windows PowerShell 会话。

    -   在 Windows 桌面上，右键单击任务栏上的 Windows PowerShell。

    -   在 Windows“开始”屏幕上，单击 Windows PowerShell.

2.  键入以下命令，然后按 Enter.

    **Install-PswaWebApplication -UseTestCertificate**

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> 安全说明 </span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><span class="code">UseTestCertificate</span> 参数仅可在专用测试环境中使用。 对于安全的生产环境，建议使用证书颁发机构已签名的有效证书。</p></td>
    </tr>
    </tbody>
    </table>

    通过运行 cmdlet，在 IIS 默认网站容器中安装 Windows PowerShell Web 访问 Web 应用程序。 Cmdlet 创建在默认网站 (https://&lt;server_name&gt;/pswa) 上运行 Windows PowerShell Web 访问所必需的基础结构。 若要在不同的网站上安装 web 应用程序，请添加 <span class="code">WebSiteName</span> 参数，以提供网站名称。 若要更改 Web 应用程序的名称（默认名称是 <span class="code">pswa</span>），请添加 <span class="code">WebApplicationName</span> 参数。

    通过运行 cmdlet，配置以下设置。 必要时，你可在 IIS 管理器控制台中手动更改这些设置。

    -   Path: /pswa

    -   ApplicationPool: pswa\_pool

    -   EnabledProtocols: http

    -   PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot

    <span class="label">示例：</span> <span class="code">Install-PswaWebApplication –webApplicationName myWebApp –useTestCertificate</span>

    在本示例中，Windows PowerShell Web 访问的相关网站是 https://&lt; *server_name*&gt;/myWebApp。

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
    <td><p>你将无法登录，直到用户通过添加授权规则，获得访问该网站的权限。 有关详细信息，请参阅<a href="#BKMK_step3">第 3 步：配置受限的授权规则</a>和 <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Windows PowerShell Web 访问的授权规则和安全功能</a>.</p></td>
    </tr>
    </tbody>
    </table>

#### 使用 Install-PswaWebApplication 和 IIS 管理器，配置带有正版证书的 Windows PowerShell Web 访问网关

1.  执行以下操作之一，打开 Windows PowerShell 会话。

    -   在 Windows 桌面上，右键单击任务栏上的 Windows PowerShell。

    -   在 Windows“开始”屏幕上，单击 Windows PowerShell.

2.  键入以下命令，然后按 Enter.

    **Install-PswaWebApplication**

    通过运行 cmdlet，配置以下网关设置。 必要时，你可在 IIS 管理器控制台中手动更改这些设置。 你还可以为 <span class="code">Install-pswawebapplication</span> cmdlet 的 <span class="code">WebsiteName</span> 和<span class="code">WebApplicationName</span> 参数指定值。

    -   Path: /pswa

    -   ApplicationPool: pswa\_pool

    -   EnabledProtocols: http

    -   PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot

3.  通过执行以下操作之一，打开 IIS 管理器控制台。

    -   在 Windows 桌面上，启动服务器管理器，方法是单击 Windows 任务栏中的“服务器管理器”。 在“服务器管理器”的“工具”菜单中，单击“Internet Information Services (IIS) 管理器”。.

    -   在 Windows“开始”屏幕上，单击“服务器管理器”。.

4.  在 IIS 管理器树窗格中，展开已安装 Windows PowerShell Web 访问的服务器的节点，直到“站点”文件夹可见。 展开“网站”文件夹。

5.  选择你已安装 Windows PowerShell Web 访问的 Web 应用程序的网站。 在“操作”窗格中，单击“绑定”.

6.  在“网站绑定”对话框中，单击“添加”.

7.  在“添加网站绑定”对话框的“类型”字段中，选择“https”.

8.  在“SSL 证书”字段中，从下拉菜单中选择你的已签名证书。  **[絋﹚]** 有关如何获得证书的详细信息，请参阅本主题中的[在 IIS 管理器中配置 SSL 证书](#BKMK_cert)。

    现可配置 Windows PowerShell Web 访问 Web 应用程序，以便使用已签名的 SSL 证书。 你可通过在浏览器窗口中打开 https://&lt;server_name&gt;/pswa 访问 Windows PowerShell Web 访问。

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
    <td><p>你将无法登录，直到用户通过添加授权规则，获得访问该网站的权限。 有关详细信息，请参阅<a href="#BKMK_step3">第 3 步：配置受限的授权规则</a>和 <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Windows PowerShell Web 访问的授权规则和安全功能</a>.</p></td>
    </tr>
    </tbody>
    </table>

<a href="" id="BKMK_step3"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步骤 3：配置受限的授权规则</span></a>

------------------------------------------------------------------------

安装 Windows PowerShell Web 访问和配置网关后，用户可在浏览器中打开登录页面，但他们无法登录，直到 Windows PowerShell Web 访问管理员明确授予用户访问权限。 Windows PowerShell Web 访问的访问控制通过使用下表所述的 Windows PowerShell cmdlet 集进行管理。 没有相当的 GUI 可用于添加或管理授权规则。 有关 Windows PowerShell Web 访问 cmdlet 的更多详细信息，请参阅 cmdlet 参考主题 [Windows PowerShell Web 访问 Cmdlets](https://technet.microsoft.com/library/hh918342.aspx).

有关 Windows PowerShell Web 访问授权规则和安全性的详细信息，请参阅 [Windows PowerShell Web 访问的授权规则和安全功能](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).

#### 添加受限的授权规则

1.  使用提升的用户权限执行以下操作之一以打开 Windows PowerShell 会话。

    -   在 Windows 桌面上，右键单击任务栏上的 Windows PowerShell，然后单击“以管理员身份运行”.

    -   在 Windows“开始”屏幕上，右键单击“Windows PowerShell”，然后单击“以管理员身份运行”.

2.  <span class="label">使用会话配置限制用户访问的可选步骤：</span>验证要在规则中使用的会话配置已存在。 如果尚未创建这些配置，则使用 MSDN 上 [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) 中用于创建会话配置的说明。

3.  键入以下命令，然后按 Enter.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_f9e7959b-75d0-4d63-8f8e-02334a8dd09d'); "Copy to clipboard.")

        Add-PswaAuthorizationRule –UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    本授权规则允许特定用户通过他们通常访问的网络访问一台计算机，以及可让特定用户拥有对满足用户常见的脚本和 cmdlet 需求的特定会话配置的权限。 在以下示例中，<span class="code">Contoso</span> 域中名为 <span class="code">JSmith</span> 的用户获得访问权限，以管理计算机 <span class="code">Contoso_214</span>，并使用名为 <span class="code">NewAdminsOnly 的会话配置</span>.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_ebd5bc5e-ec5d-4955-a86a-63843e480e37'); "Copy to clipboard.")

        Add-PswaAuthorizationRule –UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  确保已通过运行 **Get-PswaAuthorizationRule** cmdlet 或 **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt; 创建该规则。 例如，**Test-PswaAuthorizationRule –UserName Contoso\\JSmith –ComputerName Contoso_214**.

配置授权规则之后，授权用户便可以登录基于 Web 的控制台并开始使用 Windows PowerShell Web 访问。

<a href="" id="BKMK_custom"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">自定义部署</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

通过使用服务器管理器中的“添加角色和功能向导”，你可以在运行 Windows Server 2012 R2 或 Windows Server 2012 的服务器上安装 Windows PowerShell Web 访问网关。 安装 Windows PowerShell Web 访问之后，可以在 IIS 管理器中自定义网关的配置。

<a href="" id="BKMK_custom1"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步骤 1：安装 Windows PowerShell Web 访问</span></a>

------------------------------------------------------------------------

#### 若要使用“添加角色和功能向导”安装 Windows PowerShell Web 访问

1.  如果服务器管理器已经打开，则继续执行下一步。 如果服务器管理器尚未打开，请执行以下任一操作打开它。

    -   在 Windows 桌面上，启动服务器管理器，方法是单击 Windows 任务栏中的“服务器管理器”。

    -   在 Windows“开始”屏幕上，单击“服务器管理器”。.

2.  在“管理”菜单上，单击“添加角色和功能”。.

3.  在“选择安装类型”页上，选择“基于角色或基于功能的安装”。 单击“下一步”.

4.  在“选择目标服务器”页面上，从服务器池中选择一台服务器，或选择脱机 VHD。 若要将离线的 VHD 选择为你的目标服务器，则先选择安装 VHD 的服务器，然后选择 VHD 文件。 有关如何将服务器添加到服务器池的详细信息，请参阅服务器管理器帮助。 选择目标服务器后，单击“下一步”.

5.  在向导的“选择功能”页面上，展开 Windows PowerShell，然后选择“Windows PowerShell Web 访问”。.

6.  注意，系统提示你添加所需的功能，例如 .NET Framework 4.5 以及 Web 服务器 (IIS) 的角色服务。 添加所需的功能并继续操作。

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
    <td><p>通过使用“添加角色和功能向导”安装 Windows PowerShell Web 访问还将安装 Web 服务器 (IIS)，包括 IIS 管理器管理单元。 如果你使用“添加角色和功能向导”，则在默认情况下，也安装了管理单元及其他 IIS 管理工具。 如果你按照以下步骤，使用 Windows PowerShell cmdlet 安装 Windows PowerShell Web 访问，则不会默认添加管理工具。</p></td>
    </tr>
    </tbody>
    </table>

7.  在“确认安装选择”页面上，如果 Windows PowerShell Web 访问的功能文件并不存储在你在步骤 4 中所选的目标服务器上，则单击“指定备用的源路径”，并提供功能文件的路径。 否则，单击“安装”.

8.  单击“安装”后，“安装进度”页面将显示安装进度、结果以及有关警告、故障或 Windows PowerShell Web 访问所必需的安装后配置步骤的信息。 安装 Windows PowerShell Web 访问后，系统将提示你查看自述文件，该文件包含网关的基本且必需的设置说明。 这些说明也包括在本主题中。 自述文件的路径是 <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步骤 2：配置网关</span></a>

------------------------------------------------------------------------

本部分中的说明涉及在网站的子目录（而非根目录）中安装 Windows PowerShell Web 访问 Web 应用程序。 本步骤与 <span class="code">Install-PswaWebApplication</span> cmdlet 执行的基于 GUI 的操作等效。 本部分还包括有关如何使用 IIS 管理器将 Windows PowerShell Web 访问网关配置为根网站的说明。

-   [使用 IIS 管理器在现有的网站中配置网关](#BKMK_configman)

-   [使用 IIS 管理器，将网关配置为带有测试证书的根网站](#BKMK_configroot)

-   

#### 使用 IIS 管理器在现有的网站中配置网关

1.  通过执行以下操作之一，打开 IIS 管理器控制台。

    -   在 Windows 桌面上，启动服务器管理器，方法是单击 Windows 任务栏中的“服务器管理器”。 在“服务器管理器”的“工具”菜单中，单击“Internet Information Services (IIS) 管理器”。.

    -   在 Windows“开始”屏幕上，键入“Internet 信息服务 (IIS) 管理器”名称的任何部分。 当它在“应用程序”结果中显示时，单击快捷方式。

2.  为 Windows PowerShell Web 访问创建新的应用程序池。 在 IIS 管理器树窗格中展开网关服务器的节点，选择“应用程序池”，然后单击“操作”窗格中的“添加应用程序池”。

3.  为新的应用程序池添加名称 **pswa_pool**，或提供其他名称。 单击“确定”.

4.  在 IIS 管理器树窗格中，展开已安装 Windows PowerShell Web 访问的服务器的节点，直到“站点”文件夹可见。 选择“站点”文件夹。

5.  右键单击你想添加 Windows PowerShell Web 访问网站的网站（例如，**“默认网站”**），然后单击“添加应用程序”.

6.  在“别名”字段中，键入 pswa 或提供其他别名。 别名变为虚拟目录的名称。 例如，以下 URL 中的 **pswa** 表示在本步骤中指定的别名：https://&lt;server_name&gt;/pswa。

7.  在“应用程序池”字段中，选择在步骤 3 中创建的应用程序池。

8.  在“物理路径”字段中，浏览到应用程序的位置。 你可使用默认的位置，即 %windir%/Web/PowerShellWebAccess/wwwroot。 单击“确定”.

9.  执行本主题中的[在 IIS 管理器中配置 SSL 证书](#BKMK_cert)程序所述的步骤。

10. <span class="label">可选的安全步骤：</span>利用树窗格中所选的网站，双击内容窗格中的“SSL 设置”。 选择“需要 SSL”，然后在“操作”窗格中，单击“应用”。 此外，在“SSL 设置”窗格中，你可要求连接到 Windows PowerShell Web 访问网站的用户持有客户端证书。 客户端证书可协助验证客户端设备用户的身份。 有关要求提供客户端证书如何提高 Windows PowerShell Web 访问的安全性的详细信息，请参阅本指南中 [Windows PowerShell Web 访问的授权规则和安全功能](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)。

11. 在客户端设备上打开浏览器会话。 有关受支持的浏览器和设备的详细信息，请参阅本主题中的[浏览器和客户端设备支持](#BKMK_browser)。

12. 打开新的 Windows PowerShell Web 访问网站 https://&lt; *gateway_server_name*&gt;/pswa。

    浏览器应显示 Windows PowerShell Web 访问控制台登录页面。

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
    <td><p>你将无法登录，直到用户通过添加授权规则，获得访问该网站的权限。</p></td>
    </tr>
    </tbody>
    </table>

13. 在使用提升的用户权限打开的 Windows PowerShell 会话（以管理员身份运行）中，运行以下脚本（其中 *application_pool_name* 表示你在步骤 3 中创建的应用程序池的名称），以便向应用程序池提供授权文件的访问权限。

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_c1a80a93-8fcf-4beb-a025-5f81bfb8bdae'); "Copy to clipboard.")

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    若要查看授权文件的现有访问权限，请运行以下命令：

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_ac2179c2-9548-4a17-8663-267fdd105380'); "Copy to clipboard.")

        c:\windows\system32\icacls.exe $authorizationFile

#### 使用 IIS 管理器，将网关配置为带有测试证书的根网站

1.  通过执行以下操作之一，打开 IIS 管理器控制台。

    -   在 Windows 桌面上，启动服务器管理器，方法是单击 Windows 任务栏中的“服务器管理器”。 在“服务器管理器”的“工具”菜单中，单击“Internet Information Services (IIS) 管理器”。.

    -   在 Windows“开始”屏幕上，键入“Internet 信息服务 (IIS) 管理器”名称的任何部分。 当它在“应用程序”结果中显示时，单击快捷方式。

2.  在 IIS 管理器树窗格中，展开已安装 Windows PowerShell Web 访问的服务器的节点，直到“站点”文件夹可见。 选择“站点”文件夹。

3.  在“操作”窗格中，单击“添加网站”。.

4.  键入网站的名称，例如 **Windows PowerShell Web 访问**。.

5.  新网站的应用程序池自动创建。 若果使用其他应用程序池，请单击“选择”，以选择与新网站相关的应用程序池。 在“选择应用程序池”对话框中选择备用的应用程序池，然后单击“确定”.

6.  在“物理路径”文本框中，导航到 %*windir%*/Web/PowerShellWebAccess/wwwroot。

7.  在“绑定”区域的“类型”字段中，选择 https.

8.  向网站分配一个不再被其他网站或应用程序使用的端口号。 若要定位打开的端口，你可在“命令提示符”窗口中运行 **netstat** 命令。 默认端口号为 443。

    如果其他网站已经使用 443，或你有其他更改端口号的安全原因，则更改默认端口。 如果在你的网关服务器上运行的其他网站使用你所选的端口，当你在“添加网站”对话框中单击“确定”时，将会显示一条警告信息。 必须使用未使用的端口运行 Windows PowerShell Web 访问。

9.  此外，如果你的组织有需要，请指定你的组织和用户都接受的主机名称，例如 **www.contoso.com**。 单击“确定”.

10. 为提高生产环境的安全性，我们强烈建议提供证书颁发机构已签名的有效证书。 你必须提供 SSL 证书，因为用户仅可通过 HTTPS 网站连接到 Windows PowerShell Web 访问。 有关如何获得证书的详细信息，请参阅本主题中的[在 IIS 管理器中配置 SSL 证书](#BKMK_cert)。

11. 单击“确定”关闭“添加网站”对话框。

12. 在使用提升的用户权限打开的 Windows PowerShell 会话（以管理员身份运行）中，运行以下脚本（其中 *application_pool_name* 表示你在步骤 4 中创建的应用程序池的名称），以便向应用程序池提供授权文件的访问权限。

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_35ae9944-ca44-4af7-9c96-616083b3e3db'); "Copy to clipboard.")

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    若要查看授权文件的现有访问权限，请运行以下命令：

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_0eb6d70a-2807-498b-b088-fa5233ed68d5'); "Copy to clipboard.")

        c:\windows\system32\icacls.exe $authorizationFile

13. 利用在 IIS 管理器树窗格中选择的新网站，单击“操作”窗格中的“启动”，以启动网站。

14. 在客户端设备上打开浏览器会话。 有关受支持的浏览器和设备的详细信息，请参阅本文档中的[浏览器和客户端设备支持](#BKMK_browser)。

15. 打开新的 Windows PowerShell Web 访问网站。

    因为根网站指向 Windows PowerShell Web 访问文件夹，所以当你打开 https://&lt; *gateway_server_name*&gt; 时，浏览器应显示 Windows PowerShell Web 访问登录网页。 你无需向 URL 添加 **/pswa**。

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
    <td><p>你将无法登录，直到用户通过添加授权规则，获得访问该网站的权限。</p></td>
    </tr>
    </tbody>
    </table>

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">步骤 3：配置受限的授权规则</span></a>

------------------------------------------------------------------------

安装 Windows PowerShell Web 访问和配置网关后，用户可在浏览器中打开登录页面，但他们无法登录，直到 Windows PowerShell Web 访问管理员明确授予用户访问权限。 Windows PowerShell Web 访问的访问控制通过使用下表所述的 Windows PowerShell cmdlet 集进行管理。 没有相当的 GUI 可用于添加或管理授权规则。 有关 Windows PowerShell Web 访问 cmdlet 的更多详细信息，请参阅 cmdlet 参考主题 [Windows PowerShell Web 访问 Cmdlets](https://technet.microsoft.com/library/hh918342.aspx).

有关 Windows PowerShell Web 访问授权规则和安全性的详细信息，请参阅 [Windows PowerShell Web 访问的授权规则和安全功能](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).

#### 添加受限的授权规则

1.  使用提升的用户权限执行以下操作之一以打开 Windows PowerShell 会话。

    -   在 Windows 桌面上，右键单击任务栏上的 Windows PowerShell，然后单击“以管理员身份运行”.

    -   在 Windows“开始”屏幕上，右键单击“Windows PowerShell”，然后单击“以管理员身份运行”.

2.  <span class="label">使用会话配置限制用户访问的可选步骤：</span>验证要在规则中使用的会话配置已存在。 如果尚未创建这些配置，则使用 MSDN 上 [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) 中用于创建会话配置的说明。

3.  键入以下命令，然后按 Enter.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_4df22c91-f56f-4bb5-91e7-99f9b365ed5d'); "Copy to clipboard.")

        Add-PswaAuthorizationRule –UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    本授权规则允许特定用户通过他们通常访问的网络访问一台计算机，以及可让特定用户拥有对满足用户常见的脚本和 cmdlet 需求的特定会话配置的权限。 在以下示例中，<span class="code">Contoso</span> 域中名为 <span class="code">JSmith</span> 的用户获得访问权限，以管理计算机 <span class="code">Contoso_214</span>，并使用名为 <span class="code">NewAdminsOnly 的会话配置</span>.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_efc3999a-2905-453f-86cd-014b41658ffc'); "Copy to clipboard.")

        Add-PswaAuthorizationRule –UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  确保已通过运行 **Get-PswaAuthorizationRule** cmdlet 或 **Test-PswaAuthorizationRule -UserName &lt;domain\\user | computer\\user&gt; -ComputerName** &lt;computer_name&gt; 创建该规则。 例如，**Test-PswaAuthorizationRule –UserName Contoso\\JSmith –ComputerName Contoso_214**.

配置授权规则之后，授权用户便可以登录基于 Web 的控制台并开始使用 Windows PowerShell Web 访问。

<a href="" id="BKMK_configcert"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">配置正版证书</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

对于安全的生产环境，请始终使用证书颁发机构 (CA) 已签名的有效 SSL 证书。 本部分中的过程介绍如何从 CA 获取并应用有效的 SSL 证书。

### 在 IIS 管理器中配置 SSL 证书

1.  在 IIS 管理器树窗格中，选择已安装 Windows PowerShell Web 访问的服务器。

2.  在内容窗格中，双击“服务器证书”.

3.  在“操作”窗格中，执行以下操作之一。 有关在 IIS 中配置服务器证书的详细信息，请参阅[在 IIS 7 中配置服务器证书](https://technet.microsoft.com/library/cc732230.aspx)。.

    -   单击“导入”，以从网络上的位置中导入现有的有效证书。

    -   单击“创建证书请求”，以请求证书颁发机构颁发的证书，例如 VeriSign(TM)、Thawte 或 GeoTrust(R)。 证书的公用名必须与申请的主机头相匹配。 例如，如果客户端浏览器申请 http://www.contoso.com/，则公用名也必须是 http://www.contoso.com/。 这是向 Windows PowerShell Web 访问网关提供证书的最安全的推荐方案。

    -   单击“创建自签名的证书”，以创建你可立即使用的证书，必要时稍后再由 CA 签名。 为自签名的证书指定一个友好名称，例如 **Windows PowerShell Web 访问**。 此选项被视为不安全的，仅建议在专用测试环境中使用。

4.  创建或获得证书后，在 IIS 管理器树窗格中选择要应用证书的网站（如默认网站），然后单击“操作”窗格中的“绑定”。

5.  如果尚未显示，则在“添加网站绑定”对话框中，向网站添加 **https** 绑定。 如果使用的不是自签名的证书，请从本程序的步骤 3 中指定主机名称。 如果使用的是自签名的证书，则无需执行此步骤。

6.  选择在此过程步骤 3 中获取或创建的证书，然后单击“确定”.

<a href="" id="BKMK_using"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">使用基于 Web 的 Windows PowerShell 控制台</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_5" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

安装 Windows PowerShell Web 访问以及按照本主题所述完成网关配置之后，基于 Web 的 Windows PowerShell 控制台随时可用。 有关基于 Web 的控制台的入门详细信息，请参阅[使用基于 Web 的 Windows PowerShell 控制台](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx).

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">另请参阅</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_6" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

[Internet 信息服务 (IIS) 7.0 文档](https://technet.microsoft.com/library/cc753433.aspx)
[IIS 管理器 7.0 帮助](https://technet.microsoft.com/library/cc732664.aspx)
[配置 Web 服务器安全 (IIS 7)](https://technet.microsoft.com/library/cc731278.aspx)
[IPsec 部署资源](https://technet.microsoft.com/network/bb531150)

<span>显示：</span>继承内容受保护

<span class="stdr-votetitle">此页面是否有所帮助？</span>
是
否

更多反馈？

<span class="stdr-count"><span class="stdr-charcnt">剩余 1500</span> 个字符</span>
提交
跳过此部分

<span class="stdr-thankyou">感谢你参与！</span> <span class="stdr-appreciate">我们非常感谢你的反馈意见。</span>

[管理你的个人资料](https://social.technet.microsoft.com/profile)

|

<a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> 站点反馈</a>
站点反馈

<a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a>

告诉我们你的体验...

页面加载速度快吗？

<span> 是<span> </span></span> <span>否<span> </span></span>

你喜欢页面设计吗？

<span> 是<span> </span></span> <span>否<span> </span></span>

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


<!--HONumber=May16_HO2-->


