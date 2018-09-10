---
ms.date: 08/24/2018
keywords: powershell,cmdlet
title: 了解 PowerShell 名称
ms.assetid: b4d0fd22-8298-4ee6-82ae-9b6f2907c986
ms.openlocfilehash: 44c66488a20c38d8528c92d753f6b32dda5a2dcb
ms.sourcegitcommit: c170a1608d20d3c925d79c35fa208f650d014146
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2018
ms.locfileid: "43353260"
---
# <a name="learning-powershell-names"></a>了解 PowerShell 名称

学习命令和参数的名称需要在了解大多数命令行接口方面投入大量的时间。 问题是模式很少。 记忆是学习需要定期使用的命令和参数的唯一方法。

使用新命令或参数时，不能总是使用已经知道的内容。 必须找到并了解一个新名称。 按照惯例，命令行界面从一小组工具开始，并随着增量添加而增长。 这就很容易理解命令行界面为什么没有标准结构。
这似乎是命令名称的逻辑，因为每个命令都是一个单独的工具。 PowerShell 有一种更好的方法来处理命令名称。

## <a name="learning-command-names-in-traditional-shells"></a>学习传统 shell 中的命令名称

大多数命令用于管理操作系统或应用程序中的元素，如服务或进程。 命令具有多个名称，这些名称可能或可能不会纳入一个系列。 例如，在 Windows 系统中，你可以使用 `net start` 和 `net stop` 命令来启动和停止服务。 Sc.exe 是另一个适用于 Windows 的服务控制工具。 该名称不会纳入 net.exe 服务命令的命名模式。 对于流程管理，Windows 使用 tasklist.exe 命令列出进程，使用 taskkill.exe 命令终止进程。

另外，这些命令的参数规范不规则。 不能使用 `net start` 命令来启动远程计算机上的服务。 sc.exe  命令可以启动远程计算机上的服务。 但是，若要指定远程计算机，则必须在其名称前添加双反斜杠作为前缀。 若要在名为 DC01 的远程计算机上启动后台处理程序服务，请键入 `sc.exe \\DC01 start spooler`。
若要列出在 DC01 上运行的任务，请使用 /S 参数和不带反斜杠的计算机名称。 例如，`tasklist /S DC01`。

> [!NOTE]
> 在 PowerShell v6 之前，`sc` 是 `Set-Content` cmdlet 的别名。 若要运行 sc.exe 命令，必须包含此文件扩展名。

服务和进程是计算机上具有明确定义的生命周期的可管理元素的示例。 你可能想要启动或停止服务或进程，或获取所有当前正在运行的服务或进程的列表。 虽然它们之间存在重要的技术差异，但在服务和进程上执行的操作在概念上是相同的。 此外，通过指定参数自定义操作所做的选择从概念上讲也是相似的。

PowerShell 利用这些相似之处减少了解和使用 cmdlet 时需要知道的不同名称的数量。

## <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a>Cmdlet 使用谓词-名词的名称来减少命令记忆

PowerShell 使用“谓词 - 名词”命名系统。 每个 cmdlet 名称都由一个标准谓词、连字符和特定名词组成。 PowerShell 谓词并不始终是英文谓词，但在 PowerShell 中表达特定的操作。 名词非常类似于任何语言中的名词。 它们描述在系统管理中十分重要的特定类型的对象。 通过查看一些示例，可以很容易地演示这些包含两个部分的名称如何减少学习的负担。

PowerShell 有一套推荐的标准谓词。 名词所受限制较少，但它们应始终描述谓词作用的对象。 PowerShell 具有 `Get-Process`、`Stop-Process`、`Get-Service` 和 `Stop-Service` 等命令。

对于包含两个名词和两个谓词的此示例，一致性并未简化太多学习。 将该列表扩展为一组标准化的 10 个谓词和 10 个名词。 现在你只需要了解 20 个词。
但是这些词可以组合形成 100 个不同的命令名称。

通过阅读其名称，可以很容易地了解 PowerShell 命令的作用。 关闭计算机的命令是 `Stop-Computer`。 列出网络上所有计算机的命令是 `Get-Computer`。 获取系统日期的命令是 `Get-Date`。

可以使用 `Get-Command` 的 Verb 参数列出包含特定谓词的所有命令。 例如，若要查看使用谓词 `Get` 的所有 cmdlet，键入：

```
PS> Get-Command -Verb Get

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Acl                         Get-Acl [[-Path] <String[]>]...
Cmdlet          Get-Alias                       Get-Alias [[-Name] <String[]...
Cmdlet          Get-AuthenticodeSignature       Get-AuthenticodeSignature [-...
Cmdlet          Get-ChildItem                   Get-ChildItem [[-Path] <Stri...
...
```

使用 Noun 参数查看将对同一类型的对象产生影响的命令系列。 例如，运行以下命令可以查看用于管理服务的命令：

```
PS> Get-Command -Noun Service

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Service                     Get-Service [[-Name] <String...
Cmdlet          New-Service                     New-Service [-Name] <String>...
Cmdlet          Restart-Service                 Restart-Service [-Name] <Str...
Cmdlet          Resume-Service                  Resume-Service [-Name] <Stri...
Cmdlet          Set-Service                     Set-Service [-Name] <String>...
Cmdlet          Start-Service                   Start-Service [-Name] <Strin...
Cmdlet          Stop-Service                    Stop-Service [-Name] <String...
Cmdlet          Suspend-Service                 Suspend-Service [-Name] <Str...
...
```

## <a name="cmdlets-use-standard-parameters"></a>Cmdlet 使用标准参数

如前文所述，在传统命令行接口中使用的命令并不总是具有一致的参数名称。 参数通常是易于键入但对新用户来说不能轻松理解的单个字符或缩写词。

不同于大多数其他传统的命令行接口，PowerShell 直接处理参数，并使用参数的这种直接访问权限以及开发人员指南标准化参数名称。 本指南建议但不会保证每个 cmdlet 都符合标准。

PowerShell 还标准化参数分隔符。 使用 PowerShell 命令，参数名称前面始终带有“-”。 请考虑以下示例：

```powershell
Get-Command -Name Clear-Host
```

参数的名称为 Name，但在命令行上用作参数时，将其键入为 `-Name`。

以下是标准参数名称和用法的一些一般特征。

### <a name="the-help-parameter-"></a>帮助参数 (?)

在任何 cmdlet 上指定 `-Help` 或 `-?` 参数时，PowerShell 将显示该 cmdlet 的帮助。 未执行此 cmdlet。

### <a name="common-parameters"></a>通用参数

PowerShell 有几个通用参数。 这些参数由 PowerShell 引擎控制。 通用参数的行为方式始终相同。 通用参数有 **WhatIf**、**Confirm**、**Verbose**、**Debug**、**Warn**、**ErrorAction**、**ErrorVariable**、**OutVariable** 和 **OutBuffer**

### <a name="recommended-parameter-names"></a>建议的参数名称

对于类似的参数，PowerShell 核心 cmdlet 使用标准名称。 尽管不强制使用这些标准名称，但是具有明确的指南来鼓励进行标准化。

例如，指示计算机的参数的建议名称是 ComputerName，而不是 Server、Host、System、Node 或其他常见的备选单词。 其他重要的建议参数名称是 Force、Exclude、Include、PassThru、Path 和 CaseSensitive。