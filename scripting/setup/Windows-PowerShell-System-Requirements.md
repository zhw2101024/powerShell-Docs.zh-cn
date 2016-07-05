---
title: "Windows PowerShell 系统要求"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 6d1d3c75-3be4-4fc9-8805-ca9b2c454d42
translationtype: Human Translation
ms.sourcegitcommit: 1ae9150b226147c039acf0738690de4da8686a71
ms.openlocfilehash: e2e129c1c90ab7561861a7d9c71fb654569d5712

---

# Windows PowerShell 系统要求
本主题列出了用于 Windows PowerShell 3.0 和 Windows PowerShell 4.0，以及用于特殊功能（如 Windows PowerShell 集成脚本环境 (ISE)、CIM 命令和工作流的系统要求。

Windows® 8.1 和 Windows Server® 2012 R2 包括所有必需的程序。 本主题主要面向 Windows 早期版本的用户。

## 操作系统要求
Windows PowerShell 4.0 在以下 Windows 版本上运行。

-   Windows 8.1，默认安装

-   Windows Server 2012 R2，默认安装

-   Windows® 7 Service Pack 1，安装 [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkId=293881) 以运行 Windows PowerShell 4.0

-   Windows Server® 2008 R2 Service Pack 1，安装 [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkId=293881) 以运行 Windows PowerShell 4.0

Windows PowerShell 3.0 在以下 Windows 版本上运行。

-   Windows 8，默认安装

-   Windows Server 2012，默认安装

-   Windows® 7 Service Pack 1，安装 [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) 以运行 Windows PowerShell 3.0

-   Windows Server® 2008 R2 Service Pack 1，安装 [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) 以运行 Windows PowerShell 3.0

-   Windows Server 2008 Service Pack 2，安装 [Windows Management Framework 3.0](http://www.microsoft.com/download/details.aspx?id=34595) 以运行 Windows PowerShell 3.0

## Microsoft .NET Framework 要求
Windows PowerShell 4.0 需要完全安装 Microsoft .NET Framework 4.5。 Windows 8.1 和 Windows Server 2012 R2 默认包括 Microsoft.NET Framework 4.5。

Windows PowerShell 3.0 需要完全安装 Microsoft .NET Framework 4。 默认情况下，Windows 8 和 Windows Server 2012 中包含了满足此要求的 Microsoft .NET Framework 4.5。

若要安装 Microsoft .NET Framework 4.5 (dotNetFx45\_Full\_setup.exe)，请参阅 Microsoft 下载中心的 [Microsoft .NET Framework 4.5](http://go.microsoft.com/fwlink/?LinkID=242919)。

若要安装 Microsoft .NET Framework 4 (dotNetFx40\_Full\_setup.exe) 的完全安装，请参阅 Microsoft 下载中心的 [Microsoft .NET Framework 4（Web 安装程序）](http://go.microsoft.com/fwlink/?LinkID=212931)。

## WS\-Management 3.0
Windows PowerShell 3.0 和 Windows PowerShell 4.0 需要支持 WinRM 服务和 WSMan 协议的 WS\-Management 3.0。 Windows 8.1、Windows Server 2012 R2、Windows 8、Windows Server 2012、Windows Management Framework 4.0 和 Windows Management Framework 3.0 中包含此程序。

## Windows Management Instrumentation 3.0
Windows PowerShell 3.0 和 Windows PowerShell 4.0 要求安装 Windows Management Instrumentation 3.0 (WMI)。 Windows 8.1、Windows Server 2012 R2、Windows 8、Windows Server 2012、Windows Management Framework 4.0 和 Windows Management Framework 3.0 中包含此程序。 如果计算机上未安装此程序，则不能运行需要 WMI 的功能，如 CIM 命令。

## 公共语言运行时 4.0
针对公共语言运行时 (CLR) 4.0 编译 Windows PowerShell 3.0 和 Windows PowerShell 4.0。

## 图形用户界面要求
Windows PowerShell 是基于控制台的应用程序，不需要图形用户界面。 因此，它适用于没有屏幕或监视器或用户界面的计算机，例如 Windows Server 2012 R2 或 Windows Server 2012 的服务器核心安装选项。

但是，以下的一些项则需要图形用户界面。 有关详细信息，请参阅每个项的帮助主题。

-   Windows PowerShell 集成脚本环境 (ISE)

-   Cmdlet

    1.  [Out-GridView](https://technet.microsoft.com/en-us/library/70915a86-d753-464e-8349-cba02316154c)

    2.  [Show-Command](https://technet.microsoft.com/en-us/library/65bba50b-91a8-49d5-80a2-a30fc684ba41)

    3.  [Show-ControlPanelItem](https://technet.microsoft.com/en-us/library/0685d42c-37cc-498f-acf6-0ecfeb0cb162)

    4.  [Show-EventLog](https://technet.microsoft.com/en-us/library/a3b0f5ad-0438-42c7-915b-d1b4793a431c)

-   参数

    1.  [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) cmdlet 的 **ShowWindow** 参数。

    2.  [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) 和 [Set-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) cmdlet 的 **ShowSecurityDescriptorUI** 参数。

## Windows PowerShell 引擎要求
Windows PowerShell 4.0 旨在能够与 Windows PowerShell 3.0 和 Windows PowerShell 2.0 向后兼容。 为 Windows PowerShell 2.0 和 Windows PowerShell 3.0 编写的 cmdlet、提供程序、管理单元、模块以及脚本无需更改，即可在 Windows PowerShell 4.0 中运行。

但是，由于 Microsoft.NET framework 4 中的运行时激活策略的更改，为 Windows PowerShell 2.0 编写并使用公共语言运行时 (CLR) 2.0 编译的 Windows PowerShell 主机程序在使用 CLR 4.0 编译的 Windows PowerShell 3.0 中未进行修改时，将无法运行。

Windows PowerShell 2.0 引擎至少需要 Microsoft .NET Framework 2.0.50727。 Microsoft .NET Framework 3.5 Service Pack 1 满足此要求。 Microsoft .NET Framework 4 和更高版本的 Microsoft .NET Framework 不满足此要求。

有关添加或安装 Windows PowerShell 2.0 引擎，以及添加或安装 Microsoft.NET Framework 所需版本的详细信息，请参阅[安装 Windows PowerShell 2.0 引擎](Installing-the-Windows-PowerShell-2.0-Engine.md)。 有关启动 Windows PowerShell 2.0 引擎的信息，请参阅[启动 Windows PowerShell 2.0 引擎](Starting-the-Windows-PowerShell-2.0-Engine.md)。

## Windows 预安装环境
Windows PowerShell 2.0、Windows PowerShell 3.0 和 Windows PowerShell 4.0 在 Windows 预安装环境 (Windows PE) 中运行。 但是，不支持以下 cmdlet。

-   [后台智能传输服务 (BITS) Cmdlet](http://go.microsoft.com/fwlink/?LinkId=257514)

-   [Get-EventLog](https://technet.microsoft.com/en-us/library/b4985b11-82bf-487d-928d-becd96fc0419)

-   [Get-WinEvent](https://technet.microsoft.com/en-us/library/5fe94870-ed6b-4ce2-9500-93846cc65c95)

-   [Save-Help](https://technet.microsoft.com/en-us/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa)

-   [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545)

同时，Windows PE 上不存在**WinRM**服务。

## 另请参阅
[Windows PowerShell 入门](../getting-started/Getting-Started-with-Windows-PowerShell.md)

[安装 Windows PowerShell](Installing-Windows-PowerShell.md)

[启动 Windows PowerShell](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)




<!--HONumber=Jun16_HO4-->


