---
ms.date: 08/23/2018
keywords: powershell,cmdlet
title: 了解重要的 PowerShell 概念
ms.openlocfilehash: 8f9af370db46ea47dbccbabb7cc90fc27b8f2765
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030978"
---
# <a name="understanding-important-powershell-concepts"></a>了解重要的 PowerShell 概念

PowerShell 设计集成了很多不同环境的概念。 具有 shell 或编程环境经验的人会熟悉几个概念。 但是，很少有人会了解所有这些概念。 查看其中一些概念可获得有关 Shell 的有用概述。

## <a name="output-is-object-based"></a>输出是基于对象的

不同于传统的命令行接口，PowerShell cmdlet 旨在处理对象。
对象是结构化信息，不仅仅是屏幕上出现的字符串。 命令输出会始终包含你在需要时可使用的额外信息。

如果以前使用过文本处理工具来处理数据，那么在 PowerShell 中使用时，会发现它们的行为有所不同。 在大多数情况下，不需要文本或文本处理工具来提取特定信息。 可以使用标准 PowerShell 对象语法直接访问数据的各部分。

## <a name="the-command-family-is-extensible"></a>命令系列是可扩展的

接口（如 cmd.exe  ）不提供可直接扩展内置命令集的方法。 可以创建在 cmd.exe  中运行的外部命令行工具。 但这些外部工具不包含服务，例如帮助集成。  cmd.exe 不会自动知道这些外部工具是否为有效命令。

PowerShell 中的本机命令称为 cmdlet  （读作 command-let）。 可以使用编译的代码或脚本创建自己的 cmdlet 模块和函数。 模块可以向 shell 添加 cmdlet 和提供程序。 PowerShell 还支持类似于 UNIX shell 脚本和 cmd.exe  批处理文件的脚本。

## <a name="powershell-handles-console-input-and-display"></a>PowerShell 处理控制台输入和显示

当你键入命令时，PowerShell 会始终直接处理命令行输入。 PowerShell 还会对你在屏幕上看到的输出进行格式设置。 这种差异非常重要，因为它减少了每个 cmdlet 必须完成的工作量。 它确保你始终可以使用任何 cmdlet 以相同的方式执行操作。 Cmdlet 开发人员无需编写代码来分析命令行参数或格式化输出。

传统的命令行工具有自己的用于请求和显示帮助的方案。 某些命令行工具使用 **/?** 来触发显示帮助内容；其他工具则使用 **-?** 、 **/H** 或 **//** 。 有些工具会在 GUI 窗口而不是在控制台显示区域显示帮助。 如果你使用的参数有误，该工具可能会忽略你键入的内容并自动开始执行任务。
由于 PowerShell 会自动分析并处理命令行，-?  参数始终意味着“显示关于此命令的帮助”。

> [!NOTE]
> 如果在 PowerShell 中运行图形应用程序，将随即打开该应用程序的窗口。
> PowerShell 仅会在处理你提供的命令行输入或返回到控制台窗口中的应用程序输出时才会进行干预。 它不会内在地影响应用程序的工作方式。

## <a name="powershell-uses-some-c-syntax"></a>PowerShell 使用某些 C# 语法

PowerShell 基于 .NET Framework 构建。 它与 C# 编程语言共享一些语法功能和关键字。 了解 PowerShell 后，就可以更轻松地了解 C#。 如果你已经熟悉了 C#，这种相似性就可以使 PowerShell 的学习变得容易许多。
