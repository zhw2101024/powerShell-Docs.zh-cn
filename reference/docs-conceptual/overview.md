---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: PowerShell 脚本
ms.openlocfilehash: 281f2e798b3d3fa1c150b079d633cb7e8490dcec
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "62058482"
---
# <a name="powershell"></a>PowerShell

PowerShell 是构建于 .NET 上基于任务的命令行 shell 和脚本语言。
PowerShell 可帮助系统管理员和高级用户快速自动执行用于管理操作系统（Linux、macOS 和 Windows）和流程的任务。

使用 PowerShell 命令可以从命令行管理计算机。 PowerShell 提供程序可让你访问数据存储（如注册表和证书存储），与你访问文件系统一样方便。 PowerShell 具有丰富的表达式分析器和完全开发的脚本语言。

## <a name="powershell-is-open-source"></a>PowerShell 是开放源代码

PowerShell 基本源代码目前在 GitHub 中提供，且对社区贡献开放。
请参阅 [GitHub 上的 PowerShell 源](https://github.com/powershell/powershell)。

可以从[获取 PowerShell](https://github.com/PowerShell/PowerShell#get-powershell) 的内容入手。
或者可以快速查看[入门](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)。

## <a name="powershell-design-goals"></a>PowerShell 设计目标

PowerShell 旨在消除长期存在的问题和添加新功能，从而改进命令行和脚本环境。

### <a name="discoverability"></a>可发现性

PowerShell 简化了它的功能发现过程。 例如，若要查找用于查看和更改 Windows 服务的 cmdlet 列表，请键入：

```powershell
Get-Command *-Service
```

发现完成任务的 cmdlet 后，可以运行 `Get-Help` cmdlet 来详细了解此 cmdlet。 例如，若要显示 `Get-Service` cmdlet 的帮助信息，请键入：

```powershell
Get-Help Get-Service
```

大多数 cmdlet 会返回对象，这些对象可获得操作，然后再呈现为显示文本。 若要全面了解 cmdlet 的输出，请将输出通过管道传递给 `Get-Member` cmdlet。 例如，下面的命令显示 `Get-Service` cmdlet 的输出对象成员的相关信息。

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>一致性

管理系统是一项复杂的任务。 具有一致的接口的工具有助于控制固有的复杂性。 遗憾的是，命令行工具和可编写脚本的组件对象模型 (COM) 对象的一致性均未知。

PowerShell 一致性是它的主要资产之一。 例如，如果了解如何使用 `Sort-Object` cmdlet，可以利用这一知识对任何 cmdlet 的输出进行排序。 不需要了解每个 cmdlet 的不同排序例程。

此外，cmdlet 开发人员无需为其 cmdlet 设计排序功能。 PowerShell 提供了一个框架，其中包含强制执行一致性的基本功能。 该框架消除了留给开发人员的一些选择。 但是，它也因而使得 cmdlet 的开发更加简单。

### <a name="interactive-and-scripting-environments"></a>交互式脚本编写环境

Windows 命令提示符提供了一个可访问命令行工具和基本脚本的交互式 shell。 Windows 脚本宿主 (WSH) 具有可编写脚本的命令行工具和 COM 自动化对象，但不提供交互式 shell。

PowerShell 结合了交互式 shell 和脚本编写环境。 PowerShell 可以访问命令行工具、COM 对象和 .NET 类库。 此功能组合可扩展交互用户、脚本编写者和系统管理员的功能。

### <a name="object-orientation"></a>面向对象

PowerShell 基于对象而非文本。 命令的输出是一个对象。 可以将输出对象通过管道发送给另一个命令以作为其输入。

此管道为具有使用其他 shell 经验的人员提供熟悉的界面。 通过发送对象而不是文本，PowerShell 扩展了这一概念。

### <a name="easy-transition-to-scripting"></a>轻松转换到脚本

借助 PowerShell 的命令可发现性，可以从以交互方式键入命令轻松转换为创建和运行脚本。 使用 PowerShell 脚本和历史记录，可以轻松地将命令复制到文件以用作脚本。
