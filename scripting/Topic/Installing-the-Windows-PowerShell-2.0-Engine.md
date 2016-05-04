---
title: 安装 Windows PowerShell 2.0 引擎
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 82928f2b-f96a-4ae6-a0d0-6e7b181da308
---
# 安装 Windows PowerShell 2.0 引擎
本主题说明了如何安装 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎。

[!INCLUDE[psversion3](../Token/psversion3_md.md)] 旨在与 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 向后兼容。 Cmdlet、提供程序、管理单元、模块，以及为 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 编写的脚本照常在 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 和 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 中运行。 但是，由于 Microsoft.NET framework 4 中的运行时激活策略的更改，为 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 编写并使用公共语言运行时 (CLR) 2.0 编译的 Windows PowerShell 主机程序在使用 CLR 4.0 编译的 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 的更高版本中未进行修改时，将无法运行。

为了保持受这些更改影响的命令和主机程序的向后兼容性，[!INCLUDE[psversion2](../Token/psversion2_md.md)]、[!INCLUDE[psversion3](../Token/psversion3_md.md)] 和 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 引擎被设计为并排运行。 此外，[!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎包含在 [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)]、[!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)]、[!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)]、[!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] 和 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 中。 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎仅在当前脚本或主机程序无法运行时使用，因为它与 [!INCLUDE[psversion3](../Token/psversion3_md.md)]、[!INCLUDE[psversion4](../Token/psversion4_md.md)] 或 Microsoft .NET Framework 4 不兼容。 这种情况很少见。

[!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎是 [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)]、[!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)]、[!INCLUDE[win8_client_1](../Token/win8_client_1_md.md)] 和 [!INCLUDE[win8_server_1](../Token/win8_server_1_md.md)] 的可选功能。 在早期版本的 Windows 中，当你安装 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 时，[!INCLUDE[psversion3](../Token/psversion3_md.md)] 安装将完全替换 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 安装目录中的 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 安装。 但是，将保留 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎。

有关启动 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎的信息，请参阅[启动 Windows PowerShell 2.0 引擎](../Topic/Starting-the-Windows-PowerShell-2.0-Engine.md)。

## 在 [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)] 和 [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)] 上
在 [!INCLUDE[winblue_client_2](../Token/winblue_client_2_md.md)] 和 [!INCLUDE[win8_client_2](../Token/win8_client_2_md.md)] 上，将默认开启 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎功能。 但是，若要使用它，则需要打开它所要求的 Microsoft.NET Framework 3.5 的选项。 本节还介绍了如何打开和关闭 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎功能。

#### 打开 .NET Framework 3.5

1.  在“开始”屏幕上，键入“Windows 功能”。

2.  在“应用”工具栏上，单击“设置”，然后单击“打开或关闭 Windows 功能”。

3.  在“Windows 功能”框中，单击“.NET Framework 3.5（包括.NET 2.0 和 3.0）”以将其选中。

    当你选择“.NET Framework 3.5（包括.NET 2.0 和 3.0）”后，将填充该框，以指示仅选中功能的一部分。 但是，这对 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎已足够。

#### 打开和关闭 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎

1.  在“开始”屏幕上，键入“Windows 功能”。

2.  在“应用”工具栏上，单击“设置”，然后单击“打开或关闭 Windows 功能”。

3.  在“Windows 功能”框中，展开 **[!INCLUDE[psversion2](../Token/psversion2_md.md)]** 节点，然后单击“[!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎”框来选择或清除它。

## 在 [!INCLUDE[winblue_server_2](../Token/winblue_server_2_md.md)] 和 [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] 上
使用以下过程来添加 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎和 Microsoft.NET Framework 3.5 功能。 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎至少需要 Microsoft .NET Framework 2.0.50727。 Microsoft .NET Framework 3.5 满足此要求。

#### 添加 .NET Framework 3.5 功能

1.  在“服务器管理器”中，从“管理”菜单上，选择“添加角色和功能”。

    或者在“服务器管理器”中，单击“所有服务器”，右键单击某个服务器名称，然后选择“添加角色和功能”。

2.  在“安装类型”页上，选择“基于角色或基于功能的安装”。

3.  在“功能”页上，展开“.NET 3.5 Framework 功能”节点，然后选择“.NET Framework 3.5（包括 .NET 2.0 和 3.0）”。

    [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎不需要该节点下的其他选项。

#### 添加 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎功能

-   在“服务器管理器”中，从“管理”菜单上，选择“添加角色和功能”。

    或者“服务器管理器”，单击“所有服务器”，右键单击服务器名称，然后选择“添加角色和功能”。

-   在“安装类型”页上，选择“基于角色或基于功能的安装”。

-   在“功能”页上，展开“[!INCLUDE[mshshort](../Token/mshshort_md.md)]（已安装）”节点，然后选择“[!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎”。

有关启动 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎的信息，请参阅[启动 Windows PowerShell 2.0 引擎](../Topic/Starting-the-Windows-PowerShell-2.0-Engine.md)。

## 在较早的系统上
在 [!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)]、[!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] 和 [!INCLUDE[win8_server_2](../Token/win8_server_2_md.md)] 上安装 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 的 [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) 安装包包括 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎。 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎已启用并可供使用（若需要），而无需其他安装、设置或配置。

在 [!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)]、[!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] 和 [!INCLUDE[lserver](../Token/lserver_md.md)] 上安装 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 的 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 安装包包括 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎。 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 引擎已启用并可供使用（若需要），而无需其他安装、设置或配置。

## 另请参阅
[Windows PowerShell 系统要求](../Topic/Windows-PowerShell-System-Requirements.md)
[安装 Windows PowerShell](../Topic/Installing-Windows-PowerShell.md)
[启动 Windows PowerShell [ps]](assetId:///8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)
[启动 Windows PowerShell 2.0 引擎](../Topic/Starting-the-Windows-PowerShell-2.0-Engine.md)



<!--HONumber=Apr16_HO1-->


