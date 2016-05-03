---
title: Windows PowerShell 系统要求
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6d1d3c75-3be4-4fc9-8805-ca9b2c454d42
---
# Windows PowerShell 系统要求
本主题列出了 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 和 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 的系统要求以及特殊功能，例如 [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)]、CIM 命令和工作流。

[!INCLUDE[winblue_client_1](../Token/winblue_client_1_md.md)] 和 [!INCLUDE[winblue_server_1](../Token/winblue_server_1_md.md)] 包括了所有所需的程序。 本主题主要面向 Windows 早期版本的用户。

## 操作系统要求
[!INCLUDE[psversion4](../Token/psversion4_md.md)] 在以下的 Windows 版本上运行。

-   [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)]（默认安装）

-   [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)]（默认安装）

-   [!INCLUDE[win7_client_firstref](../Token/win7_client_firstref_md.md)] Service Pack 1，安装 [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkId=293881) 以运行 [!INCLUDE[psversion4](../Token/psversion4_md.md)]

-   [!INCLUDE[win7_server_firstref](../Token/win7_server_firstref_md.md)] Service Pack 1，安装 [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkId=293881) 以运行 [!INCLUDE[psversion4](../Token/psversion4_md.md)]

[!INCLUDE[psversion3](../Token/psversion3_md.md)] 在以下的 Windows 版本上运行。

-   [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)]（默认安装）

-   [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)]（默认安装）

-   [!INCLUDE[win7_client_firstref](../Token/win7_client_firstref_md.md)] Service Pack 1，安装 [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) 以运行 [!INCLUDE[psversion3](../Token/psversion3_md.md)]

-   [!INCLUDE[win7_server_firstref](../Token/win7_server_firstref_md.md)] Service Pack 1，安装 [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) 以运行 [!INCLUDE[psversion3](../Token/psversion3_md.md)]

-   [!INCLUDE[lserver](../Token/lserver_md.md)] Service Pack 2，安装 [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) 以运行 [!INCLUDE[psversion3](../Token/psversion3_md.md)]

## Microsoft .NET Framework 要求
[!INCLUDE[psversion4](../Token/psversion4_md.md)] 需要完全安装 Microsoft .NET Framework 4.5。 默认情况下，[!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)] 和 [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)] 中包含了 Microsoft .NET Framework 4.5。

[!INCLUDE[psversion3](../Token/psversion3_md.md)] 需要完全安装 Microsoft .NET Framework 4。 默认情况下，[!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)] 和 [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] 中包含了满足此要求的 Microsoft .NET Framework 4.5。

若要安装 Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe)，请参阅 Microsoft 下载中心的 [Microsoft .NET Framework 4.5](http://go.microsoft.com/fwlink/?LinkID=242919)。

若要安装 Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) 的完全安装，请参阅 Microsoft 下载中心的 [Microsoft .NET Framework 4 (Web Installer)](http://go.microsoft.com/fwlink/?LinkID=212931)。

## WS-Management 3.0
[!INCLUDE[psversion3](../Token/psversion3_md.md)] 和 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 需要支持 WinRM 服务和 WSMan 协议的 WS-Management 3.0。 此程序包含在 [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)]、[!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)]、[!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)]、[!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)]、Windows Management Framework 4.0 和 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 中。

## Windows Management Instrumentation 3.0
[!INCLUDE[psversion3](../Token/psversion3_md.md)] 和 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 要求 Windows Management Instrumentation 3.0 (WMI)。 此程序包含在 [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)]、[!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)]、[!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)]、[!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)]、Windows Management Framework 4.0 和 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 中。 如果计算机上未安装此程序，则不能运行需要 WMI 的功能，如 CIM 命令。

## 公共语言运行时 4.0
[!INCLUDE[psversion3](../Token/psversion3_md.md)] 和 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 针对公共语言运行时 (CLR) 4.0 而编译。

## 图形用户界面要求
[!INCLUDE[wps_2](../Token/wps_2_md.md)] 是基于控制台的应用程序，不需要图形用户界面。 因此，它适用于没有屏幕或监视器或用户界面的计算机，例如 [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)] 或 [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] 的服务器核心安装选项。

但是，以下的一些项则需要图形用户界面。 有关详细信息，请参阅每个项的帮助主题。

-   [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)]

-   Cmdlet

    1.  [Out-GridView](https://technet.microsoft.com/en-us/library/70915a86-d753-464e-8349-cba02316154c)

    2.  [Show-Command](https://technet.microsoft.com/en-us/library/65bba50b-91a8-49d5-80a2-a30fc684ba41)

    3.  [Show-ControlPanelItem](https://technet.microsoft.com/en-us/library/0685d42c-37cc-498f-acf6-0ecfeb0cb162)

    4.  [Show-EventLog](https://technet.microsoft.com/en-us/library/a3b0f5ad-0438-42c7-915b-d1b4793a431c)

-   参数

    1.  [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) cmdlet 的 **ShowWindow** 参数。

    2.  [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) 和 [Set-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) cmdlet 的 **ShowSecurityDescriptorUi** 参数。

## Windows PowerShell 引擎要求
[!INCLUDE[psversion4](../Token/psversion4_md.md)] 旨在与 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 和 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 向后兼容。 Cmdlet、提供程序、管理单元、模块，以及为 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 和 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 编写的脚本可在未经改变的情况下在 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 中运行。

但是，由于 Microsoft.NET framework 4 中运行时激活策略的更改，为 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 编写并使用公共语言运行时 (CLR) 2.0 编译的 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 主机程序无法在不经修改的情况下在 [!INCLUDE[psversion3](../Token/psversion3_md.md)]（使用 CLR 4.0 进行编译）中运行。

[!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎至少需要 Microsoft .NET Framework 2.0.50727。 Microsoft .NET Framework 3.5 Service Pack 1 满足此要求。 Microsoft .NET Framework 4 和更高版本的 Microsoft .NET Framework 不满足此要求。

有关添加或安装 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎，以及添加或安装 Microsoft.NET Framework 所需版本的详细信息，请参阅[安装 Windows PowerShell 2.0 引擎](../Topic/Installing-the-Windows-PowerShell-2.0-Engine.md)。 有关启动 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎的信息，请参阅[启动 Windows PowerShell 2.0 引擎](../Topic/Starting-the-Windows-PowerShell-2.0-Engine.md)。

## Windows 预安装环境
[!INCLUDE[psversion2](../Token/psversion2_md.md)]、[!INCLUDE[psversion3](../Token/psversion3_md.md)] 和 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 可在 Windows 预安装环境 (Windows PE) 中运行。 但是，不支持以下 cmdlet。

-   [后台智能传输服务 (BITS) Cmdlet](http://go.microsoft.com/fwlink/?LinkId=257514)

-   [Get-EventLog](https://technet.microsoft.com/en-us/library/b4985b11-82bf-487d-928d-becd96fc0419)

-   [Get-WinEvent[PSITPro5_Diagnostic]](https://technet.microsoft.com/en-us/library/5fe94870-ed6b-4ce2-9500-93846cc65c95)

-   [Save-Help](https://technet.microsoft.com/en-us/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa)

-   [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545)

同时，Windows PE 上不存在 **WinRm** 服务。

## 另请参阅
[Windows PowerShell 入门](../Topic/Getting-Started-with-Windows-PowerShell.md)
[安装 Windows PowerShell](../Topic/Installing-Windows-PowerShell.md)
[启动 Windows PowerShell [ps]](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)



<!--HONumber=Apr16_HO2-->


