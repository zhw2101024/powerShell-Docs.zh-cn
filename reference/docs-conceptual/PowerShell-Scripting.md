---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: PowerShell 脚本
ms.openlocfilehash: c6ba3abc2544834e2cbec16a524f79399a1d2599
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094045"
---
# <a name="powershell"></a>PowerShell

PowerShell 在 .NET Framework 基础之上构建，是一种基于任务的命令行 Shell 脚本语言；专门面向系统管理员和高级用户，可快速自动化多个操作系统（Linux、macOS、Unix 和 Windows）和这些操作系统上运行的应用程序相关进程的管理。

## <a name="powershell-is-open-source"></a>PowerShell 是开放源代码

PowerShell 基本源代码目前在 GitHub 中提供，且对社区贡献开放。
请参阅 [GitHub 上的 PowerShell 源](https://github.com/powershell/powershell)。

可以从[获取 PowerShell](https://github.com/PowerShell/PowerShell#get-powershell) 中的所需位数入手。
或者快速查看[入门](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)

## <a name="powershell-design-goals"></a>PowerShell 设计目标
PowerShell 旨在消除长期存在的问题和添加新功能，从而改进命令行和脚本环境。

### <a name="discoverability"></a>可发现性
PowerShell 简化了它的功能发现过程。 例如，若要查找用于查看和更改 Windows 服务的 cmdlet 列表，请键入：

```powershell
Get-Command *-Service
```

发现完成任务的 cmdlet 后，可以运行 `Get-Help` cmdlet 来详细了解此 cmdlet。
例如，若要显示 `Get-Service` cmdlet 的帮助信息，请键入：

```powershell
Get-Help Get-Service
```
大多数 cmdlet 会发出对象，这些对象可获得操作，然后再呈现为显示文本。
若要全面了解此 cmdlet 的输出，请将它的输出通过管道传递给 `Get-Member` cmdlet。
例如，下面的命令显示 `Get-Service` cmdlet 的输出对象成员的相关信息。

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a>一致性
管理系统是一项复杂的任务，具有一致的接口的工具有助于控制固有的复杂性。
遗憾的是，命令行工具和可脚本化 COM 对象的一致性均未知。

PowerShell 一致性是它的主要资产之一。
例如，如果了解如何使用 `Sort-Object` cmdlet，可以利用这一知识对任何 cmdlet 的输出进行排序。
不需要了解每个 cmdlet 的不同排序例程。

此外，cmdlet 开发人员无需为其 cmdlet 设计排序功能。
PowerShell 包含提供基本功能的框架，并强制在接口的多个方面保持一致。
该框架消除了通常留给开发人员的某些选择，但它也因而使得开发可靠的和易于使用的 cmdlet 变得简单得多。

### <a name="interactive-and-scripting-environments"></a>交互式脚本编写环境
PowerShell 是组合的交互式脚本编写环境，便于用户访问命令行工具和 COM 对象，并使用 .NET Framework 类库 (FCL) 的强大功能。

此环境改进了 Windows 命令提示，它将提供具有多个命令行工具的交互式环境。
它还改进了 Windows 脚本宿主 (WSH) 脚本，让你可以使用多个命令行工具和 COM 自动化对象，但不提供交互式环境。

通过结合使用以上所有功能，PowerShell 可以扩展交互用户和脚本编写者的能力，并提高系统可管理性。

### <a name="object-orientation"></a>面向对象
尽管可以在文本框中键入命令与 PowerShell 交互，PowerShell 仍以对象（而不是文本）为基础。
命令的输出是一个对象。
可以将输出对象发送给另一个命令以作为其输入。
因此，PowerShell 为使用过其他命令行管理程序的用户提供熟悉界面，同时引入新的强大命令行范例。
它让你能够发送对象而不是文本，从而扩展了在命令之间发送数据的概念。

### <a name="easy-transition-to-scripting"></a>轻松转换到脚本
借助 PowerShell，可以从以交互方式键入命令轻松转换为创建和运行脚本。
可以在 PowerShell 命令提示符处键入命令，从而发现执行某项任务的命令。
然后，你可以在将这些命令保存到副本或历史记录中，然后将其复制到文件以用作脚本。
