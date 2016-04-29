---
title: 安装 Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6fbb0409-5a54-48ec-95e6-7f8b7d8c4969
---
# 安装 Windows PowerShell
[!INCLUDE[win8_client_1](../Token/win8_client_1_md.md)] 和 [!INCLUDE[win8_server_1](../Token/win8_server_1_md.md)] 包括 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 及其所有必备条件。 系统还包括 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎，以获得与不能使用 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 的主机程序的向后兼容性。

本主题说明如何在早期系统上安装 [!INCLUDE[psversion3](../Token/psversion3_md.md)]，以及安装和启用所需的功能。

本主题包含下列部分：

-   [在 Windows 8 和 Windows Server 2012 上安装 Windows PowerShell](../Topic/Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows8andWindowsServer2012)

-   [在 Windows 7 和 Windows Server 2008 R2 上安装 Windows PowerShell](../Topic/Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows7andWindowsServer2008R2)

-   [在 Windows Server 2008 上安装 Windows PowerShell](../Topic/Installing-Windows-PowerShell.md#BKMK_InstallingOnWindowsServer2008LH)

-   [在 Server Core 上安装 Windows PowerShell](../Topic/Installing-Windows-PowerShell.md#BKMK_InstallingOnServerCore)

-   [部署 Windows PowerShell Web 访问](assetId:///639d0eff-98a3-4124-b52c-26921ebd98b0)

-   [安装 Windows PowerShell 2.0 引擎](../Topic/Installing-the-Windows-PowerShell-2.0-Engine.md)

## <a name="BKMK_InstallingOnWindows8andWindowsServer2012"></a>在 Windows 8 和 Windows Server 2012 上安装 Windows PowerShell
[!INCLUDE[psversion3](../Token/psversion3_md.md)] 已安装、配置，并可供使用。 已安装并启用 [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)]。 有关启动 [!INCLUDE[mshshort](../Token/mshshort_md.md)] 的信息，请参阅[在 Windows 8 上启动 Windows PowerShell](assetId:///d7be1668-8617-4890-ad90-dd9765fbd2c3) 和[在 Windows Server 2012 上启动 Windows PowerShell](assetId:///4fc0110a-cc0c-42a4-bbb5-3cc89a0fc968)。

## <a name="BKMK_InstallingOnWindows7andWindowsServer2008R2"></a>在 Windows 7 和 Windows Server 2008 R2 上安装 Windows PowerShell
这些说明解释了如何在运行带有 Service Pack 1 的 [!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)] 和带有 Service Pack 1 的 [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] 的计算机上安装 [!INCLUDE[psversion3](../Token/psversion3_md.md)]。 下面是适用于使用 [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] 的 Server Core 安装选项运行的单独的安装说明。

#### 正在准备安装

-   安装 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 之前，请卸载任何早期版本的 Windows Management Framework 3.0。

#### 安装 [!INCLUDE[psversion3](../Token/psversion3_md.md)]

1.  从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547) 安装 Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) 的完全安装版。

    或者，从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919) 安装 Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) 的完全安装版。

2.  从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290) 安装 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)]。

有关启动 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 的信息，请参阅[在早期版本的 Windows 上启动 Windows PowerShell](../Topic/Starting-Windows-PowerShell-on-Earlier-Versions-of-Windows.md)。

## <a name="BKMK_InstallingOnServerCore"></a>在 Server Core 上安装 Windows PowerShell
这些说明解释了如何在运行带有 Service Pack 1 的 [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] 的 Server Core 安装选项的计算机上安装 [!INCLUDE[psversion3](../Token/psversion3_md.md)]。

该过程的第一步使用部署映像服务和管理 (DISM) 命令来为 Server Core 和 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 安装 Microsoft [!INCLUDE[dnprdnlong](../Token/dnprdnlong_md.md)]。 这些程序是在后续步骤中安装的 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 的先决条件。

#### 正在准备安装

-   安装 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 之前，请卸载任何早期版本的 Windows Management Framework 3.0。

#### 安装 [!INCLUDE[psversion3](../Token/psversion3_md.md)]

1.  启动 Cmd.exe

2.  运行以下 DISM 命令。 这些命令将安装 [!INCLUDE[dnprdnlong](../Token/dnprdnlong_md.md)] 和 [!INCLUDE[psversion2](../Token/psversion2_md.md)]。

    ```
    dism /online /enable-feature:NetFx2-ServerCore
    dism /online /enable-feature:MicrosoftWindowsPowerShell
    dism /online /enable-feature:NetFx2-ServerCore-WOW64
    ```

3.  从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=248450](http://go.microsoft.com/fwlink/?LinkID=248450) 为 Server Core 安装 Microsoft [!INCLUDE[netfx40_short](../Token/netfx40_short_md.md)] 的完全安装版。

4.  从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290) 安装 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)]。

## <a name="BKMK_InstallingOnWindowsServer2008LH"></a>在 Windows Server 2008 上安装 Windows PowerShell
这些说明解释了如何在运行带有 Service Pack 2 的 [!INCLUDE[lserver](../Token/lserver_md.md)] 的计算机上安装 [!INCLUDE[psversion3](../Token/psversion3_md.md)]。

在 [!INCLUDE[lserver](../Token/lserver_md.md)] 系统中，Windows Management Framework（[!INCLUDE[psversion2](../Token/psversion2_md.md)]，KB 968930）是 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 的先决条件。 “扩展的身份验证保护”功能可使计算机免受身份验证转发攻击，并允许你在创建远程会话时，使用 **UseSSL** 参数 若要安装 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 和 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎，请执行以下步骤。

#### 正在准备安装

-   安装 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 之前，请卸载任何早期版本的 Windows Management Framework 3.0。

#### 安装 [!INCLUDE[psversion3](../Token/psversion3_md.md)]

1.  从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=242910](http://go.microsoft.com/fwlink/?LinkID=242910) 安装具有 Service Pack 1 的 Microsoft .NET Framework 3.5。

2.  从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkId=243035](http://go.microsoft.com/fwlink/?LinkId=243035) 安装 Windows Management Framework（[!INCLUDE[psversion2](../Token/psversion2_md.md)]KB 968930）

3.  从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547) 安装 Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) 的完全安装版。

    或者，从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919) 安装 Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) 的完全安装版。

4.  从 [http://go.microsoft.com/fwlink/?LinkID=186398](http://go.microsoft.com/fwlink/?LinkID=186398) 安装“扩展的身份验证保护”(KB 968389)。

5.  从 Microsoft 下载中心 [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290) 安装 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)]。

## 另请参阅
[Windows PowerShell 系统要求](../Topic/Windows-PowerShell-System-Requirements.md)
[启动 Windows PowerShell [ps]](assetId:///8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)



<!--HONumber=Apr16_HO1-->


