---
title:  了解重要的 Windows PowerShell 概念
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  3e601e38-4520-4578-a48d-b6779f1d35ee
---

# 了解重要的 Windows PowerShell 概念
Windows PowerShell 设计集成了很多不同环境的概念。 具有特定 Shell 或编程环境方面经验的人会对其中几种比较熟悉，但很少有人了解全部概念。 查看其中一些概念可获得有关 Shell 的有用概述。

### 命令不基于文本
与传统的命令行接口命令不同，Windows PowerShell cmdlet 旨在处理对象结构的信息，这些信息不仅仅只是显示在屏幕上的字符串。 命令输出会始终包含你在需要时可使用的额外信息。 我们将在本文档中深入讨论这个主题。

如果你过去使用过文本处理工具来处理命令行数据，你会发现它们在 Windows PowerShell 中的使用和工作方式会有所不同。 在大多数情况下，你不需要文本或文本处理工具来提取特定信息。 可以使用标准 Windows PowerShell 对象操作命令直接访问部分数据。

### 命令系列是可扩展的
接口（比如 Cmd.exe）不提供可直接扩展内置命令集的方法。 你可以创建在 Cmd.exe 中运行的外部命令行工具，但这些外部工具没有服务（例如帮助集成），并且 Cmd.exe 不能自动了解它们是有效命令。

Windows PowerShell 中的本机二进制命令称为 *cmdlet*（读作 command-lets），可以通过创建 cmdlet 和使用管理单元向 Windows PowerShell 添加 cmdlet 来进行扩充。 已对 Windows PowerShell *管理单元*进行编译，就像任何其他接口中的二进制工具一样。 可以使用它们将 Windows PowerShell 提供程序以及新的 cmdlet 添加到 Shell 中。

由于 Windows PowerShell 内部命令的特殊性质，我们将视其为 *cmdlet*。

> [!NOTE]
> Windows PowerShell 可运行不同于 cmdlet 的其他命令。 我们不会在 Windows PowerShell 用户指南中详细讨论这些命令，但作为不同类型的命令，对它们进行了解会很有用。 Windows PowerShell 支持类似于 UNIX shell 脚本和 Cmd.exe 批处理文件但文件扩展名为 .ps1 的脚本。 Windows PowerShell 还允许你创建可在接口或脚本中直接使用的内部函数。

### Windows PowerShell 处理控制台输入和显示
当你键入命令时，Windows PowerShell 会始终直接处理命令行输入。 Windows PowerShell 还会对你在屏幕上看到的输出进行格式设置。 这很重要，因为它减少了每个 cmdlet 所需执行的工作，并确保你始终可以相同的方式执行操作而不用考虑所使用的 cmdlet。 一个有关这会如何简化工具开发人员和用户生活的例子是命令行帮助。

传统的命令行工具有自己的用于请求和显示帮助的方案。 某些命令行工具使用 **/?** 来触发显示帮助内容；其他工具则使用 **\-?**、**\/H** 或 **\/\/**。 有些工具会在 GUI 窗口而不是在控制台显示区域显示帮助。 一些复杂的工具，比如应用程序更新程序，在显示帮助前先将内部文件解压缩。 如果你使用的参数有误，该工具可能会忽略你键入的内容并自动开始执行任务。

当你在 Windows PowerShell 中输入命令时，Windows PowerShell 会自动分析并预处理你输入的任何内容。 如果你将 **-?** 参数 和 Windows PowerShell cmdlet 结合使用，则始终意味着“显示此命令的帮助”。 Cmdlet 开发人员无需分析命令；只需提供帮助文本。

即使在 Windows PowerShell 中运行传统命令行工具，也仍可使用 Windows powershell 的帮助功能，了解这一点很重要。 Windows PowerShell 处理参数并将结果传递给外部工具。

> [!NOTE]
> 如果在 Windows PowerShell 中运行图形应用程序，将随即打开该应用程序的窗口。 Windows PowerShell 仅会在处理你提供的命令行输入或返回到控制台窗口中的应用程序输出时才会进行干预；它不会内在地影响应用程序的工作方式。

### Windows PowerShell 使用某些 C\# 语法
Windows PowerShell 所具有的语法功能和关键字与 C# 编程语言中所使用的十分类似，因为 Windows PowerShell 是基于 .NET Framework。 如果你对 C# 语言感兴趣，那么学习 Windows PowerShell 会让 C# 语言的学习变得更加容易。

如果你不是 C# 程序员，这种相似性就不重要了。 但是，如果你已经熟悉了 C#，这种相似性就可以使 Windows PowerShell 的学习变得容易许多。



<!--HONumber=May16_HO2-->


