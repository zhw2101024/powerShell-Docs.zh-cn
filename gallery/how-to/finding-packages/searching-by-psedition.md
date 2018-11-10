---
ms.date: 06/12/2017
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
title: 具有兼容的 PowerShell 版本的包
ms.openlocfilehash: e16cfb0ee30e344c9399bec2985baafc5a252fd7
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003667"
---
# <a name="packages-with-compatible-powershell-editions"></a>具有兼容的 PowerShell 版本的包

从版本 5.1 开始，PowerShell 以表现出不同功能集和平台兼容性的不同版本提供。

- **桌面版：** 以 .NET Framework 为基础构建，提供与面向在完整功能 Windows 版本（如服务器核心和 Windows 桌面）上运行的 PowerShell 版本的脚本和模块的兼容性。
- **核心版：** 以 .NET Core 为基础构建，提供与面向在缩减功能 Windows 版本（如 Nano Server 和 Windows IoT）上运行的 PowerShell 版本的脚本和模块的兼容性。

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-packages-compatible-for-specific-powershell-editions"></a>PowerShell 库提取支持的 PSEditions 元数据，并允许筛选兼容特定 PowerShell 版本的包

如果某个包已指定兼容的 PSEditions，则会在包显示页和包结果中将其列为“PowerShell 版本”的一部分。

![具有 PSEditions 的项显示页](../../Images/manual_package_download.png)

## <a name="search-for-packages-in-the-gallery-ui-which-works-on-powershellcore"></a>搜索在 PowerShellCore 上工作的库 UI 中的包

使用标记“PSEdition_Desktop”和标记“PSEdition_Core”筛选 PowerShell 库中的包。

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>使用标记“PSEdition_Core”搜索兼容 PowerShell 核心版本的项。

![在结果中搜索兼容 Core PSEdition 的项](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>使用标记“PSEdition_Desktop”搜索兼容 PowerShell Desktop Edition 的项。

![在结果中搜索兼容 Desktop PSEdition 的项](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>有关创作和查找兼容的 PowerShell 版本的包的更多详细信息

- [PSEditions 模块](../../concepts/module-psedition-support.md)
- [PSEditions 脚本](../../concepts/script-psedition-support.md)
