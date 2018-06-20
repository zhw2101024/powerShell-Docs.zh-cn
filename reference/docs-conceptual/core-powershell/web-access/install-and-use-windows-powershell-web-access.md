---
ms.date: 08/23/2017
keywords: powershell,cmdlet
title: 安装和使用 Windows PowerShell Web 访问
ms.openlocfilehash: 8f140e73ce833fd1cfadbe1d8ee0fe0bb2d08873
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953916"
---
# <a name="install-and-use-windows-powershell-web-access"></a>安装和使用 Windows PowerShell Web 访问

更新日期：2013 年 11 月 5 日（编辑日期：2017 年 8 月 23 日）

适用于：Windows Server 2012 R2、Windows Server 2012

## <a name="introduction"></a>简介

Windows PowerShell Web 访问在 Windows Server 2012 中首次引入，充当 Windows PowerShell 网关，提供以远程计算机为目标的基于 Web 的 Windows PowerShell 控制台。 它可让 IT 专业人士在 Web 浏览器中运行来自 Windows PowerShell 控制台的 Windows PowerShell 命令和脚本，无需在客户端设备上安装 Windows PowerShell、远程管理软件或浏览器插件。 运行基于 Web 的 Windows PowerShell 控制台只需要正确配置的 Windows PowerShell Web 访问网关以及支持 JavaScript 和接受 Cookie 的客户端设备浏览器。

客户端设备的示例包括便携式计算机、非工作的个人计算机、借来的计算机、平板计算机、Web 展台、不运行基于 Windows 的操作系统的计算机和手机浏览器。 IT 专业人士可在远程基于 Windows 的服务器上执行重要的管理任务，这些服务器所属的设备配有 Web 浏览器，并可访问 Internet 连接。

成功安装和配置网关后，用户可通过使用 Web 浏览器访问 Windows PowerShell 控制台。 当用户打开安全的 Windows PowerShell Web 访问网站时，他们可在成功通过身份验证后运行基于 Web 的 Windows PowerShell 控制台。

Windows PowerShell Web 访问安装和配置过程包含三个步骤：

