---
title: "安装 Windows PowerShell"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 6fbb0409-5a54-48ec-95e6-7f8b7d8c4969
translationtype: Human Translation
ms.sourcegitcommit: f856f170c6e18be8758d52df9b50ac443531fdf2
ms.openlocfilehash: 415e68b372c831ed8dd4535c2968e5a36b5cb65d

---

# 安装 Windows PowerShell
Windows® 8 和 Windows Server® 2012 包括 Windows PowerShell 3.0 及其所有先决条件。 系统还包括 Windows PowerShell 2.0 引擎，以实现与不能使用 Windows PowerShell 3.0 的主机程序的向后兼容性。

本主题说明如何在早期系统上安装 Windows PowerShell 3.0，以及安装和启用所需的功能。

本主题包含下列部分：

-   [在 Windows 8 和 Windows Server 2012 上安装 Windows PowerShell](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows8andWindowsServer2012)

-   [在 Windows 7 和 Windows Server 2008 R2 上安装 Windows PowerShell](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows7andWindowsServer2008R2)

-   [在 Windows Server 2008 上安装 Windows PowerShell](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindowsServer2008LH)

-   [在 Server Core 上安装 Windows PowerShell](Installing-Windows-PowerShell.md#BKMK_InstallingOnServerCore)

-   [部署 Windows PowerShell Web 访问](https://technet.microsoft.com/en-us/library/639d0eff-98a3-4124-b52c-26921ebd98b0)

-   [安装 Windows PowerShell 2.0 引擎](Installing-the-Windows-PowerShell-2.0-Engine.md)

## <a name="BKMK_InstallingOnWindows8andWindowsServer2012"></a>在 Windows 8 和 Windows Server 2012 上安装 Windows PowerShell
Windows PowerShell 3.0 已安装和配置，并可供使用。 Windows PowerShell 集成脚本环境 (ISE) 已安装并已启用。 有关启动 Windows PowerShell 的信息，请参阅 [Starting Windows PowerShell on Windows 8](https://technet.microsoft.com/en-us/library/d7be1668-8617-4890-ad90-dd9765fbd2c3)（在 Windows 8 上启动 Windows PowerShell）和 [Starting Windows PowerShell on Windows Server 2012](https://technet.microsoft.com/library/hh831491.aspx#BKMK_powershell)（在 Windows Server 2012 上启动 Windows PowerShell）。

## <a name="BKMK_InstallingOnWindows7andWindowsServer2008R2"></a>在 Windows 7 和 Windows Server 2008 R2 上安装 Windows PowerShell
这些说明解释了如何在运行 Windows 7 Service Pack 1 和 Windows Server 2008 R2 Service Pack 1 的计算机上安装 Windows PowerShell 3.0。 下面是适用于运行 Windows Server 2008 R2 的 Server Core 安装选项的计算机的单独安装说明。

#### 正在准备安装

-   安装 Windows Management Framework 3.0 之前，请卸载所有早期版本的 Windows Management Framework 3.0。

#### 安装 Windows PowerShell 3.0

1.  从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547) 安装 Microsoft .NET Framework 4 (dotNetFx40\_Full\_setup.exe) 的完全安装版。

    或者，从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919) 安装 Microsoft .NET Framework 4.5 (dotNetFx45\_Full\_setup.exe)。

2.  从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290) 安装 Windows Management Framework 3.0。

有关启动 Windows PowerShell 3.0 的信息，请参阅[在早期版本的 Windows 上启动 Windows PowerShell](Starting-Windows-PowerShell-on-Earlier-Versions-of-Windows.md)。

## <a name="BKMK_InstallingOnServerCore"></a>在 Server Core 上安装 Windows PowerShell
这些说明解释了如何在运行 Windows Server 2008 R2 Service Pack 1 的 Server Core 安装选项的计算机上安装 Windows PowerShell 3.0。

该过程的第一步使用部署映像服务和管理 (DISM) 命令来为 Server Core 和 Windows PowerShell 2.0 安装 Microsoft .NET Framework 2.0。 这些程序是在后续步骤中安装的 Windows Management Framework 3.0 的先决条件。

#### 正在准备安装

-   安装 Windows Management Framework 3.0 之前，请卸载所有早期版本的 Windows Management Framework 3.0。

#### 安装 Windows PowerShell 3.0

1.  启动 Cmd.exe

2.  运行以下 DISM 命令。 这些命令用于安装 .NET Framework 2.0 和 Windows PowerShell 2.0。

    ```
    dism /online /enable-feature:NetFx2-ServerCore
    dism /online /enable-feature:MicrosoftWindowsPowerShell
    dism /online /enable-feature:NetFx2-ServerCore-WOW64
    ```

3.  从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=248450](http://go.microsoft.com/fwlink/?LinkID=248450) 为服务器核心安装 Microsoft .NET Framework 4.0 的完全安装版。

4.  从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290) 安装 Windows Management Framework 3.0。

## <a name="BKMK_InstallingOnWindowsServer2008LH"></a>在 Windows Server 2008 上安装 Windows PowerShell
这些说明解释了如何在运行 Windows Server 2008 Service Pack 2 的计算机上安装 Windows PowerShell 3.0。

在 Windows Server 2008 系统上，Windows Management Framework（Windows PowerShell 2.0，KB 968930）是 Windows Management Framework 3.0 的先决条件。 “扩展的身份验证保护”功能可使计算机免受身份验证转发攻击，并允许你在创建远程会话时，使用 **UseSSL** 参数 若要安装 Windows PowerShell 3.0 和 Windows PowerShell 2.0 引擎，请使用以下过程。

#### 正在准备安装

-   安装 Windows Management Framework 3.0 之前，请卸载所有早期版本的 Windows Management Framework 3.0。

#### 安装 Windows PowerShell 3.0

1.  从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=242910](http://go.microsoft.com/fwlink/?LinkID=242910) 安装具有 Service Pack 1 的 Microsoft .NET Framework 3.5。

2.  从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkId=243035](http://go.microsoft.com/fwlink/?LinkId=243035) 安装 Windows Management Framework （Windows PowerShell 2.0，KB 968930）。

3.  从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547) 安装 Microsoft .NET Framework 4 (dotNetFx40\_Full\_setup.exe) 的完全安装版。

    或者，从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919) 安装 Microsoft .NET Framework 4.5 (dotNetFx45\_Full\_setup.exe)。

4.  从 [http://go.microsoft.com/fwlink/?LinkID=186398](http://go.microsoft.com/fwlink/?LinkID=186398) 安装“扩展的身份验证保护”(KB 968389)。

5.  从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290) 安装 Windows Management Framework 3.0。

## 另请参阅
[Windows PowerShell 系统要求](Windows-PowerShell-System-Requirements.md)
[启动 Windows PowerShell [ps]](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)



<!--HONumber=Jun16_HO4-->


