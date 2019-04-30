---
ms.date: 08/23/2017
keywords: powershell,cmdlet
title: 使用基于 Web 的 Windows PowerShell 控制台
ms.openlocfilehash: 2bb9c6ef486ef32012a15f9890997cf2fa6a3a0b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086625"
---
# <a name="use-the-web-based-windows-powershell-console"></a>使用基于 Web 的 Windows PowerShell 控制台

更新时间：2013 年 6 月 24 日

适用于：Windows Server 2012 R2、Windows Server 2012

Windows PowerShell Web 访问使用户可登录到安全的网站，以使用 Windows PowerShell 会话、cmdlet 和脚本管理远程计算机。

由于 Windows PowerShell 控制台在 Web 浏览器中运行，因此可以在众多客户端设备中打开；它几乎适用于所有能运行 Web 浏览器的设备。

基于 Web 的 Windows PowerShell 控制台以用户在登录过程中指定的远程计算机为目标。

本主题描述如何登录以及开始使用 Windows PowerShell Web 访问基于 Web 的控制台。

本主题不描述如何使用 Windows PowerShell 或运行 cmdlet 或脚本。
有关如何使用 Windows PowerShell 和脚本资源的信息，请参阅本主题结尾的[另请参阅](#see-also)部分。

## <a name="supported-browsers-and-client-devices"></a>受支持的浏览器和客户端设备

Windows PowerShell Web 访问支持以下 Internet 浏览器。
虽然移动浏览器未正式受到支持，但许多此类浏览器均可运行基于 Web 的 Windows PowerShell 控制台。
其他接受 Cookies、运行 JavaScript 和 HTTPS 网站的浏览器有望投入使用，但尚未接受正式测试。

### <a name="supported-desktop-computer-browsers"></a>受支持的台式计算机浏览器

- 适用于 Microsoft Windows 8.0、9.0、10.0 和 11.0 的 Windows Internet Explorer
- Mozilla Firefox 10.0.2
- 适用于 Windows 的 Google Chrome 17.0.963.56m
- 适用于 Windows 的 Apple Safari 5.1.2
- 适用于 Mac OS 的 Apple Safari 5.1.2

### <a name="minimally-tested-mobile-devices-or-browsers"></a>经过最小限度测试的移动设备或浏览器

- Windows Phone 7 和 Windows Phone 7.5
- Google Android WebKit 3.1 Browser Android 2.2.1（内核 2.6）
- iPhone 操作系统 5.0.1 的 Apple Safari
- iPad 2 操作系统 5.0.1 的 Apple Safari

### <a name="browser-requirements"></a>浏览器要求

若要使用 Windows PowerShell Web 访问基于 Web 的控制台，浏览器必须执行以下操作。

- 允许 Windows PowerShell Web 访问网关网站中的 Cookie。
- 可打开和访问 HTTPS 页面。
- 打开和运行使用 JavaScript 的网站。

## <a name="signing-in-to-windows-powershell-web-access"></a>登录到 Windows PowerShell Web Access

Windows PowerShell Web 访问管理员应为你提供一个 URL，该 URL 是贵组织 Windows PowerShell Web 访问网关网站的地址。
默认情况下，此网址为 https://\<server_name\>/pswa。

在登录到 Windows PowerShell Web 访问之前，确保拥有想要管理的远程计算机的名称或 IP 地址。
你必须是远程计算机上的授权用户，并且必须将远程计算机配置为可远程管理。
有关将计算机配置为可远程管理的详细信息，请参阅[在 Windows PowerShell 中启用和使用远程命令](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting)。

将计算机配置为可远程管理的最简单方法是：在使用提升的用户权限打开的 Windows PowerShell 会话中（**以管理员身份运行**），在计算机上运行**Enable-PSRemoting -force** cmdlet。

### <a name="to-sign-in-to-windows-powershell-web-access"></a>登录到 Windows PowerShell Web Access

1. 在 Internet 浏览器窗口或选项卡中打开 Windows PowerShell Web 访问网站。

1. 在 Windows PowerShell Web 访问登录页面中，提供你的网络用户名、密码以及你想管理（以及你是其授权用户）的计算机的名称。 如果 Windows PowerShell Web 访问管理员指示你将 URI（而非计算机名称）用于自定义网站或代理服务器，请在“连接类型”字段中选择“连接 URI”，然后提供 URI。

    > ![Note](images/Note.jpeg) **注意**：
    >
    > - 如果目标计算机在工作组中，则使用以下语法，提供用户名并登录到计算机：`<workgroup_name>\<user_name>`
    > - 如果目标计算机是网关服务器，则可在“计算机名”字段中指定 `localhost`。
    > - 如果目标计算机是网关服务器，并且该网关服务器在工作组中，则必须在“用户名”字段中使用 `<workgroup name>\<user_name>`。 可在“计算机名”字段中使用 `localhost`。

1. “可选的连接设置”部分涉及你想要管理的远程计算机的授权要求。 有关与可选的连接设置等效的参数的详细信息，请参阅 [Enter-PSSession](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet 帮助。

    一般情况下，你用于通过 Windows PowerShell Web 访问网关的凭据与你想要管理的远程计算机所识别的凭据是一样的。 但是，如果你想要使用不同的凭据管理你在步骤 2 中指定的远程计算机，请展开“可选的连接设置”部分，并提供备用凭据。 否则，请跳到步骤 6。

1. 如果 Windows PowerShell Web 访问管理员已经为 Windows PowerShell Web 访问用户创建了自定义会话配置，则在“配置名称”字段中键入会话配置名称。 有关会话配置的详细信息，请参阅 [about_Session_Configurations](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations)。

1. 除非 Windows PowerShell Web 访问管理员指示你以其他方式处理，否则将“身份验证类型”设置保持为“默认”。

1. 单击**登录**。

## <a name="signing-out-and-timing-out"></a>注销和超时

执行以下任一操作，均可注销基于 Web 的 Windows PowerShell 会话。

- 在控制台的右下角单击“注销”。 （仅限 Windows Server 2012）

- 在控制台的右下角单击“保存”或“退出”（仅适用于 Windows Server 2012 R2）。 单击“保存”将保存并关闭你的 Windows PowerShell Web 访问会话；稍后可以重新连接到该会话。 再次登录到 Windows PowerShell Web 访问时，Windows PowerShell Web 访问将显示已保存会话的列表；你可以选择并重新连接到某个已保存的会话，也可以启动新的会话。 允许用户打开的最大会话数（包括已保存的会话和活动会话）由网关管理员配置。

    单击“退出”将直接注销 Windows PowerShell Web 访问会话，而不保存该会话。

- 尝试登录，以便在相同的浏览器会话中或在相同浏览器会话的新选项卡中，管理不同的远程计算机。 （这种情况不适用于运行 Windows Server 2012 R2 的网关服务器；Windows Server 2012 R2 上运行的 Windows PowerShell Web 访问允许在相同浏览器会话的新选项卡中打开多个用户会话。）有关如何在相同计算机上使用多个活动会话的详细信息，请参阅本主题[基于 Web 的控制台的限制](#limitations-of-the-web-based-console)部分中的“同时连接到多台目标计算机”。

- 会话停止活动 20 分钟。 网关管理员可以自定义停止活动超时时间；有关详细信息，请参阅[会话管理](authorization-rules-and-security-features-of-windows-powershell-web-access.md#session-management)。

    - 如果你从基于 Web 的控制台中的会话断开连接是由于网络错误或其他计划外关机或故障，而不是因为自己关闭了会话，Windows PowerShell Web 访问会话将继续运行并连接到目标计算机，直到客户端的超时期结束。 默认情况下，此超时期为 20 分钟，并由网关管理员配置。 会话在默认的 20 分钟或网关管理员指定的超时期（以时间较短者为准）后断开连接。

        如果网关服务器正在运行 Windows Server 2012 R2，Windows PowerShell Web 访问将允许用户稍后重新连接到已保存的会话，但是，需在网关管理员指定的超时期过后，才能查看或重新连接到已保存的会话。

- 关闭浏览器窗口或选项卡。

- 关闭正在运行浏览器的客户端设备，或将它从网络中断开。

- 在 Web 控制台中运行“退出”命令。 如果已连接的会话配置为支持 [NoLanguage](https://msdn.microsoft.com/library/windows/desktop/system.management.automation.pslanguagemode.aspx) 模式，或处于受限的运行空间中，则此命令不可用。

如果你想再次登录，可再次打开 Windows PowerShell Web 访问网页，然后执行本主题中[登录到 Windows PowerShell Web 访问](#signing-in-to-windows-powershell-web-access)部分的以下步骤，即可登录。

## <a name="differences-in-the-web-based-windows-powershell-console"></a>基于 Web 的 Windows PowerShell 控制台的独特之处

在登录到 Windows PowerShell Web 访问之后, 在浏览器窗口或选项卡中将打开一个基于 Web 的 Windows PowerShell 控制台。因为控制台连接到你在登录过程中指定的远程计算机，所以在控制台中仅可使用那些在远程计算机上可用的 Windows PowerShell cmdlet 或脚本。 本部分介绍 Windows PowerShell Web 访问控制台存在的限制，以及 Windows PowerShell Web 访问控制台和已安装的 **PowerShell.exe** 控制台之间的差异。

### <a name="functional-disparity-with-powershellexe"></a>PowerShell.exe 的功能差异

大多数 Windows PowerShell 主机功能都可在 Windows PowerShell Web 访问基于 Web 的控制台中使用，但有些功能则不可用。

- 将会显示嵌套的进度。

  Windows PowerShell Web 访问显示 cmdlet 的进度 GUI（报告进度），但仅显示最高层的进度信息。

- 输入颜色修改。

  无法更改输入颜色（前景和背景）。 输出风格、警告、详细和错误信息均可通过运行脚本进行更改。

- PSHostRawUserInterface。

  Windows PowerShell Web 访问通过 Windows PowerShell 远程管理实施，并且使用远程运行空间。 Windows PowerShell Web 访问在此界面不执行一些方法；例如，任何写入 Windows 控制台的命令。 **PowerTab** 等命令在 Windows PowerShell Web 访问中不起作用。

- 功能键。

  在许多种情况下，Windows PowerShell Web 访问并不支持一些功能键，因为浏览器保留了此类命令。

### <a name="unsupported-shortcut-keys"></a>不支持的快捷键

功能键 | 操作
-- | --
Ctrl+C | 在 Windows PowerShell Web 访问中，浏览器使用 **Ctrl + C** 复制内容。 控制台提供“取消”按钮，用户还可使用 **Ctrl+Q** 来取消命令。
Alt-space、e、l | 滚动屏幕缓冲区
Alt+Space、e、f | 搜索屏幕缓冲区中的文本
Alt+Space、e、k | 选择从屏幕缓冲区中复制而来的文本
Alt+Space、e、p | 将剪贴板内容粘贴到 Windows PowerShell 控制台
Alt+Space、c | 关闭 Windows PowerShell 控制台
Ctrl+Break | 强制关闭 Windows PowerShell 窗口
Ctrl+Home | 从当前命令行的开始部分删除
Ctrl+End | 在命令行的末尾结束删除
F1 | 将光标向命令行的右侧移动一个字符
F2 | 通过将最后一个命令复制到你键入的字符，创建新的命令
F3 | 用最后一个命令行中的内容完成命令行
F4 | 从光标位置删除字符
F5 | 向后扫描你的命令历史记录。 若要访问 Windows PowerShell Web 访问的命令历史记录中的命令，请在基于 Web 的控制台中单击“历史记录”滚动按钮。
F7 | 从命令历史记录中交互选择一个命令
F8 | 扫描与当前文本匹配的历史记录显示命令
F9 | 运行历史记录中特定编号的命令
Page Up | 运行历史记录中的第一个命令
Page Down | 运行历史记录中的最后一个命令
Alt+F7 | 清空命令历史记录列表

### <a name="limitations-of-the-web-based-console"></a>基于 Web 的控制台的限制

- 双跃点

    如果尝试通过使用 Windows PowerShell Web 访问来创建或运行新的会话，你会遇到双跃点（或从第一个连接到第二台计算机之间的连接）限制。 Windows PowerShell Web 访问使用远程运行空间，目前，**PowerShell.exe** 不支持建立从远程运行空间到第二台计算机的远程连接。 例如，如果尝试使用 Enter-PSSession cmdlet 从现有的连接连接到第二台远程计算机，你会遇到各种错误，例如“无法获得网络资源”。

    若要避免双跃点错误，管理员应在组织的网络环境中配置 CredSSP 身份验证。 有关如何配置 CredSSP 身份验证的详细信息，请参阅 Microsoft 网站上的[适用于第二跃点远程处理的 CredSSP](https://blogs.msdn.com/b/powershell/archive/2008/06/05/credssp-for-second-hop-remoting-part-i-domain-account.aspx)。 当你想要管理第二台远程计算机时，你还可提供显式凭据；隐式凭据不可能接受第二跃点。

- 远程处理

    Windows PowerShell Web 访问使用远程 Windows PowerShell 会话并具有与它相同的限制。 直接调用 Windows 控制台 API 的命令（例如基于控制台的编辑器或基于文本的菜单程序）不可用，因为此类命令不可读取或写入标准的输入、输出和错误管道。 因此，启用可执行文件（如 notepad.exe）或显示 GUI（如 `ogv` 或 `OpenGridView`）的命令不可用。 此操作将影响你的体验；你会觉得好像 Windows PowerShell Web 访问并不响应你的命令。

- Tab 自动补全

    Tab 自动补全不适用于带有受限运行空间的会话配置或在 **NoLanguage** 模式下的会话配置。 虽然管理员可以配置会话以支持选项卡完成，但出于安全考虑，建议不要这样做，因为此操作会向未授权用户披露以下信息。

    - 内部文件系统路径

    - 内部计算机上的共享文件夹

    - 运行空间中的变量

    - 已加载的类型或 .NET Framework 名称空间

    - 环境变量

- NoLanguage 会话，或受限制的运行空间

    登录到 **NoLanguage** 会话配置或 Windows PowerShell Web 访问的受限运行空间的用户不能运行“退出”命令以结束会话。 若要注销，用户应在控制台页面上单击“注销”。

- 同时连接到多台目标计算机。

    如果网关服务器正在运行 Windows Server 2012，Windows PowerShell Web 访问仅允许每个浏览器会话连接一台远程计算机；它不允许用户只登录一次，即使用独立的浏览器选项卡连接到多台远程计算机。 当你打开新的选项卡或浏览器窗口时，Windows PowerShell Web 访问将提示你断开当前的会话，并启动新的会话，以使你可以连接到新的（或相同的）远程计算机。 但是，如果不同的远程计算机需要两个或更多独立会话，可使用 Internet Explorer 中的功能创建新的会话。 若要在 Internet Explorer 中启动新的浏览器会话，请按下 ALT，打开“文件”菜单，然后选择“新建会话”。 随后在新的会话中打开 Windows PowerShell Web 访问网站，登录即可访问其他远程计算机。

    当 Windows PowerShell Web 访问网关在 Windows Server 2012 R2 上运行时，用户可以在不同的浏览器选项卡中打开与远程计算机之间的多个连接。 如果想要使用基于 Web 的 Windows PowerShel 控制台打开与远程计算机之间的多个连接，请咨询 Windows PowerShell Web 访问网关管理员，了解网关服务器是否支持此功能。

- 持续的 Windows PowerShell 会话（重新连接）。

    Windows PowerShell Web 访问网关超时后，网关和目标计算机之间的远程连接将关闭。 这会阻止当前正在运行的任何 cmdlet 或脚本。 执行长时间运行的任务时，建议使用 -Job 基础结构，这样就可以启动作业，断开计算机的连接，稍后重新连接，让作业持续进行。 使用 -Job cmdlet 的另一个好处是，可以使用 Windows PowerShell Web 访问启动它们，注销并通过运行 Windows PowerShell Web 访问或另一台主机（如 Windows PowerShell 集成脚本环境 (ISE)）来重新连接它们。

- 调整控制台大小。

    可通过以下三种方式调整 **PowerShell.exe** 控制台窗口大小。

    - 拖动并使用鼠标调整控制台窗口大小

    - 使用控制台属性的 GUI，更改高度和宽度属性

    - 使用 cmdlet，更改控制台窗口的高度和宽度

        可按以下方式使用 cmdlet 来配置 Windows PowerShell Web 访问控制台窗口。 在下例中，用户将 Windows PowerShell Web 访问控制台的宽度更改为**20**。

            $newSize = $Host.UI.RawUI.WindowSize
            $newSize.Width = $newSize.Width - 20

            $oldSize = $Host.UI.RawUI.WindowSize

            $Host.UI.RawUI.WindowSize = $newSize

        你可以使用类似的方式更改控制台的高度。

        如要获取自定义控制台视图的其他示例，请参阅 [Windows PowerShell 团队博客](https://blogs.msdn.com/b/powershell/)。

## <a name="see-also"></a>另请参阅

- [Windows PowerShell cmdlet 参考资料](https://technet.microsoft.com/library/ee407531(ws.10).aspx)
- [Microsoft TechNet 上的 Windows PowerShell](https://technet.microsoft.com/library/bb978526.aspx)
- [TechNet 脚本中心储存库](https://gallery.technet.microsoft.com/scriptcenter)
- [脚本中心 -“嗨, 脚本专家!”](https://technet.microsoft.com/scriptcenter)
- [Windows PowerShell 团队博客](https://blogs.msdn.com/b/powershell/)