1. [安装 Windows PowerShell Web 访问](#install-windows-powershell-web-access)
1. [配置网关](#configure-the-gateway)
1. [配置受限的授权规则](#configure-a-restrictive-authorization-rule)

安装和配置 Windows PowerShell Web Access 前，我们建议你阅读该完整指南，其中包括有关如何安装、保护和卸载 Windows PowerShell Web 访问的说明。
[使用基于 Web 的 Windows PowerShell 控制台](https://technet.microsoft.com/library/hh831417(v=ws.11).aspx)主题介绍了用户如何登录基于 Web 的控制台，并涵盖基于 Web 的 Windows PowerShell 控制台与 **powershell.exe** 控制台之间的限制和差异。 基于 Web 的控制台的最终用户应阅读[使用基于 Web 的 Windows PowerShell 控制台](use-the-web-based-windows-powershell-console.md)部分，但无需阅读本指南的其余部分。

本主题并不提供详尽的 IIS Web Server 操作指导；仅描述配置 Windows PowerShell Web 访问网关所必需的步骤。 有关配置和保护 IIS 中的网站安全的详细信息，请参阅“另请参阅”部分中的 IIS 文档资源。

下图显示 Windows PowerShell Web 访问的工作原理。

![Windows PowerShell Web Access 图](images/Windows-PowerShell-Web-Access-diagram.jpg)

## <a name="requirements-for-running-windows-powershell-web-access"></a>运行 Windows PowerShell Web 访问的要求

Windows PowerShell Web 访问需要 Web 服务器 (IIS)、.NET Framework 4.5 和 Windows PowerShell 3.0 或 Windows PowerShell 4.0 在你想运行网关的服务器上运行。 通过使用服务器管理器中的“添加角色和功能向导”或适用于服务器管理器的 Windows PowerShell 部署 cmdlet，你可以在运行 Windows Server 2012 R2 或 Windows Server 2012 的服务器上安装 Windows PowerShell Web 访问。 当你使用服务器管理器或其部署 cmdlet 安装 Windows PowerShell Web 访问时，所需的角色和功能将在安装过程中自动添加。

Windows PowerShell Web 访问可让远程用户使用 Web 浏览器中的 Windows PowerShell 访问你组织中的计算机。 虽然 Windows PowerShell Web 访问是便利和功能强大的管理工具，但基于 Web 的访问存在安全风险，应尽可能安全地配置。 我们建议配置 Windows PowerShell Web 访问网关的管理员使用可用的安全层，它们分别是包括在 Windows PowerShell Web 访问内的基于 cmdlet 的授权规则以及在 Web 服务器 (IIS) 中和第三方应用程序中可用的安全层。 本文档包括仅建议在测试环境中使用的不安全示例以及建议在安全部署过程中使用的示例。

## <a name="browser-and-client-device-support"></a>浏览器和客户端设备支持

Windows PowerShell Web 访问支持以下 Internet 浏览器。
虽然移动浏览器未正式受到支持，但许多此类浏览器均可运行基于 Web 的 Windows PowerShell 控制台。 其他接受 Cookies、运行 JavaScript 和 HTTPS 网站的浏览器有望投入使用，但尚未接受正式测试。

### <a name="supported-desktop-computer-browsers"></a>受支持的台式计算机浏览器

- 适用于 Microsoft Windows 8.0、9.0、10.0 和 11.0 的 Windows Internet Explorer
- Mozilla Firefox 10.0.2
- 适用于 Windows 的 Google Chrome 17.0.963.56m
- 适用于 Windows 的 Apple Safari 5.1.2
- 适用于 Mac OS 的 Apple Safari 5.1.2

### <a name="minimally-tested-mobile-devices-or-browsers"></a>经过最小限度测试的移动设备或浏览器

- Windows Phone 7 和 7.5
- Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)
- iPhone 操作系统 5.0.1 的 Apple Safari
- iPad 2 操作系统 5.0.1 的 Apple Safari

### <a name="browser-requirements"></a>浏览器要求

若要使用 Windows PowerShell Web 访问基于 Web 的控制台，浏览器必须执行以下操作。

- 允许 Windows PowerShell Web 访问网关网站中的 Cookie。
- 可打开和访问 HTTPS 页面。
- 打开和运行使用 JavaScript 的网站。

## <a name="recommended-quick-deployment"></a>建议的快速部署

通过使用 Windows PowerShell cmdlet 或从服务器管理器中打开的“添加角色和功能向导”，你可以在运行 Windows Server 2012 R2 或 Windows Server 2012 的服务器上安装 Windows PowerShell Web 访问网关。 对于快速安装和配置，使用 Windows PowerShell cmdlet，如本部分中所述。

1. [安装 Windows PowerShell Web 访问](#install-Windows-powershell-web-access)
1. [配置网关](#configure-the-gateway)
1. [配置受限的授权规则](#configure-a-restrictive-authorization-rule)

### <a name="install-windows-powershell-web-access"></a>安装 Windows PowerShell Web 访问

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a>使用 Windows PowerShell cmdlet 安装 Windows PowerShell Web 访问

1. 使用提升的用户权限执行以下操作之一打开 Windows PowerShell 会话。
    - 在 Windows 桌面上，右键单击任务栏上的**Windows PowerShell**，然后单击**以管理员身份运行**。
    - 在 Windows **开始**屏幕上，右键单击**Windows PowerShell**，然后单击**以管理员身份运行**。

    >**![Note](images/note.jpeg) 注意** 在 Windows PowerShell 3.0 和 4.0 中，在运行作为模块一部分的 cmdlet 之前，无需将 Server Manager cmdlet 模块导入到 Windows PowerShell 会话。 在你首次运行 cmdlet（模块的一部分）时，模块被自动导入。 此外，Windows PowerShell cmdlet 不区分大小写。

1. 键入以下内容，然后按 **Enter**，其中 *computer_name* 代表要安装 Windows PowerShell Web 访问的远程计算机（如果适用）。 必要时，`-Restart` 参数自动重新启动目标服务器。

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart`

   >**![Note](images/note.jpeg) 注意**
   >
   >使用 Windows PowerShell cmdlet 安装 Windows PowerShell Web 访问在默认情况下不会添加 Web 服务器 (IIS) 管理工具。 如果希望在相同的服务器上安装管理工具并用作 Windows PowerShell Web 访问网关，请将 `-IncludeManagementTools` 参数添加到安装命令（如本步骤所述）。 如果通过远程计算机管理 Windows PowerShell Web 访问网站，请安装 IIS Manager 管理单元，方法是在希望通过其管理网关的计算机上安装[适用于 Windows 8.1 的远程服务器管理工具](http://go.microsoft.com/fwlink/?LinkID=304145)或[适用于 Windows 8 的远程服务器管理工具](http://go.microsoft.com/fwlink/p/?LinkID=238560)。

   若要在离线的 VHD 上安装角色和功能，你必须添加 `-ComputerName` 参数和 `-VHD` 参数。 `-ComputerName` 参数含有安装 VHD 的服务器名称，`-VHD` 参数含有 VHD 在指定服务器上的路径。

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart`

1. 安装完成后，验证 Windows PowerShell Web 访问是否已安装在目标服务器上，方法是在使用提升的用户权限打开的 Windows PowerShell 控制台中，在目标服务器上运行 **Get-WindowsFeature**。 你还可以验证 Windows PowerShell Web 访问是否已安装在 Server Manager 控制台中，方法是在“所有服务器”页面上选择目标服务器，然后查看所选服务器的“角色和功能”磁贴。 你还可以查看 Windows PowerShell Web 访问的自述文件。

1. 安装 Windows PowerShell Web 访问后，系统将提示你查看自述文件，该文件包含网关的基本且必需的设置说明。 有关这些设置说明，还可以参阅以下部分：[配置网关](#configure-the-gateway)。 自述文件的路径是 **C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt**。

### <a name="configure-the-gateway"></a>配置网关

使用 **Install-PswaWebApplication** cmdlet 可快速配置 Windows PowerShell Web 访问。 虽然你可将 `UseTestCertificate` 参数添加到 `Install-PswaWebApplication` cmdlet，以出于测试目的而安装自签名的 SSL 证书，但这种做法是不安全的；对安全的生产环境而言，应始终使用证书颁发机构 (CA) 已签名的有效的 SSL 证书。
管理员可通过 IIS 管理器控制台，使用自行选择的已签名证书代替测试证书。

可完成 Windows PowerShell Web 访问 Web 应用程序配置，方法是运行 `Install-PswaWebApplication` cmdlet，或在 IIS Manager 中执行基于 GUI 的配置步骤。 默认情况下，cmdlet 在**默认网站**容器中安装 Web 应用程序、**pswa**（及其应用程序池 **pswa_pool**），如 IIS 管理器所示；必要时，你可指示 cmdlet 更改 Web 应用程序的默认网站容器。 IIS 管理器提供可供 Web 应用程序使用的配置选项，例如更改端口号或安全套接字层 (SSL) 证书。

>**![Security Note](images/securitynote.jpeg) 安全说明**
>
>我们强烈推荐管理员配置网关，以使用 CA 已签名的有效证书。

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a>使用 Install-PswaWebApplication，配置带有测试证书的 Windows PowerShell Web 访问网关。

1. 执行以下操作之一，打开 Windows PowerShell 会话。

    - 在 Windows 桌面上，右键单击任务栏上的 Windows PowerShell。

    - 在 Windows **开始**屏幕上，单击**Windows PowerShell**。

2. 键入以下命令，然后按**Enter**。

    **Install-PswaWebApplication -UseTestCertificate**

  >**![Security Note](images/securitynote.jpeg) 安全说明**
  >
  >
            `UseTestCertificate` 参数仅可在专用测试环境中使用。 对于安全的生产环境，建议使用证书颁发机构已签名的有效证书。

通过运行 cmdlet，在 IIS 默认网站容器中安装 Windows PowerShell Web 访问 Web 应用程序。 cmdlet 创建在默认网站 `https://<server_name>/pswa` 上运行 Windows PowerShell Web 访问所必需的基础结构。 若要在不同的网站上安装 Web 应用程序，请添加 `WebSiteName` 参数，以提供网站名称。 若要更改 Web 应用程序的名称（默认名称是 `pswa`），请添加 `WebApplicationName` 参数。

通过运行 cmdlet，配置以下设置。 必要时，你可在 IIS 管理器控制台中手动更改这些设置。

- Path: /pswa
- ApplicationPool: pswa_pool
- EnabledProtocols: http
- PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot

示例：`Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate`

在本示例中，Windows PowerShell Web 访问的相关网站是 https://\<server_name\>/myWebApp。

>**![Note](images/note.jpeg) 注意**
>
>你将无法登录，直到用户通过添加授权规则，获得访问该网站的权限。 有关详细信息，请参阅[配置受限的授权规则](#configure-a-restrictive-authorization-rule)和 [Windows PowerShell Web 访问的授权规则和安全功能](authorization-rules-and-security-features-of-windows-powershell-web-access.md)。

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a>使用 Install-PswaWebApplication 和 IIS 管理器，配置带有正版证书的 Windows PowerShell Web 访问网关

1. 执行以下操作之一，打开 Windows PowerShell 会话。

    - 在 Windows 桌面上，右键单击任务栏上的 Windows PowerShell。

    - 在 Windows **开始**屏幕上，单击**Windows PowerShell**。

2. 键入以下命令，然后按**Enter**。

    **Install-PswaWebApplication**

    通过运行 cmdlet，配置以下网关设置。
    必要时，你可在 IIS 管理器控制台中手动更改这些设置。
    你还可为 `WebsiteName` cmdlet 的 `WebApplicationName` 和 `Install-PswaWebApplication` 参数指定值。

    - Path: /pswa

    - ApplicationPool: pswa_pool

    - EnabledProtocols: http

    - PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot

3. 通过执行以下操作之一，打开 IIS 管理器控制台。

    - 在 Windows 桌面上，启动服务器管理器，方法是单击 Windows 任务栏中的“服务器管理器”。 在“服务器管理器”的**工具**菜单中，单击**Internet Information Services (IIS) Manager**。

    - 在 Windows **开始**屏幕上，单击**服务器管理器**。

4. 在 IIS 管理器树窗格中，展开已安装 Windows PowerShell Web 访问的服务器的节点，直到“站点”文件夹可见。 展开“网站”文件夹。

5. 选择你已安装 Windows PowerShell Web 访问的 Web 应用程序的网站。 在**操作**窗格中，单击**绑定**。

6. 在**网站绑定**对话框中，单击**添加**。

7. 在**添加网站绑定**对话框中，在**类型**字段，选择**https**。

8. 在“SSL 证书”字段中，从下拉菜单中选择你的已签名证书。 单击**确定**。 有关如何获得证书的详细信息，请参阅本主题中的[在 IIS 管理器中配置 SSL 证书](#to-configure-an-ssl-certificate-in-iis-Manager)。

    现可配置 Windows PowerShell Web 访问 Web 应用程序，以便使用已签名的 SSL 证书。

    可通过在浏览器窗口中打开 https://\<server_name\>/pswa 访问 Windows PowerShell Web 访问。

>**![Note](images/note.jpeg) 注意**
>
>你将无法登录，直到用户通过添加授权规则，获得访问该网站的权限。
>有关详细信息，请参阅本部分中的[配置受限的授权规则](#configure-a-restrictive-authorization-rule)和 [Windows PowerShell Web 访问的授权规则和安全功能](authorization-rules-and-security-features-of-windows-powershell-web-access.md)。

### <a name="configure-a-restrictive-authorization-rule"></a>配置受限的授权规则

安装 Windows PowerShell Web 访问和配置网关后，用户可在浏览器中打开登录页面，但他们无法登录，直到 Windows PowerShell Web 访问管理员明确授予用户访问权限。 Windows PowerShell Web 访问的访问控制通过使用下表所述的 Windows PowerShell cmdlet 集进行管理。 没有相当的 GUI 可用于添加或管理授权规则。 有关 Windows PowerShell Web 访问 cmdlet 的更多详细信息，请参阅 cmdlet 参考主题 [Windows PowerShell Web 访问 Cmdlet](cmdlets/web-access-cmdlets.md)。

有关 Windows PowerShell Web 访问授权规则和安全性的详细信息，请参阅 [Windows PowerShell Web 访问的授权规则和安全功能](authorization-rules-and-security-features-of-windows-powershell-web-access.md)。

#### <a name="to-add-a-restrictive-authorization-rule"></a>添加受限的授权规则

1. 使用提升的用户权限执行以下操作之一打开 Windows PowerShell 会话。

    - 在 Windows 桌面上，右键单击任务栏上的**Windows PowerShell**，然后单击**以管理员身份运行**。

    - 在 Windows **开始**屏幕上，右键单击**Windows PowerShell**，然后单击**以管理员身份运行**。

2. 使用会话配置限制用户访问的可选步骤：验证要在规则中使用的会话配置已存在。 如果尚未创建这些配置，则使用 [about_Session_Configuration_Files](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations) 中用于创建会话配置的说明。

3. 键入以下命令，然后按**Enter**。

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   本授权规则允许特定用户通过他们通常访问的网络访问一台计算机，以及可让特定用户拥有对满足用户常见脚本和 cmdlet 需求的特定会话配置的权限。

   在以下示例中，`JSmith` 域中名为 `Contoso` 的用户获得访问权限，以管理计算机 `Contoso_214`，并使用名为 `NewAdminsOnly` 的会话配置。

   `Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

4. 验证是否已通过运行 `Get-PswaAuthorizationRule` cmdlet 或 `Test-PswaAuthorizationRule -UserName <domain\user> -ComputerName <computer-name>` 创建了规则

5. 例如，`Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`。

配置授权规则之后，授权用户便可以登录基于 Web 的控制台并开始使用 Windows PowerShell Web 访问。

## <a name="custom-deployment"></a>自定义部署

通过使用服务器管理器中的“添加角色和功能向导”，你可以在运行 Windows Server 2012 R2 或 Windows Server 2012 的服务器上安装 Windows PowerShell Web 访问网关。 安装 Windows PowerShell Web 访问之后，可以在 IIS 管理器中自定义网关的配置。

### <a name="install-windows-powershell-web-access"></a>安装 Windows PowerShell Web 访问

#### <a name="to-install-windows-powershell-web-access-by-using-the-add-roles-and-features-wizard"></a>若要使用“添加角色和功能向导”安装 Windows PowerShell Web 访问

1. 如果服务器管理器已经打开，则继续执行下一步。 如果服务器管理器尚未打开，请执行以下任一操作打开它。

    - 在 Windows 桌面上，启动服务器管理器，方法是单击 Windows 任务栏中的“服务器管理器”。

    - 在 Windows **开始**屏幕上，单击**服务器管理器**。

2. 在**管理**菜单上，单击**添加角色和功能**。

3. 在“选择安装类型”页上，选择“基于角色或基于功能的安装”。 单击**下一步**。

4. 在“选择目标服务器”页面上，从服务器池中选择一台服务器，或选择脱机 VHD。 若要将离线的 VHD 选择为你的目标服务器，则先选择安装 VHD 的服务器，然后选择 VHD 文件。 有关如何将服务器添加到服务器池的详细信息，请参阅服务器管理器帮助。 选择目标服务器后，单击**下一步**。

5. 在向导的**选择功能**页面上，展开**Windows PowerShell**，然后选择**Windows PowerShell Web 访问**。

6. 注意，系统提示你添加所需的功能，例如 .NET Framework 4.5 以及 Web 服务器 (IIS) 的角色服务。 添加所需的功能并继续操作。

    >**![Note](images/note.jpeg) 注意**
    >
    >通过使用“添加角色和功能向导”安装 Windows PowerShell Web 访问还将安装 Web 服务器 (IIS)，包括 IIS 管理器管理单元。 如果你使用“添加角色和功能向导”，则在默认情况下，也安装了管理单元及其他 IIS 管理工具。 如果你按照以下步骤，使用 Windows PowerShell cmdlet 安装 Windows PowerShell Web 访问，则不会默认添加管理工具。

7. 在“确认安装选择”页面上，如果 Windows PowerShell Web 访问的功能文件并不存储在你在步骤 4 中所选的目标服务器上，则单击“指定备用的源路径”，并提供功能文件的路径。 否则，单击**安装**。

8. 单击“安装”后，“安装进度”页面将显示安装进度、结果以及有关警告、故障或 Windows PowerShell Web 访问所必需的安装后配置步骤的信息。 安装 Windows PowerShell Web 访问后，系统将提示你查看自述文件，该文件包含网关的基本且必需的设置说明。 这些说明也包括在本主题中。 自述文件路径为 `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`。

### <a name="configure-the-gateway"></a>配置网关

本部分中的说明涉及在网站的子目录（而非根目录）中安装 Windows PowerShell Web 访问 Web 应用程序。 本步骤与 `Install-PswaWebApplication` cmdlet 执行的基于 GUI 的操作等效。 本部分还包括有关如何使用 IIS 管理器将 Windows PowerShell Web 访问网关配置为根网站的说明。

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a>使用 IIS 管理器在现有的网站中配置网关

1. 通过执行以下操作之一，打开 IIS 管理器控制台。

    - 在 Windows 桌面上，启动服务器管理器，方法是单击 Windows 任务栏中的“服务器管理器”。 在“服务器管理器”的**工具**菜单中，单击**Internet Information Services (IIS) Manager**。

    - 在 Windows“开始”屏幕上，键入“Internet 信息服务 (IIS) 管理器”名称的任何部分。 当它在“应用程序”结果中显示时，单击快捷方式。

2. 为 Windows PowerShell Web 访问创建新的应用程序池。 在 IIS 管理器树窗格中展开网关服务器的节点，选择“应用程序池”，然后单击“操作”窗格中的“添加应用程序池”。

3. 为新的应用程序池添加名称 **pswa_pool**，或提供其他名称。 单击**确定**。

4. 在 IIS 管理器树窗格中，展开已安装 Windows PowerShell Web 访问的服务器的节点，直到“站点”文件夹可见。 选择“站点”文件夹。

5. 右键单击你想添加 Windows PowerShell Web 访问网站的网站（例如，**默认网站**），然后单击**添加应用程序**。

6. 在“别名”字段中，键入 pswa 或提供其他别名。 别名变为虚拟目录的名称。 例如，以下 URL 中的 pswa 表示在本步骤中指定的别名：https://\<server-name\>/pswa。

7. 在“应用程序池”字段中，选择在步骤 3 中创建的应用程序池。

8. 在“物理路径”字段中，浏览到应用程序的位置。 你可使用默认的位置，即 %windir%/Web/PowerShellWebAccess/wwwroot。 单击**确定**。

9. 请按照本主题中的“在 IIS Manager 中配置 SSL 证书程序](#to-configure-an-ssl-certificate-in-iis-Manager)”所述的步骤操作。

10. ![](images/SecurityNote.jpeg) 可选安全步骤：

    利用树窗格中所选的网站，双击内容窗格中的“SSL 设置”。
选择“需要 SSL”，然后在“操作”窗格中，单击“应用”。
此外，在“SSL 设置”窗格中，你可要求连接到 Windows PowerShell Web 访问网站的用户持有客户端证书。 客户端证书可协助验证客户端设备用户的身份。
有关要求提供客户端证书如何提高 Windows PowerShell Web 访问的安全性的详细信息，请参阅本指南中 [Windows PowerShell Web 访问的授权规则和安全功能](authorization-rules-and-security-features-of-windows-powershell-web-access.md)。

11. 在客户端设备上打开浏览器会话。 有关受支持的浏览器和设备的详细信息，请参阅本主题中的[浏览器和客户端设备支持](#browser-and-client-device-support)。

12. 打开新的 Windows PowerShell Web 访问网站 https://\<gateway-server-name\>/pswa。

    浏览器应显示 Windows PowerShell Web 访问控制台登录页面。

    >**![Note](images/note.jpeg) 注意**
    >
    >你将无法登录，直到用户通过添加授权规则，获得访问该网站的权限。
    >有关详细信息，请参阅本部分中的[配置受限的授权规则](#configure-a-restrictive-authorization-rule)和 [Windows PowerShell Web 访问的授权规则和安全功能](authorization-rules-and-security-features-of-windows-powershell-web-access.md)。

13. 在使用提升的用户权限打开的 Windows PowerShell 会话（以管理员身份运行）中，运行以下脚本（其中 *application_pool_name* 表示你在步骤 3 中创建的应用程序池的名称），以便向应用程序池提供授权文件的访问权限。

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    若要查看授权文件的现有访问权限，请运行以下命令：

        c:\windows\system32\icacls.exe $authorizationFile

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a>使用 IIS 管理器，将网关配置为带有测试证书的根网站

1. 通过执行以下操作之一，打开 IIS 管理器控制台。

    - 在 Windows 桌面上，启动服务器管理器，方法是单击 Windows 任务栏中的“服务器管理器”。 在“服务器管理器”的**工具**菜单中，单击**Internet Information Services (IIS) Manager**。

    - 在 Windows“开始”屏幕上，键入“Internet 信息服务 (IIS) 管理器”名称的任何部分。 当它在“应用程序”结果中显示时，单击快捷方式。

2. 在 IIS 管理器树窗格中，展开已安装 Windows PowerShell Web 访问的服务器的节点，直到“站点”文件夹可见。 选择“站点”文件夹。

3. 在**操作**窗格中，单击**添加网站**。

4. 键入网站的名称，例如**Windows PowerShell Web 访问**。

5. 新网站的应用程序池自动创建。 若果使用其他应用程序池，请单击“选择”，以选择与新网站相关的应用程序池。 在**选择应用程序池**对话框中选择备用的应用程序池，然后单击**确定**。

6. 在“物理路径”文本框中，导航到 %*windir%*/Web/PowerShellWebAccess/wwwroot。

7. 在**绑定**区域的**类型**字段中，选择**https**。

8. 向网站分配一个不再被其他网站或应用程序使用的端口号。 若要定位打开的端口，你可在“命令提示符”窗口中运行 **netstat** 命令。 默认端口号为 443。

    如果其他网站已经使用 443，或你有其他更改端口号的安全原因，则更改默认端口。 如果在你的网关服务器上运行的其他网站使用你所选的端口，当你在“添加网站”对话框中单击“确定”时，将会显示一条警告信息。 必须使用未使用的端口运行 Windows PowerShell Web 访问。

9. 此外，如果你的组织有需要，请指定你的组织和用户都接受的主机名称，例如 **www.contoso.com**。单击**确定**。

10. 为提高生产环境的安全性，我们强烈建议提供证书颁发机构已签名的有效证书。 你必须提供 SSL 证书，因为用户仅可通过 HTTPS 网站连接到 Windows PowerShell Web 访问。 有关如何获得证书的详细信息，请参阅本主题中的[在 IIS Manager 中配置 SSL 证书](#to-configure-an-ssl-certificate-in-iis-Manager)。

11. 单击“确定”关闭“添加网站”对话框。

12. 在使用提升的用户权限打开的 Windows PowerShell 会话（以管理员身份运行）中，运行以下脚本（其中 *application_pool_name* 表示你在步骤 4 中创建的应用程序池的名称），以便向应用程序池提供授权文件的访问权限。

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    若要查看授权文件的现有访问权限，请运行以下命令：

        c:\windows\system32\icacls.exe $authorizationFile

13. 利用在 IIS 管理器树窗格中选择的新网站，单击“操作”  窗格中的“启动”  ，以启动网站。

14. 在客户端设备上打开浏览器会话。 有关受支持的浏览器和设备的详细信息，请参阅本文档中的[浏览器和客户端设备支持](#browser-and-client-device-support)。

15. 打开新的 Windows PowerShell Web 访问网站。

    因为根网站指向 Windows PowerShell Web 访问文件夹，所以打开 https://\<gateway_server_name\>时，浏览器应显示 Windows PowerShell Web 访问登录网页。 你无需向 URL 添加 **/pswa**。

    >**![Note](images/note.jpeg) 注意**
    >
    >你将无法登录，直到用户通过添加授权规则，获得访问该网站的权限。
    >有关详细信息，请参阅本部分中的[配置受限的授权规则](#configure-a-restrictive-authorization-rule)和 [Windows PowerShell Web 访问的授权规则和安全功能](authorization-rules-and-security-features-of-windows-powershell-web-access.md)。

### <a name="configure-a-restrictive-authorization-rule"></a>配置受限的授权规则

安装 Windows PowerShell Web 访问和配置网关后，用户可在浏览器中打开登录页面，但他们无法登录，直到 Windows PowerShell Web 访问管理员明确授予用户访问权限。 Windows PowerShell Web 访问的访问控制通过使用下表所述的 Windows PowerShell cmdlet 集进行管理。 没有相当的 GUI 可用于添加或管理授权规则。 有关 Windows PowerShell Web 访问 cmdlet 的更多详细信息，请参阅 cmdlet 参考主题 [Windows PowerShell Web 访问 Cmdlet](cmdlets/web-access-cmdlets.md)。

有关 Windows PowerShell Web 访问授权规则和安全性的详细信息，请参阅 [Windows PowerShell Web 访问的授权规则和安全功能](authorization-rules-and-security-features-of-windows-powershell-web-access.md)。

#### <a name="to-add-a-restrictive-authorization-rule"></a>添加受限的授权规则

1. 使用提升的用户权限执行以下操作之一打开 Windows PowerShell 会话。

    - 在 Windows 桌面上，右键单击任务栏上的**Windows PowerShell**，然后单击**以管理员身份运行**。

    - 在 Windows **开始**屏幕上，右键单击**Windows PowerShell**，然后单击**以管理员身份运行**。

2. ![安全说明](images/SecurityNote.jpeg) 使用会话配置限制用户访问的可选步骤：

    确保规则中已经存在你要使用的会话配置。 如果尚未创建这些配置，则使用 [about_Session_Configuration_Files](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configurations) 中用于创建会话配置的说明。

3. 键入以下命令，然后按**Enter**。

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    本授权规则允许特定用户通过他们通常访问的网络访问一台计算机，以及可让特定用户拥有对满足用户常见脚本和 cmdlet 需求的特定会话配置的权限。

    在以下示例中，`JSmith` 域中名为 `Contoso` 的用户获得访问权限，以管理计算机 `Contoso_214`，并使用名为 `NewAdminsOnly` 的会话配置。

        Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4. 验证是否已通过运行 `Get-PswaAuthorizationRule` cmdlet 或 `Test-PswaAuthorizationRule -UserName '<domain\user>' -ComputerName <computer-name>` 创建了规则。

    例如，`Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`。

配置授权规则之后，授权用户便可以登录基于 Web 的控制台并开始使用 Windows PowerShell Web 访问。

## <a name="configure-a-genuine-certificate"></a>配置正版证书

对于安全的生产环境，请始终使用证书颁发机构 (CA) 已签名的有效 SSL 证书。 本部分中的过程介绍如何从 CA 获取并应用有效的 SSL 证书。

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a>在 IIS 管理器中配置 SSL 证书

1. 在 IIS 管理器树窗格中，选择已安装 Windows PowerShell Web 访问的服务器。

2. 在内容窗格中，双击**服务器证书**。

3. 在“操作”窗格中，执行以下操作之一。 有关在 IIS 中配置服务器证书的详细信息，请参阅[在 IIS 7 中配置服务器证书](https://technet.microsoft.com/library/cc732230.aspx)。

    - 单击“导入”，以从网络上的位置中导入现有的有效证书。

    - 单击“创建证书请求”，以请求证书颁发机构颁发的证书，例如 [VeriSign](http://www.verisign.com/)、[Thawte](https://www.thawte.com/) 或 [GeoTrust](https://www.geotrust.com/)。 证书的公用名必须与申请的主机头相匹配。

      例如，如果客户端浏览器申请 http://www.contoso.com/，则公用名也必须是 http://www.contoso.com/。 这是向 Windows PowerShell Web 访问网关提供证书的最安全的推荐方案。

    - 单击“创建自签名的证书”，以创建你可立即使用的证书，必要时稍后再由 CA 签名。 为自签名的证书指定一个友好名称，例如 **Windows PowerShell Web 访问**。 此选项被视为不安全的，仅建议在专用测试环境中使用。

4. 创建或获得证书后，在 IIS 管理器树窗格中选择要应用证书的网站（如默认网站），然后单击“操作”窗格中的“绑定”。

5. 如果尚未显示，则在“添加网站绑定”对话框中，向网站添加 **https** 绑定。 如果使用的不是自签名的证书，请从本程序的步骤 3 中指定主机名称。 如果使用的是自签名的证书，则无需执行此步骤。

6. 选择要使用或在步骤 3 中创建的证书，然后单击**确定**。

## <a name="using-the-web-based-windows-powershell-console"></a>使用基于 Web 的 Windows PowerShell 控制台

安装 Windows PowerShell Web 访问以及按照本主题所述完成网关配置之后，基于 Web 的 Windows PowerShell 控制台随时可用。 有关基于 Web 的控制台的入门详细信息，请参阅[使用基于 Web 的 Windows PowerShell 控制台](use-the-web-based-windows-powershell-console.md)。

## <a name="see-also"></a>另请参阅

- [Internet Information Services (IIS) 7.0 文档](https://technet.microsoft.com/library/cc753433.aspx)
- [IIS Manager 7.0 帮助](https://technet.microsoft.com/library/cc732664.aspx)
- [配置 Web 服务器安全 (IIS 7)](https://technet.microsoft.com/library/cc731278.aspx)
- [IPsec 部署资源](https://technet.microsoft.com/network/bb531150)