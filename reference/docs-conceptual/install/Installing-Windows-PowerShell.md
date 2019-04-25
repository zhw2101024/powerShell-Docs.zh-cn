---
ms.date: 08/09/2017
keywords: powershell, cmdlet, 下载, 安装, 设置, windows 10, windows 8.1, windows 8.0, windows 7
title: 安装 Windows PowerShell
ms.openlocfilehash: 345cde8012bece730e7217ed16be6175ad26bb28
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086470"
---
# <a name="installing-windows-powershell"></a>安装 Windows PowerShell

从 Windows 7 SP1 和 Windows Server 2008 R2 SP1 开始，每个 Windows 中默认随附安装有 Windows PowerShell。

如果你对 PowerShell 6 及更高版本感兴趣，则需要安装 PowerShell Core 而不是 Windows PowerShell。 关于相应的信息，请参阅[在 Windows 上安装 PowerShell Core](Installing-PowerShell-Core-on-Windows.md)。

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a>在 Windows 10、8.1、8.0 和 7 中查找 PowerShell

有时在 Windows 中查找 PowerShell 控制台或 ISE（集成脚本环境）并非易事，因为其位置会随不同的 Windows 版本而发生移动。

以下表格应有助于在使用的 Windows 版本中查找 PowerShell。
此处列出的所有版本均为发布时的原始版本，没有进行任何更新。

### <a name="for-console"></a>控制台

版本 | Location
-- | --
Windows 10 | 单击左下角的 Windows 图标，键入 PowerShell
Windows 8.1、8.0 | 在开始屏幕上，键入 PowerShell。<br/>如果位于桌面，请单击左下角的 Windows 图标，键入 PowerShell
Windows 7 SP1 | 单击左下角的 Windows 图标，在搜索框中键入 PowerShell

### <a name="for-ise"></a>ISE

版本 | Location
-- | --
Windows 10 | 单击左下角的 Windows 图标，键入 ISE
Windows 8.1、8.0 | 在“开始”屏幕上，键入 PowerShell ISE。<br/>如果位于桌面，请单击左下角的 Windows 图标，键入 PowerShell ISE
Windows 7 SP1 | 单击左下角的 Windows 图标，在搜索框中键入 PowerShell

## <a name="finding-powershell-in-windows-server-versions"></a>在 Windows Server 版本中查找 PowerShell

从 Windows Server 2008 R2 开始，安装操作系统可不包含图形用户界面 (GUI)。
不含 GUI 的 Windows Server 版本名为“核心”版本，包含 GUI 的版本名为“桌面”版本。

### <a name="windows-server-core-editions"></a>Windows Server 核心版本

在所有核心版本中，登录到服务器时会显示 Windows 命令提示符窗口。

键入 `powershell` 并按“Enter”可在命令提示符会话内启动 PowerShell。
键入 `exit` 可终止 PowerShell 会话并返回命令提示符。

### <a name="windows-server-desktop-editions"></a>Windows Server 桌面版本

在所有桌面版本中，单击左下角的 Windows 图标，键入 PowerShell。
将显示控制台和 ISE 选项。

上述规则的唯一例外是 Windows Server 2008 R2 SP1 中的 ISE；这种情况下，请单击左下角的 Windows 图标，键入 PowerShell ISE。

## <a name="how-to-check-the-version-of-powershell"></a>如何检查 PowerShell 版本

若要查看已安装的 PowerShell 版本，请启动 PowerShell 控制台（或 ISE），键入 `$PSVersionTable`，然后按“Enter”。 查找 `PSVersion` 值。

## <a name="upgrading-existing-windows-powershell"></a>升级现有 Windows PowerShell

PowerShell 安装包随附于 WMF 安装程序内。
WMF 安装程序版本与 PowerShell 版本一致；不提供 Windows PowerShell 独立安装程序。

如需在 Windows 中更新现有 PowerShell 版本，请使用下表找到要更新至的 PowerShell 版本的安装程序。

Windows | PS 3.0 | PS 4.0 | PS 5.0 | PS 5.1 |
--|--|--|--|--|
Windows 10（参见说明 1）<br/>Windows Server 2016 | - | - | - | 已安装
Windows 8.1<br/>Windows Server 2012 R2 | - | 已安装 | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 8<br/>Windows Server 2012 | 已安装 | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 7 SP1<br/>Windows Server 2008 R2 SP1 | [WMF 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> [!NOTE]
>
> Windows 10 初始版本中，由于已启用自动更新，因此 PowerShell 会从版本 5.0 更新至 5.1。
>
> 如果 Windows 10 原始版本未通过 Windows 更新进行更新，则 PowerShell 版本为 5.0。

## <a name="need-azure-powershell"></a>需要 Azure PowerShell

如需要 Azure PowerShell，请先参阅 [Azure PowerShell 概述](/powershell/azure/overview)。

或者，可能需要参阅[安装和配置 Azure PowerShell](/powershell/azure/install-az-ps)

## <a name="see-also"></a>另请参阅

[Windows PowerShell 系统要求](Windows-PowerShell-System-Requirements.md)

[启动 Windows PowerShell](../getting-started/Starting-Windows-PowerShell.md)
