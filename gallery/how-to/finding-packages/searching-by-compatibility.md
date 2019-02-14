---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: 库,powershell,cmdlet,psgallery
title: 具有兼容 PowerShell 版本或操作系统包
ms.openlocfilehash: 8230866561d3021379a48cc2c83fb4104a4058c1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676910"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a>具有兼容 PowerShell 版本或操作系统包

从版本 5.1 开始，PowerShell 提供了各种版本，表现出不同的功能集和平台兼容性。

## <a name="searching-by-powershell-edition"></a>搜索的 PowerShell 版本 
两个 Powershell 版本是：
- **桌面版：** .NET Framework 上构建，并提供与面向新版的 Server Core 等的 Windows 和 Windows 桌面的完整占用空间减小版本上运行的 PowerShell 脚本和模块的兼容性。
- **核心版：**.NET Core 上生成，并提供与面向版本的 Nano Server 等的 Windows 和 Windows IoT 的占用空间减少的版本上运行的 PowerShell 脚本和模块的兼容性。

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a>PowerShell 库允许您为特定 PowerShell 版本筛选兼容包

如果包具有兼容 PSEditions 指定，它们被列为 PowerShell Editions 的一部分包显示页和包的结果。
您还可以使用 PowerShell 的兼容包的搜索。

![具有 PSEditions 的项显示页](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a>搜索的库 UI 中的包适用于 PowerShell Core

使用标记“PSEdition_Desktop”和标记“PSEdition_Core”筛选 PowerShell 库中的包。

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>使用标记“PSEdition_Core”搜索兼容 PowerShell 核心版本的项。

![在结果中搜索兼容 Core PSEdition 的项](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>使用标记“PSEdition_Desktop”搜索兼容 PowerShell Desktop Edition 的项。

![在结果中搜索兼容 Desktop PSEdition 的项](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a>搜索以查找使用 PowerShell 的兼容版本的包
可以指定标记 PowerShell 版本和操作系统进行筛选。 您使用`Find-Package`cmdlet 指定`-Tag`参数来指定 edition （和 OS） 您的目标。
喜欢这个：

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a>搜索由操作系统 

由于 PowerShell Core 是适用于 Windows、 Linux 和 MacOS，库中的包可能会针对这些操作系统任意组合进行设计。 在库 UI 中使用以下 searchs 标记查找包由操作系统标记：

- 标记:"Windows"
- 标记:"Linux"
- 标记："MacOS" 

可以指定这些标记`Find-Module`（和 PowerShellGet 模块中的其他 cmdlet），如下所示：

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a>搜索多个兼容性

您可以查找使用语法中具有多个兼容的包： 

标记："1>""Compatibility2" 

例如，如果您要查找与我的 Windows 和 Linux 计算机运行的 PowerShell Core 兼容性包，使用搜索标记：

标记："PSEdition_Core" "Windows" "Linux" 

若要使用 PowerShell 进行搜索，可以使用`Find-Module`（和 PowerShellGet 模块中的其他 cmdlet），如下所示：

```powewrshell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>有关创作和查找兼容的 PowerShell 版本的包的更多详细信息

- [PSEditions 模块](../../concepts/module-psedition-support.md)
- [PSEditions 脚本](../../concepts/script-psedition-support.md)
