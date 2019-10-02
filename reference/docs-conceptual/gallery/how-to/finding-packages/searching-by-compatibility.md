---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: 库,powershell,cmdlet,psgallery
title: 具有兼容 PowerShell 版本或操作系统的包
ms.openlocfilehash: 14038aa9b0453e1d06e6587e97da391b56297c75
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328438"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a>具有兼容 PowerShell 版本或操作系统的包

从版本 5.1 开始，PowerShell 提供了各种版本，表现出不同的功能集和平台兼容性。

## <a name="searching-by-powershell-edition"></a>按 PowerShell 版本搜索

两个 PowerShell 版本是：
- **桌面版：** 以 .NET Framework 为基础构建，提供与面向在完整功能 Windows 版本（如服务器核心和 Windows 桌面）上运行的 PowerShell 版本的脚本和模块的兼容性。
- **核心版：** 以 .NET Core 为基础构建，提供与面向在缩减功能 Windows 版本（如 Nano Server 和 Windows IoT）上运行的 PowerShell 版本的脚本和模块的兼容性。

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a>PowerShell 库允许筛选对特定 PowerShell 版本兼容的包

如果某个包已指定兼容的 PSEditions，则会在包显示页和包结果中将其列为“PowerShell 版本”的一部分。
还可以使用 PowerShell 搜索兼容包。

![具有 PSEditions 的项显示页](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a>在库 UI 中搜索在 PowerShell Core 上工作的包

使用标记“PSEdition_Desktop”和标记“PSEdition_Core”筛选 PowerShell 库中的包。

### <a name="use-tagspsedition_core-to-search-items-compatible-with-powershell-core-edition"></a>使用标记“PSEdition_Core”搜索兼容 PowerShell 核心版本的项。

![在结果中搜索兼容 Core PSEdition 的项](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspsedition_desktop-to-search-items-compatible-with-powershell-desktop-edition"></a>使用标记“PSEdition_Desktop”搜索兼容 PowerShell Desktop Edition 的项。

![在结果中搜索兼容 Desktop PSEdition 的项](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a>使用 PowerShell 搜索包以查找兼容版本
可以指定标记以针对 PowerShell 版本和操作系统进行筛选。
可使用 `Find-Package` cmdlet，指定 `-Tag` 参数来指定作为目标的版本（和操作系统）。
类似于下面这样：

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a>按操作系统搜索

由于 PowerShell Core 适用于 Windows、Linux 和 MacOS，因此可以针对这些操作系统的任意组合设计库中的包。 在库 UI 中，使用以下搜索标记查找按操作系统进行标记的包：

- 标记：“Windows”
- 标记：“Linux”
- 标记：“MacOS”

可以对 `Find-Module`（以及 PowerShellGet 模块中的其他 cmdlet）指定这些标记，类似于下面这样：

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a>搜索多个兼容性

可以使用以下语法查找具有多个兼容性的包：

标记："Compatibility1" "Compatibility2"

例如，如果要查找具有在 Windows 和 Linux 计算机上运行的 PowerShell Core 兼容性的包，请使用搜索标记：

标记："PSEdition_Core" "Windows" "Linux"

若要使用 PowerShell 进行搜索，可以使用 `Find-Module`（以及 PowerShellGet 模块中的其他 cmdlet），类似于下面这样：

```powershell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>有关创作和查找兼容的 PowerShell 版本的包的更多详细信息

- [PSEditions 模块](../../concepts/module-psedition-support.md)
- [PSEditions 脚本](../../concepts/script-psedition-support.md)
