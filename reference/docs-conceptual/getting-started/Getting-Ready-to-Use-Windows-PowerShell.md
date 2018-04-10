---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 准备好使用 Windows PowerShell
ms.assetid: 6dc7052d-cc5a-4220-950f-98f963a2b587
ms.openlocfilehash: 5e095984286ff89958dc0a4e3d27e40eae5b2c5e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="getting-ready-to-use-windows-powershell"></a>准备好使用 Windows PowerShell
安装并启动 Windows PowerShell 后，请考虑以下设置选项。 随时可以执行这些任务。

- **安装帮助文件。** Windows PowerShell 3.0 中包含的 cmdlet 不附带帮助文件。 但是，可以使用 [Update-Help](/powershell/module/microsoft.powershell.core/update-help) cmdlet 在计算机上下载并安装最新帮助文件。 安装文件后，可以使用 [Get-Help](/powershell/module/microsoft.powershell.core/get-help) cmdlet 在命令行右侧显示它们。 有关详细信息，请参阅 [about_Updatable_Help](/powershell/module/microsoft.powershell.core/about/about_updatable_help)。

    如果决定不安装帮助文件，你仍可以在线阅读帮助主题。 若要打开任何 cmdlet 帮助主题的在线版本，请键入：`Get-Help <CmdletName> -Online`。 若要浏览 Windows PowerShell 帮助主题，请参阅 [PowerShell 文档](/powershell/scripting)。

- **运行脚本。** 为确保 Windows PowerShell 安全，Windows PowerShell 上的默认执行策略为**受限**。 此策略允许你运行 cmdlet，但不允许运行脚本。 若要运行脚本，请使用 [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) cmdlet 将执行策略更改为 AllSigned 或 RemoteSigned。 只有计算机上管理员组的成员才能运行此 cmdlet。 有关详细信息，请参阅 [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies)。

- **启用远程。** 系统已进行了配置，以便你在其他计算机上运行远程命令。 在 Windows Server 2012 R2 和 Windows Server 2012 上，系统总是配置为接收远程命令，也就是说，允许其他计算机在本地计算机上运行远程命令。 若要允许运行其他版本 Windows 的计算机接收远程命令，请在你想远程管理的计算机上运行 [Enable-PSRemoting](/powershell/module/microsoft.powershell.core/enable-psremoting) cmdlet。 只有计算机上管理员组的成员才能运行此 cmdlet。 有关详细信息，请参阅 [about_Remote](/powershell/module/microsoft.powershell.core/about/about_remote)。

    注意：如果已在运行 Windows PowerShell 2.0 的计算机上启用远程，则安装 Windows Management Framework 3.0 后仍将启用远程。 但是，在 Windows Server 2008（而非 Windows Server 2008 R2）上，你必须在安装 Windows Management Framework 3.0 后重新启用远程。

## <a name="see-also"></a>另请参阅
- [安装 Windows PowerShell](../setup/Installing-Windows-PowerShell.md)
- [启动 Windows PowerShell](/powershell/scripting/setup/starting-windows-powershell)