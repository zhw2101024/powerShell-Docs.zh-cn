---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Windows PowerShell 系统要求"
ms.assetid: 6d1d3c75-3be4-4fc9-8805-ca9b2c454d42
ms.openlocfilehash: 33824eac4de28de97990ffa1ea2500e61e03e847
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/29/2017
---
# <a name="windows-powershell-system-requirements"></a>Windows PowerShell 系统要求
本主题列出了用于 Windows PowerShell 3.0、Windows PowerShell 4.0 和 Windows PowerShell 5.0，以及用于特殊功能（如 Windows PowerShell 集成脚本环境 (ISE)、CIM 命令和工作流）的系统要求。

Windows® 8.1 和 Windows Server® 2012 R2 包括所有必需的程序。 本主题主要面向 Windows 早期版本的用户。

## <a name="operating-system-requirements"></a>操作系统要求
Windows PowerShell 5.0 在以下 Windows 版本上运行。

- Windows Server 2016，默认安装

- Windows Server 2012 R2，安装 [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) 以运行 Windows PowerShell 5.0

- Windows Server 2012，安装 [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) 以运行 Windows PowerShell 5.0

- Windows Server 2008 R2 Service Pack 1，安装 [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) 以运行 Windows PowerShell 5.0

- Windows 8.1

- Windows 7 Service Pack 1，安装 [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) 以运行 Windows PowerShell 5.0

Windows PowerShell 4.0 在以下 Windows 版本上运行。

- Windows 8.1，默认安装

- Windows Server 2012 R2，默认安装

- Windows® 7 Service Pack 1，安装 [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) 以运行 Windows PowerShell 4.0

- Windows Server® 2008 R2 Service Pack 1，安装 [Windows Management Framework 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) 以运行 Windows PowerShell 4.0

Windows PowerShell 3.0 在以下 Windows 版本上运行。

- Windows 8，默认安装

- Windows Server 2012，默认安装

- Windows® 7 Service Pack 1，安装 [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) 以运行 Windows PowerShell 3.0

- Windows Server® 2008 R2 Service Pack 1，安装 [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) 以运行 Windows PowerShell 3.0

- Windows Server 2008 Service Pack 2，安装 [Windows Management Framework 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) 以运行 Windows PowerShell 3.0

## <a name="microsoft-net-framework-requirements"></a>Microsoft .NET Framework 要求
Windows PowerShell 5.0 需要完全安装 Microsoft .NET Framework 4.5。 Windows 8.1 和 Windows Server 2012 R2 默认包括 Microsoft.NET Framework 4.5。

Windows PowerShell 4.0 需要完全安装 Microsoft .NET Framework 4.5。 Windows 8.1 和 Windows Server 2012 R2 默认包括 Microsoft.NET Framework 4.5。

Windows PowerShell 3.0 需要完全安装 Microsoft .NET Framework 4。 默认情况下，Windows 8 和 Windows Server 2012 中包含了满足此要求的 Microsoft .NET Framework 4.5。

