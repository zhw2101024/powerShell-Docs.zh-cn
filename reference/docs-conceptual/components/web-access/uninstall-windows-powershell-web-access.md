---
ms.date: 08/23/2017
keywords: powershell,cmdlet
title: 卸载 Windows PowerShell Web 访问
ms.openlocfilehash: 22c874d766445dccedd8494097daf16c30fa66ff
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058129"
---
# <a name="uninstall-windows-powershell-web-access"></a>卸载 Windows PowerShell Web 访问

更新时间：2013 年 6 月 24 日

适用于：Windows Server 2012 R2、Windows Server 2012

本主题中的步骤说明了如何从已安装 Windows PowerShell Web 访问网站的网关服务器中删除该网站及其应用程序。

## <a name="notify-users"></a>通知用户

开始前，先通知基于 Web 控制台的用户，你准备删除网站。

卸载 Windows PowerShell Web 访问并不卸载 IIS 或任何其他自动安装的功能，因为 Windows PowerShell Web 访问需要它们处于运行状态。
卸载过程保留了依赖 Windows PowerShell Web 访问的功能；必要时你可以单独卸载那些功能。

## <a name="recommended-quick-uninstallation"></a>建议（快速）卸载

本部分内容可帮助你卸载以下内容：

- Windows PowerShell Web 访问 Web 应用程序
- Windows PowerShell Web 访问功能

方法是使用 Windows PowerShell cmdlet。

### <a name="step-1-delete-the-web-application-using-cmdlets"></a>步骤 1：使用 cmdlet 删除 Web 应用程序

1. 执行以下操作之一，打开 Windows PowerShell 会话。

    -   在 Windows 桌面上，右键单击任务栏上的 Windows PowerShell。

    -   在 Windows **开始**屏幕上，单击**Windows PowerShell**。

2. 键入 `Uninstall-PswaWebApplication`，然后按 Enter。
   1. 如果指定了自己的自定义网站名称，请将 `-WebsiteName` 参数添加到命令中，并指定网站名称。

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. 如果使用了自定义 Web 应用程序（不是默认应用程序 pswa），请将 `-WebApplicationName` 参数添加到命令中，并指定 Web 应用程序的名称。

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. 如果你使用的是测试证书，则将 `DeleteTestCertificate` 参数添加到 cmdlet（如以下示例所述）。

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a>步骤 2：使用 cmdlet 卸载 Windows PowerShell Web 访问

1. 使用提升的用户权限执行以下操作之一打开 Windows PowerShell 会话。 如果会话已经打开，则继续执行下一步。

    -   在 Windows 桌面上，右键单击任务栏上的**Windows PowerShell**，然后单击**以管理员身份运行**。

    -   在 Windows **开始**屏幕上，右键单击**Windows PowerShell**，然后单击**以管理员身份运行**。

1. 键入以下内容，然后按 **Enter**，其中的 *computer_name* 代表要从中删除 Windows PowerShell Web 访问的远程服务器。 如果在删除过程中有必要，则 `-Restart` 参数将自动重新启动目标服务器。

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    若要在离线的 VHD 上删除角色和功能，你必须添加 `-ComputerName` 参数和 `-VHD` 参数。 `-ComputerName` 参数含有安装 VHD 的服务器名称， `-VHD` 参数含有 VHD 在指定服务器上的路径。

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. 删除完成后，验证你已删除 Windows PowerShell Web 访问，方法是打开服务管理器中的“所有服务器”页面，选择要删除其功能的服务器，然后在选定服务器的页面上查看“角色和功能”磁贴。

    也可针对选定的服务器运行 `Get-WindowsFeature` cmdlet (Get-WindowsFeature -ComputerName &lt;computer_name&gt;)，以查看该服务器上安装的角色和功能的列表。

## <a name="custom-uninstallation"></a>自定义卸载

本部分中的过程帮助你通过使用服务管理器中的“删除角色和功能向导”和 IIS 管理器卸载 Windows PowerShell Web 访问 Web 应用程序和 Windows PowerShell Web 访问功能。

### <a name="step-1-delete-the-web-application-using-iis-manager"></a>步骤 1：使用 IIS Manager 删除 Web 应用程序


1. 通过执行以下操作之一，打开 IIS 管理器控制台。 如果该控制台已经打开，则继续执行下一步。

    -   在 Windows 桌面上，启动服务器管理器，方法是单击 Windows 任务栏中的“服务器管理器”。 在“服务器管理器”的**工具**菜单中，单击**Internet Information Services (IIS) Manager**。

    -   在 Windows“开始”屏幕上，键入“Internet 信息服务 (IIS) 管理器”名称的任何部分。 当快捷方式在“应用程序”结果中显示时，单击它。

1. 在 IIS 管理器树窗格中，选择运行 Windows PowerShell Web 访问 Web 应用程序的网站。

1. 在**操作**窗格中，在**管理网站**下，单击**停止**。

1. 在树窗格中，右键单击运行 Windows PowerShell Web 访问 Web 应用程序的网站中的 Web 应用程序，然后单击**删除**。

1. 在树窗格中，选择“应用程序池”，并选择 Windows PowerShell Web 访问应用程序池文件夹，单击“操作”窗格中的“停止”，然后单击内容窗格中的“删除”。

1. 关闭 IIS 管理器。

> ![警告注意](images/SecurityNote.jpeg)**注意**：
>
> 在卸载过程中未删除证书。
>
> 如果你创建了自签名的证书或使用测试证书，现想将它删除，则可在 IIS 管理器中删除该证书。

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a>步骤 2：使用“删除角色和功能向导”卸载 Windows PowerShell Web 访问

1. 如果服务器管理器已经打开，则继续执行下一步。 如果服务器管理器尚未打开，请执行以下任一操作打开它。

    -   在 Windows 桌面上，启动服务器管理器，方法是单击 Windows 任务栏中的“服务器管理器”。

    -   在 Windows **开始**屏幕上，单击**服务器管理器**。

1. 在**管理**菜单上，单击**删除角色和功能**。

1. 在“选择目标服务器”页面上，选择你想删除其功能的服务器或离线 VHD。 若要选择离线的 VHD，请选择安装 VHD 的服务器，然后选择 VHD 文件。 选择目标服务器后，单击**下一步**。

1. 再次单击“下一步”，跳到“删除功能”页面。

1. 清除**Windows PowerShell Web 访问**复选框，然后单击**下一步**。

1. 在**确认删除选择**页面上，单击**删除**。

## <a name="see-also"></a>另请参阅

- [安装和使用 Windows PowerShell Web 访问](install-and-use-windows-powershell-web-access.md)
- [IIS Manager 7.0 帮助](https://technet.microsoft.com/library/cc732664.aspx)