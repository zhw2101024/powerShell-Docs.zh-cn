---
title:  学习 Windows PowerShell 名称
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  b4d0fd22-8298-4ee6-82ae-9b6f2907c986
---

# 学习 Windows PowerShell 名称
学习命令和命令参数的名称是使用大多数命令行接口时重要的时间投入。 问题是模式非常少，因此学习的唯一方法是通过记住需要定期使用的每个命令和每个参数。

当使用新命令或参数时，你通常不能使用已知名称；你需要查找和学习新的名称。 如果你看看接口是如何从一小组工具通过递增添加发展为功能，那就很容易明白为什么结构是非标准的。 特别是命令名称，由于每个命令都是独立的工具，所以听起来可能很有逻辑，但还有更好的方法来处理命令名称。

大多数命令用于管理操作系统或应用程序中的元素，如服务或进程。 命令具有众多名称，这些名称可能或可能不会纳入一个系列。 例如，在 Windows 系统中，你可以使用 **net start** 和 **net stop** 命令来启动和停止服务。 还有另一种对 Windows 更通用的服务控制工具，该工具具有完全不同的名称，即 **sc**，但该名称未纳入 **net** 服务命令的命名模式。 对于流程管理，Windows 使用 **tasklist** 命令列出进程，使用 **taskkill** 命令终止进程。

采用参数的命令的参数规范不规则。 不能使用 **net start** 命令来启动远程计算机上的服务。 **sc** 命令将在远程计算机上启动服务，但若要指定远程计算机，必须在其名称前使用双反斜杠作为前缀。 例如，若要在名为 DC01 的远程计算机上启动后台处理程序服务，应键入 **sc \DC01 start spooler**。 若要列出在 DC01 上运行的任务，你需要使用 **/S**（代指“系统”）参数并提供没有反斜杠的名称 DC01，如：**tasklist /S DC01**。

尽管服务和进程之间具有重要的技术区别，但它们都是计算机上的可管理元素的示例，具有定义完善的生命周期。 你可能想要启动或停止服务或进程，或获取所有当前正在运行的服务或进程的列表。 换而言之，尽管服务和过程是不同的事物，我们对服务或进程执行的操作通常从概念上讲是相同的。 此外，通过指定参数自定义操作所做的选择从概念上讲也是相似的。

Windows PowerShell 利用这些相似之处减少了解和使用 cmdlet 时需要知道的不同名称的数量。

### Cmdlet 使用谓词-名词的名称来减少命令记忆
Windows PowerShell 使用“谓词-名词”命名系统，其中每个 cmdlet 名称由标准谓词、连字符、特定名词组成。 Windows PowerShell 谓词并不始终是英文谓词，但在 Windows PowerShell 中表达特定的操作。 名词非常类似于任何语言中的名词，它们描述在系统管理中十分重要的特定类型的对象。 通过查看一些谓词和名词的示例，可以很容易地演示这些包含两个部分的名称如何减少学习的负担。

名词所受限制更少，但它们应始终描述命令作用的对象。 Windows PowerShell 很多命令，例如 **Get-Process**、**Stop-Process**、**Get-Service** 和 **Stop-Service**。

在两个名词和两个谓词的情况下，一致性并未简化太多学习。 但是，如果你查看 10 个谓词和 10 个名词的标准集，那么你仅需了解 20 个词，但这些词可用于组成 100 个不同的命令名。

通常情况下，你通过阅读命令的名称就可以识别命令，对新的命令该使用什么名称通常是显而易见的。 例如，计算机关机命令可能是 **Stop-Computer**。 列出网络上的所有计算机的命令可能是 **Get-Computer**。 获取系统日期的命令是 **Get-Date**。

你可以使用 **Get-Command** 的 **-Verb** 参数列出包含特定谓词的所有命令（我们将在下一节中详细介绍 **Get-Command**）。 例如，若要查看使用谓词 **Get** 的所有 cmdlet，键入：

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

**-Noun** 参数更有用，因为它可让你查看将对同一类型的对象产生影响的命令系列。 例如，如果你想要查看哪些命令可用于管理服务，请键入以下命令：

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

命令不一定是 cmdlet，只是因为命令具有谓词-名词的命名结构。 并非 cmdlet 但具有谓词-名词名称的本地 Windows PowerShell 命令的一个例子为，用于清除控制台窗口的命令：Clear-Host。 Clear-Host 命令实际上是内部函数，如果你对其运行 Get-Command 便可知道：

```
PS> Get-Command -Name Clear-Host

CommandType     Name                            Definition
-----------     ----                            ----------
Function        Clear-Host                      $spaceType = [System.Managem...
```

### Cmdlet 使用标准参数
如前文所述，在传统命令行接口中使用的命令通常没有一致的参数名称。 有时参数根本没有名称。 若有名称，通常是可以快速输入但对新用户来说不能轻松理解的单个字符或缩写词。

不同于大多数其他传统的命令行接口，Windows PowerShell 直接处理参数，并使用参数的这种直接访问权限以及开发人员指南标准化参数名称。 尽管这样并不保证每个 cmdlet 将始终符合标准，但还是备受鼓舞。

> [!NOTE]
> 使用时，参数名始终具有一个预置的“-”，以允许 Windows PowerShell 清楚地将它们标识为参数。 在 **Get-Command -Name Clear-Host** 示例中，参数的名称为 **Name**，但输入时为 -**Name**

以下是标准参数名称和用法的一些一般特征。

#### 帮助参数 (?)
当你指定 **-?** 参数到任何 cmdlet，将不会执行 cmdlet。 相反，Windows PowerShell 将显示有关 cmdlet 的帮助。

#### 通用参数
Windows PowerShell 具有一些名为“通用参数”的参数。 因为这些参数由 Windows PowerShell 引擎控制，每当 cmdlet 实现这些参数时，它们的行为方式将始终相同。 通用参数有 **WhatIf**、**Confirm**、**Verbose**、**Debug**、**Warn**、**ErrorAction**、**ErrorVariable**、**OutVariable** 和 **OutBuffer**

#### 建议参数
对于类似的参数，Windows PowerShell 核心 cmdlet 使用标准名称。 尽管不强制使用参数名称，但是具有明确的用法指南支持标准化。

例如，本指南建议使用例如 **ComputerName** 等名称命名指示计算机的参数，而不使用 Server、Host、System、Node 或其他常见的备选单词。 重要的建议参数名称有 **Force**、**Exclude**、**Include**、**PassThru**、**Path** 和 **CaseSensitive**。



<!--HONumber=May16_HO2-->