若要安装 Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe)，请参阅 Microsoft 下载中心的 [Microsoft .NET Framework 4.5](http://go.microsoft.com/fwlink/?LinkID=242919)。

若要安装 Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) 的完全安装，请参阅 Microsoft 下载中心的 [Microsoft .NET Framework 4 (Web Installer)](http://go.microsoft.com/fwlink/?LinkID=212931)。

## <a name="windows-management-framework-40"></a>Windows Management Framework 4.0
Windows PowerShell 5.0 要求在 Windows Server 2008 R2 SP1 和 Windows 7 SP1 上预先安装 Windows Management Framework 4.0。

## <a name="ws-management-30"></a>WS-Management 3.0
Windows PowerShell 3.0 和 Windows PowerShell 4.0 需要支持 WinRM 服务和 WSMan 协议的 WS-Management 3.0。 Windows 8.1、Windows Server 2012 R2、Windows 8、Windows Server 2012、Windows Management Framework 4.0 和 Windows Management Framework 3.0 中包含此程序。

## <a name="windows-management-instrumentation-30"></a>Windows Management Instrumentation 3.0
Windows PowerShell 3.0 和 Windows PowerShell 4.0 要求安装 Windows Management Instrumentation 3.0 (WMI)。 Windows 8.1、Windows Server 2012 R2、Windows 8、Windows Server 2012、Windows Management Framework 4.0 和 Windows Management Framework 3.0 中包含此程序。 如果计算机上未安装此程序，则不能运行需要 WMI 的功能，如 CIM 命令。

## <a name="common-language-runtime-40"></a>公共语言运行时 4.0
针对公共语言运行时 (CLR) 4.0 编译 Windows PowerShell 3.0、Windows PowerShell 4.0 和 Windows PowerShell 5.0。

## <a name="graphical-user-interface-requirements"></a>图形用户界面要求
Windows PowerShell 是基于控制台的应用程序，不需要图形用户界面。 因此，它适用于没有屏幕或监视器或用户界面的计算机，例如 Windows Server 2012 R2 或 Windows Server 2012 的服务器核心安装选项。

但是，以下的一些项则需要图形用户界面。 有关详细信息，请参阅每个项的帮助主题。

- Windows PowerShell 集成脚本环境 (ISE)

- Cmdlet

    1.  [Out-GridView](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/out-gridview)

    2.  [Show-Command](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Utility/Show-Command)

    3.  [Show-ControlPanelItem](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Management/Show-ControlPanelItem)

    4.  [Show-EventLog](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Management/Show-EventLog)

- 参数

    1.  [Get-Help](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet 的 **ShowWindow** 参数。

    2.  [Register-PSSessionConfiguration](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration) 和 [Set-PSSessionConfiguration](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration) cmdlet 的 **ShowSecurityDescriptorUI** 参数。

## <a name="windows-powershell-engine-requirements"></a>Windows PowerShell 引擎要求
Windows PowerShell 4.0 旨在能够与 Windows PowerShell 3.0 和 Windows PowerShell 2.0 向后兼容。 为 Windows PowerShell 2.0 和 Windows PowerShell 3.0 编写的 Cmdlet、提供程序、管理单元、模块以及脚本无需更改，即可在 Windows PowerShell 4.0 中运行。

但是，由于 Microsoft.NET framework 4 中的运行时激活策略的更改，为 Windows PowerShell 2.0 编写并使用公共语言运行时 (CLR) 2.0 编译的 Windows PowerShell 主机程序在使用 CLR 4.0 编译的 Windows PowerShell 3.0 中未进行修改时，将无法运行。

Windows PowerShell 2.0 引擎至少需要 Microsoft .NET Framework 2.0.50727。 Microsoft .NET Framework 3.5 Service Pack 1 满足此要求。 Microsoft .NET Framework 4 和更高版本的 Microsoft .NET Framework 不满足此要求。

有关添加或安装 Windows PowerShell 2.0 引擎，以及添加或安装 Microsoft.NET Framework 所需版本的详细信息，请参阅[安装 Windows PowerShell 2.0 引擎](Installing-the-Windows-PowerShell-2.0-Engine.md)。 有关启动 Windows PowerShell 2.0 引擎的信息，请参阅[启动 Windows PowerShell 2.0 引擎](Starting-the-Windows-PowerShell-2.0-Engine.md)。

## <a name="windows-preinstallation-environment"></a>Windows 预安装环境
Windows PowerShell 2.0、Windows PowerShell 3.0 和 Windows PowerShell 4.0 在 Windows 预安装环境 (Windows PE) 中运行。 但是，不支持以下 cmdlet。

- [后台智能传输服务 (BITS) Cmdlet](http://go.microsoft.com/fwlink/?LinkId=257514)

- [Get-EventLog](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Management/Get-EventLog)

- [Get-WinEvent](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent)

- [Save-Help](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Core/Save-Help)

- [Update-Help](https://docs.microsoft.com/en-us/powershell/module/Microsoft.PowerShell.Core/Update-Help)

同时，Windows PE 上不存在**WinRM**服务。

## <a name="see-also"></a>另请参阅
- [Windows PowerShell 入门](../getting-started/Getting-Started-with-Windows-PowerShell.md)
- [安装 Windows PowerShell](Installing-Windows-PowerShell.md)
- [启动 Windows PowerShell](Starting-Windows-PowerShell.md)

